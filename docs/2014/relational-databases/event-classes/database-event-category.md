---
title: Database イベント カテゴリ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- event classes [SQL Server], Database event category
- Database event category [SQL Server]
- SQL Server event classes, Database event category
ms.assetid: b61af738-f144-4992-b0b2-d44cb7240991
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 2c68c5f735c494776c9e798b3786c6dcda048f7e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48078612"
---
# <a name="database-event-category"></a>Database イベント カテゴリ
  **Database** イベント カテゴリには、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]を監視するためのイベント クラスが含まれています。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|説明|  
|-----------|-----------------|  
|[Data File Auto Grow イベント クラス](data-file-auto-grow-event-class.md)|データ ファイルが自動的に拡張されたことを示します。 データ ファイルが ALTER DATABASE により明示的に拡張された場合、このイベントはトリガーされません。|  
|[Data File Auto Shrink イベント クラス](data-file-auto-shrink-event-class.md)|データ ファイルが圧縮されたことを示します。|  
|[Database Mirroring Connection イベント クラス](database-mirroring-connection-event-class.md)|データベース ミラーリングのトランスポート接続のステータスをレポートするために生成されるイベントです。|  
|[Database Mirroring State Change イベント クラス](database-mirroring-state-change-event-class.md)|ミラー化されたデータベースの状態が変更された時点を示します。|  
|[Database Suspect Data Page イベント クラス](database-suspect-data-page-event-class.md)|**msdb** データベースの **suspect_pages** テーブルにページが加わった時点を示します。|  
|[Log File Auto Grow イベント クラス](log-file-auto-grow-event-class.md)|ログ ファイルが自動的に拡張されたことを示します。 ログ ファイルが ALTER DATABASE により明示的に拡張された場合、このイベントはトリガーされません。|  
|[Log File Auto Shrink イベント クラス](log-file-auto-shrink-event-class.md)|ログ ファイルが自動的に拡張されたことを示します。 ログ ファイルが ALTER DATABASE により明示的に圧縮された場合、このイベントはトリガーされません。|  
  
## <a name="see-also"></a>関連項目  
 [拡張イベント](../extended-events/extended-events.md)  
  
  
