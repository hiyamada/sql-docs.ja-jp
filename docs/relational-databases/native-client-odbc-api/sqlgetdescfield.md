---
title: SQLGetDescField |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLGetDescField function
ms.assetid: 3e59a37a-28ee-4c91-8968-7fe3b966739d
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 410aec64f1a10f8deaf7923fedda8b79c114eef3
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2018
ms.locfileid: "51669591"
---
# <a name="sqlgetdescfield"></a>SQLGetDescField
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーのみ実装行記述子 (IRD) のドライバー固有の記述子フィールドを公開します。 IRD 内[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]記述子フィールドは、ドライバー固有の列の属性によって参照されます。 使用可能なドライバー固有の記述子フィールドの完全な一覧については、次を参照してください。 [SQLColAttribute](../../relational-databases/native-client-odbc-api/sqlcolattribute.md)します。  
  
 列 ID 文字列を含む記述子フィールドは、多くの場合、長さが 0 の文字列になります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 固有のすべての記述子フィールドの値は読み取り専用です。  
  
 SQLColAttribute では属性のようがレポートの行レベルの属性 (SQL_CA_SS_COMPUTE_ID など) は報告される結果セット内のすべての列の記述子フィールドを取得します。  
  
## <a name="sqlgetdescfield-and-table-valued-parameters"></a>SQLGetDescField とテーブル値パラメーター  
 SQLGetDescField は、テーブル値パラメーターおよびテーブル値パラメーター列の拡張属性の値を取得できます。 テーブル値パラメーターの詳細については、次を参照してください。[テーブル値パラメーター &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)します。  
  
## <a name="sqlgetdescfield-support-for-enhanced-date-and-time-features"></a>SQLGetDescField による機能強化された日付と時刻のサポート  
 新しい日付/時刻型で使用できる記述子フィールドについては、次を参照してください。[パラメーターと結果のメタデータ](../../relational-databases/native-client-odbc-date-time/metadata-parameter-and-result.md)します。  
  
 詳細については、次を参照してください。[日付と時刻の強化&#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)します。  
  
 以降で[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、SQLGetDescField を返すことができます**SQL_C_SS_TIME2** (の**時間**型) または**SQL_C_SS_TIMESTAMPOFFSET** (の**datetimeoffset**) の代わりに**SQL_C_BINARY**場合、アプリケーションで ODBC 3.8 が使用されます。  
  
## <a name="sqlgetdescfield-support-for-large-clr-udts"></a>SQLGetDescField による大きな CLR UDT のサポート  
 **SQLGetDescField**大きなの CLR ユーザー定義型 (Udt) をサポートしています。 詳細については、次を参照してください。 [Large CLR User-Defined 型&#40;ODBC&#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md)します。  
  
## <a name="sqlgetdescfield-support-for-sparse-columns"></a>SQLGetDescField によるスパース列のサポート  
 SQLGetDescField は、新しい IRD フィールド SQL_CA_SS_IS_COLUMN_SET を決定する列がクエリに使用できる、 **column_set**列。  
  
 詳細については、次を参照してください。[スパース列のサポート&#40;ODBC&#41;](../../relational-databases/native-client/odbc/sparse-columns-support-odbc.md)します。  
  
## <a name="example"></a>例  
  
```  
typedef struct tagCOMPUTEBYLIST  
    {  
    SQLSMALLINT nBys;  
    SQLSMALLINT aByList[1];  
    } COMPUTEBYLIST;  
typedef COMPUTEBYLIST* PCOMPUTEBYLIST;   
  
SQLHDESC    hIRD;   
SQLINTEGER  cbIRD;   
SQLINTEGER  nSet = 0;   
  
// . . .  
// Execute a statement that contains a COMPUTE clause,  
//  then get the descriptor handle of the IRD and  
//  get some IRD values.  
  
SQLGetStmtAttr(g_hStmt, SQL_ATTR_IMP_ROW_DESC,  
    (SQLPOINTER) &hIRD, sizeof(SQLHDESC), &cbIRD);  
  
// For statement-wide column attributes, any  
//  descriptor record will do. You know that 1 exists,  
//  so use it.  
SQLGetDescField(hIRD, 1, SQL_CA_SS_NUM_COMPUTES,  
    (SQLPOINTER) &nComputes, SQL_IS_INTEGER, &cbIRD);  
  
if (nSet == 0)  
    {  
    SQLINTEGER      nOrderID;  
  
    printf_s("Normal result set.\n");  
  
    for (nCol = 0; nCol < nCols; nCol++)  
        {  
        SQLGetDescField(hIRD, nCol+1,  
            SQL_CA_SS_COLUMN_ORDER,  
            (SQLPOINTER) &nOrderID, SQL_IS_INTEGER,  
            &cbIRD);  
  
        if (nOrderID != 0)  
            {  
            printf_s("Col in ORDER BY, pos: %ld",  
                nOrderID);  
            }  
            printf_s("\n");  
        }  
  
    printf_s("\n");  
    }  
else  
    {  
    PCOMPUTEBYLIST  pByList;  
    SQLSMALLINT     nBy;  
    SQLINTEGER      nColID;  
  
    printf_s("Computed result set number: %lu\n",  
        nSet);  
  
    SQLGetDescField(hIRD, 1, SQL_CA_SS_COMPUTE_BYLIST,  
        (SQLPOINTER) &pByList, SQL_IS_INTEGER,  
        &cbIRD);  
  
    if (pByList != NULL)  
        {  
        printf_s("Clause ordered by columns: ");  
        for (nBy = 0; nBy < pByList->nBys; )  
            {  
            printf_s("%u", pByList->aByList[nBy]);  
            nBy++;  
  
            if (nBy == pByList->nBys)  
                {  
                printf_s("\n");  
                }  
            else  
                {  
                printf_s(", ");  
                }  
            }  
        }  
    else  
        {  
        printf_s("Compute clause set not ordered.\n");  
        }  
  
    for (nCol = 0; nCol < nCols; nCol++)  
        {  
        SQLGetDescField(hIRD, nCol+1,  
            SQL_CA_SS_COLUMN_ID, (SQLPOINTER) &nColID,  
            SQL_IS_INTEGER, &cbIRD);  
        printf_s("ColumnID: %lu, nColID);  
        }  
    printf_s("\n");  
    }  
  
if (SQLMoreResults(g_hStmt) == SQL_SUCCESS)  
    {  
    // Determine the result set indicator.  
    SQLGetDescField(hIRD, 1, SQL_CA_SS_COMPUTE_ID,  
        (SQLPOINTER) &nSet, SQL_IS_INTEGER, &cbIRD);  
    }  
```  
  
## <a name="see-also"></a>参照  
 [SQLGetDescField 関数](https://go.microsoft.com/fwlink/?LinkId=59351)   
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
