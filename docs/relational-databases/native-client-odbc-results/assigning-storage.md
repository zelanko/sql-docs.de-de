---
title: Zuweisen von Speicher | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- column-wise binding [ODBC]
- SQL Server Native Client ODBC driver, result sets
- ODBC applications, result sets
- SQLBindCol function
- storing data [ODBC]
- result sets [ODBC], storage
- SQL Server Native Client ODBC driver, data storage
- row-wise binding
- binding result sets [SQL Server Native Client]
- array binding
ms.assetid: 11c81955-5300-495f-925f-9256f2587b58
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d9afee1aa24f5f3cd15791038d12f5ac0bc842fe
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "73779366"
---
# <a name="assigning-storage"></a>Zuweisen von Speicher
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Eine Anwendung kann vor oder nach der Ausführung einer SQL-Anweisung Speicher für Ergebnisse zuweisen. Wenn eine Anwendung die SQL-Anweisung zum ersten Mal vorbereitet oder ausführt, kann sie Informationen zum Resultset einholen, bevor sie Speicher für die Ergebnisse zuweist. Wenn das Resultset beispielsweise unbekannt ist, muss die Anwendung die Anzahl der Spalten abrufen, bevor sie diesen Speicher zuweisen kann.  
  
 Um Speicher für eine Datenspalte zuzuordnen, ruft eine Anwendung [SQLBindCol](../../relational-databases/native-client-odbc-api/sqlbindcol.md)auf und übergibt Sie:  
  
-   Den Datentyp, in den die Daten konvertiert werden sollen.  
  
-   Die Adresse eines Ausgabepuffers für die Daten.  
  
     Die Anwendung muss Speicher für diesen Puffer zuweisen, und der Puffer muss so groß sein, dass die Daten in dem Format, in das sie konvertiert werden sollen, darin Platz finden.  
  
-   Die Länge des Ausgabepuffers.  
  
     Dieser Wert wird ignoriert, wenn die zurückgegebenen Daten über eine feste Breite in C verfügen, z. B. eine ganze Zahl, reelle Zahl oder Datumsstruktur.  
  
-   Die Adresse eines Speicherpuffers, in den die Anzahl von Bytes verfügbarer Daten zurückgegeben werden soll.  
  
 Eine Anwendung kann auch Resultsetspalten an Arrays von Programmvariablen binden, um das Abrufen von Resultsetzeilen in Blöcken zu unterstützen. Es gibt zwei verschiedene Arten der Arraybindung:  
  
-   Die spaltenweise Bindung ist fertig gestellt, wenn jede Spalte an sein eigenes Array von Variablen gebunden wurde.  
  
     Die spaltenweise Bindung wird angegeben, indem [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) aufgerufen wird, wobei *Attribute* auf SQL_ATTR_ROW_BIND_TYPE und *ValuePtr* auf SQL_BIND_BY_COLUMN festgelegt ist. Alle Arrays müssen über die gleiche Anzahl von Elementen verfügen.  
  
-   Die zeilenweise Bindung ist fertig gestellt, wenn alle Parameter in der SQL-Anweisung als Einheit an ein Array von Strukturen gebunden wurden, die die einzelnen Variablen für die Parameter enthalten.  
  
     Die zeilenweise Bindung wird angegeben, indem **SQLSetStmtAttr** aufgerufen wird, wobei *Attribute* auf SQL_ATTR_ROW_BIND_TYPE festgelegt ist und *ValuePtr* auf die Größe der Struktur festgelegt ist, die die Variablen enthält, die die Resultsetspalten empfangen.  
  
 Die Anwendung legt zudem SQL_ATTR_ROW_ARRAY_SIZE auf die Anzahl der Elemente im Spalten- oder Zeilenarray sowie SQL_ATTR_ROW_STATUS_PTR und SQL_ATTR_ROWS_FETCHED_PTR fest.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verarbeitungsergebnisse &#40;ODBC-&#41;](../../relational-databases/native-client-odbc-results/processing-results-odbc.md)  
  
  
