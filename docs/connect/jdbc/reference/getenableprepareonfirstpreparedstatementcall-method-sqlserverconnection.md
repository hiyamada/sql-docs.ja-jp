---
title: getEnablePrepareOnFirstPreparedStatementCall メソッド (SQLServerConnection) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.getEnablePrepareOnFirstPreparedStatementCall
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7e5a03b231b86be065ff19dd0f0a6818ba560bf5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47671741"
---
# <a name="getenableprepareonfirstpreparedstatementcall-method-sqlserverconnection"></a>getEnablePrepareOnFirstPreparedStatementCall メソッド (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

 値を返します**enablePrepareOnFirstPreparedStatementCall**接続プロパティです。 最初の実行が sp_executesql を呼び出すし、準備は、false の場合は 2 番目の実行が発生した後、ステートメントが sp_prepexec を呼び出すし、準備されたステートメント ハンドルを実際に設定します。 次の実行は sp_execute を呼び出します。 これによって準備されたステートメントで sp_unprepare の必要性閉じる場合は、ステートメントは 1 回だけ実行します。 このオプションの既定値は、呼び出し元 setDefaultEnablePrepareOnFirstPreparedStatementCall() で変更できます。

## <a name="syntax"></a>構文  
  
```  
  
public boolean getEnablePrepareOnFirstPreparedStatementCall()  
```  

## <a name="return-value"></a>戻り値
 A**ブール**の値を格納している**enablePrepareOnFirstPreparedStatementCall**接続プロパティです。

## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Remarks  
 このメソッドは、JDBC driver 6.4 から利用できるとは。
 
## <a name="see-also"></a>参照  
 [SQLServerConnection のメンバー](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection クラス](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
