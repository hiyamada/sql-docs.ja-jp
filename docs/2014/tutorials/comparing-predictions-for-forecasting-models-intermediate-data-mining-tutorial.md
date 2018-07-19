---
title: 予測 (中級者向けデータ マイニング チュートリアル) をモデルの予測との比較 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ead8a1fe-60d8-4017-8fb8-6fe32168e46d
caps.latest.revision: 28
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a8ff27b38e2268ead42a1238250902b6ebf9cf18
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37165775"
---
# <a name="comparing-predictions-for-forecasting-models-intermediate-data-mining-tutorial"></a>予測モデルの予測の比較 (中級者向けデータ マイニング チュートリアル)
  このチュートリアルのこれまでの手順では、複数の時系列モデルを作成しました。  
  
-   個々のモデルと地域のデータのみに基づく地域とモデルの組み合わせごとの予測  
  
-   更新したデータに基づく地域ごとの予測  
  
-   集計データに基づく全世界におけるすべてのモデルの予測  
  
-   集計モデルに基づく北米地域の M200 モデルの予測  
  
 時系列予測の機能をまとめるため、変更を検討し、データを拡張または置換するオプションの使用が予測結果に与えた影響を確認します。  
  
 [EXTEND_MODEL_CASES](#bkmk_EXTEND)  
  
 [REPLACE_MODEL_CASES](#bkmk_REPLACE)  
  
##  <a name="bkmk_EXTEND"></a> データを追加した後、元の結果の結果を比較します。  
 太平洋地域の M200 製品ラインのデータだけを見て、新しいデータでのモデルの更新による結果への影響を調べます。 元のデータ系列は 2004 年 6 月に終了し、7 月、8 月、9 月の新しいデータを取得したことに注意してください。  
  
-   最初の列は、追加された新しいデータを示します。  
  
-   2 番目の列は、元のデータ系列に基づく 7 月以降の予測を示しています。  
  
-   3 番目の列は、拡張したデータに基づく予測を示しています。  
  
|**M200 Pacific**|更新された実売上データ|データを追加する前の予測|拡張された予測|  
|----------------------|-----------------------------|------------------------------------|-------------------------|  
|7-25-2008|**65**|32|**65**|  
|8-25-2008|**54**|37|**54**|  
|9-25-2008|**61**|32|**61**|  
|10-25-2008|データなし|36|32|  
|11-25-2008|データなし|31|41|  
|12-25-2008|データなし|34|32|  
  
 拡張データを使用した予測 (ここでは太字で表示) が実際のデータ ポイントを正確に繰り返していることがわかります。 この繰り返しは、意図的なものです。 予測クエリは、使用する実データ ポイントがある限りは実際の値を返し、新しい実際のデータ ポイントをすべて使用した後でのみ新しい予測値を出力します。  
  
 一般に、アルゴリズムでは、モデル データの開始からのデータより、新しいデータでの変更に、より大きい重みを設定します。 しかし、このケースでは、新しい売上の値は前の期間に対して 20 ～ 30% だけの増加を示しているので、予測される売上にはわずかな上昇しかなく、その後の売上予測は再度下降して、新しいデータの前の数か月の傾向と同じようになっています。  
  
##  <a name="bkmk_REPLACE"></a> 元とクロス予測の結果の比較  
 元のマイニング モデルでは、地域と製品ラインの間に大きな差が見られました。 たとえば、M200 モデルの売上は非常に強い一方で、T1000 モデルの売上はすべての地域でかなり低くなっています。 また、一部の系列には十分なデータがありませんでした。 系列は不規則であり、開始位置が異なることを意味しました。  
  
 ![M200 および T1000 の数量を予測するシリーズ](../../2014/tutorials/media/6series-defaultforecasting.gif "M200 および T1000 の数量を予測するシリーズ")  
  
 元のデータ セットではなく世界的な売上に基づく汎用モデルに基づく予測を行うと、どのように変化したでしょうか。 情報が失われたり予測が偏ったりしていないことを確認するには、結果をテーブルに保存し、予測のテーブルを履歴データのテーブルに結合して、履歴データと予測の 2 セットをグラフ化します。  
  
 次の図は、ただ 1 つの製品ライン M200 に基づいています。 グラフでは、初期のマイニング モデルによる予測と、集計されたマイニング モデルによる予測が比較されます。  
  
 ![予測を比較する Excel グラフ](../../2014/tutorials/media/m200-predictions-compared.gif "予測を比較する Excel グラフ")  
  
 この図からは、個々のデータ系列の変動を最小限に抑えると同時に、集計マイニング モデルによって値の全体的な範囲と傾向が保持されていることがわかります。  
  
## <a name="conclusion"></a>まとめ  
 予測に使用できる時系列モデルを作成してカスタマイズする方法について学習しました。  
  
 新しいデータを追加し、パラメーター EXTEND_MODEL_CASES を使用して予測を作成することによって、時系列モデルを再処理することなく更新する方法を学習しました。  
  
 REPLACE_MODEL_CASES パラメーターを使用し、異なるデータ系列にモデルを適用することによって、クロス予測に使用できるモデルを作成する方法について学習しました。  
  
## <a name="see-also"></a>参照  
 [中級者向けデータ マイニング チュートリアル&#40;Analysis Services - データ マイニング&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)   
 [タイム シリーズ モデルのクエリ例](../../2014/analysis-services/data-mining/time-series-model-query-examples.md)  
  
  