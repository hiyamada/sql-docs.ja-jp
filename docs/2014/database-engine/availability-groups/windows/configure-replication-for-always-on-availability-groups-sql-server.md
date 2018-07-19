---
title: AlwaysOn 可用性グループ用のレプリケーションの構成 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], interoperability
- replication [SQL Server], AlwaysOn Availability Groups
ms.assetid: 4e001426-5ae0-4876-85ef-088d6e3fb61c
caps.latest.revision: 14
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a57ba4393c23920b98a407176de51034715a54c6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37229602"
---
# <a name="configure-replication-for-always-on-availability-groups-sql-server"></a>AlwaysOn 可用性グループ用のレプリケーションの構成 (SQL Server)
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] でのレプリケーションおよび AlwaysOn 可用性グループの構成には、7 つのステップが必要です。 各ステップの詳細については、以下のセクションで説明します。  
  

  
##  <a name="step1"></a> 1.データベースのパブリケーションとサブスクリプションを構成する  
 **ディストリビューターの構成**  
  
 ディストリビューターは、パブリッシング データベースが属している (またはこれから属する) 可用性グループの現在の (または目的の) レプリカのホストにはしないでください。  
  
1.  ディストリビューター側のディストリビューションを構成します。 ストアド プロシージャを使用して構成する場合は、`sp_adddistributor` を実行します。 *@password* パラメーターを使用して、リモート パブリッシャーからディストリビューターに接続するときに使用するパスワードを指定します。 このパスワードは、各リモート パブリッシャーでリモート ディストリビューターを設定するときにも必要になります。  
  
    ```  
    USE master;  
    GO  
    EXEC sys.sp_adddistributor  
        @distributor = 'MyDistributor',  
        @password = '**Strong password for distributor**';  
    ```  
  
2.  ディストリビューター側のディストリビューション データベースを作成します。 ストアド プロシージャを使用して構成する場合は、`sp_adddistributiondb` を実行します。  
  
    ```  
    USE master;  
    GO  
    EXEC sys.sp_adddistributiondb  
        @database = 'distribution',  
        @security_mode = 1;  
    ```  
  
