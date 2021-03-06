---
title: 既定のドライバーのサブキー |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- default subkey [ODBC]
- registry entries for components [ODBC], default subkey
- subkeys [ODBC], default subkey
- drivers subkey [ODBC]
ms.assetid: 9e58b24f-ebfc-4286-a272-0843b4d6f2d5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d78101fd564e18467e6833f480cec2409dc2c44b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47856260"
---
# <a name="default-driver-subkey"></a>既定のドライバーのサブキー
既定のサブキーには、既定のデータ ソースで使用するドライバーを記述する 1 つの値が含まれています。 この値の形式は、次の表に示します。  
  
|名前|データ型|data|  
|----------|---------------|----------|  
|**[ドライバー]**|REG_SZ|*既定の説明ドライバー*|  
  
 *既定の説明ドライバー*名前は、ドライバーを記述する ODBC ドライバーのサブキーの下の値の名前と同じです。  
  
 たとえば、既定のデータ ソースは、SQL Server ドライバーを使用している場合、既定のサブキーの下の値可能性があります。  
  
```  
Driver : REG_SZ : SQL Server  
```  
  
> [!NOTE]  
>  既定のサブキーに含まれている既定のドライバーは、既定のユーザー DSN または既定のシステム DSN のいずれかを参照できます。 両方の既定のユーザー DSN と既定のシステム DSN を作成場合、最初に作成された DSN の有効な入力ができない可能性がありますので、既定のドライバーは最後に、作成された DSN で決定されます。
