---
title: パブリッシングおよびディストリビューションの構成 | Microsoft Docs
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], distribution
- distribution configuration [SQL Server replication]
- publishing [SQL Server replication], configuring
ms.assetid: 3cfc8966-833e-42fa-80cb-09175d1feed7
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c93dda12a8a100f78db3568620afdffacc1258bf
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48087041"
---
# <a name="configure-publishing-and-distribution"></a>パブリッシングおよびディストリビューションの構成
  このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、 [!INCLUDE[tsql](../../includes/tsql-md.md)]、またはレプリケーション管理オブジェクト (RMO) を使用して、パブリッシングとディストリビューションを構成する方法について説明します。  
  
  
##  <a name="BeforeYouBegin"></a> 作業を開始する準備  
  
###  <a name="Security"></a> セキュリティ  
 詳細については、「[セキュリティで保護された配置 &#40;レプリケーション&#41;](security/secure-deployment-replication.md)」を参照してください。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 パブリケーションの新規作成ウィザードまたはディストリビューションの構成ウィザードを使用して、ディストリビューションを構成します。 ディストリビューターを構成したら、**[ディストリビューターのプロパティ - \<ディストリビューター>]** ダイアログ ボックスでプロパティを表示および変更します。 **db_owner** 固定データベース ロールのメンバーがパブリケーションを作成できるようにディストリビューターを構成する場合、またはパブリッシャーではないリモート ディストリビューターを構成する必要がある場合は、ディストリビューションの構成ウィザードを使用します。  
  
#### <a name="to-configure-distribution"></a>ディストリビューションを構成するには  
  
1.  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、ディストリビューターとなるサーバーに接続し (多くの場合、パブリッシャーとディストリビューターは同じサーバーです)、サーバー ノードを展開します。  
  
2.  **[レプリケーション]** フォルダーを右クリックし、 **[ディストリビューションの構成]** をクリックします。  
  
3.  ディストリビューションの構成ウィザードに従って、次の操作を実行します。  
  
    -   ディストリビューターを選択します。 ローカル ディストリビューターを使用するには、**['\<ServerName' を独自のディストリビューターとする (SQL Server はディストリビューション データベースとログを作成します)]** を選択します。 リモート ディストリビューターを使用するには、 **[以下のサーバーをディストリビューターとして使用する]** を選択し、サーバーを選択します。 このサーバーは既にディストリビューターとして構成されている必要があり、パブリッシャーではこのディストリビューターを使用できるようになっている必要があります。 詳細については、「[ディストリビューターでのリモート パブリッシャーの有効化 &#40;SQL Server Management Studio&#41;](enable-a-remote-publisher-at-a-distributor-sql-server-management-studio.md)」を参照してください。  
  
         リモート ディストリビューターを選択した場合、パブリッシャーからディストリビューターへの接続に対して、 **[管理パスワード]** ページでパスワードを入力する必要があります。 このパスワードは、リモート ディストリビューターでパブリッシャーを有効にしたときに指定したパスワードと一致する必要があります。  
  
    -   ローカル ディストリビューターに対してルート スナップショット フォルダーを指定します。 スナップショット フォルダーは、共有として指定したディレクトリです。このフォルダーの読み取りと書き込みをするエージェントには、このフォルダーへのアクセスを可能にする十分な権限が必要です。 このディストリビューターを使用する各パブリッシャーによって、ルート フォルダーの下にフォルダーが作成され、各パブリケーションでは、パブリッシャー フォルダーの下にスナップショット ファイルを格納するフォルダーが作成されます。 フォルダーの適切なセキュリティ保護の詳細については、「[スナップショット フォルダーのセキュリティ保護](security/secure-the-snapshot-folder.md)」を参照してください。  
  
    -   ローカル ディストリビューターに対してディストリビューション データベースを指定します。 ディストリビューション データベースには、すべての種類のレプリケーションのメタデータと履歴データ、およびトランザクション レプリケーションに対するトランザクションが格納されます。  
  
    -   必要に応じて、その他のパブリッシャーでディストリビューターを使用できるようにします。 その他のパブリッシャーがディストリビューターを使用できるようになっている場合は、これらのパブリッシャーからディストリビューターへの接続に対して、 **[ディストリビューター パスワード]** ページでパスワードを入力する必要があります。  
  
    -   必要に応じて、構成の設定のスクリプトを作成します。 詳しくは、「 [Scripting Replication](scripting-replication.md)」をご覧ください。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 レプリケーションのパブリッシングおよびディストリビューションは、レプリケーションのストアド プロシージャを使用してプログラムから構成できます。  
  
#### <a name="to-configure-publishing-using-a-local-distributor"></a>ローカル ディストリビューターを使用してパブリッシングを構成するには  
  
1.  [sp_get_distributor &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-get-distributor-transact-sql) を実行して、サーバーが既にディストリビューターとして構成されているかどうかを調べます。  
  
    -   結果セットの **installed** の値が **0** の場合は、ディストリビューターの master データベースで [sp_adddistributor &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-adddistributor-transact-sql) を実行します。  
  
    -   結果セットの **distribution db installed** の値が **0** の場合は、ディストリビューターの master データベースで [sp_adddistributiondb &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-adddistributiondb-transact-sql) を実行します。 このとき、 **@database**」を参照してください。 必要に応じて、トランザクションの最大保有期間 ( **@max_distretention** ) および履歴保有期間 ( **@history_retention**」を参照してください。 新しいデータベースを作成する場合は、必要なデータベース プロパティのパラメーターを指定します。  
  
2.  ディストリビューター (兼パブリッシャー) で、[sp_adddistpublisher &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql) を実行します。このとき、**@working_directory** には、既定のスナップショット フォルダーとして使用する UNC 共有を指定します。  
  
3.  パブリッシャーで、[sp_replicationdboption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql) を実行します。 パブリッシュするデータベースを指定**@dbname**、レプリケーションの種類 **@optname**の値と`true`の**@value**.  
  
#### <a name="to-configure-publishing-using-a-remote-distributor"></a>リモート ディストリビューターを使用してパブリッシングを構成するには  
  
1.  [sp_get_distributor &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-get-distributor-transact-sql) を実行して、サーバーが既にディストリビューターとして構成されているかどうかを調べます。  
  
    -   結果セットの **installed** の値が **0** の場合は、ディストリビューターの master データベースで [sp_adddistributor &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-adddistributor-transact-sql) を実行します。 **@password** には強力なパスワードを指定してください。 この **distributor_admin** アカウントのパスワードは、パブリッシャーがディストリビューターに接続する際に使用されます。  
  
    -   結果セットの **distribution db installed** の値が **0** の場合は、ディストリビューターの master データベースで [sp_adddistributiondb &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-adddistributiondb-transact-sql) を実行します。 このとき、 **@database**」を参照してください。 必要に応じて、トランザクションの最大保有期間 ( **@max_distretention** ) および履歴保有期間 ( **@history_retention**」を参照してください。 新しいデータベースを作成する場合は、必要なデータベース プロパティのパラメーターを指定します。  
  
2.  ディストリビューターで、[sp_adddistpublisher &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql) を実行します。このとき、**@working_directory** には、既定のスナップショット フォルダーとして使用する UNC 共有を指定します。 ディストリビューターがパブリッシャーに接続する際に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用する場合、さらに **0** @value **@security_mode** を指定し、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] と **@login** に **@password**」を参照してください。  
  
3.  パブリッシャーの master データベースで [sp_adddistributor &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-adddistributor-transact-sql) を実行します。 **@password** には、手順 1. で使用した強力なパスワードを指定してください。 このパスワードは、パブリッシャーがディストリビューターに接続する際に使用されます。  
  
4.  パブリッシャーで、[sp_replicationdboption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql) を実行します。 このとき、 **@dbname**にはパブリッシュするデータベースを、 **@optname**にはレプリケーションの種類を、 **@value**」を参照してください。  
  
###  <a name="TsqlExample"></a> 例 (Transact-SQL)  
 次の例に、パブリッシングおよびディストリビューションをプログラムから構成する方法を示します。 この例では、パブリッシャーおよびローカル ディストリビューターとして構成するサーバーの名前をスクリプト変数を使って指定しています。 レプリケーションのパブリッシングおよびディストリビューションは、レプリケーションのストアド プロシージャを使用してプログラムから構成できます。  
  
 [!code-sql[HowTo#AddDistPub](../../snippets/tsql/SQL15/replication/howto/tsql/adddistpub.sql#adddistpub)]  
  
##  <a name="RMOProcedure"></a> レプリケーション管理オブジェクト (RMO) の使用  
  
#### <a name="to-configure-publishing-and-distribution-on-a-single-server"></a>パブリッシングおよびディストリビューションを単一サーバーで構成するには  
  
1.  <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスを使用して、サーバーへの接続を作成します。  
  
2.  <xref:Microsoft.SqlServer.Replication.ReplicationServer> クラスのインスタンスを作成します。 手順 1. の <xref:Microsoft.SqlServer.Management.Common.ServerConnection> を渡します。  
  
3.  <xref:Microsoft.SqlServer.Replication.DistributionDatabase> クラスのインスタンスを作成します。  
  
4.  <xref:Microsoft.SqlServer.Replication.DistributionDatabase.Name%2A> プロパティにデータベース名を設定し、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティに手順 1. の <xref:Microsoft.SqlServer.Management.Common.ServerConnection> を設定します。  
  
5.  <xref:Microsoft.SqlServer.Replication.ReplicationServer.InstallDistributor%2A> メソッドを呼び出してディストリビューターをインストールします。 手順 3. の <xref:Microsoft.SqlServer.Replication.DistributionDatabase> オブジェクトを渡します。  
  
6.  <xref:Microsoft.SqlServer.Replication.DistributionPublisher> クラスのインスタンスを作成します。  
  
7.  次の <xref:Microsoft.SqlServer.Replication.DistributionPublisher>のプロパティを設定します。  
  
    -   <xref:Microsoft.SqlServer.Replication.DistributionPublisher.Name%2A> - パブリッシャーの名前。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> - 手順 1. の <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 。  
  
    -   <xref:Microsoft.SqlServer.Replication.DistributionPublisher.DistributionDatabase%2A> - 手順 5. で作成したデータベースの名前。  
  
    -   <xref:Microsoft.SqlServer.Replication.DistributionPublisher.WorkingDirectory%2A> - スナップショット ファイルのアクセスに使用する共有。  
  
    -   <xref:Microsoft.SqlServer.Replication.DistributionPublisher.PublisherSecurity%2A> - パブリッシャーに接続するときに使用されるセキュリティ モード。 <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.WindowsAuthentication%2A> が推奨されます。  
  
8.  <xref:Microsoft.SqlServer.Replication.DistributionPublisher.Create%2A> メソッドを呼び出します。  
  
#### <a name="to-configure-publishing-and-distribution-using-a-remote-distributor"></a>リモート ディストリビューターを使用してパブリッシングおよびディストリビューションを構成するには  
  
1.  <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスを使用して、リモート ディストリビューター サーバーへの接続を作成します。  
  
2.  <xref:Microsoft.SqlServer.Replication.ReplicationServer> クラスのインスタンスを作成します。 手順 1. の <xref:Microsoft.SqlServer.Management.Common.ServerConnection> を渡します。  
  
3.  <xref:Microsoft.SqlServer.Replication.DistributionDatabase> クラスのインスタンスを作成します。  
  
4.  <xref:Microsoft.SqlServer.Replication.DistributionDatabase.Name%2A> プロパティにデータベース名を設定し、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティに手順 1. の <xref:Microsoft.SqlServer.Management.Common.ServerConnection> を設定します。  
  
5.  <xref:Microsoft.SqlServer.Replication.ReplicationServer.InstallDistributor%2A> メソッドを呼び出してディストリビューターをインストールします。 安全なパスワード (パブリッシャーがリモート ディストリビューターへの接続時に使用) および手順 3. の <xref:Microsoft.SqlServer.Replication.DistributionDatabase> オブジェクトを指定します。 詳細については、「[ディストリビューターのセキュリティ保護](security/secure-the-distributor.md)」を参照してください。  
  
    > [!IMPORTANT]  
    >  可能であれば、実行時、ユーザーに対してセキュリティ資格情報の入力を要求します。 資格情報を保存する必要がある場合は、 [Windows .NET&#xA0;Framework に用意されている](http://go.microsoft.com/fwlink/?LinkId=34733) 暗号化サービス [!INCLUDE[msCoName](../../includes/msconame-md.md)] を使用します。  
  
6.  <xref:Microsoft.SqlServer.Replication.DistributionPublisher> クラスのインスタンスを作成します。  
  
7.  次の <xref:Microsoft.SqlServer.Replication.DistributionPublisher>のプロパティを設定します。  
  
    -   <xref:Microsoft.SqlServer.Replication.DistributionPublisher.Name%2A> - ローカル パブリッシャー サーバーの名前。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> - 手順 1. の <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 。  
  
    -   <xref:Microsoft.SqlServer.Replication.DistributionPublisher.DistributionDatabase%2A> - 手順 5. で作成したデータベースの名前。  
  
    -   <xref:Microsoft.SqlServer.Replication.DistributionPublisher.WorkingDirectory%2A> - スナップショット ファイルのアクセスに使用する共有。  
  
    -   <xref:Microsoft.SqlServer.Replication.DistributionPublisher.PublisherSecurity%2A> - パブリッシャーに接続するときに使用されるセキュリティ モード。 <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.WindowsAuthentication%2A> が推奨されます。  
  
8.  <xref:Microsoft.SqlServer.Replication.DistributionPublisher.Create%2A> メソッドを呼び出します。  
  
9. <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスを使用して、ローカル パブリッシャー サーバーへの接続を作成します。  
  
10. <xref:Microsoft.SqlServer.Replication.ReplicationServer> クラスのインスタンスを作成します。 手順 9. の <xref:Microsoft.SqlServer.Management.Common.ServerConnection> を渡します。  
  
11. <xref:Microsoft.SqlServer.Replication.ReplicationServer.InstallDistributor%2A> メソッドを呼び出します。 リモート ディストリビューターの名前、および手順 5. で指定したリモート ディストリビューターのパスワードを渡します。  
  
    > [!IMPORTANT]  
    >  可能であれば、実行時、ユーザーに対してセキュリティ資格情報の入力を要求します。 資格情報を保存する必要がある場合は、Windows .NET Framework に用意されている [暗号化サービス](http://go.microsoft.com/fwlink/?LinkId=34733) を使用します。  
  
###  <a name="PShellExample"></a> 例 (RMO)  
 レプリケーション管理オブジェクト (RMO) を使用することで、プログラムによってレプリケーション パブリッシングおよびディストリビューションを構成できます。  
  
 [!code-csharp[HowTo#rmo_AddDistPub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_adddistpub)]  
  
 [!code-vb[HowTo#rmo_vb_AddDistPub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_adddistpub)]  
  
## <a name="see-also"></a>参照  
 [View and Modify Distributor and Publisher Properties (ディストリビューターとパブリッシャーのプロパティの表示および変更)](view-and-modify-distributor-and-publisher-properties.md)   
 [Replication System Stored Procedures Concepts](concepts/replication-system-stored-procedures-concepts.md)   
 [[ディストリビューションの構成]](configure-distribution.md)   
 [Replication Management Objects Concepts](concepts/replication-management-objects-concepts.md)   
 [AlwaysOn 可用性グループのレプリケーションを構成する&#40;SQL Server&#41;](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md) 
  
  
