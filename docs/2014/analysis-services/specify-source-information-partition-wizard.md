---
title: ソース情報 (パーティション ウィザード) を指定します |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.asvs.partitionwizard.specifydsvandfacttables.f1
ms.assetid: b6c13587-c690-45d9-af90-b3d652afc55b
caps.latest.revision: 20
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c6f60f8470c45e8dbc97de12d7a13b19bea9becb
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37310452"
---
# <a name="specify-source-information-partition-wizard"></a>[基になる情報の指定] (パーティション ウィザード)
  **[基になる情報の指定]** ページを使用すると、パーティションを作成するメジャー グループと、パーティションのデータ ソース ビューとフィルター テーブルを選択できます。  
  
> [!CAUTION]  
>  他のパーティションによって使用される **[使用できるテーブル]** 内のテーブルを指定する場合は、 **[行の制限]** ページ内でクエリを指定するか、キューブ内でリスクの複製データを指定する必要があります。  
  
## <a name="options"></a>および  
 **メジャー グループ**  
 このパーティションのメジャー グループを選択します。  
  
 **Look in**  
 このパーティションのソース テーブルを含む、データ ソースまたはデータ ソース ビューを選択します。 メジャー グループによって使用されるデータ ソース ビューが既定で選択されます。  
  
 **テーブルをフィルター処理します。**  
 **[使用できるテーブル]** に表示されるテーブルを、テーブル名で制限するために使用する文字列を入力します。  
  
 **テーブルを検索します。**  
 **[使用できるテーブル]** 内のテーブルの一覧を更新します。文字列が **[フィルター テーブル]** で指定された場合は、さらに一覧を制限します。  
  
 **使用可能なテーブル**  
 テーブルを選択し、パーティションのソース テーブルとして使用します。 **パーティション ウィザード** により、 **[使用できるテーブル]** で選択したテーブルごとに 1 つのパーティションが作成されます。  
  
 **[フィルター テーブル]** でフィルターが指定されていない場合は、 **[検索対象]** で指定されているデータ ソースまたはデータ ソース ビューで、 **[メジャー グループ]** で指定されているメジャー グループが使用するファクト テーブルと同じ構造を持つデータ ソースまたはデータ ソース ビュー内のすべてのテーブルが、このオプションによって一覧表示されます。  
  
 **[フィルター テーブル]** でフィルターが指定されている場合は、以前の条件に一致するテーブル名に対するフィルターを比較することによってさらにリストが制限されます。 **[フィルター テーブル]** で指定された文字列を含むテーブルのみが表示されます。  
  
> [!NOTE]  
>  複数のテーブルが選択されている場合は、 **[行の制限]** ページは表示されず、選択したテーブルから作成されるパーティションに対して、行を制限することはできません。 パーティションごとに行を制限するには、パーティションを作成するテーブルごとにパーティション ウィザードを 1 回実行します。  
  
## <a name="see-also"></a>参照  
 [パーティション&#40;Analysis Services - 多次元データ&#41;](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md)  
  
  