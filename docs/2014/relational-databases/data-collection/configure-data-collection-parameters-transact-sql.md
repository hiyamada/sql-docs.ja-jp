---
title: データ コレクションのパラメーターの構成 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- data collection [SQL Server]
ms.assetid: 850905b6-35d2-4ed1-ab51-de64daa832b2
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0261adbe86f1320984b4c56790835cf8cfd492cb
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48099922"
---
# <a name="configure-data-collection-parameters-transact-sql"></a>データ コレクションのパラメーターの構成 (Transact-SQL)
  カスタム コレクション セットを作成する前に、データ コレクションのパラメーターを構成しておく必要があります。 これには、データ コレクターで用意されているストアド プロシージャを使用します。 この作業には、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] のクエリ エディターを使用した次の手順の実行も含まれます。  
  
> [!NOTE]  
>  データ コレクションのパラメーターは一度構成するだけです。 構成後に作成した追加のコレクション セットには、すべてこれらのパラメーターが使用されます。  
  
### <a name="configure-data-collection-parameters"></a>データ コレクションのパラメーターの構成  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、カスタム コレクション セットを作成するデータベースに接続します。  
  
2.  クエリ エディターで、次のステートメントを実行します。  
  
    ```tsql  
    USE msdb;  
    EXEC sp_syscollector_set_warehouse_instance_name N'INSTANCE_NAME';-- where instance name is the name of the SQL Server instance  
    EXEC sp_syscollector_set_warehouse_database_name N'MDW';  
    EXEC sp_syscollector_set_cache_directory N'D:\tempdata';  
    ```  
  
## <a name="see-also"></a>参照  
 [データ コレクション](data-collection.md)   
 [データ コレクター ストアド プロシージャ &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql)  
  
  
