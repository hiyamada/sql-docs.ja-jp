---
title: DROP PARTITION FUNCTION (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP PARTITION FUNCTION
- DROP_PARTITION_FUNCTION_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- deleting partition functions
- DROP PARTITION FUNCTION statement
- partition functions [SQL Server], removing
- dropping partition functions
- removing partition functions
ms.assetid: a4bb055a-a538-4db9-a6fb-550d1eabfa18
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: dbf800653dd5cfeaef9eca4867770852fc6af374
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47766730"
---
# <a name="drop-partition-function-transact-sql"></a>DROP PARTITION FUNCTION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  現在のデータベースからパーティション関数を削除します。 パーティション関数の作成には CREATE PARTITION FUNCTION を使用し、変更には ALTER PARTITION FUNCTION を使用します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
DROP PARTITION FUNCTION partition_function_name [ ; ]  
```  
  
## <a name="arguments"></a>引数  
 *partition_function_name*  
 削除するパーティション関数の名前を指定します。  
  
## <a name="remarks"></a>Remarks  
 パーティション関数を削除できるのは、対象となるパーティション関数が、現在どのパーティション構成でも使用されていない場合のみです。 パーティション関数が、いずれかのパーティション構成で使用されている場合、DROP PARTITION FUNCTION ではエラーが返されます。  
  
## <a name="permissions"></a>アクセス許可  
 次のいずれかの権限が与えられていれば、DROP PARTITION FUNCTION を実行できます。  
  
-   ALTER ANY DATASPACE 権限。 この権限は、既定では **sysadmin** 固定サーバー ロール、 **db_owner** 固定データベース ロール、および **db_ddladmin** 固定データベース ロールのメンバーに与えられています。  
  
-   パーティション関数が作成されたデータベースでの CONTROL または ALTER 権限。  
  
-   パーティション関数が作成されたデータベースのサーバーでの CONTROL SERVER または ALTER ANY DATABASE 権限。  
  
## <a name="examples"></a>使用例  
 次の例では、パーティション関数 `myRangePF` が現在のデータベースで作成されたことを前提としています。  
  
```  
DROP PARTITION FUNCTION myRangePF;  
```  
  
## <a name="see-also"></a>参照  
 [CREATE PARTITION FUNCTION &#40;Transact-SQL&#41;](../../t-sql/statements/create-partition-function-transact-sql.md)   
 [ALTER PARTITION FUNCTION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-partition-function-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [sys.partition_functions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-partition-functions-transact-sql.md)   
 [sys.partition_parameters &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-partition-parameters-transact-sql.md)   
 [sys.partition_range_values &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-partition-range-values-transact-sql.md)   
 [sys.partitions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-partitions-transact-sql.md)   
 [sys.tables &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md)   
 [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)  
  
  
