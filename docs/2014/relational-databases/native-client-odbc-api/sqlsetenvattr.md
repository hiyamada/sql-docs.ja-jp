---
title: SQLSetEnvAttr |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLSetEnvAttr function
ms.assetid: d4114571-feca-4330-b2e4-7bfd1050b812
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5bc8edc3a898223c49cdf79b1d1691898cc8cc28
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48168512"
---
# <a name="sqlsetenvattr"></a>SQLSetEnvAttr
  [ODBC プログラマ リファレンス](http://go.microsoft.com/fwlink/?LinkId=45250)ODBC ドライバーを解釈する方法を定義、 **SQLSetEnvAttr**属性の ODBC 2 に書かれたアプリケーションからの仕様 *。x*または ODBC 3 *。x* API。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーは、これらの規則に準拠します。  
  
 によって制御される属性の 1 つ**SQLSetEnvAttr**は使用するかどうかが接続プールします。 接続プールを使用した場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバー、 *DriverCompletion*いずれかで接続するときに、パラメーターを SQL_DRIVER_NOPROMPT に設定する必要があります[SQLDriverConnect](sqldriverconnect.md)または**SQLConnect**します。  
  
## <a name="see-also"></a>参照  
 [SQLSetEnvAttr 関数](http://go.microsoft.com/fwlink/?LinkId=59369)   
 [ODBC API 実装の詳細](odbc-api-implementation-details.md)  
  
  
