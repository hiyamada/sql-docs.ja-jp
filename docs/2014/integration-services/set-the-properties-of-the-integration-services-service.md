---
title: Integration Services サービスのプロパティを設定 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services service, configuring
- Integration Services service, properties
ms.assetid: 3a8ad546-0f58-4b31-ab56-58d6313b1098
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 04568c9e0a22f0f7e6335f96908d62582f0a4d62
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48228652"
---
# <a name="set-the-properties-of-the-integration-services-service"></a>Integration Services サービスのプロパティを設定する
    
> [!IMPORTANT]  
>  このトピックでは、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージを管理するための Windows サービスである [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスについて説明します。 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] では、以前のリリースの [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] との互換性を維持するために、このサービスをサポートしています。 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]以降では、Integration Services サーバー上のパッケージなどのオブジェクトを管理できます。  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスは、 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]でパッケージを管理および監視します。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]を初めてインストールするときに、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスが起動され、スタートアップの種類が自動に設定されます。  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスをインストールしたら、SQL Server 構成マネージャーまたはサービス MMC スナップインを使用してサービスのプロパティを設定できます。  
  
 パッケージを格納および管理する場所など、サービスのその他の重要な機能を構成するには、サービスの構成ファイルを変更する必要があります。 詳細については、「[Integration Services サービスの構成 (SSIS サービス)](service/integration-services-service-ssis-service.md)」を参照してください。  
  
### <a name="to-set-properties-of-the-integration-services-service-by-using-sql-server-configuration-manager"></a>SQL Server 構成マネージャーを使用して Integration Services サービスのプロパティを設定するには  
  
1.  **[スタート]** ボタンをクリックし、 **[すべてのプログラム]**、 **[Microsoft SQL Server]**、 **[構成ツール]** の順にポイントして、 **[SQL Server 構成マネージャー]** をクリックします。  
  
2.  **[SQL Server 構成マネージャー]** スナップインで、サービスの一覧から **[SQL Server Integration Services]** を探します。次に、 **[SQL Server Integration Services]** を右クリックし、 **[プロパティ]** をクリックします。  
  
3.  **[SQL Server Integration Services のプロパティ]** ダイアログ ボックスでは、次の操作を行うことができます。  
  
    -   **[ログオン]** タブをクリックして、アカウント名などのログオン情報を表示します。  
  
    -   **[サービス]** タブをクリックして、ホスト コンピューター名などのサービスに関する情報を表示し、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスの開始モードを指定します。  
  
        > [!NOTE]  
        >  **[詳細設定]** タブに、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスに関する情報は表示されません。  
  
4.  **[OK]** をクリックします。  
  
5.  **[ファイル]** メニューの **[終了]** をクリックして **[SQL Server 構成マネージャー]** スナップインを終了します。  
  
### <a name="to-set-properties-of-the-integration-services-service-by-using-services"></a>[サービス] を使用して Integration Services サービスのプロパティを設定するには  
  
1.  **[コントロール パネル]** で、クラシック表示を使用している場合は **[管理ツール]**、カテゴリの表示を使用している場合は **[パフォーマンスとメンテナンス]** をクリックしてから **[管理ツール]** をクリックします。  
  
2.  **[サービス]** をクリックします。  
  
3.  **[サービス]** スナップインで、サービスの一覧から **[SQL Server Integration Services]** を探します。 **[SQL Server Integration Services]** を右クリックし、 **[プロパティ]** をクリックします。  
  
4.  **[SQL Server Integration Services のプロパティ]** ダイアログ ボックスでは、次の操作を行うことができます。  
  
    -   **[全般]** タブをクリックします。サービスを有効にするには、[スタートアップの種類] で [手動] または [自動] を選択します。 サービスを無効にするには、 **[スタートアップの種類]** ボックスで [無効] を選択します。 [無効] を選択しても、実行中のサービスは停止されません。  
  
         サービスが既に有効になっている場合は、 **[停止]** をクリックしてサービスを停止したり、 **[開始]** をクリックしてサービスを開始したりできます。  
  
    -   **[ログオン]** タブをクリックして、ログオン情報を表示または編集します。  
  
    -   **[復旧]** タブをクリックして、サービスが失敗した場合のコンピューターの既定の応答を表示します。 これらのオプションは、環境に合わせて変更できます。  
  
    -   **[依存関係]** タブをクリックして、依存サービスの一覧を表示します。 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスは、依存関係を持ちません。  
  
5.  **[OK]** をクリックします。  
  
6.  [スタートアップの種類] で [手動] または [自動] を選択している場合は、必要に応じて、 **[SQL Server Integration Services]** を右クリックし、 **[開始]、[停止]、または [再起動]** をクリックできます。  
  
7.  **[ファイル]** メニューの **[終了]** をクリックして **[サービス]** スナップインを終了します。  
  
## <a name="see-also"></a>参照  
 [Integration Services サービスを管理する](../../2014/integration-services/manage-the-integration-services-service.md)  
  
  
