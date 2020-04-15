---
title: Binden von Arrays von Parametern | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- binding parameter arrays [ODBC]
- arrays of parameter values [ODBC]
- parameter arrays [ODBC]
ms.assetid: 037afe23-052d-4f3a-8aa7-45302b199ad0
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 73cfcde89e89edb87a4955cf0854c66a01d81e6f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81283420"
---
# <a name="binding-arrays-of-parameters"></a>Binden von Parameterarrays
Anwendungen, die Arrays von Parametern verwenden, binden die Arrays an die Parameter in der SQL-Anweisung. Es gibt zwei Bindungsstile:  
  
-   Binden Sie ein Array an jeden Parameter. Jede Datenstruktur (Array) enthält alle Daten für einen einzelnen Parameter. Dies wird als *spaltenweise Bindung* bezeichnet, da eine Spalte mit Werten für einen einzelnen Parameter gebunden wird.  
  
-   Definieren Sie eine Struktur, um die Parameterdaten für einen ganzen Satz von Parametern zu halten, und binden Sie ein Array dieser Strukturen. Jede Datenstruktur enthält die Daten für eine einzelne SQL-Anweisung. Dies wird als *zeilenweise Bindung* bezeichnet, da eine Reihe von Parametern gebunden wird.  
  
 Wie wenn die Anwendung einzelne Variablen an Parameter bindet, ruft sie **SQLBindParameter auf,** um Arrays an Parameter zu binden. Der einzige Unterschied besteht darin, dass es sich bei den übergebenen Adressen um Arrayadressen und nicht um Adressen mit nur einer Variablen handelt. Die Anwendung legt das attribut SQL_ATTR_PARAM_BIND_TYPE-Anweisung fest, um anzugeben, ob es spaltenweise (Standard) oder zeilenweise Bindung verwendet. Ob spalten- oder zeilenweise Bindung verwendet werden soll, ist weitgehend eine Frage der Anwendungspräferenz. Je nachdem, wie der Prozessor auf den Arbeitsspeicher zugreift, kann die zeilenweise Bindung schneller sein. Der Unterschied ist jedoch mit Ausnahme einer sehr großen Anzahl von Parameterzeilen wahrscheinlich vernachlässigbar.  
  
