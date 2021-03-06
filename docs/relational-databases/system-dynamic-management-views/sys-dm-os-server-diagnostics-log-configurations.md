---
title: sys.dm_os_server_diagnostics_log_configurations | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_os_server_diagnostics_log_configurations
- sys.dm_os_server_diagnostics_log_configurations_TSQL
- dm_os_server_diagnostics_log_configurations
- dm_os_server_diagnostics_log_configurations_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dm_os_server_diagnostics_log_configurations
- sys.dm_os_server_diagnostics_log_configurations
ms.assetid: c09ea433-d283-4f83-af69-d458aad59217
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 9a3e03058b42e256991a525a70d6c1fe57e061e8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47752790"
---
# <a name="sysdmosserverdiagnosticslogconfigurations"></a>sys.dm_os_server_diagnostics_log_configurations
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  1 つの行の現在の構成を返します、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]フェールオーバー クラスター診断ログ。 診断ログのオンまたはオフ、ログ ファイルの場所、数、およびサイズは、これらのプロパティ設定によって決まります。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|is_enabled|**bit**|ログ記録がオンとオフのどちらであるかを示します。<br /><br /> 1 = 診断ログはオンです。<br /><br /> 0 = 診断ログはオフです。|  
|max_size|**int**|各診断ログの最大サイズ (MB 単位)。 既定値は 100 MB です。|  
|max_files|**int**|新しい診断ログとして再利用されるまでにコンピューターに格納できる診断ログ ファイルの最大数。|  
|path|**nvarchar(260)**|診断ログの場所を示すパス。 既定の場所は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フェールオーバー クラスター インスタンスのインストール フォルダー内の \<\MSSQL\Log> です。|  
  
## <a name="permissions"></a>アクセス許可  
 SQL Server フェールオーバー クラスター インスタンスに対する VIEW SERVER STATE 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、sys.dm_os_server_diagnostics_log_configurations を使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フェールオーバー診断ログのプロパティ設定を返します。  
  
```  
SELECT <list of columns>  
FROM sys.dm_os_server_diagnostics_log_configurations;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
|IS_ENABLED|PATH|MAX_SIZE|MAX_FILES|  
|-----------------|----------|---------------|----------------|  
|1|\<C:\Program files \microsoft SQL server \mssql13\mssql\log >|10|10|  
  
## <a name="see-also"></a>参照  
 [フェールオーバー クラスター インスタンスの診断ログを表示して読む方法](../../sql-server/failover-clusters/windows/view-and-read-failover-cluster-instance-diagnostics-log.md)  
  
  
