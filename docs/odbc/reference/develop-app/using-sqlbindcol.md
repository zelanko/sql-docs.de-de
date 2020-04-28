---
title: Verwenden von SQLBindCol | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- result sets [ODBC], binding columns
- binding columns [ODBC]
- SQLBindCol function [ODBC], using
ms.assetid: 17277ab3-33ad-44d3-a81c-a26b5e338512
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: da49ad4db80b93d02534a0c4ecacdc2621c9cf8d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81294630"
---
# <a name="using-sqlbindcol"></a>Verwenden von SQLBindCol
Die Anwendung bindet Spalten durch Aufrufen von **SQLBindCol**. Diese Funktion bindet jeweils eine Spalte. Dabei gibt die Anwendung Folgendes an:  
  
-   Die Spaltennummer. Spalte 0 ist die Lesezeichen Spalte. Diese Spalte ist nicht in einigen Resultsets enthalten. Alle anderen Spalten werden beginnend mit der Zahl 1 nummeriert. Es ist ein Fehler, eine Spalte mit höherer Nummerierung zu binden, als Spalten im Resultset vorhanden sind. Dieser Fehler kann erst erkannt werden, wenn das Resultset erstellt wurde, sodass es von **SQLFetch**, nicht von **SQLBindCol**, zurückgegeben wird.  
  
-   Der C-Datentyp, die Adresse und die Byte Länge der Variablen, die an die Spalte gebunden ist. Es ist ein Fehler, einen C-Datentyp anzugeben, in den der SQL-Datentyp der Spalte nicht konvertiert werden kann. Dieser Fehler wird möglicherweise erst erkannt, wenn das Resultset erstellt wurde, sodass er von **SQLFetch**, nicht von **SQLBindCol**, zurückgegeben wird. Eine Liste der unterstützten Konvertierungen finden [Sie unter Konvertieren von Daten aus SQL-in C-Datentypen](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md) in Anhang D: Datentypen. Weitere Informationen zur Byte Länge finden Sie unter [Datenpuffer Länge](../../../odbc/reference/develop-app/data-buffer-length.md).  
  
-   Die Adresse eines Längen-/Indikatorpuffers. Der Längen-/Indikatorpuffer ist optional. Es wird verwendet, um die Byte Länge von Binär-oder Zeichendaten zurückzugeben oder um SQL_NULL_DATA zurückzugeben, wenn die Daten NULL sind. Weitere Informationen finden Sie unter [Verwenden von Längen-/indikatorenwerten](../../../odbc/reference/develop-app/using-length-and-indicator-values.md).  
  
 Wenn **SQLBindCol** aufgerufen wird, ordnet der Treiber diese Informationen der-Anweisung zu. Wenn jede Daten Zeile abgerufen wird, verwendet Sie die Informationen, um die Daten für jede Spalte in den gebundenen Anwendungsvariablen zu platzieren.  
  
 Mit dem folgenden Code werden beispielsweise Variablen an die Spalten SalesPerson und CustID gebunden. Daten für die Spalten werden in " *SalesPerson* " und " *CustId*" zurückgegeben. Da *SalesPerson* ein Zeichen Puffer ist, gibt die Anwendung die Bytelänge (11) an, damit der Treiber bestimmen kann, ob die Daten abgeschnitten werden sollen. Die Byte Länge des zurückgegebenen Titels oder ob NULL ist, wird in *salespersonlenorind*zurückgegeben.  
  
 Da *CustId* eine ganzzahlige Variable ist und eine festgelegte Länge aufweist, muss die Byte Länge nicht angegeben werden. der Treiber geht davon aus, dass es sich um **sizeof (** SQLUINTEGER **)** handelt. Die Byte Länge der zurückgegebenen Kunden-ID-Daten oder ob Sie NULL ist, wird in *custidind*zurückgegeben. Beachten Sie, dass die Anwendung nur daran interessiert ist, ob das Gehalt NULL ist, da die Byte Länge immer **sizeof (** SQLUINTEGER **)** ist.  
  