## <a name="column-wise-binding"></a>Spaltenbezogenes Binden  
 Bei verwendung der spaltenweisen Bindung bindet eine Anwendung ein oder zwei Arrays an jeden Parameter, für den Daten bereitgestellt werden sollen. Das erste Array enthält die Datenwerte, und das zweite Array enthält Längen-/Indikatorpuffer. Jedes Array enthält so viele Elemente, wie Werte für den Parameter vorhanden sind.  
  
 Spaltenweise Bindung ist die Standardeinstellung. Die Anwendung kann auch von zeilenweise bindung zu spaltenweise Bindung ändern, indem das SQL_ATTR_PARAM_BIND_TYPE Anweisungsattribut. Die folgende Abbildung zeigt, wie spaltenweise Bindung funktioniert.  
  
 ![Zeigt, wie&#45;weise Bindung stritt](../../../odbc/reference/develop-app/media/pr31.gif "pr31")  
  
 Der folgende Code bindet beispielsweise 10-Element-Arrays an Parameter für die Spalten PartID, Description und Price und führt eine Anweisung zum Einfügen von 10 Zeilen aus. Es verwendet spaltenweise Bindung.  
  
```  
#define DESC_LEN 51  
#define ARRAY_SIZE 10  
  
SQLCHAR *      Statement = "INSERT INTO Parts (PartID, Description,  Price) "  
                                                "VALUES (?, ?, ?)";  
SQLUINTEGER    PartIDArray[ARRAY_SIZE];  
SQLCHAR        DescArray[ARRAY_SIZE][DESC_LEN];  
SQLREAL        PriceArray[ARRAY_SIZE];  
SQLINTEGER     PartIDIndArray[ARRAY_SIZE], DescLenOrIndArray[ARRAY_SIZE],  
               PriceIndArray[ARRAY_SIZE];  
SQLUSMALLINT   i, ParamStatusArray[ARRAY_SIZE];  
SQLULEN ParamsProcessed;  
  
memset(DescLenOrIndArray, 0, sizeof(DescLenOrIndArray));  
memset(PartIDIndArray, 0, sizeof(PartIDIndArray));  
memset(PriceIndArray, 0, sizeof(PriceIndArray));  
  
// Set the SQL_ATTR_PARAM_BIND_TYPE statement attribute to use  
// column-wise binding.  
SQLSetStmtAttr(hstmt, SQL_ATTR_PARAM_BIND_TYPE, SQL_PARAM_BIND_BY_COLUMN, 0);  
  
// Specify the number of elements in each parameter array.  
SQLSetStmtAttr(hstmt, SQL_ATTR_PARAMSET_SIZE, ARRAY_SIZE, 0);  
  
// Specify an array in which to return the status of each set of  
// parameters.  
SQLSetStmtAttr(hstmt, SQL_ATTR_PARAM_STATUS_PTR, ParamStatusArray, 0);  
  
// Specify an SQLUINTEGER value in which to return the number of sets of  
// parameters processed.  
SQLSetStmtAttr(hstmt, SQL_ATTR_PARAMS_PROCESSED_PTR, &ParamsProcessed, 0);  
  
// Bind the parameters in column-wise fashion.  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_ULONG, SQL_INTEGER, 5, 0,  
                  PartIDArray, 0, PartIDIndArray);  
SQLBindParameter(hstmt, 2, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR, DESC_LEN - 1, 0,  
                  DescArray, DESC_LEN, DescLenOrIndArray);  
SQLBindParameter(hstmt, 3, SQL_PARAM_INPUT, SQL_C_FLOAT, SQL_REAL, 7, 0,  
                  PriceArray, 0, PriceIndArray);  
  
// Set part ID, description, and price.  
for (i = 0; i < ARRAY_SIZE; i++) {  
   GetNewValues(&PartIDArray[i], DescArray[i], &PriceArray[i]);  
   PartIDIndArray[i] = 0;  
   DescLenOrIndArray[i] = SQL_NTS;  
   PriceIndArray[i] = 0;  
}  
  
// Execute the statement.  
SQLExecDirect(hstmt, Statement, SQL_NTS);  
  
// Check to see which sets of parameters were processed successfully.  
for (i = 0; i < ParamsProcessed; i++) {  
   printf("Parameter Set  Status\n");  
   printf("-------------  -------------\n");  
   switch (ParamStatusArray[i]) {  
      case SQL_PARAM_SUCCESS:  
      case SQL_PARAM_SUCCESS_WITH_INFO:  
         printf("%13d  Success\n", i);  
         break;  
  
      case SQL_PARAM_ERROR:  
         printf("%13d  Error\n", i);  
         break;  
  
      case SQL_PARAM_UNUSED:  
         printf("%13d  Not processed\n", i);  
         break;  
  
      case SQL_PARAM_DIAG_UNAVAILABLE:  
         printf("%13d  Unknown\n", i);  
         break;  
  
   }  
}  
```  
  
## <a name="row-wise-binding"></a>Zeilenbezogenes Binden  
 Bei verwendung der zeilenweisen Bindung definiert eine Anwendung eine Struktur für jeden Satz von Parametern. Die Struktur enthält ein oder zwei Elemente für jeden Parameter. Das erste Element enthält den Parameterwert, und das zweite Element enthält den Längen-/Indikatorpuffer. Die Anwendung weist dann ein Array dieser Strukturen zu, das so viele Elemente enthält, wie Werte für jeden Parameter vorhanden sind.  
  
 Die Anwendung deklariert die Größe der Struktur für den Treiber mit dem Attribut SQL_ATTR_PARAM_BIND_TYPE.- Die Anwendung bindet die Adressen der Parameter in der ersten Struktur des Arrays. So kann der Fahrer die Adresse der Daten für eine bestimmte Zeile und Spalte als  
  
```  
Address = Bound Address + ((Row Number - 1) * Structure Size) + Offset  
```  
  
 wobei Zeilen von 1 bis zur Größe des Parametersatzes nummeriert werden. Der Offset, sofern definiert, ist der Wert, auf den das Attribut SQL_ATTR_PARAM_BIND_OFFSET_PTR Anweisung zeigt. Die folgende Abbildung zeigt, wie zeilenweise Bindung funktioniert. Die Parameter können in beliebiger Reihenfolge in der Struktur platziert werden, werden aber aus Gründen der Übersichtlichkeit in sequenzieller Reihenfolge angezeigt.  
  
 ![Zeigt, wie Die&#45;weise Bindung funktioniert](../../../odbc/reference/develop-app/media/pr32.gif "pr32")  
  
 Der folgende Code erstellt eine Struktur mit Elementen für die Werte, die in den Spalten PartID, Beschreibung und Preis gespeichert werden sollen. Anschließend wird ein 10-Element-Array dieser Strukturen zugewiesen und mithilfe der zeilenweisen Bindung an Parameter für die Spalten PartID, Description und Price gebunden. Anschließend wird eine Anweisung ausgeführt, um 10 Zeilen einzufügen.  
  
```  
#define DESC_LEN 51  
#define ARRAY_SIZE 10  
  
typedef tagPartStruct {  
   SQLREAL       Price;  
   SQLUINTEGER   PartID;  
   SQLCHAR       Desc[DESC_LEN];  
   SQLINTEGER    PriceInd;  
   SQLINTEGER    PartIDInd;  
   SQLINTEGER    DescLenOrInd;  
} PartStruct;  
  
PartStruct PartArray[ARRAY_SIZE];  
SQLCHAR *      Statement = "INSERT INTO Parts (PartID, Description,  
                Price) "  
               "VALUES (?, ?, ?)";  
SQLUSMALLINT   i, ParamStatusArray[ARRAY_SIZE];  
SQLULEN ParamsProcessed;  
  
// Set the SQL_ATTR_PARAM_BIND_TYPE statement attribute to use  
// column-wise binding.  
SQLSetStmtAttr(hstmt, SQL_ATTR_PARAM_BIND_TYPE, sizeof(PartStruct), 0);  
  
// Specify the number of elements in each parameter array.  
SQLSetStmtAttr(hstmt, SQL_ATTR_PARAMSET_SIZE, ARRAY_SIZE, 0);  
  
// Specify an array in which to return the status of each set of  
// parameters.  
SQLSetStmtAttr(hstmt, SQL_ATTR_PARAM_STATUS_PTR, ParamStatusArray, 0);  
  
// Specify an SQLUINTEGER value in which to return the number of sets of  
// parameters processed.  
SQLSetStmtAttr(hstmt, SQL_ATTR_PARAMS_PROCESSED_PTR, &ParamsProcessed, 0);  
  
// Bind the parameters in row-wise fashion.  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_ULONG, SQL_INTEGER, 5, 0,  
                  &PartArray[0].PartID, 0, &PartArray[0].PartIDInd);  
SQLBindParameter(hstmt, 2, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR, DESC_LEN - 1, 0,  
                  PartArray[0].Desc, DESC_LEN, &PartArray[0].DescLenOrInd);  
SQLBindParameter(hstmt, 3, SQL_PARAM_INPUT, SQL_C_FLOAT, SQL_REAL, 7, 0,  
                  &PartArray[0].Price, 0, &PartArray[0].PriceInd);  
  
// Set part ID, description, and price.  
for (i = 0; i < ARRAY_SIZE; i++) {  
   GetNewValues(&PartArray[i].PartID, PartArray[i].Desc, &PartArray[i].Price);  
   PartArray[0].PartIDInd = 0;  
   PartArray[0].DescLenOrInd = SQL_NTS;  
   PartArray[0].PriceInd = 0;  
}  
  
// Execute the statement.  
SQLExecDirect(hstmt, Statement, SQL_NTS);  
  
// Check to see which sets of parameters were processed successfully.  
for (i = 0; i < ParamsProcessed; i++) {  
   printf("Parameter Set  Status\n");  
   printf("-------------  -------------\n");  
   switch (ParamStatusArray[i]) {  
      case SQL_PARAM_SUCCESS:  
      case SQL_PARAM_SUCCESS_WITH_INFO:  
         printf("%13d  Success\n", i);  
         break;  
  
      case SQL_PARAM_ERROR:  
         printf("%13d  Error\n", i);  
         break;  
  
      case SQL_PARAM_UNUSED:  
         printf("%13d  Not processed\n", i);  
         break;  
  
      case SQL_PARAM_DIAG_UNAVAILABLE:  
         printf("%13d  Unknown\n", i);  
         break;  
  
   }  
```
