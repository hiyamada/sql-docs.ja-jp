---
title: CDC スプリッター | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.cdcsplitter.f1
ms.assetid: 167bc5c6-fa36-439d-987c-b20acd1a77e2
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 03f677f8214fb086f3feb6077608fed83d7089d4
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48086258"
---
# <a name="cdc-splitter"></a>CDC スプリッター
  CDC スプリッターは、CDC ソース データの変更行の単一フローを、挿入、更新、削除の各操作のための個別のデータ フローに分割します。 データベースは、必須の列 `__$operation` と、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 変更テーブル内のその標準の値に基づいて分割されます。  
  
|操作の値|[出力]|説明|  
|------------------------|------------|-----------------|  
|1|DELETE|削除された行|  
|2|Insert|挿入された行 ( **"結合を含む差分"** CDC モードを使用する場合は使用不可)|  
|3|Update|更新前の行 ( **"古い値を含むすべて"** CDC モードの場合のみ使用可)|  
|4|Update|更新後の行 (更新前と同じ)|  
|5|Update|マージ行 ( **"結合を含む差分"** CDC モードを使用する場合のみ使用可)|  
|その他|[エラー]||  
  
 スプリッターを使用して、定義済みの挿入、削除、更新の各出力に接続し、さらに処理を実行することができます。  
  
 CDC スプリッター変換には、1 つの標準入力と 1 つのエラー出力があります。  
  
## <a name="error-handling"></a>エラー処理  
 CDC スプリッター変換にはエラー出力があります。 $operation 列の値が無効な入力行はエラーと見なされ、入力の **ErrorRowDisposition** プロパティに従って処理されます。  
  
 コンポーネントのエラー出力には、次の出力列があります。  
  
-   **エラー コード**: 1 に設定されます。  
  
-   **エラー列**: (変換エラーの) エラーの原因となるソース列。  
  
-   **エラー行の列**: エラーの原因となった行の入力列。  
  
## <a name="configuring-the-cdc-splitter"></a>CDC スプリッターの構成  
 CDC スプリッターに構成可能なプロパティはありません。  
  
 CDC スプリッターの使用方法の詳細については、「Microsoft SQL Server Integration Services の CDC コンポーネント」を参照してください。  
  
 **[詳細エディター]** ダイアログ ボックスには、プログラムによって設定できるプロパティが表示されます。  
  
 **[詳細エディター]** ダイアログ ボックスを開くには、次の操作を実行します。  
  
-   **プロジェクトの** [データ フロー] [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] 画面で、CDC スプリッターを右クリックし、 **[詳細エディターの表示]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [変更の種類に応じた CDC ストリームのダイレクト](direct-the-cdc-stream-according-to-the-type-of-change.md)  
  
  
