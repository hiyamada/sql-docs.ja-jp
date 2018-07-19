---
title: オプション (テキスト エディター - XML/全般 ページ) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.General
ms.assetid: 46a9f913-d0b9-40ff-b382-9bbdec7461a6
caps.latest.revision: 20
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 7a6a5f53bbccbd0d30aaada30366d01af23a3a5f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37322782"
---
# <a name="options-text-editor---xml---general-page"></a>[オプション] ([テキスト エディター]/[XML]/[全般] ページ)
  このダイアログ ボックスを使用すると、XML ドキュメントの編集に使用される XML エディターの全般的な編集の動作を変更できます。 これらの設定を変更するには、 **[ツール]** メニューの **[オプション]** をクリックし、 **[XML]** サブフォルダーを展開します。次に、 **[全般]** をクリックします。  
  
## <a name="setting-options-in-multiple-locations"></a>複数の場所でのオプション設定  
 XML エディターを設定することものオプションは、**すべて言語全般**ダイアログ。 ただし、DMX エディターや MDX エディターなど、他の **エディターに対し、** [すべての言語] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] のダイアログを使用して異なるオプションを設定する場合は、ここで紹介したダイアログを使用して XML エディターのオプションを設定し直す必要があります。  
  
## <a name="statement-completion"></a>[入力候補]  
 **自動メンバー表示**  
 このチェック ボックスがオンの場合、エディターでの入力に合わせて、使用できるメンバー、プロパティ、値、またはメソッドの一覧が表示されます。 ポップアップ リストから項目を選択してコードに挿入します。  
  
 **高度なメンバーを非表示にします。**  
 このチェック ボックスは使用できません。  
  
 **パラメーター情報**  
 このチェック ボックスがオンの場合、エディター内の挿入ポイントの左側に、現在の宣言またはプロシージャの完全な構文が、使用可能なすべてのパラメーターと共に表示されます。 割り当て可能な次のパラメーターは、太字で表示されます。  
  
## <a name="settings"></a>[設定]  
 **仮想空間を有効にします。**  
 このチェック ボックスがオンの場合、各コード行の末尾にスペースが挿入されます。 コードの横の一定の場所にコメントを記述する場合に、このチェック ボックスをオンにします。  
  
 **ワード ラップ**  
 このチェック ボックスがオンの場合、表示可能なエディター領域の幅からはみ出した行を次の行に折り返して表示します。 このチェック ボックスをオンにすると、 **[右端の折り返しの記号を表示する]** チェック ボックスが有効になります。  
  
 **折り返しの記号を表示します。**  
 このチェック ボックスがオンの場合、改行が行われている箇所に矢印形の改行インジケーターが表示されます。 このインジケーターを表示しないようにするには、このチェック ボックスをオフにします。  
  
> [!NOTE]  
>  改行インジケーターはコードに追加されているわけではないので、印刷されません。 これは単に表示用です。  
  
 **選択されていない場合は、空白行に切り取り/コピー コマンドを適用します。**  
 このチェック ボックスは、空白行にカーソルを置き、何も選択していない状態で **[コピー]** または **[切り取り]** をクリックしたときのエディターの動作を設定します。  
  
 このチェック ボックスがオンの場合、空白行がコピーまたは切り取られます。 その後で **[貼り付け]** をクリックすると、新しい空白行が挿入されます。  
  
 このチェック ボックスがオフの場合、何もコピーまたは切り取られません。 その後で **[貼り付け]** をクリックすると、最後にコピーした内容が貼り付けられます。 それまでに何もコピーされていない場合は、何も貼り付けられません。  
  
 行が空白でない場合、 **[コピー]** または **[切り取り]** の動作はこの設定の影響を受けません。 何も選択されていない場合、行全体がコピーまたは切り取られます。 その後で **[貼り付け]** をクリックすると、行全体のテキストと行末文字が貼り付けられます。  
  
## <a name="display"></a>表示  
 **行番号**  
 このチェック ボックスがオンの場合、各コード行の横に行番号が表示されます。  
  
> [!NOTE]  
>  この行番号はコードに追加されているわけではないので、印刷されません。 これは単に表示用です。  
  
 **シングル クリックでの URL ナビゲーションを有効にします。**  
 このチェック ボックスがオンの場合、エディター内で URL 上にカーソルを移動すると、カーソルが指差しカーソルに変わります。 URL をクリックすると、該当するページが Web ブラウザーに表示されます。  
  
 **ナビゲーション バー**  
 このチェック ボックスは使用できません。  
  
  