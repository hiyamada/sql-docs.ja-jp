---
title: "position (java.sql.NClob, long) メソッド |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2354278-d128-4cf4-a170-22c05fcb763b
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 0be71ad3437edf9febc776f83b26953593f294f7
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="position-method-javasqlnclob-long"></a>position (java.sql.NClob, long) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  文字の位置を取得、指定した**NClob**オブジェクト*searchstr*にこれが表示されます**NClob**オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
long position(java.sql.NClob searchstr,  
              long start)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *searchstr*  
  
 検索対象の NClob オブジェクトです。  
  
 *開始*  
  
 検索を開始する位置です。最初の位置は 1 です。  
  
## <a name="return-value"></a>戻り値  
 部分文字列が現れる位置です。部分文字列がない場合は -1 が返されます。 最初の位置は 1 です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この位置メソッドは、位置、java.sql.NClob インターフェイスのメソッドでによって指定されます。  
  
## <a name="see-also"></a>参照  
 [方法 &#40; を配置します。SQLServerNClob &#41;](../../../connect/jdbc/reference/position-method-sqlservernclob.md)   
 [SQLServerNClob のメソッド](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [SQLServerNClob のメンバー](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [SQLServerNClob クラス](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  