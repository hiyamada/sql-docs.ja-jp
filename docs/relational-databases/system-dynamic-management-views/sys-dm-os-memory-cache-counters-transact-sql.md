---
title: sys.dm_os_memory_cache_counters (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 08/18/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_os_memory_cache_counters_TSQL
- dm_os_memory_cache_counters_TSQL
- sys.dm_os_memory_cache_counters
- dm_os_memory_cache_counters
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_memory_cache_counters dynamic management view
ms.assetid: ca7bd036-d661-4c17-b00a-e1a975bd8932
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 19beaafe3e73265eb12f825190ee8aafcdf59897
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47701420"
---
# <a name="sysdmosmemorycachecounters-transact-sql"></a>sys.dm_os_memory_cache_counters (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で、キャッシュのヘルスのスナップショットを返します。 **sys.dm_os_memory_cache_counters**キャッシュ エントリに割り当てられているキャッシュ エントリに関する実行時の情報、使用、およびメモリのソースを提供します。  
  
> **注:** これから[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、名前を使用して、 **sys.dm_pdw_nodes_os_memory_cache_counters**します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**cache_address**|**varbinary(8)**|特定のキャッシュに関連付けられているカウンターのアドレス (主キー) を示します。 NULL 値は許可されません。|  
|**name**|**nvarchar (256)**|キャッシュの名前を指定します。 NULL 値は許可されません。|  
|**type**|**nvarchar(60)**|このエントリに関連付けられているキャッシュの型を示します。 NULL 値は許可されません。|  
|**single_pages_kb**|**bigint**|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<br /><br /> 割り当てられている単一ページ メモリの量 (KB 単位)。 これは、単一ページ アロケーターを使用することによって割り当てられたメモリの量です。 キャッシュ用にバッファー プールから直接取得された 8 KB ページを表します。 NULL 値は許可されません。|  
|**pages_kb**|**bigint**|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> キャッシュ内で割り当てられているメモリの量を KB 単位で指定します。 NULL 値は許可されません。|  
|**multi_pages_kb**|**bigint**|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<br /><br /> 割り当てられている複数ページ メモリの量 (KB 単位)。 メモリ ノードの複数ページ アロケーターを使用することによって割り当てられるメモリの量です。 このメモリは、バッファー プール外に割り当てられ、メモリ ノードの仮想アロケーターを利用します。 NULL 値は許可されません。|  
|**pages_in_use_kb**|**bigint**|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> キャッシュ内で割り当てられ、使用されているメモリの量を KB 単位で指定します。 NULL 値が許可されます。  `USERSTORE_<*>` 型のオブジェクトの値は追跡されません。  これらについては NULL が報告されます。|  
|**single_pages_in_use_kb**|**bigint**|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<br /><br /> 使用されている単一ページ メモリの量 (KB 単位)。 NULL 値が許可されます。 この情報は userstore _ の型のオブジェクトに対しては追跡されません\<* >、これらの値は NULL になります。|  
|**multi_pages_in_use_kb**|**bigint**|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<br /><br /> 使用されている複数ページ メモリの量 (KB 単位)。 NULL 値は許可されます。 この情報は userstore _ の型のオブジェクトに対しては追跡されません\<* >、これらの値は NULL になります。|  
|**entries_count**|**bigint**|キャッシュ内のエントリの数を指定します。 NULL 値は許可されません。|  
|**entries_in_use_count**|**bigint**|使用されているキャッシュ内のエントリの数を指定します。 NULL 値は許可されません。|  
|**pdw_node_id**|**int**|**適用対象**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> この配布であるノードの識別子。|  
  
## <a name="permissions"></a>アクセス許可 

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]、必要があります`VIEW SERVER STATE`権限。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]が必要です、`VIEW DATABASE STATE`データベースの権限。   

## <a name="see-also"></a>関連項目  
  [SQL Server オペレーティング システム関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


