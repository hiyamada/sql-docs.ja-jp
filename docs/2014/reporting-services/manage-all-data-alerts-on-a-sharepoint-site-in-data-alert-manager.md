---
title: データ警告マネージャーで SharePoint サイトのすべてのデータ警告を管理する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- managing, alerts
- managing, data alerts
ms.assetid: 9c70b0f4-2db8-4c2e-acbf-96e2a55ddc48
caps.latest.revision: 12
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: ae29372fbed6f61e81c975dfd397a9190354eafc
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37313152"
---
# <a name="manage-all-data-alerts-on-a-sharepoint-site-in-data-alert-manager"></a>データ警告マネージャーで SharePoint サイトのすべてのデータ警告を管理する
  SharePoint 警告管理者は、サイト ユーザーによって作成されたデータ警告の一覧と、警告に関する情報を表示できます。 また、警告管理者は警告を削除することもできます。 次の図に、警告管理者がデータ警告マネージャー内で使用できる機能を示します。  
  
 ![SharePoint サイト管理者用の警告マネージャー](media/rs-alertmanagersite.gif "SharePoint サイト管理者用の警告マネージャー")  
  
### <a name="to-view-a-list-of-alerts-created-by-a-site-user"></a>サイト ユーザーが作成した警告の一覧を表示するには  
  
1.  データ警告定義が保存されている SharePoint サイトに移動します。  
  
2.  ホーム ページで、 **[サイトの操作]** をクリックします。  
  
3.  一覧の一番下までスクロールし、 **[サイトの設定]** をクリックします。  
  
4.  **[Reporting Services]** で、 **[データ警告の管理]** をクリックします。  
  
5.  **[ユーザー用の警告の表示]** の一覧で下矢印をクリックし、警告を表示するユーザーを選択します。  
  
6.  **[レポート用の警告の表示]** の一覧の横にある下矢印をクリックして、表示する特定の警告を選択するか、 **[すべて表示]** をクリックして、選択したユーザーによって作成されたすべての警告を表示します。  
  
     テーブルに、名前、レポート名、データ警告の作成者の名前、データ警告が送信された回数、データ警告定義が最後に変更された時刻、およびデータ警告の状態が一覧表示されます。 データ警告の生成や送信ができない場合は、エラーに関する情報が状態列に含まれているので、これを利用して問題のトラブルシューティングを行います。  
  
### <a name="to-delete-an-alert-definition"></a>警告の定義を削除するには  
  
-   削除するデータ警告を右クリックして、 **[削除]** をクリックします。  
  
    > [!NOTE]  
    >  警告を削除すると、それ以降、警告メッセージは送信されません。 ただし、警告データベースを照会すると、警告の定義がまだ存在している場合があります。 警告サービスではスケジュールに基づいてクリーンアップが実行され、警告の定義は次回のクリーンアップで完全に削除されます。 既定のクリーンアップ間隔は 20 分です。 クリーンアップ間隔は設定可能です。 詳細については、「 [Reporting Services のデータ警告](../ssms/agent/alerts.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [警告管理者用のデータ警告マネージャー](../../2014/reporting-services/data-alert-manager-for-alerting-administrators.md)   
 [Reporting Services のデータ警告](../ssms/agent/alerts.md)  
  
  