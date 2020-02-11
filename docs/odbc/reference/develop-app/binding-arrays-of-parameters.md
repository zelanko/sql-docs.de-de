---
title: Binden von Arrays von Parametern | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 597142d41ed8d3cff26891dfdcc89398543dab43
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68103821"
---
# <a name="binding-arrays-of-parameters"></a>Binden von Parameterarrays
Anwendungen, die Arrays von Parametern verwenden, binden die Arrays an die Parameter in der SQL-Anweisung. Es gibt zwei Bindungs Stile:  
  
-   Binden Sie ein Array an jeden Parameter. Jede Datenstruktur (Array) enthält alle Daten für einen einzelnen Parameter. Dies wird *spaltenweise Bindung* genannt, da eine Spalte mit Werten für einen einzelnen Parameter gebunden wird.  
  
-   Definieren Sie eine Struktur, in der die Parameterdaten für einen vollständigen Satz von Parametern enthalten sind, und binden Sie ein Array dieser Strukturen. Jede Datenstruktur enthält die Daten für eine einzelne SQL-Anweisung. Diese wird *zeilenweise Bindung* genannt, da Sie eine Zeile mit Parametern bindet.  
  
 Wenn die Anwendung einzelne Variablen an Parameter bindet, wird **SQLBindParameter** aufgerufen, um Arrays an Parameter zu binden. Der einzige Unterschied besteht darin, dass es sich bei den bestandenen Adressen um Array Adressen handelt, nicht um Einzel Variablen Adressen Die Anwendung legt das SQL_ATTR_PARAM_BIND_TYPE Statement-Attribut fest, um anzugeben, ob es spaltenweise (Standard) oder zeilenweise Bindung verwendet. Ob spaltenweise oder zeilenweise Bindung verwendet werden soll, ist größtenteils eine Frage der Anwendungs Einstellung. Abhängig davon, wie der Prozessor auf den Arbeitsspeicher zugreift, ist die zeilenweise Bindung möglicherweise schneller. Der Unterschied ist jedoch wahrscheinlich unerheblich, außer bei einer sehr großen Anzahl von Zeilen mit Parametern.  
  
## <a name="column-wise-binding"></a>Spaltenbezogenes Binden  
 Wenn die spaltenweise Bindung verwendet wird, bindet eine Anwendung ein oder zwei Arrays an jeden Parameter, für den Daten bereitgestellt werden sollen. Das erste Array enthält die Datenwerte, und das zweite Array enthält Länge/Indikator Puffer. Jedes Array enthält so viele Elemente, wie Werte für den Parameter vorhanden sind.  
  
 Die spaltenweise Bindung ist die Standardeinstellung. Die Anwendung kann auch durch Festlegen des Attributs der SQL_ATTR_PARAM_BIND_TYPE Anweisung von der Zeilen bezogenen Bindung in die spaltenweise Bindung wechseln. Die folgende Abbildung zeigt, wie die spaltenweise Bindung funktioniert.  
  
 ![Zeigt, wie die&#45;Weise Bindung von Spalten funktioniert](../../../odbc/reference/develop-app/media/pr31.gif "pr31")  
  
 Der folgende Code bindet z. b. 10-Element-Arrays an Parameter für die Spalten partid, Description und Price und führt eine-Anweisung aus, um 10 Zeilen einzufügen. Sie verwendet die spaltenweise Bindung.  
  
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
 Wenn die zeilenweise Bindung verwendet wird, definiert eine Anwendung eine Struktur für jeden Parametersatz. Die-Struktur enthält ein oder zwei-Elemente für jeden Parameter. Das erste Element enthält den Parameterwert, und das zweite Element enthält den Längen-/indikatorenpuffer. Die Anwendung ordnet dann ein Array dieser Strukturen zu, das so viele Elemente enthält, wie Werte für jeden Parameter vorhanden sind.  
  
 Die Anwendung deklariert die Größe der Struktur mit dem SQL_ATTR_PARAM_BIND_TYPE Statement-Attribut für den Treiber. Die Anwendung bindet die Adressen der Parameter in der ersten Struktur des Arrays. Daher kann der Treiber die Adresse der Daten für eine bestimmte Zeile und Spalte als  
  
```  
Address = Bound Address + ((Row Number - 1) * Structure Size) + Offset  
```  
  
 , wobei Zeilen von 1 bis zur Größe des Parameter Satzes nummeriert werden. Der Offset ist, wenn er definiert ist, der Wert, auf den das SQL_ATTR_PARAM_BIND_OFFSET_PTR-Anweisungs Attribut verweist. In der folgenden Abbildung wird gezeigt, wie die zeilenweise Bindung funktioniert. Die Parameter können in beliebiger Reihenfolge in der Struktur platziert werden, werden jedoch in sequenzieller Reihenfolge zur Verdeutlichung angezeigt.  
  
 ![Zeigt, wie die Zeilen&#45;Weise Bindung funktioniert](../../../odbc/reference/develop-app/media/pr32.gif "pr32")  
  
 Der folgende Code erstellt eine-Struktur mit-Elementen für die Werte, die in den Spalten partitiond, Description und Price gespeichert werden sollen. Anschließend wird ein 10-Element-Array dieser Strukturen zugewiesen und mithilfe der Zeilen bezogenen Bindung an Parameter für die Spalten partitiond, Description und Price gebunden. Anschließend wird eine-Anweisung ausgeführt, um 10 Zeilen einzufügen.  
  
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
