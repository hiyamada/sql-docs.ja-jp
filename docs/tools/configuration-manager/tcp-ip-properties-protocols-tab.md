---
title: TCP/IP のプロパティ ([プロトコル] タブ) |Microsoft Docs
ms.custom: ''
ms.date: 08/24/2016
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- TCP/IP [SQL Server], configuration options
ms.assetid: 007638fc-3a24-4460-adbe-545ded5d6f88
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6b8e961af919f3d92dad4aba5d87e910e341ce07
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47797412"
---
# <a name="tcpip-properties-protocols-tab"></a>[TCP/IP のプロパティ] ダイアログ ボックス ([プロトコル] タブ)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  **[TCP/IP のプロパティ]** ダイアログ ボックスは、TCP/IP プロトコルのオプションを構成するために使用します。 左ペインで **[TCP/IP]** をクリックすると、詳細ペインに個々の IP アドレス構成が表示されます。  
  
 変更を有効にするには、Microsoft SQL Server を再起動する必要があります。  
  
## <a name="options"></a>[変数]  
 **有効**  
 可能な値は、 **[はい]** と **[いいえ]** です。  
  
 **[Keep Alive]**  
 接続のリモート側のコンピューターが使用可能かどうかを確認するために、Keep Alive パケットを送信する間隔 (ミリ秒) を指定します。  
  
 **[すべて受信待ち]**  
 コンピューター上のネットワーク カードに割り当てられているすべての IP アドレスで SQL Server がリッスンするかどうかを指定します。 **[いいえ]** に設定した場合は、各 IP アドレスのプロパティ ダイアログ ボックスを使用して、IP アドレスごとに個別の構成を行ってください。 **[はい]** に設定した場合は、 **[IPAll]** プロパティ ボックスの設定がすべての IP アドレスに適用されます。 既定値は **[はい]** です。  
  
 **[遅延なし]**  
 SQL Server では、このプロパティに対する変更は実装されません。  
  
## <a name="see-also"></a>参照  
 [ネットワーク プロトコルの選択](https://msdn.microsoft.com/library/ms187892(v=sql.130).aspx)   
 [TCP/IP を使用した有効な接続文字列の作成](creating-a-valid-connection-string-using-tcp-ip.md)  
  
  
