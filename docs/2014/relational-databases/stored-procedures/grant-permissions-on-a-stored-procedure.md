---
title: ストアド プロシージャに対する権限の許可 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- stored procedures [SQL Server], permissions
ms.assetid: a7d15816-a788-4099-ad91-dc4b26618299
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 79abbfe8d9c3fd8d88c883e5fbbdb198f9de4e1d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48223892"
---
# <a name="grant-permissions-on-a-stored-procedure"></a>ストアド プロシージャに対する権限の許可
  このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、ストアド プロシージャに対する権限を許可する方法について説明します。 権限は、データベース内の既存のユーザー、データベース ロール、またはアプリケーション ロールに許可することができます。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
     [Security](#Security)  
  
-   **ストアド プロシージャに対する権限を許可するために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> 作業を開始する準備  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、システム プロシージャやシステム関数に対する権限を許可することはできません。 代わりに、 [GRANT (オブジェクト権限の許可)](/sql/t-sql/statements/grant-object-permissions-transact-sql) を使用してください。  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> Permissions  
 権限の許可者 (または AS オプションで指定されたプリンシパル) は、GRANT OPTION によって与えられた権限を保持しているか、権限が暗黙的に与えられる上位の権限を保持している必要があります。 プロシージャが属しているスキーマに対する ALTER 権限、またはプロシージャに対する CONTROL 権限が必要です。 詳細については、「 [GRANT (オブジェクトの権限の許可) &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-object-permissions-transact-sql)を使用して、ストアド プロシージャに対する権限を許可する方法について説明します。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-grant-permissions-on-a-stored-procedure"></a>ストアド プロシージャに対して権限を許可するには  
  
1.  オブジェクト エクスプローラーで、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] に接続し、そのインスタンスを展開します。  
  
2.  **[データベース]** を展開し、プロシージャが属するデータベースを展開し、 **[プログラミング]** を展開します。  
  
3.  **[ストアド プロシージャ]** を展開し、権限を許可するプロシージャを右クリックして、 **[プロパティ]** をクリックします。  
  
4.  **[ストアド プロシージャのプロパティ]** で、 **[権限]** ページを選択します。  
  
5.  ユーザー、データベース ロール、またはアプリケーション ロールに権限を許可するには、 **[検索]** をクリックします。  
  
6.  **[ユーザーまたはロールの選択]** で、 **[オブジェクトの種類]** をクリックして目的のユーザーやロールを追加または削除します。  
  
7.  **[参照]** をクリックしてユーザーまたはロールの一覧を表示します。 権限を許可するユーザーまたはロールを選択します。  
  
8.  **[明示的な権限]** グリッドで、指定したユーザーまたはロールに許可する権限を選択します。 すべてのアクセス許可の説明については、「[権限 &#40;データベース エンジン&#41;](../security/permissions-database-engine.md) 」を参照してください。  
  
 **[許可]** を選択すると、指定した権限が与えられます。 **[許可の有無]** を選択すると、指定した権限をさらに他のプリンシパルにも許可できるようになります。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### <a name="to-grant-permissions-on-a-stored-procedure"></a>ストアド プロシージャに対して権限を許可するには  
  
1.  [!INCLUDE[ssDE](../../../includes/ssde-md.md)]に接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。 この例では、ストアド プロシージャ `EXECUTE` に対する `HumanResources.uspUpdateEmployeeHireInfo` 権限を、アプリケーション ロール `Recruiting11`に対して許可します。  
  
```tsql  
USE AdventureWorks2012;   
GRANT EXECUTE ON OBJECT::HumanResources.uspUpdateEmployeeHireInfo  
    TO Recruiting11;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sys.fn_builtin_permissions &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql)   
 [GRANT (オブジェクトの権限の許可) &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-object-permissions-transact-sql)   
 [ストアド プロシージャの作成](../stored-procedures/create-a-stored-procedure.md)   
 [ストアド プロシージャの変更](modify-a-stored-procedure.md)   
 [ストアド プロシージャの削除](../stored-procedures/delete-a-stored-procedure.md)   
 [ストアド プロシージャの名前の変更](rename-a-stored-procedure.md)  
  
  
