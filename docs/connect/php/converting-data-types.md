---
title: データ型の変換 |Microsoft Docs
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 508542ec-cc28-4a17-80f4-52325d6a48db
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b6a7ed91da704fa81b0c8f101f8da5cd71ff48f9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47857200"
---
# <a name="converting-data-types"></a>データ型の変換
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] では、データを送信するとき、または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] からデータを取得するときにデータ型を指定できます。 データ型の指定は省略できます。 データ型を指定しない場合、既定の型が使用されます。 このセクションのトピックでは、データ型を指定する方法と既定のデータ型の詳細について説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|[説明]|  
|---------|---------------|  
|[既定の SQL Server のデータ型](../../connect/php/default-sql-server-data-types.md)|サーバーにデータを送信するときの既定の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型について説明します。|  
|[既定の PHP データ型](../../connect/php/default-php-data-types.md)|サーバーからデータを取得するときの既定の PHP データ型について説明します。|  
|[方法: SQL Server データ型を指定する](../../connect/php/how-to-specify-sql-server-data-types-when-using-the-sqlsrv-driver.md)|サーバーにデータを送信する際に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型を指定する方法について説明します。|  
|[方法: PHP データ型を指定する](../../connect/php/how-to-specify-php-data-types.md)|サーバーからデータを取得するときに PHP データ型を指定する方法について説明します。|  
|[方法: 組み込みの UTF-8 サポートを使用した UTF-8 データの送信と取得](../../connect/php/how-to-send-and-retrieve-utf-8-data-using-built-in-utf-8-support.md)|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] に備わっている UTF-8 データ サポートを使用する方法について説明します。<br /><br />UTF-8 文字のサポートは [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] のバージョン 1.1 で追加されました。|  
|[方法: Linux および macOS での ASCII データの送信と取得](../../connect/php/how-to-send-and-retrieve-ascii-data-in-linux-mac.md)|使用する方法を示します[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]の Linux または macOS での ASCII データをサポートします。<br /><br />バージョン 5.2 の Windows 以外の環境での ASCII 文字のサポートが追加されました、[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]します。|
  
## <a name="see-also"></a>参照  
[For PHP for SQL Server のプログラミング、Microsoft ドライバーのガイド](../../connect/php/programming-guide-for-php-sql-driver.md)

[SQLSRV ドライバー API リファレンス](../../connect/php/sqlsrv-driver-api-reference.md)

[定数 &#40;Microsoft Drivers for PHP for SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)

[サンプル アプリケーション &#40;SQLSRV ドライバー&#41;](../../connect/php/example-application-sqlsrv-driver.md)  
  
