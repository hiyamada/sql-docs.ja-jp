---
title: 汎用アプリケーション |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], generic applications
- interoperability [ODBC], levels
- generic applications [ODBC]
ms.assetid: dda2a3c4-76ef-40a6-b3a1-9e95bed61618
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 59110f66c512845ff5ce1f2f246c05c63fa755b9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47751289"
---
# <a name="generic-applications"></a>汎用アプリケーション
汎用アプリケーション、データベースからデータを取得するスプレッドシートなど、ハード コーディングされたタスクの実行場合があります。 さまざまなユーザーが入力して、SQL ステートメントを実行できる汎用クエリ アプリケーションなどのユーザー定義のタスクを実行する場合もします。 どのような汎用アプリケーションが共通は、さまざまな異なる Dbms で動作する必要があることと、開発者がわからない事前なりますこれらの Dbms です。  
  
 そのため、汎用アプリケーションは、高い相互運用できるようにする必要があります。 開発者は、機能については、相互運用性を犠牲に多くの選択を行う必要があり、広範な機能をサポートするドライバーを必要とするコードを記述する必要があります。 一般的な Dbms を使用する汎用的なアプリケーションをチューニングする場合があります、中にドライバー固有または DBMS 固有のコードほとんど含まれます。
