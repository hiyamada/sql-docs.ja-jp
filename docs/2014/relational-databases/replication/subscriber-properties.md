---
title: '[サブスクライバーのプロパティ] | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.configdistwizard.subscribers.f1
helpviewer_keywords:
- Subscriber Properties dialog box
ms.assetid: 32aa0347-64e4-4aa4-ac57-6bd3e5d52070
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b48e20c2dd1838ae01447c12d8f65a8929b9d5c3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48075502"
---
# <a name="subscriber-properties"></a>[サブスクライバーのプロパティ]
  **[サブスクライバーのプロパティ]** ダイアログ ボックスには、[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] より前のバージョンの [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を実行しているサブスクライバーに関連する情報が表示されます。  
  
## <a name="options"></a>および  
 **[サブスクライバーへのエージェント接続]**  
 ディストリビューターからサブスクライバーに、ディストリビューション エージェントとマージ エージェントを接続する際のコンテキストです。これは [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]より前のバージョンにのみ適用されます。  
  
 **[エージェント プロセス アカウントを借用する]** を選択して、ディストリビューターで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのアカウントのコンテキストを使用してサブスクライバーへの接続を作成するか、 **[SQL Server 認証]** を指定して **[ログイン]** および **[パスワード]** の値を入力します。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] では、 **[エージェント プロセス アカウントを借用する]** を選択することをお勧めします。  
  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンでは、サブスクリプションの新規作成ウィザードで各サブスクリプションについて接続情報を指定します。接続情報の変更は **[サブスクリプションのプロパティ]** ダイアログ ボックスで行います。  
  
 **[既定のエージェントのスケジュール]**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] より前のバージョンの [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]を実行しているサブスクライバーでは、サブスクリプションの新規作成ウィザードで既定のスケジュールが使用されます。  
  
 **その他**  
 サブスクライバーとサブスクライバーの種類に関する情報が含まれています。  
  
## <a name="see-also"></a>参照  
 [View and Modify Distributor and Publisher Properties (ディストリビューターとパブリッシャーのプロパティの表示および変更)](view-and-modify-distributor-and-publisher-properties.md)   
 [プロパティ リファレンス &#40;レプリケーション&#41;](properties-reference-replication.md)   
 [パブリケーションのサブスクライブ](subscribe-to-publications.md)  
  
  
