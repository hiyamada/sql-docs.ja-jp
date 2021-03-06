---
title: Item プロパティ (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Parameters::GetItem
- Indexes::GetItem
- Parameters::Item
- Tables::Item
- Procedures::Item
- Users::GetItem
- Tables::GetItem
- Procedures::GetItem
- Users::get_Item
- Users::Item
- Views::GetItem
- Groups::Item
- Groups::get_Item
- Columns::Item
- Indexes::Item
- Fields15::GetItem
- Columns::GetItem
- Fields::Item
- Indexes::get_Item
- Columns::get_Item
- Fields15::Item
- Views::get_Item
- Groups::GetItem
- Errors::get_Item
- Fields15::get_Item
- Tables::get_Item
- Views::Item
- Errors::GetItem
- Parameters::get_Item
- Errors::Item
- Procedures::get_Item
helpviewer_keywords:
- Item property [ADO]
ms.assetid: e11484bb-c5c7-42d8-9bb8-21572125d727
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 776a74422941118e2091c9240d14edbf8c1f0fec
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47655656"
---
# <a name="item-property-ado"></a>Item プロパティ (ADO)
名前または序数で、コレクションの特定のメンバーを示します。  
  
## <a name="syntax"></a>構文  
  
```  
Set object = collection.Item ( Index )  
```  
  
## <a name="return-value"></a>戻り値  
 オブジェクト参照を返します。  
  
## <a name="parameters"></a>パラメーター  
 *Index*  
 A**バリアント**名前またはコレクション内のオブジェクトの序数のいずれかに評価される式。  
  
## <a name="remarks"></a>コメント  
 使用して、**項目**コレクションに特定のオブジェクトを返すプロパティ。 場合**項目**に対応するコレクションでオブジェクトを検索することはできません、*インデックス*引数、エラーが発生します。 また、一部のコレクションが名前付きのオブジェクトをサポートしません。これらのコレクションの序数参照を使用する必要があります。  
  
 **項目**プロパティは、すべてのコレクションの既定のプロパティ。 そのため、次の構文形式を交換できます。  
  
```  
collection.Item (Index)  
collection (Index)  
```  
  
## <a name="applies-to"></a>適用対象  
  
||||  
|-|-|-|  
|[Axes コレクション (ADO MD)](../../../ado/reference/ado-md-api/axes-collection-ado-md.md)|[Columns コレクション (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)|[CubeDefs コレクション (ADO MD)](../../../ado/reference/ado-md-api/cubedefs-collection-ado-md.md)|  
|[Dimensions コレクション (ADO MD)](../../../ado/reference/ado-md-api/dimensions-collection-ado-md.md)|[Errors コレクション (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)|[Fields コレクション (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)|  
|[Groups コレクション (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)|[Hierarchies コレクション (ADO MD)](../../../ado/reference/ado-md-api/hierarchies-collection-ado-md.md)|[Indexes コレクション (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md)|  
|[Keys コレクション (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md)|[Levels コレクション (ADO MD)](../../../ado/reference/ado-md-api/levels-collection-ado-md.md)|[Members コレクション (ADO MD)](../../../ado/reference/ado-md-api/members-collection-ado-md.md)|  
|[Parameters コレクション (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)|[Positions コレクション (ADO MD)](../../../ado/reference/ado-md-api/positions-collection-ado-md.md)|[Procedures コレクション (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)|  
|[Properties コレクション (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)|[Tables コレクション (ADOX)](../../../ado/reference/adox-api/tables-collection-adox.md)|[Users コレクション (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)|  
|[Views コレクション (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)|||  
  
## <a name="see-also"></a>参照  
 [項目プロパティの例 (VB)](../../../ado/reference/ado-api/item-property-example-vb.md)   
 [Item プロパティの例 (VC++)](../../../ado/reference/ado-api/item-property-example-vc.md)   
