---
title: Abrufen von Ergebnisdaten | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLFetchScroll function
- SQL Server Native Client ODBC driver, result sets
- ODBC applications, result sets
- data types [ODBC], fetching
- SQLBindCol function
- result sets [ODBC], fetching
- fetching [ODBC]
- ODBC data types, fetching
- SQLFetch function
- SQL Server Native Client ODBC driver, data types
- SQLGetData function
ms.assetid: b289c7fb-5017-4d7e-a2d3-19401e9fc4cd
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e1d9fdfcd7bcc4f86afacc75dff5b40b77bb7b2a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304611"
---
# <a name="fetching-result-data"></a>Abrufen von Ergebnisdaten
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Eine ODBC-Anwendung bietet drei Optionen zum Abrufen von Ergebnisdaten.  
  
 Die erste Option basiert auf [SQLBindCol](../../relational-databases/native-client-odbc-api/sqlbindcol.md). Vor dem Abrufen des Resultsets verwendet die Anwendung **SQLBindCol,** um jede Spalte im Resultset an eine Programmvariable zu binden. Nachdem die Spalten gebunden wurden, überträgt der Treiber die Daten der aktuellen Zeile in die Variablen, die an die Ergebnissatzspalten gebunden sind, jedes Mal, wenn die Anwendung **SQLFetch** oder [SQLFetchScroll](../../relational-databases/native-client-odbc-api/sqlfetchscroll.md)aufruft. Der Treiber führt Datenkonvertierungen durch, wenn die Resultsetspalte und die Programmvariable verschiedene Datentypen aufweisen. Wenn die Anwendung SQL_ATTR_ROW_ARRAY_SIZE satzgrößer als 1 hat, kann sie Ergebnisspalten an Arrays von Variablen binden, die alle bei jedem Aufruf von **SQLFetchScroll**ausgefüllt werden.  
  
 Die zweite Option basiert auf [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md). Die Anwendung verwendet **SQLBindCol** nicht, um Resultsetspalten an Programmvariablen zu binden. Nach jedem Aufruf von **SQLFetch**ruft die Anwendung **SQLGetData** einmal für jede Spalte im Resultset auf. **SQLGetData** weist den Treiber an, Daten aus einer bestimmten Ergebnissatzspalte in eine bestimmte Programmvariable zu übertragen, und gibt die Datentypen der Spalte und der Variablen an. Dies ermöglicht es dem Treiber, Daten zu konvertieren, wenn die Datentypen der Ergebnisspalte und der Programmvariablen nicht übereinstimmen. **Text-,** **ntext-** und **Bildspalten** sind in der Regel zu groß, um in eine Programmvariable zu passen, können aber dennoch mit **SQLGetData**abgerufen werden. Wenn die **Text-,** **ntext-** oder **Bilddaten** in der Ergebnisspalte größer als die Programmvariable sind, gibt **SQLGetData** SQL_SUCCESS_WITH_INFO und SQLSTATE 01004 zurück (Zeichenfolgendaten, rechts abgeschnitten). Aufeinanderfolgende Aufrufe von **SQLGetData** geben aufeinanderfolgende Blöcke der **Text-** oder **Bilddaten** zurück. Wenn das Ende der Daten erreicht ist, gibt **SQLGetData** SQL_SUCCESS zurück. Jeder Abruf gibt einen Satz von Zeilen oder ein Rowset zurück, wenn SQL_ATTR_ROW_ARRAY_SIZE größer als 1 ist. Bevor Sie **SQLGetData**verwenden, müssen Sie **sqlSetPos** zuerst verwenden, um eine bestimmte Zeile innerhalb des Rowsets als aktuelle Zeile anzugeben.  
  
 Die dritte Option besteht darin, eine Mischung aus **SQLBindCol** und **SQLGetData**zu verwenden. Eine Anwendung kann z. B. die ersten zehn Spalten eines Resultsets binden und dann bei jedem Abruf **dreimal SQLGetData** aufrufen, um die Daten aus drei ungebundenen Spalten abzurufen. Dies wird in der Regel verwendet, wenn ein Resultset eine oder mehrere **Text-** oder **Bildspalten** enthält.  
  
 Abhängig von den für das Resultset festgelegten Cursoroptionen kann eine Anwendung auch die Bildlaufoptionen von **SQLFetchScroll** verwenden, um das Resultset zu umblättern.  
  
 Die übermäßige Verwendung von **SQLBindCol** zum Binden einer Ergebnissatzspalte an eine Programmvariable ist teuer, da **SQLBindCol** dazu führt, dass ein ODBC-Treiber Speicher zuweist. Wenn Sie eine Ergebnisspalte an eine Variable binden, bleibt diese Bindung so lange wirksam, bis Sie entweder [SQLFreeHandle aufrufen,](../../relational-databases/native-client-odbc-api/sqlfreehandle.md) um das Anweisungshandle freizugeben, oder [SQLFreeStmt](../../relational-databases/native-client-odbc-api/sqlfreestmt.md) aufrufen, wobei *fOption* auf SQL_UNBIND festgelegt ist. Die Bindungen werden nicht automatisch rückgängig gemacht, wenn die Anweisung abgeschlossen ist.  
  
 Diese Logik ermöglicht Ihnen das effektive Ausführen derselben SELECT-Anweisung mehrere Male mit verschiedenen Parametern. Da das Resultset die gleiche Struktur beibehält, können Sie das Resultset einmal binden, alle SELECT-Anweisungen verarbeiten und dann **SQLFreeStmt** aufrufen, wobei *fOption* nach der letzten Ausführung auf SQL_UNBIND festgelegt ist. Sie sollten **SQLBindCol** nicht aufrufen, um die Spalten in einem Resultset zu binden, ohne zuvor **SQLFreeStmt** aufzurufen, wobei *fOption* auf SQL_UNBIND festgelegt ist, um alle vorherigen Bindungen freizugeben.  
  
 Bei Verwendung von **SQLBindCol**können Sie entweder zeilen- oder spaltenweise binden. Zeilenbezogene Bindungen sind etwas schneller als spaltenbezogene Bindungen.  
  
 Sie können **SQLGetData** verwenden, um Daten spaltenweise abzurufen, anstatt Resultsetspalten mithilfe von **SQLBindCol**zu binden. Wenn ein Resultset nur wenige Zeilen enthält, ist die Verwendung von **SQLGetData** anstelle von **SQLBindCol** schneller. Andernfalls bietet **SQLBindCol** die beste Leistung. Wenn Sie die Daten nicht immer in denselben Satz von Variablen einteilen, sollten Sie **SQLGetData** verwenden, anstatt ständig neu zu binden. Sie können **SQLGetData** nur für Spalten verwenden, die sich in der Auswahlliste befinden, nachdem alle Spalten mit **SQLBindCol**gebunden sind. Die Spalte muss auch nach allen Spalten angezeigt werden, für die Sie bereits **SQLGetData**verwendet haben.  
  
 Die ODBC-Funktionen, die sich mit dem Verschieben von Daten in oder aus Programmvariablen wie **SQLGetData**, **SQLBindCol**und [SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md)befassen, unterstützen implizite Datentypkonvertierung. Wenn beispielsweise eine Anwendung eine Spalte mit ganzen Zahlen an eine Zeichenfolgen-Programmvariable bindet, konvertiert der Treiber automatisch die Daten aus einer ganzen Zahl in ein Zeichen, bevor sie in der Programmvariablen abgelegt werden.  
  
 Datenkonvertierungen in Anwendungen sollten reduziert werden. Nur wenn eine Datenkonvertierung für die von der Anwendung durchgeführte Verarbeitung erforderlich ist, sollten Anwendungen Spalten und Parameter an Programmvariablen desselben Datentyps binden. Wenn die Daten von einem Typ in einen anderen konvertiert werden müssen, ist es effektiver, wenn der Treiber die Konvertierung durchführt, anstatt dies in der Anwendung durchzuführen. Der ODBC-Treiber für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client überträgt normalerweise einfach Daten direkt aus den Netzwerkpuffern an die Variablen der Anwendung. Wenn Sie die Datenkonvertierung durch den Treiber anfordern, zwingt dies den Treiber, die Daten zu puffern und CPU-Zyklen für das Konvertieren der Daten zu verwenden.  
  
 Programmvariablen sollten groß genug sein, um Daten aufzunehmen, die aus einer Spalte übertragen werden, mit Ausnahme von **Text-,** **ntext-** und **Bilddaten.** Wenn eine Anwendung versucht, Resultsetdaten abzurufen und in einer Variablen abzulegen, die für die Aufnahme dieser Daten zu klein ist, generiert der Treiber eine Warnung. Dies zwingt den Treiber, Speicher für die Meldung zu belegen, und sowohl der Treiber als auch die Anwendung müssen CPU-Zyklen für die Verarbeitung der Meldung und die Durchführung der Fehlerbehandlung aufwenden. Die Anwendung sollte entweder eine Variable zuordnen, die groß genug ist, die abgerufenen Daten aufzunehmen, oder die SUBSTRING-Funktion in der Auswahlliste verwenden, um die Größe der Spalte im Resultset zu reduzieren.  
  
 Beim Verwenden von SQL_C_DEFAULT zur Angabe des Typs der C-Variablen müssen Sie mit Bedacht vorgehen. SQL_C_DEFAULT gibt an, dass der Typ der C-Variablen mit dem SQL-Datentyp der Spalte oder des Parameters übereinstimmt. Wenn SQL_C_DEFAULT für eine **ntext**-, **nchar**- oder **nvarchar-Spalte** angegeben ist, werden Unicode-Daten an die Anwendung zurückgegeben. Dies kann verschiedene Probleme verursachen, wenn die Anwendung nicht codiert wurde, um Unicode-Daten zu behandeln. Dieselben Arten von Problemen können mit dem Datentyp **uniqueidentifier** (SQL_GUID) auftreten.  
  
 **text**, **ntext**und **Image-Daten** sind in der Regel zu groß, um in eine einzelne Programmvariable zu passen, und werden in der Regel mit **SQLGetData** anstelle von **SQLBindCol**verarbeitet. Bei Verwendung von Servercursorn ist [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] der NATIVE Client ODBC-Treiber so optimiert, dass die Daten für ungebundene **Text-,** **ntext-** oder **Bildspalten** zum Zeitpunkt des Abrufens der Zeile nicht übertragen werden. Die **Text-,** **ntext-** oder **Bilddaten** werden erst dann vom Server abgerufen, wenn die Anwendung **SQLGetData** für die Spalte ausgibt.  
  
 Diese Optimierung kann auf Anwendungen angewendet werden, sodass keine **Text-,** **ntext-** oder **Bilddaten** angezeigt werden, während ein Benutzer einen Cursor nach oben und unten scrollt. Nachdem der Benutzer eine Zeile ausgewählt hat, kann die Anwendung **SQLGetData** aufrufen, um die **Text-,** **ntext-** oder **Bilddaten** abzurufen. Dadurch wird die Übertragung der **Text-,** **ntext-** oder **Bilddaten** für eine der Zeilen gespeichert, die der Benutzer nicht auswählt, und kann die Übertragung sehr großer Datenmengen speichern.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verarbeitungsergebnisse &#40;ODBC&#41;](../../relational-databases/native-client-odbc-results/processing-results-odbc.md)  
  
  
