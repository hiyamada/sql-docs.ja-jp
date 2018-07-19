---
title: '[全般] プロパティ ページ、リソース (レポート マネージャー) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 23eed41b-283a-49df-a3aa-062dde8d6354
caps.latest.revision: 25
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 269cd82820bb8e07ec1ac66ccc8d3e8b8ceeb43a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37164185"
---
# <a name="general-properties-page-resources-report-manager"></a>[全般] プロパティ ページ、リソース (レポート マネージャー)
  リソースの [全般] プロパティ ページでは、リソースの名前変更、削除、移動、または置換を行うことができます。 リソースの追加またはプロパティの変更を行ったユーザーに関する情報が、ページ上部に表示されます。  
  
 このページを開くには、リソースを選択し、ページ上部の **[プロパティ]** タブをクリックします。  
  
## <a name="navigation"></a>ナビゲーション  
 ユーザー インターフェイス (UI) のこの場所に移動するには、次の手順に従います。  
  
###### <a name="to-open-the-general-properties-page-for-a-resource"></a>リソースの [全般] プロパティ ページを開くには  
  
1.  レポート マネージャーを開き、プロパティを表示または構成するリソースを探します。  
  
2.  リソースの上にマウス ポインターを移動し、下矢印をクリックします。  
  
3.  ドロップダウン メニューの **[管理]** をクリックします。 この操作により、リソースの [全般] プロパティ ページが開きます。  
  
## <a name="options"></a>および  
 **名前**  
 リソースの名前を指定します。 名前には、少なくとも 1 つの英数字が含まれている必要があります。 また、スペースおよびいくつかの記号を含めることもできます。 名前を指定するときに、; ? : @ & = +, $/* \< > |"または/名前を指定します。  
  
 **[説明]**  
 リソースの説明を入力します。 この説明は、リソースへのアクセス権を持っているユーザーの [コンテンツ] ページに表示されます。  
  
 **リスト ビューで非表示にします。**  
 このオプションをオンにすると、レポート マネージャーでリスト ビュー モードを使用しているユーザーにリソースを表示しません。 リスト ビュー モードは、レポート サーバー フォルダー階層を参照するときの既定のビュー形式です。 リスト ビューでは、アイテム名および説明がページに表示されます。 別の形式として詳細ビューがあります。 詳細ビューでは説明が省略されますが、そのアイテムに関するその他の情報は含まれます。 リスト ビューのアイテムは非表示にできますが、詳細ビューのアイテムは非表示にできません。 アイテムへのアクセスを制限する場合は、ロールの割り当てを作成する必要があります。  
  
 **型**  
 リソースの MIME の種類を指定します。 このプロパティは読み取り専用です。  
  
 **[適用]**  
 変更を保存する場合にクリックします。  
  
 **削除**  
 レポート サーバー データベースからリソースを削除する場合にクリックします。  
  
 **Move**  
 レポート サーバーのフォルダー階層内でリソースを再配置する場合にクリックします。 このボタンをクリックすると、アイテムの移動ページが表示され、フォルダーを参照して新しい場所を選択できます。  
  
 **[置換]**  
 クリックすると、ファイル共有のリソース ファイルの選択に使用する [リソースのインポート] ページが開きます。  
  
## <a name="see-also"></a>参照  
 [レポート マネージャー &#40;SSRS ネイティブ モード&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md)   
 [ページで、リソースを表示&#40;レポート マネージャー&#41;](../../2014/reporting-services/view-page-resources-report-manager.md)   
 [レポート マネージャー F1 ヘルプ](../../2014/reporting-services/report-manager-f1-help.md)   
 [[セキュリティのプロパティ] ページ、アイテム (レポート マネージャー)](../../2014/reporting-services/security-properties-page-items-report-manager.md)  
  
  