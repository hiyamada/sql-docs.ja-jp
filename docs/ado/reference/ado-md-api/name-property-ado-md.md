---
title: "Name プロパティ (ADO MD) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Level::Name
- CubeDef::Name
- Member::Name
- Catalog::Name
- Dimension::Name
- Name
- Axis::Name
- Hierarchy::Name
helpviewer_keywords:
- Name property [ADO MD]
ms.assetid: 4a04380b-51dc-4aaf-8d25-123cdd589641
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8d898b2e478b9a5dfccb431d0d29088c9e8d9286
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="name-property-ado-md"></a>Name プロパティ (ADO MD)
オブジェクトの名前を示します。  
  
## <a name="return-values"></a>戻り値  
 返します、**文字列**は読み取り専用とします。  
  
## <a name="remarks"></a>解説  
 取得することができます、**名前**名で直接するまで、オブジェクトを参照できます、序数参照オブジェクトのプロパティです。 たとえば場合、 `cdf.CubeDefs(0).Name` "振りビデオ Store"が得られますこれを参照することができます[CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)として`cdf.CubeDefs("Bobs Video Store")`です。  
  
## <a name="applies-to"></a>適用対象  
  
||||  
|-|-|-|  
|[軸オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/axis-object-ado-md.md)|[カタログ オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/catalog-object-ado-md.md)|[CubeDef オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)|  
|[ディメンション オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)|[Hierarchy オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md)|[レベル オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/level-object-ado-md.md)|  
|[メンバー オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)|||  
  
## <a name="see-also"></a>参照  
 [カタログの例 (VB)](../../../ado/reference/ado-md-api/catalog-example-vb.md)   
 [Caption プロパティ (ADO MD)](../../../ado/reference/ado-md-api/caption-property-ado-md.md)   
 [Description プロパティ (ADO MD)](../../../ado/reference/ado-md-api/description-property-ado-md.md)   
 [UniqueName プロパティ (ADO MD)](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md)