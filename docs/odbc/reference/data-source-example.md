---
title: データ ソースの例 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], examples
ms.assetid: cbf15f32-0550-4c74-8088-8f7ac3855469
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 69cc3a0d32c12c71b3909bda23dea93417475f2a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47847631"
---
# <a name="data-source-example"></a>データ ソースの例
Microsoft® Windows NT® Server または Windows 2000 Server、Microsoft Windows NT のワークステーションと Windows 2000 Professional、または Microsoft Windows® 95/98、マシンのデータを実行するコンピューターでは、基になる情報がレジストリに格納されます。 によって、どのレジストリ キー情報が格納されている、データ ソースと呼ばれます、*ユーザー データ ソース*または*システム データ ソース*します。 ユーザー データ ソースは、HKEY_CURRENT_USER キーに格納され、現在のユーザーにのみ使用します。 システム データ ソースは、HKEY_LOCAL_MACHINE キーの下では保存され、1 台のコンピューターの 1 つ以上のユーザーが使用することができます。 また、システム全体のサービスは、コンピューターにユーザーがログインしていない場合でも、データ ソースへのアクセスを獲得しによっても使用できます。 ユーザーおよびシステム データ ソースの詳細については、次を参照してください。 [SQLManageDataSources](../../odbc/reference/syntax/sqlmanagedatasources.md)します。  
  
 ユーザーが次の 3 つのユーザー データ ソースを持っているとします Oracle DBMS では; を使用して、担当者およびインベントリ。給与支払、Microsoft SQL Server DBMS を使用します。 データ ソースのレジストリ値は次のようになります。  
  
```  
HKEY_CURRENT_USER  
SOFTWARE  
          ODBC  
               Odbc.ini  
                    ODBC Data Sources  
                    Personnel : REG_SZ : Oracle  
                    Inventory : REG_SZ : Oracle  
                    Payroll : REG_SZ : SQL Server  
```  
  
 あり、給与データ ソースのレジストリ値があります。  
  
```  
HKEY_CURRENT_USER  
     SOFTWARE  
          ODBC  
               Odbc.ini  
                    Payroll  
                         Driver : REG_SZ : C:\WINDOWS\SYSTEM\Sqlsrvr.dll  
                         Description : REG_SZ : Payroll database  
                         Server : REG_SZ : PYRLL1  
                         FastConnectOption : REG_SZ : No                          UseProcForPrepare : REG_SZ : Yes  
                         OEMTOANSI : REG_SZ : No  
                         LastUser : REG_SZ : smithjo  
                         Database : REG_SZ : Payroll  
                         Language : REG_SZ :  
```