```  
SQLCHAR       SalesPerson[11];  
SQLUINTEGER   CustID;  
SQLINTEGER    SalesPersonLenOrInd, CustIDInd;  
SQLRETURN     rc;  
SQLHSTMT      hstmt;  
  
// Bind SalesPerson to the SalesPerson column and CustID to the   
// CustID column.  
SQLBindCol(hstmt, 1, SQL_C_CHAR, SalesPerson, sizeof(SalesPerson),  
            &SalesPersonLenOrInd);  
SQLBindCol(hstmt, 2, SQL_C_ULONG, &CustID, 0, &CustIDInd);  
  
// Execute a statement to get the sales person/customer of all orders.  
SQLExecDirect(hstmt, "SELECT SalesPerson, CustID FROM Orders ORDER BY SalesPerson",  
               SQL_NTS);  
  
// Fetch and print the data. Print "NULL" if the data is NULL. Code to   
// check if rc equals SQL_ERROR or SQL_SUCCESS_WITH_INFO not shown.  
while ((rc = SQLFetch(hstmt)) != SQL_NO_DATA) {  
   if (SalesPersonLenOrInd == SQL_NULL_DATA)   
            printf("NULL                     ");  
   else   
            printf("%10s   ", SalesPerson);  
   if (CustIDInd == SQL_NULL_DATA)   
         printf("NULL\n");  
   else   
            printf("%d\n", CustID);  
}  
  
// Close the cursor.  
SQLCloseCursor(hstmt);  
```  
  
 Der folgende Code führt eine vom Benutzer eingegebene **Select** -Anweisung aus und druckt jede Daten Zeile im Resultset. Da die Anwendung die Form des von der **Select** -Anweisung erstellten Resultsets nicht vorhersagen kann, kann Sie keine hart codierten Variablen an das Resultset binden, wie im vorherigen Beispiel gezeigt. Stattdessen ordnet die Anwendung einen Puffer zu, der die Daten enthält, und einen Längen-/Indikatorpuffer für jede Spalte in dieser Zeile. Für jede Spalte wird der Offset bis zum Anfang des Speichers für die Spalte berechnet, und dieser Offset wird so angepasst, dass die Daten-und Längen-/Indikatorpuffer für die Spalte an Ausrichtungs Grenzen beginnen. Anschließend wird der Speicher, beginnend am Offset, an die Spalte gebunden. Aus Sicht des Treibers kann die Adresse dieses Speichers nicht von der Adresse einer Variablen, die im vorherigen Beispiel gebunden ist, unterschieden werden. Weitere Informationen zur Ausrichtung finden Sie unter [Alignment](../../../odbc/reference/develop-app/alignment.md).  
  