3.  リモート パブリッシャーを構成します。 ストアド プロシージャを使用してディストリビューターを構成する場合は、`sp_adddistpublisher` を実行します。 *@security_mode* パラメーターを使用して、レプリケーション エージェントから実行されるパブリッシャーの検証ストアド プロシージャを現在のプライマリに接続する方法を指定します。 1 に設定すると、現在のプライマリへの接続に Windows 認証が使用されます。 0 に設定すると、指定した [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] @login *@login* @password *@password* 認証が使用されます。 検証ストアド プロシージャをセカンダリ レプリカに正常に接続するには、各レプリカで有効なログインとパスワードを指定する必要があります。  
  
    > [!NOTE]  
    >  変更されたレプリケーション エージェントをディストリビューター以外のコンピューターで実行する場合、プライマリへの接続に Windows 認証を使用するには、レプリカのホスト コンピューター間の通信に使用する Kerberos 認証を構成する必要があります。 現在のプライマリへの接続に [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ログインを使用する場合は、Kerberos 認証は必要ありません。  
  
    ```  
    USE master;  
    GO  
    EXEC sys.sp_adddistpublisher  
        @publisher = 'AGPrimaryReplicaHost',  
        @distribution_db = 'distribution',  
        @working_directory = '\\MyReplShare\WorkingDir',  
        @login = 'MyPubLogin',  
        @password = '**Strong password for publisher**';  
    ```  
  
 詳細については、「[sp_adddistpublisher &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql)」を参照してください。  
  
 **元のパブリッシャーでのパブリッシャーの構成**  
  
1.  リモート ディストリビューションを構成します。 実行の場合は、パブリッシャーを構成するストアド プロシージャを使用、`sp_adddistributor`します。 同じ値を指定*@password*とき`sp_adddistrbutor`が実行された、ディストリビューターでディストリビューションを設定します。  
  
    ```  
    exec sys.sp_adddistributor  
        @distributor = 'MyDistributor',  
        @password = 'MyDistPass'  
    ```  
  
2.  データベースでレプリケーションを有効にします。 実行の場合は、パブリッシャーを構成するストアド プロシージャを使用、`sp_replicationdboption`します。 データベースに対してトランザクション レプリケーションとマージ レプリケーションの両方を構成する場合は、それぞれを有効にする必要があります。  
  
    ```  
    USE master;  
    GO  
    EXEC sys.sp_replicationdboption  
        @dbname = 'MyDBName',  
        @optname = 'publish',  
        @value = 'true';  
  
    EXEC sys.sp_replicationdboption  
        @dbname = 'MyDBName',  
        @optname = 'merge publish',  
        @value = 'true';  
    ```  
  
3.  レプリケーションのパブリケーション、アーティクル、およびサブスクリプションを作成します。 レプリケーションを構成する方法の詳細については、「データとデータベース オブジェクトのパブリッシュ」を参照してください。  
  
##  <a name="step2"></a> 2.AlwaysOn 可用性グループを構成する  
 目的のプライマリで、メンバー データベースとしてパブリッシュされている (またはパブリッシュする) データベースを含む可用性グループを作成します。 可用性グループ ウィザードを使用する場合は、ウィザードで最初にセカンダリ レプリカ データベースを同期するか、バックアップと復元を使用して手動で初期化を実行するかを選択することができます。  
  
 現在のプライマリへの接続にレプリケーション エージェントで使用される可用性グループの DNS リスナーを作成します。 指定したリスナー名は、元のパブリッシャーとパブリッシュされたデータベースのペアに対してリダイレクトの対象として使用されます。 たとえば、DDL を使用して可用性グループを構成する場合は、次のコード例に従って、`MyAG` という名前の既存の可用性グループの可用性グループ リスナーを指定できます。  
  
```  
ALTER AVAILABILITY GROUP 'MyAG'   
    ADD LISTENER 'MyAGListenerName' (WITH IP (('10.120.19.155', '255.255.254.0')));  
```  
  
 詳細については、「[可用性グループの作成と構成 &#40;SQL Server&#41;](creation-and-configuration-of-availability-groups-sql-server.md)」を参照してください。  
  
##  <a name="step3"></a> 3.セカンダリ レプリカのすべてのホストでレプリケーションが構成されていることを確認する  
 セカンダリ レプリカの各ホストで、レプリケーションをサポートするように [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] が構成されていることを確認します。 レプリケーションがインストールされているかどうかを確認するには、セカンダリ レプリカの各ホストで次のクエリを実行します。  
  
```  
USE master;  
GO  
DECLARE @installed int;  
EXEC @installed = sys.sp_MS_replication_installed;  
SELECT @installed;  
```  
  
 元のパブリッシャーに *@installed* が 0 の場合、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インストールにレプリケーションを追加する必要があります。  
  
##  <a name="step4"></a> 4.セカンダリ レプリカのホストをレプリケーションのパブリッシャーとして構成する  
 セカンダリ レプリカはレプリケーションのパブリッシャーまたはリパブリッシャーとしては機能しませんが、フェールオーバー後にセカンダリで処理を引き継ぐようにレプリケーションを構成する必要があります。 ディストリビューターで、セカンダリ レプリカの各ホストのディストリビューションを構成します。 ディストリビューション データベースと作業ディレクトリは、元のパブリッシャーをディストリビューターに追加したときと同じものを指定します。 ストアド プロシージャを使用してディストリビューションを構成する場合は、`sp_adddistpublisher` を使用してリモート パブリッシャーをディストリビューターに関連付けます。 元のパブリッシャーに *@login* @password *@password* を使用した場合は、セカンダリ レプリカのホストをパブリッシャーとして追加する際に同じ値をそれぞれ指定します。  
  
```  
EXEC sys.sp_adddistpublisher  
    @publisher = 'AGSecondaryReplicaHost',  
    @distribution_db = 'distribution',  
    @working_directory = '\\MyReplShare\WorkingDir',  
    @login = 'MyPubLogin',  
    @password = '**Strong password for publisher**';  
```  
  
 セカンダリ レプリカの各ホストで、ディストリビューションを構成します。 リモート ディストリビューターには、元のパブリッシャーのディストリビューターを指定します。 同じパスワードを使用するときと`sp_adddistributor`ディストリビューターで最初に実行されました。 ディストリビューションの構成ストアド プロシージャを使用する場合、 *@password*パラメーターの`sp_adddistributor`パスワードを指定するために使用します。  
  
```  
EXEC sp_adddistributor   
    @distributor = 'MyDistributor',  
    @password = '**Strong password for distributor**';  
```  
  
 セカンダリ レプリカの各ホストで、データベースのパブリケーションのプッシュ サブスクライバーがリンク サーバーとして表示されることを確認します。 使用してリモート パブリッシャーを構成するには、ストアド プロシージャを使用されているが場合、`sp_addlinkedserver`にサブスクライバーを追加 (まだ存在しない場合)、パブリッシャーにリンク サーバーとして。  
  
```  
EXEC sys.sp_addlinkedserver   
    @server = 'MySubscriber';  
```  
  
##  <a name="step5"></a> 5.元のパブリッシャーを AG リスナー名にリダイレクトする  
 ディストリビューター側のディストリビューション データベースで、ストアド プロシージャ `sp_redirect_publisher` を実行して、元のパブリッシャーとパブリッシュされたデータベースを可用性グループの可用性グループ リスナー名に関連付けます。  
  
```  
USE distribution;  
GO  
EXEC sys.sp_redirect_publisher   
@original_publisher = 'MyPublisher',  
    @publisher_db = 'MyPublishedDB',  
    @redirected_publisher = 'MyAGListenerName';  
```  
  
##  <a name="step6"></a> 6.レプリケーションの検証ストアド プロシージャを実行して構成を確認する  
 ディストリビューター側のディストリビューション データベースで、ストアド プロシージャ `sp_validate_replica_hosts_as_publishers` を実行して、レプリカのすべてのホストが、パブリッシュされたデータベースのパブリッシャーとして機能するように構成されていることを確認します。  
  
```  
USE distribution;  
GO  
DECLARE @redirected_publisher sysname;  
EXEC sys.sp_validate_replica_hosts_as_publishers  
    @original_publisher = 'MyPublisher',  
    @publisher_db = 'MyPublishedDB',  
    @redirected_publisher = @redirected_publisher output;  
```  
  
 ストアド プロシージャ `sp_validate_replica_hosts_as_publishers` は、可用性グループ レプリカの各ホストで、可用性グループに関する情報をクエリするための十分な権限を持つログインから実行する必要があります。 異なり`sp_validate_redirected_publisher`、呼び出し元の資格情報を使用し、可用性グループ レプリカに接続する msdb.dbo.MSdistpublishers に保持されているログインを使用しません。  
  
> [!NOTE]  
>  `sp_validate_replica_hosts_as_publishers` 読み取りを読み取りアクセスを許可または必要としない、セカンダリ レプリカのホストの検証を指定する目的は、次のエラーで失敗します。  
>   
>  メッセージ 21899、レベル 11、状態 1、プロシージャ `sp_hadr_verify_subscribers_at_publisher`、行 109  
>   
>  元のパブリッシャー 'MyOriginalPublisher' のサブスクライバーの sysserver エントリがあるかどうかを判断するために、リダイレクトされたパブリッシャー 'MyReplicaHostName' で実行したクエリが、エラー '976'、エラー メッセージ 'エラー 976、レベル 14、状態 1、メッセージ: 対象になるデータベース 'MyPublishedDB' は可用性グループに参加しているため、現在クエリでアクセスできません。 データ移動が中断されているか、可用性レプリカの読み取りアクセスが有効になっていません。 このデータベースや可用性グループの他のデータベースへの読み取り専用アクセスを許可するには、グループの 1 つ以上のセカンダリ可用性レプリカへの読み取りアクセスを有効にします。  詳細については、次を参照してください。、`ALTER AVAILABILITY GROUP`ステートメント[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]オンライン ブックの「します。 '。  
>   
>  レプリカ ホスト 'MyReplicaHostName' について、1 つまたは複数のパブリッシャー検証エラーが発生しました。  
  
 これは想定されている動作です。 これらのセカンダリ レプリカのホストでは、sysserver エントリをホストで直接クエリして、サブスクライバー サーバーのエントリがあるかどうかを確認する必要があります。  
  
##  <a name="step7"></a> 7.元のパブリッシャーをレプリケーション モニターに追加する  
 それぞれの可用性グループ レプリカで、元のパブリッシャーをレプリケーション モニターに追加します。  
  
##  <a name="RelatedTasks"></a> 関連タスク  
 **レプリケーション**  
  
-   [AlwaysOn パブリケーション データベースのメンテナンス&#40;SQL Server&#41;](maintaining-an-always-on-publication-database-sql-server.md)  
  
-   [レプリケーション、変更の追跡、変更データ キャプチャ、および AlwaysOn 可用性グループ&#40;SQL Server&#41;](replicate-track-change-data-capture-always-on-availability.md)  
  
-   [管理 &#40;レプリケーション&#41;](../../../relational-databases/replication/administration/administration-replication.md)  
  
 **可用性グループを作成して構成するには**  
  
-   [可用性グループ ウィザードの使用 &#40;SQL Server Management Studio&#41;](use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [[新しい可用性グループ] ダイアログ ボックスの使用 &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [可用性グループの作成 &#40;Transact-SQL&#41;](create-an-availability-group-transact-sql.md)  
  
-   [可用性グループの作成 &#40;SQL Server PowerShell&#41;](../../../powershell/sql-server-powershell.md)  
  
-   [可用性レプリカを追加または変更する場合のエンドポイント URL の指定 &#40;SQL Server&#41;](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
-   [データベース ミラーリング エンドポイントの AlwaysOn 可用性グループの作成&#40;SQL Server PowerShell&#41;](database-mirroring-always-on-availability-groups-powershell.md)  
  
-   [可用性グループへのセカンダリ レプリカの参加 &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [可用性グループに対するセカンダリ データベースの手動準備 &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [可用性グループへのセカンダリ データベースの参加 &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [可用性グループ リスナーの作成または構成 &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)  
  
## <a name="see-also"></a>参照  
 [前提条件、制限事項、および AlwaysOn 可用性グループの推奨事項&#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)   
 [AlwaysOn 可用性グループの概要&#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [AlwaysOn 可用性グループ: 相互運用性 (SQL Server)](always-on-availability-groups-interoperability-sql-server.md)   
 [SQL Server のレプリケーション](../../../relational-databases/replication/sql-server-replication.md)  
  
  