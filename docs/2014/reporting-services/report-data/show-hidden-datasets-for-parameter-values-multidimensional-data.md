---
title: 多次元データ (レポート ビルダーおよび SSRS) のパラメーター値の非表示のデータセットの表示 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: eb01c4ca-4fd6-4629-b595-f0d2565915df
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: b0d0682e33e72686abd41e03e7936c557db740b5
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48173112"
---
# <a name="show-hidden-datasets-for-parameter-values-for-multidimensional-data-report-builder-and-ssrs"></a>多次元データのパラメーター値の非表示データセットの表示 (レポート ビルダーおよび SSRS)
  既定ではレポート データ ペインに表示されない、自動的に生成されたデータセット (非表示のデータセット) がレポートに含まれる場合があります。 これらのデータセットは次のような場合に作成されます。  
  
-   多次元データベース用のクエリ デザイナーの中には、フィルターを適用するフィールドをクエリ ペインのフィルター領域で指定して、そのフィルターのクエリ パラメーターを作成するかどうかを選択できるものがあります。 そのような場合にパラメーターを作成するように選択すると、そのレポート パラメーターの有効な値を提供するレポート データセットが自動的に作成されます。  
  
-   多次元データベースに基づくクエリをインポートすると、非表示のデータセットもレポートに含まれる場合があります。  
  
 非表示のデータセットはウィザードからは使用できません。  
  
 レポート データ ペインで、レポートのすべてのデータセットを表示するビューを変更することができます。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-display-hidden-datasets"></a>非表示のデータセットを表示するには  
  
-   レポート データ ペインで、[データセット] フォルダーを右クリックし、 **[非表示データセットの表示]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [クエリ デザイナー &#40;レポート ビルダー&#41;](../query-designers-report-builder.md)   
 [Reporting Services クエリ デザイナー](../reporting-services-query-designers.md)   
 [レポート埋め込みデータセットと共有データセット &#40;レポート ビルダーおよび SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)   
 [レポートにデータを追加&#40;レポート ビルダーおよび SSRS&#41;](report-datasets-ssrs.md)  
  
  
