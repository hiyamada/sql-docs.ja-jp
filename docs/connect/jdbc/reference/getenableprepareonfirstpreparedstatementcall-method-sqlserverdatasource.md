---
title: getEnablePrepareOnFirstPreparedStatementCall メソッド (SQLServerDataSource) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ''
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 721e19f1a4941cacfd18e04a14e6fa6d851cde60
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47667521"
---
# <a name="getenableprepareonfirstpreparedstatementcall-method-sqlserverdatasource"></a>getEnablePrepareOnFirstPreparedStatementCall メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  値を返します**enablePrepareOnFirstPreparedStatementCall**接続プロパティです。 この構成は、false を返した場合、準備されたステートメントの最初の実行が sp_executesql を呼び出すし、sp_prepexec を呼び出すし、準備されたステートメント ハンドルを実際にセットアップに 2 つ目の実行が発生すると、ステートメントを準備できません。 次の実行は sp_execute を呼び出します。 これによって準備されたステートメントで sp_unprepare の必要性閉じる場合は、ステートメントは 1 回だけ実行します。 
  
## <a name="syntax"></a>構文  
  
```
public boolean getEnablePrepareOnFirstPreparedStatementCall();  
```  
  
## <a name="return-value"></a>戻り値  
 返します、**ブール**の値、 **enablePrepareOnFirstPreparedStatementCall**接続プロパティです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Remarks  
 このメソッドは、JDBC driver 6.4 から利用できるとは。
 
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
