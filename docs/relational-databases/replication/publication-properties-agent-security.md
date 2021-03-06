---
title: '[パブリケーションのプロパティ]、[エージェント セキュリティ] | Microsoft Docs'
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.newpubwizard.pubproperties.agentsecurity.f1
ms.assetid: 03945aac-66f2-4370-b5d1-c1de694bc4c1
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: bb56972bd63a1fbd7cd265443b0db1ad86d439c5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47763000"
---
# <a name="publication-properties-agent-security"></a>[パブリケーションのプロパティ]、[エージェント セキュリティ]
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  **[パブリケーションのプロパティ]** ダイアログ ボックスの **[エージェント セキュリティ]** ページを使用すると、次のエージェントが実行されるアカウントの設定にアクセスし、レプリケーション トポロジのコンピューターへの接続を作成することができます。  
  
-   すべてのパブリケーションに対応する、スナップショット エージェント。  
  
-   すべてのトランザクション パブリケーションに対応する、ログ リーダー エージェント。 トランザクション レプリケーション用にパブリッシュされるデータベースには、それぞれ 1 つのログ リーダー エージェントがあります。 ログ リーダー エージェントの設定を変更すると、データベース内のすべてのトランザクション パブリケーションに影響します。  
  
-   キュー リーダー エージェント (キュー更新サブスクリプションを許可するトランザクション パブリケーション用) ディストリビューション データベースには、それぞれ 1 つのキュー リーダー エージェントがあります。 キュー リーダー エージェントの設定を変更すると、同じディストリビューション データベースを使用するキュー更新サブスクリプションを持つ、すべてのトランザクション パブリケーションに影響します。 キュー リーダー エージェントのセキュリティ設定の詳細については、「[レプリケーションのセキュリティ設定の表示および変更](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)」を参照してください。  
  
 各エージェントに必要なセキュリティ設定および権限の詳細については、「 [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md)」を参照してください。  
  
## <a name="options"></a>[変数]  
 **[セキュリティ設定]** または **[エージェントの作成]**  
 エージェント ジョブが作成されている場合、 **[セキュリティ設定]** をクリックして、エージェントのセキュリティ設定を変更できるダイアログ ボックスにアクセスします。 エージェント ジョブが作成されていない場合、 **[エージェントの作成]** をクリックしてエージェントの作成とセキュリティ設定を指定します。  
  
## <a name="see-also"></a>参照  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [パブリケーション プロパティの表示および変更](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [データとデータベース オブジェクトのパブリッシュ](../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Replication Security Best Practices](../../relational-databases/replication/security/replication-security-best-practices.md)   
 [セキュリティと保護 &#40;レプリケーション&#41;](../../relational-databases/replication/security/security-and-protection-replication.md)  
  
  
