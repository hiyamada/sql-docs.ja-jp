---
title: "Sqlgettypeinfo による結果の例の設定 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL data types [ODBC], examples
- SQLGetTypeInfo function [ODBC], examples
- data types [ODBC], SQL data types
ms.assetid: dc1952cc-7581-4d69-9c72-7dc1cd370836
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b43138efe4c6540b12bbfeeb0185f61ad0e65861
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="example-sqlgettypeinfo-result-set"></a>Sqlgettypeinfo による結果セットの例
アプリケーションが呼び出す**SQLGetTypeInfo**を決定するデータ型は、データ ソースとそれらのデータ型の特性でサポートされています。 次の表は、によって返される結果セットの例を示して**SQLGetTypeInfo** SQL_CHAR、SQL_LONGVARCHAR、SQL_DECIMAL、SQL_REAL、SQL_DATETIME、SQL_INTERVAL_YEAR、および SQL_INTERVAL_DAY_TO_SECOND をサポートするデータ ソースにします。  
  
|TYPE_NAME|DATA_TYPE|COLUMN_SIZE|LITERAL_PREFIX|LITERAL_SUFFIX|CREATE_PARAMS|NULLABLE|  
|----------------|----------------|------------------|---------------------|---------------------|--------------------|--------------|  
|"char"|SQL_CHAR|255|"'"|"'"|「長さ」|SQL_TRUE|  
|"text"|SQL_LONGVARCHAR|2147483647|"'"|"'"|\<Null >|SQL_TRUE|  
|"decimal"|SQL_DECIMAL|28|\<Null >|\<Null >|"precision,<br />scale"|SQL_TRUE|  
|「現実の」|SQL_REAL|7|\<Null >|\<Null >|\<Null >|SQL_TRUE|  
|"datetime"|SQL_TYPE_TIMESTAMP|23|"'"|"'"|\<Null >|SQL_TRUE|  
|"年に間隔 YEAR()"|SQL_INTERVAL_YEAR|9|"'"|"'"|"precision"|SQL_TRUE|  
|"FRACTION(5) する間隔 DAY()"|SQL_INTERVAL_DAY_TO_SECOND|24|"'"|"'"|"precision"|SQL_TRUE|  
  
|DATA_TYPE|CASE_SENSITIVE|SEARCHABLE|UNSIGNED_ATTRIBUTE|FIXED_PREC_SCALE|AUTO_UNIQUE_VALUE|LOCAL_TYPE_NAME|  
|----------------|---------------------|----------------|-------------------------|------------------------|-------------------------|-----------------------|  
|**SQL_CHAR**|SQL_FALSE|SQL_SEARCHABLE|\<Null >|SQL_FALSE|\<Null >|"char"|  
|**SQL_LONGVARCHAR**|SQL_FALSE|SQL_PRED_CHAR|\<Null >|SQL_FALSE|\<Null >|"text"|  
|**SQL_DECIMAL**|SQL_FALSE|SQL_PRED_BASIC|SQL_FALSE|SQL_FALSE|SQL_FALSE|"decimal"|  
|**SQL_REAL**|SQL_FALSE|SQL_PRED_BASIC|SQL_FALSE|SQL_FALSE|SQL_FALSE|「現実の」|  
|**SQL_TYPE_TIMESTAMP 型**|SQL_FALSE|SQL_SEARCHABLE|\<Null >|SQL_FALSE|\<Null >|"datetime"|  
|**SQL_INTERVAL_YEAR**|SQL_FALSE|SQL_SEARCHABLE|\<Null >|SQL_FALSE|\<Null >|"年に間隔 YEAR()"|  
TERVAL_DAY_TO_SECOND * *|SQL_FALSE|SQL_PRED_BASIC|\<Null >|SQL_FALSE|\<Null >|"FRACTION(5) する間隔 DAY()"|  
  
|DATA_TYPE|MINIMUM_SCALE|MAXIMUM_SCALE|SQL_DATA_TYPE|SQL_DATETIME_SUB|NUM_PREC_RADIX|INTERVAL_PRECISION|  
|----------------|--------------------|--------------------|---------------------|------------------------|----------------------|-------------------------|  
|**SQL_CHAR**|\<Null >|\<Null >|SQL_CHAR|\<Null >|\<Null >|\<Null >|  
|**SQL_LONGVARCHAR**|\<Null >|\<Null >|SQL_LONGVARCHAR|\<Null >|\<Null >|\<Null >|  
|**SQL_DECIMAL**|0|28|SQL_DECIMAL|\<Null >|10|\<Null >|  
|**SQL_REAL**|\<Null >|\<Null >|SQL_REAL|\<Null >|10|\<Null >|  
|**SQL_TYPE_TIMESTAMP 型**|3|3|SQL_DATETIME|SQL_CODE_TIMESTAMP|\<Null >|12|  
|**SQL_INTERVAL_YEAR**|0|0|SQL_INTERVAL|SQL_CODE_INTERVALYEAR|\<Null >|9|  
ERVAL_DAY_TO_SECOND * *|5|5|SQL_INTERVAL|SQL_CODE_INTERVALDAY_TO_SECOND|\<Null >|9|