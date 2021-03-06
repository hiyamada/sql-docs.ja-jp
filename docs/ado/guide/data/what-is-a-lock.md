---
title: ロックとは | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- cursors [ADO], locking
- locks [ADO], about locking
ms.assetid: f8989555-28c6-4c17-9bf8-7f44a8a5c407
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 981b2b5dc1f76d879b18e5569e7fb70dbece1538
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47813080"
---
# <a name="what-is-a-lock"></a>ロックとは
ロックは、DBMS が、マルチ ユーザー環境での行にアクセスを制限するプロセスです。 行または列の排他的ロックされると、他のユーザーは、ロックが解放されるまで、ロックされているデータへのアクセスには許可されていません。 これにより、2 人のユーザーが、行の同じ列を同時に更新できません。  
  
 ロックは、リソースの観点からは非常にコストがおよび、データの整合性を保持するために必要な場合にのみ使用する必要があります。 数百または数千のユーザーと 1 秒ごとのレコードにアクセスするデータベースの —、インターネットに接続されているデータベースなど、不要なロックが直ちにアプリケーションのパフォーマンスの低下を招きます。  
  
 どのデータ ソースおよび ADO カーソル ライブラリ、この同時実行を適切なロックのオプションを選択して管理を制御できます。  
  
 設定、 **LockType**プロパティを開く前に、**レコード セット**を開くときに、プロバイダーのロックの種類を使用する必要がありますを指定します。 開くときに使用されているロックの種類を取得するプロパティを読み取る**Recordset**オブジェクト。  
  
 プロバイダーが、すべてのロックの種類をサポートしていません。 プロバイダーをサポートして、要求された場合**LockType**設定すると、別の種類のロックで置き換えられます。 使用可能な実際のロック機能を決定する、**レコード セット**オブジェクトを使用して、[サポート](../../../ado/reference/ado-api/supports-method.md)メソッド**adUpdate**と**adUpdateBatch**.  
  
 **AdLockPessimistic**場合、設定がサポートされていません、 [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md)プロパティに設定されて**adUseClient します。** サポートされていない値が設定されている場合は、エラーは発生しません。サポートされている最も近い**LockType**が使用されます。  
  
 **LockType**プロパティが読み取り/書き込み時に、**レコード セット**が開いているときは、終了、および読み取り専用です。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [ロックの種類](../../../ado/guide/data/types-of-locks.md)
