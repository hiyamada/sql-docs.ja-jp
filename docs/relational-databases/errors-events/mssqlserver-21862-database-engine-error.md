---
title: MSSQLSERVER_21862 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 21862 (Database Engine error)
ms.assetid: a1d393dd-453b-4d45-9aa5-7d371213e32b
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 331e07fce8dc82ee090f3e28c8281ed29514fd46
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47624712"
---
# <a name="mssqlserver21862"></a>MSSQLSERVER_21862
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|MSSQLSERVER|  
|イベント ID|21862|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|SQLErrorNum21862|  
|メッセージ テキスト|FILESTREAM 列は、同期方法 'database snapshot' または 'database snapshot character' を使用して、パブリケーションでパブリッシュすることはできません。|  
  
## <a name="explanation"></a>説明  
データベース スナップショットから FILESTREAM データにアクセスできないため、パブリケーションの同期方法に *database snapshot* パラメーターまたは *database_snapshot_character* パラメーターが指定されている場合、スナップショット エージェントは FILESTREAM データを読み取ることができません。  
  
## <a name="user-action"></a>ユーザーの操作  
パブリケーションの同期方法を *database snapshot* または *database_snapshot_character* 以外の方法に変更するか、パブリケーションから FILESTREAM 列を除外します。  
  
