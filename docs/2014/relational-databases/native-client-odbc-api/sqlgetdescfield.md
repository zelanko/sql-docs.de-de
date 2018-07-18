---
title: SQLGetDescField | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLGetDescField function
ms.assetid: 3e59a37a-28ee-4c91-8968-7fe3b966739d
caps.latest.revision: 51
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0527b8260f954764ed894b1b5db60278ff483d31
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37427529"
---
# <a name="sqlgetdescfield"></a>SQLGetDescField
  Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber macht die treiberspezifische deskriptorfelder für den Implementierungszeilendeskriptor (IRD) nur. Innerhalb des IRD wird [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] deskriptorfelder durch treiberspezifische Spaltenattribute verwiesen. Weitere Informationen über eine vollständige Liste der verfügbaren treiberspezifische deskriptorfelder finden Sie unter [SQLColAttribute](sqlcolattribute.md).  
  
 Deskriptorfelder, die Spaltenbezeichner-Zeichenfolgen enthalten, sind häufig Zeichenfolgen der Länge 0 (null). Alle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-spezifischen Deskriptorfeldwerte sind schreibgeschützt.  
  
 Abgerufen, wie Attribute mit SQLColAttribute, deskriptorfelder, dass auf Zeilenebene Berichtsattribute (wie SQL_CA_SS_COMPUTE_ID) für alle Spalten im Resultset gemeldet werden.  
  
## <a name="sqlgetdescfield-and-table-valued-parameters"></a>SQLGetDescField und Tabellenwertparameter  
 SQLGetDescField kann verwendet werden, um Werte für die erweiterten Attribute von Tabellenwertparametern und Tabellenwertparameter-Spalten zu erhalten. Weitere Informationen zu Tabellenwertparametern finden Sie unter [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqlgetdescfield-support-for-enhanced-date-and-time-features"></a>SQLGetDescField-Unterstützung für erweiterte Funktionen für Datum und Uhrzeit  
 Weitere Informationen zu den verfügbaren deskriptorfelder mit den neuen Datums-/Uhrzeit-Typen finden Sie unter [Parameter- und Ergebnismetadaten](../native-client-odbc-date-time/metadata-parameter-and-result.md).  
  
 Weitere Informationen finden Sie unter [Datums- / Uhrzeitverbesserungen &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
 Ab [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], SQLGetDescField kann zurückgeben `SQL_C_SS_TIME2` (für `time` Typen) oder `SQL_C_SS_TIMESTAMPOFFSET` (für `datetimeoffset`) anstelle von `SQL_C_BINARY`, wenn die Anwendung ODBC 3.8 verwendet.  
  
## <a name="sqlgetdescfield-support-for-large-clr-udts"></a>SQLGetDescField-Unterstützung für große CLR-UDTs  
 `SQLGetDescField` unterstützt große benutzerdefinierte CLR-Typen (UDTs). Weitere Informationen finden Sie unter [Large CLR User-Defined Typen &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="sqlgetdescfield-support-for-sparse-columns"></a>SQLGetDescField-Unterstützung für Spalten mit geringer Dichte  
 SQLGetDescField kann verwendet werden, um die Abfragen die neuen IRD-Felds SQL_CA_SS_IS_COLUMN_SET, um festzustellen, ob eine Spalte ist eine `column_set` Spalte.  
  
 Weitere Informationen finden Sie unter [Sparse Columns Support &#40;ODBC&#41;](../native-client/odbc/sparse-columns-support-odbc.md).  
  
## <a name="example"></a>Beispiel  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [SQLGetDescField-Funktion](http://go.microsoft.com/fwlink/?LinkId=59351)   
 [ODBC-API-Implementierungsdetails](odbc-api-implementation-details.md)  
  
  
