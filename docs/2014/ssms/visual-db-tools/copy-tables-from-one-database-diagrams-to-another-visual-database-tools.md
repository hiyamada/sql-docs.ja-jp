---
title: もう 1 つ (Visual Database Tools) の 1 つのデータベース ダイアグラムからテーブルをコピー |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- copying tables
- duplicating tables
ms.assetid: 155a4f09-9321-4887-a7d4-aa2ce6b51277
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b4af39696c40035a20bc0c099ba242930069d1e3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48206422"
---
# <a name="copy-tables-from-one-database-diagrams-to-another-visual-database-tools"></a>データベース ダイアグラム間でのテーブルのコピー (Visual Database Tools)
  データベース ダイアグラムから同じデータベースの他のデータベース ダイアグラムにテーブルをコピーできます。  
  
 データベース ダイアグラム間でテーブルをコピーすると、コピー先のダイアグラムのテーブルに参照が追加されます。 テーブルがデータベースに複製されるわけではありません。 たとえば、データベース ダイアグラム間で `authors` テーブルをコピーすると、各ダイアグラムはデータベースの同じ `authors` テーブルを参照します。  
  
### <a name="to-copy-a-table-from-another-database-diagram"></a>他のデータベース ダイアグラムからテーブルをコピーするには  
  
1.  テーブルをコピーするデータベースに接続していることを確認します。  
  
2.  コピー元およびコピー先のデータベース ダイアグラムを開き、コピー元のダイアグラムで、コピー先のダイアグラムにコピーするテーブルを選択します。  
  
3.  ツール バーの **[コピー]** ボタンをクリックします。 選択したテーブルの定義がクリップボードにコピーされます。  
  
4.  コピー先のダイアグラムに切り替えます。 このダイアグラムは、コピー元のダイアグラムと同じデータベースにある必要があります。  
  
5.  ツール バーの **[貼り付け]** ボタンをクリックします。 クリップボードの内容が新しい場所に表示され、他の場所をクリックするまで強調表示された状態が続きます。 コピー先のダイアグラムで、選択したテーブルとダイアグラムの他のテーブルとの間にリレーションシップが存在する場合は、自動的にリレーションシップの線が引かれます。  
  
 どちらかのダイアグラムでテーブルを編集すると、両方のダイアグラムに変更が反映されます。 同様に、どちらかのダイアグラムのテーブルを保存すると、どちらのダイアグラムでもテーブルは "変更済み" と見なされなくなります。  
  
## <a name="see-also"></a>参照  
 [データベース ダイアグラムを扱う&#40;Visual Database Tools&#41;](visual-database-tools.md)   
 [ダイアグラムへのテーブルの追加 (Visual Database Tools)](add-tables-to-diagrams-visual-database-tools.md)  
  
  
