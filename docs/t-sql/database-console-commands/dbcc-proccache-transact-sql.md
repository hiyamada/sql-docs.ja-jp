---
title: DBCC PROCCACHE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/14/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DBCC PROCCACHE
- DBCC_PROCCACHE_TSQL
- PROCCACHE_TSQL
- PROCCACHE
dev_langs:
- TSQL
helpviewer_keywords:
- procedure cache [SQL Server]
- displaying procedure cache information
- DBCC PROCCACHE statement
ms.assetid: 7a4f9f8a-13ff-4bf2-ba29-c17012a23659
author: uc-msft
ms.author: umajay
manager: craigg
ms.openlocfilehash: 2d4580bb57680392c1e3901c2fd64b399c125736
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47741110"
---
# <a name="dbcc-proccache-transact-sql"></a>DBCC PROCCACHE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

テーブル フォーマット内のプロシージャ キャッシュに関する情報を表示します。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
DBCC PROCCACHE [ WITH NO_INFOMSGS ]  
```  
  
## <a name="arguments"></a>引数  
 のすべてのメンションを  
 オプションの指定を許可します。  
  
 NO_INFOMSGS  
 重大度レベル 0 ～ 10 のすべての情報メッセージを表示しないようにします。  
  
## <a name="remarks"></a>Remarks  
プロシージャ キャッシュを使用してコンパイル済みの実行プランをキャッシュし、バッチの実行速度を上げます。 プロシージャ キャッシュ内のエントリはバッチ レベルです。 プロシージャ キャッシュには、次のエントリが含まれます。
-   コンパイル済みプラン  
-   実行プラン  
-   代数ツリー  
-   拡張プロシージャ  
  
## <a name="result-sets"></a>結果セット  
次の表では、結果セットの列について説明します。
  
|列名|[説明]|  
|-----------------|-----------------|  
|**num proc buffs**|プロシージャ キャッシュ内のすべてのエントリで使用されるページの総数です。|  
|**num proc buffs used**|現在使用されているすべてのエントリで使用されるページの総数です。|  
|**num proc buffs active**|これは旧バージョンとの互換性のためにだけ用意されています。 現在使用されているすべてのエントリで使用されるページの総数です。|  
|**proc cache size**|プロシージャ キャッシュ内のエントリの総数です。|  
|**proc cache used**|現在使用されているエントリの総数です。|  
|**proc cache active**|これは旧バージョンとの互換性のためにだけ用意されています。 現在使用されているエントリの総数です。|  
  
## <a name="permissions"></a>アクセス許可  
**sysadmin** 固定サーバー ロールまたは **db_owner** 固定データベース ロールのメンバーシップが必要です。
  
## <a name="see-also"></a>参照  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)
  
  
