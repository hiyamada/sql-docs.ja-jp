---
title: カスタム インデックス (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
ms.assetid: c57bf8b8-55a6-4b6c-9adb-91b5f4f1ee3c
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 5d52335f4b80a4cd1ff06e9fe8084d46a8d0d089
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47855000"
---
# <a name="custom-index-master-data-services"></a>カスタム インデックス (マスター データ サービス)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  カスタム インデックスは、1 つの属性 (シングル インデックス) または属性の一覧 (複合インデックス) の非クラスター化インデックスを 1 つのエンティティとして作成します。 通常、インデックスによりクエリ処理のパフォーマンスが向上します。 SQL Server インデックスの詳細については、「 [インデックス](../relational-databases/indexes/indexes.md)」を参照してください。  
  
## <a name="type-of-indexes"></a>インデックスの種類  
 各エンティティには次のタイプのカスタム インデックスを複数作成することができます。  
  
-   [一意インデックス]  
  
-   一意ではないインデックス  
  
 一意インデックスにより、インデックス付き列に重複する値が含まれていないことが保証されます。 複合の一意インデックスの場合、このインデックスにより、選択した属性の一覧にある値のそれぞれの組み合わせが一意であることが保証されます。 選択した属性に対して重複する値が存在する場合、一意インデックスを作成できません。  
  
## <a name="rules"></a>ルール  
 次の規則は、一意と非一意の両方のカスタム インデックスに適用されます。  
  
-   カスタム インデックスを作成するには、少なくとも 1 つの属性を選択してください。  
  
-   同じ属性の一覧が含まれ、別のインデックスの一意性フラグが設定されているインデックスを保存しようとすると、インデックスを保存できません。 エラーがスローされます。  
  
    > [!NOTE]  
    >  MDS は自動的に特定の属性 (DBA や Code など) のインデックスを作成します。 つまり、これらの属性のいずれかを含み、その他の属性が含まれていない別のインデックスは作成できません。  
  
-   少なくとも 1 つの異なる属性が他のインデックスに含まれている場合、属性を複数のカスタム インデックスに含めることができます それ以外の場合、インデックスは同じです。  
  
-   多数の属性、またはサイズの大きな属性を含むインデックスを作成し、選択した属性の合計サイズが最大インデックス キー サイズ (900 バイト) を超える場合、インデックスを保存できません。  
  
-   カスタム インデックスはファイル属性を除くリーフ メンバー属性に対して作成できます。  
  
-   カスタム インデックスに含まれている属性を削除する場合は、次が適用されます。  
  
    -   1 つの属性のみに対してインデックスを作成すると (シングル インデックス)、属性とインデックスの両方が削除されます。  
  
    -   複数の属性に対してインデックスを作成すると (複合インデックス)、インデックスを編集するまで属性を削除できません。  
  
-   カスタム インデックスに含まれている属性の種類は変更できません。  
  
## <a name="related-tasks"></a>Related Tasks  
  
|タスクの説明|トピック|  
|----------------------|-----------|  
|インデックスを作成する|[インデックスを作成する (マスター データ サービス)](../master-data-services/create-an-index-master-data-services.md)|  
|インデックスの編集と削除|[インデックスの編集と削除 (マスター データ サービス)](../master-data-services/edit-and-delete-an-index-master-data-services.md)|  
  
  