```  
// This application allocates a buffer at run time. For each column, this   
// buffer contains memory for the column's data and length/indicator.   
// For example:  
//      column 1         column 2      column 3      column 4  
// <------------><---------------><-----><------------>  
//      db1   li1   db2   li2   db3   li3   db4   li4  
//      |      |      |      |      |      |      |         |  
//      _____V_____V________V_______V___V___V______V_____V_  
// |__________|__|_____________|__|___|__|__________|__|  
//  
// dbn = data buffer for column n  
// lin = length/indicator buffer for column n  
  
// Define a macro to increase the size of a buffer so that it is a   
// multiple of the alignment size. Thus, if a buffer starts on an   
// alignment boundary, it will end just before the next alignment   
// boundary. In this example, an alignment size of 4 is used because   
// this is the size of the largest data type used in the application's   
// buffer--the size of an SDWORD and of the largest default C data type   
// are both 4. If a larger data type (such as _int64) was used, it would   
// be necessary to align for that size.  
#define ALIGNSIZE 4  
#define ALIGNBUF(Length) Length % ALIGNSIZE ? \  
                  Length + ALIGNSIZE - (Length % ALIGNSIZE) : Length  
  
SQLCHAR        SelectStmt[100];  
SQLSMALLINT    NumCols, *CTypeArray, i;  
SQLINTEGER *   ColLenArray, *OffsetArray, SQLType, *DataPtr;  
SQLRETURN      rc;   
SQLHSTMT       hstmt;  
  
// Get a SELECT statement from the user and execute it.  
GetSelectStmt(SelectStmt, 100);  
SQLExecDirect(hstmt, SelectStmt, SQL_NTS);  
  
// Determine the number of result set columns. Allocate arrays to hold   
// the C type, byte length, and buffer offset to the data.  
SQLNumResultCols(hstmt, &NumCols);  
CTypeArray = (SQLSMALLINT *) malloc(NumCols * sizeof(SQLSMALLINT));  
ColLenArray = (SQLINTEGER *) malloc(NumCols * sizeof(SQLINTEGER));  
OffsetArray = (SQLINTEGER *) malloc(NumCols * sizeof(SQLINTEGER));  
  
OffsetArray[0] = 0;  
for (i = 0; i < NumCols; i++) {  
   // Determine the column's SQL type. GetDefaultCType contains a switch   
   // statement that returns the default C type for each SQL type.  
   SQLColAttribute(hstmt, ((SQLUSMALLINT) i) + 1, SQL_DESC_TYPE, NULL, 0, NULL, (SQLPOINTER) &SQLType);  
   CTypeArray[i] = GetDefaultCType(SQLType);  
  
   // Determine the column's byte length. Calculate the offset in the   
   // buffer to the data as the offset to the previous column, plus the   
   // byte length of the previous column, plus the byte length of the   
   // previous column's length/indicator buffer. Note that the byte   
   // length of the column and the length/indicator buffer are increased   
   // so that, assuming they start on an alignment boundary, they will  
   // end on the byte before the next alignment boundary. Although this   
   // might leave some holes in the buffer, it is a relatively   
   // inexpensive way to guarantee alignment.  
   SQLColAttribute(hstmt, ((SQLUSMALLINT) i)+1, SQL_DESC_OCTET_LENGTH, NULL, 0, NULL, &ColLenArray[i]);  
   ColLenArray[i] = ALIGNBUF(ColLenArray[i]);  
   if (i)  
      OffsetArray[i] = OffsetArray[i-1]+ColLenArray[i-1]+ALIGNBUF(sizeof(SQLINTEGER));  
}  
  
// Allocate the data buffer. The size of the buffer is equal to the   
// offset to the data buffer for the final column, plus the byte length   
// of the data buffer and length/indicator buffer for the last column.  
void *DataPtr = malloc(OffsetArray[NumCols - 1] +  
               ColLenArray[NumCols - 1] + ALIGNBUF(sizeof(SQLINTEGER)));  
  
// For each column, bind the address in the buffer at the start of the   
// memory allocated for that column's data and the address at the start   
// of the memory allocated for that column's length/indicator buffer.  
for (i = 0; i < NumCols; i++)  
   SQLBindCol(hstmt,  
            ((SQLUSMALLINT) i) + 1,  
            CTypeArray[i],  
            (SQLPOINTER)((SQLCHAR *)DataPtr + OffsetArray[i]),  
            ColLenArray[i],  
            (SQLINTEGER *)((SQLCHAR *)DataPtr + OffsetArray[i] + ColLenArray[i]));  
  
// Retrieve and print each row. PrintData accepts a pointer to the data,   
// its C type, and its byte length/indicator. It contains a switch   
// statement that casts and prints the data according to its type. Code   
// to check if rc equals SQL_ERROR or SQL_SUCCESS_WITH_INFO not shown.  
while ((rc = SQLFetch(hstmt)) != SQL_NO_DATA) {  
   for (i = 0; i < NumCols; i++) {  
      PrintData((SQLCHAR *)DataPtr[OffsetArray[i]], CTypeArray[i],  
               (SQLINTEGER *)((SQLCHAR *)DataPtr[OffsetArray[i] + ColLenArray[i]]));  
   }  
}  
  
// Close the cursor.  
SQLCloseCursor(hstmt);  
```
