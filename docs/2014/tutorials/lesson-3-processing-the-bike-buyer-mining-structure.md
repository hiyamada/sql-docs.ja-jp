---
title: 'レッスン 3: Bike Buyer マイニング構造の処理 |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: e748c2cd-339d-4e82-82f1-be2d0fc41b61
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 77c49a7b1616d1a54c652efee05ff1e827d07caf
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48053832"
---
# <a name="lesson-3-processing-the-bike-buyer-mining-structure"></a>レッスン 3: Bike Buyer マイニング構造の処理
  このレッスンでは、ステートメントとから vTargetMail ビューに INSERT を使用します、[!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)]マイニング構造とマイニング モデルで作成したを処理するサンプル データベース[レッスン 1:BikeBuyerマイニング構造を作成します。](../../2014/tutorials/lesson-1-creating-the-bike-buyer-mining-structure.md)と[レッスン 2: Bike Buyer マイニング構造にマイニング モデルの追加](../../2014/tutorials/lesson-2-adding-mining-models-to-the-bike-buyer-mining-structure.md)します。  
  
 マイニング構造の処理では、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] でソース データが読み込まれ、マイニング モデルをサポートする構造が構築されます。 マイニング モデルの処理では、マイニング構造で定義されたデータが、選択したデータ マイニング アルゴリズムを介して受け渡されます。 このアルゴリズムでは傾向とパターンが検索され、結果の情報がマイニング モデルに保存されます。 したがって、マイニング モデルには、実際のソース データではなく、アルゴリズムで検出された情報が含まれます。 マイニング モデルの処理の詳細については、次を参照してください。[処理の要件と考慮事項&#40;データ マイニング&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)します。  
  
 マイニング構造の再処理は、構造列またはソース データを変更した場合に必要です。 処理済みのマイニング構造にマイニング モデルを追加する場合は、INSERT INTO MINING MODEL ステートメントを使用して新しいマイニング モデルをトレーニングできます。  
  
## <a name="train-structure-template"></a>構造テンプレートのトレーニング  
 マイニング構造とその関連マイニング モデルをトレーニングするために使用して、 [INSERT INTO &#40;DMX&#41; ](/sql/dmx/insert-into-dmx)ステートメント。 ステートメント内のコードは、次の部分に分けることができます。  
  
-   マイニング構造の指定  
  
-   マイニング構造の列の一覧  
  
-   トレーニング データの定義  
  
 INSERT INTO ステートメントの汎用例を次に示します。  
  
```  
INSERT INTO MINING STRUCTURE [<mining structure name>]  
(  
   <mining structure columns>  
)  
OPENQUERY([<datasource>],'<SELECT statement>')  
```  
  
 コードの最初の行では、トレーニングするマイニング構造を指定します。  
  
```  
INSERT INTO MINING STRUCTURE [<mining structure name>]  
```  
  
 コードの次の行では、マイニング構造で定義される列を指定します。 ここではマイニング構造の各列を指定する必要があります。各列はソース クエリ データ内の列にマップされている必要があります。  
  
```  
(  
   <mining structure columns>  
)  
```  
  
 コードの最後の行では、マイニング構造のトレーニングに使用するデータを定義します。  
  
```  
OPENQUERY([<datasource>],'<SELECT statement>')  
```  
  
 このレッスンでは、`OPENQUERY` を使用してソース データを定義します。 ソース クエリを定義するその他の方法については、次を参照してください。 [&#60;ソース データ クエリ&#62;](/sql/dmx/source-data-query)します。  
  
## <a name="lesson-tasks"></a>このレッスンの作業  
 このレッスンでは、次のタスクを実行します。  
  
-   Bike Buyer マイニング構造の処理  
  
## <a name="processing-the-predictive-mining-structure"></a>予測マイニング構造の処理  
  
#### <a name="to-process-the-mining-structure-by-using-insert-into"></a>INSERT INTO を使用してマイニング構造を処理するには  
  
1.  **オブジェクト エクスプ ローラー**のインスタンスを右クリックして[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]、] をポイント**新しいクエリ**、] をクリックし、 **DMX**します。  
  
     クエリ エディターが開き、新しい空のクエリが表示されます。  
  
2.  上の INSERT INTO ステートメントの汎用例を空のクエリにコピーします。  
  
3.  次の部分を探します。  
  
    ```  
    [<mining structure name>]   
    ```  
  
     これを次の文字列に置き換えます。  
  
    ```  
    Bike Buyer  
    ```  
  
4.  次の部分を探します。  
  
    ```  
    <mining structure columns>  
    ```  
  
     これを次の文字列に置き換えます。  
  
    ```  
    [Customer Key],  
    [Age],  
    [Bike Buyer],  
    [Commute Distance],  
    [Education],  
    [Gender],  
    [House Owner Flag],  
    [Marital Status],  
    [Number Cars Owned],  
    [Number Children At Home],  
    [Occupation],  
    [Region],  
    [Total Children],  
    [Yearly Income]  
    ```  
  
5.  次の部分を探します。  
  
    ```  
    OPENQUERY([<datasource>],'<SELECT statement>')  
    ```  
  
     これを次の文字列に置き換えます。  
  
    ```  
    OPENQUERY([Adventure Works DW],  
       'SELECT CustomerKey, Age, BikeBuyer,  
             CommuteDistance,EnglishEducation,  
             Gender,HouseOwnerFlag,MaritalStatus,  
             NumberCarsOwned,NumberChildrenAtHome,   
             EnglishOccupation,Region,TotalChildren,  
             YearlyIncome   
        FROM dbo.vTargetMail')  
    ```  
  
     OPENQUERY ステートメントは、[!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] データ ソースを参照して、vTargetMail ビューにアクセスしています。 ビューには、マイニング モデルのトレーニングに使用されるソース データが含まれています。  
  
     最終的なステートメントは次のようになります。  
  
    ```  
    INSERT INTO MINING STRUCTURE [Bike Buyer]  
    (  
       [Customer Key],  
       [Age],  
       [Bike Buyer],  
       [Commute Distance],  
       [Education],  
       [Gender],  
       [House Owner Flag],  
       [Marital Status],  
       [Number Cars Owned],  
       [Number Children At Home],  
       [Occupation],  
       [Region],  
       [Total Children],  
       [Yearly Income]     
    )  
    OPENQUERY([Adventure Works DW],  
       'SELECT CustomerKey, Age, BikeBuyer,  
             CommuteDistance,EnglishEducation,  
             Gender,HouseOwnerFlag,MaritalStatus,  
             NumberCarsOwned,NumberChildrenAtHome,   
             EnglishOccupation,Region,TotalChildren,  
             YearlyIncome   
        FROM dbo.vTargetMail')  
    ```  
  
6.  **ファイル** メニューのをクリックして**付けて DMXQuery1.dmx を保存**します。  
  
7.  **付けて** ダイアログ ボックスで、適切なフォルダーを参照し、ファイル名前`Process Bike Buyer Structure.dmx`します。  
  
8.  ツールバーの**Execute**ボタンをクリックします。  
  
 次のレッスンでは、このレッスンでマイニング構造に追加したマイニング モデルの内容を調査します。  
  
## <a name="next-lesson"></a>次のレッスン  
 [レッスン 4: Bike Buyer マイニング モデルの参照](../../2014/tutorials/lesson-4-browsing-the-bike-buyer-mining-models.md)  
  
  
