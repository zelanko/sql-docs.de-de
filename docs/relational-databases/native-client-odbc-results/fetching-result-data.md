---
description: Abrufen von Ergebnisdaten
title: Abrufen von Ergebnisdaten | Microsoft-Dokumentation
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
ms.openlocfilehash: f30630a170463fdf7b45fb5fee851416a24889d6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88465322"
---
# <a name="fetching-result-data"></a>Abrufen von Ergebnisdaten
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Eine ODBC-Anwendung bietet drei Optionen zum Abrufen von Ergebnisdaten.  
  
 Die erste Option basiert auf [SQLBindCol](../../relational-databases/native-client-odbc-api/sqlbindcol.md). Vor dem Abrufen des Resultsets verwendet die Anwendung **SQLBindCol** , um jede Spalte im Resultset an eine Programm Variable zu binden. Nachdem die Spalten gebunden wurden, überträgt der Treiber die Daten der aktuellen Zeile in die an die Resultsetspalten gebundenen Variablen, wenn **SQLFetch** oder [SQLFetchScroll](../../relational-databases/native-client-odbc-api/sqlfetchscroll.md)von der Anwendung aufgerufen wird. Der Treiber führt Datenkonvertierungen durch, wenn die Resultsetspalte und die Programmvariable verschiedene Datentypen aufweisen. Wenn die Anwendung SQL_ATTR_ROW_ARRAY_SIZE auf einen Wert größer als 1 festgelegt ist, kann Sie Ergebnis Spalten an Variablen Arrays binden, die alle für jeden **SQLFetchScroll**-Befehl ausgefüllt werden.  
  
 Die zweite Option basiert auf [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md). Die Anwendung verwendet nicht **SQLBindCol** , um Resultsetspalten an Programmvariablen zu binden. Nach jedem Aufruf von **SQLFetch**Ruft die Anwendung **SQLGetData** einmal für jede Spalte im Resultset auf. **SQLGetData** weist den Treiber an, Daten aus einer bestimmten Resultsetspalte in eine bestimmte Programm Variable zu übertragen, und gibt die Datentypen der Spalte und der Variablen an. Dies ermöglicht es dem Treiber, Daten zu konvertieren, wenn die Datentypen der Ergebnisspalte und der Programmvariablen nicht übereinstimmen. **Text**-, **ntext**-und **Image** -Spalten sind in der Regel zu groß, um Sie in eine Programm Variable zu integrieren, können aber trotzdem mithilfe von **SQLGetData**abgerufen werden. Wenn die **Text**-, **ntext**-oder **Image** -Daten in der Ergebnisspalte größer als die Programm Variable sind, gibt **SQLGetData** SQL_SUCCESS_WITH_INFO und SQLSTATE 01004 (String Data, Right truncated) zurück. Aufeinanderfolgende Aufrufe von **SQLGetData** geben aufeinander folgende Blöcke der **Text** -oder **Bilddaten** zurück. Wenn das Ende der Daten erreicht ist, gibt **SQLGetData** SQL_SUCCESS zurück. Jeder Abruf gibt einen Satz von Zeilen oder ein Rowset zurück, wenn SQL_ATTR_ROW_ARRAY_SIZE größer als 1 ist. Vor der Verwendung von **SQLGetData**müssen Sie zuerst **SQLSetPos** verwenden, um eine bestimmte Zeile im Rowset als aktuelle Zeile anzugeben.  
  
 Die dritte Möglichkeit besteht darin, eine Mischung aus **SQLBindCol** und **SQLGetData**zu verwenden. Eine Anwendung könnte z. b. die ersten zehn Spalten eines Resultsets binden und dann bei jedem Abruf dreimal **SQLGetData** aufrufen, um die Daten aus drei ungebundenen Spalten abzurufen. Dies wird normalerweise verwendet, wenn ein Resultset mindestens eine **Text** -oder **Image** -Spalte enthält.  
  
 Abhängig von den Cursor Optionen, die für das Resultset festgelegt sind, kann eine Anwendung auch die Scrolloptionen von **SQLFetchScroll** verwenden, um einen Bildlauf um das Resultset durchzuführen.  
  
 Die übermäßige Verwendung von **SQLBindCol** , um eine Resultsetspalte an eine Programm Variable zu binden, ist aufwendig, da **SQLBindCol** bewirkt, dass ein ODBC-Treiber Arbeitsspeicher belegt. Wenn Sie eine Ergebnisspalte an eine Variable binden, bleibt diese Bindung wirksam, bis Sie entweder [SQLFreeHandle](../../relational-databases/native-client-odbc-api/sqlfreehandle.md) aufzurufen, um das Anweisungs Handle freizugeben, oder [SQLFreeStmt](../../relational-databases/native-client-odbc-api/sqlfreestmt.md) aufzurufen, wobei *fOption* auf SQL_UNBIND festgelegt ist. Die Bindungen werden nicht automatisch rückgängig gemacht, wenn die Anweisung abgeschlossen ist.  
  
 Diese Logik ermöglicht Ihnen das effektive Ausführen derselben SELECT-Anweisung mehrere Male mit verschiedenen Parametern. Da das Resultset dieselbe Struktur beibehält, können Sie das Resultset einmal binden, alle SELECT-Anweisungen verarbeiten und dann **SQLFreeStmt** mit der *Option fOption* auf SQL_UNBIND nach der letzten Ausführung festlegen. Sie sollten **SQLBindCol** nicht aufrufen, um die Spalten in einem Resultset zu binden, ohne zuerst **SQLFreeStmt** aufzurufen, wobei *fOption* auf SQL_UNBIND festgelegt ist, um vorherige Bindungen freizugeben.  
  
 Wenn Sie **SQLBindCol**verwenden, können Sie entweder zeilenweise oder spaltenweise Bindung durchführen. Zeilenbezogene Bindungen sind etwas schneller als spaltenbezogene Bindungen.  
  
 Sie können **SQLGetData** verwenden, um Daten auf Spalten Basis abzurufen, anstatt Resultsetspalten mithilfe von **SQLBindCol**zu binden. Wenn ein Resultset nur wenige Zeilen enthält, ist die Verwendung von **SQLGetData** anstelle von **SQLBindCol** schneller. Andernfalls bietet **SQLBindCol** die beste Leistung. Wenn Sie die Daten nicht immer im selben Satz von Variablen ablegen, sollten Sie **SQLGetData** anstelle der ständig erneuten Bindung verwenden. Sie können **SQLGetData** nur für Spalten verwenden, die in der SELECT-Liste enthalten sind, nachdem alle Spalten mit **SQLBindCol**gebunden wurden. Die Spalte muss auch nach allen Spalten angezeigt werden, für die Sie **SQLGetData**bereits verwendet haben.  
  
 Die ODBC-Funktionen, die sich mit dem Verschieben von Daten in oder aus Programmvariablen wie **SQLGetData**, **SQLBindCol**und [SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md)befassen, unterstützen die implizite Datentyp Konvertierung. Wenn beispielsweise eine Anwendung eine Spalte mit ganzen Zahlen an eine Zeichenfolgen-Programmvariable bindet, konvertiert der Treiber automatisch die Daten aus einer ganzen Zahl in ein Zeichen, bevor sie in der Programmvariablen abgelegt werden.  
  
 Datenkonvertierungen in Anwendungen sollten reduziert werden. Nur wenn eine Datenkonvertierung für die von der Anwendung durchgeführte Verarbeitung erforderlich ist, sollten Anwendungen Spalten und Parameter an Programmvariablen desselben Datentyps binden. Wenn die Daten von einem Typ in einen anderen konvertiert werden müssen, ist es effektiver, wenn der Treiber die Konvertierung durchführt, anstatt dies in der Anwendung durchzuführen. Der ODBC-Treiber für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client überträgt normalerweise einfach Daten direkt aus den Netzwerkpuffern an die Variablen der Anwendung. Wenn Sie die Datenkonvertierung durch den Treiber anfordern, zwingt dies den Treiber, die Daten zu puffern und CPU-Zyklen für das Konvertieren der Daten zu verwenden.  
  
 Programmvariablen sollten groß genug sein, um Daten zu speichern, die aus einer Spalte übertragen wurden, mit Ausnahme von **Text**-, **ntext**-und **Image** -Daten. Wenn eine Anwendung versucht, Resultsetdaten abzurufen und in einer Variablen abzulegen, die für die Aufnahme dieser Daten zu klein ist, generiert der Treiber eine Warnung. Dies zwingt den Treiber, Speicher für die Meldung zu belegen, und sowohl der Treiber als auch die Anwendung müssen CPU-Zyklen für die Verarbeitung der Meldung und die Durchführung der Fehlerbehandlung aufwenden. Die Anwendung sollte entweder eine Variable zuordnen, die groß genug ist, die abgerufenen Daten aufzunehmen, oder die SUBSTRING-Funktion in der Auswahlliste verwenden, um die Größe der Spalte im Resultset zu reduzieren.  
  
 Beim Verwenden von SQL_C_DEFAULT zur Angabe des Typs der C-Variablen müssen Sie mit Bedacht vorgehen. SQL_C_DEFAULT gibt an, dass der Typ der C-Variablen mit dem SQL-Datentyp der Spalte oder des Parameters übereinstimmt. Wenn SQL_C_DEFAULT für eine **ntext**-, **NCHAR**-oder **nvarchar** -Spalte angegeben ist, werden Unicode-Daten an die Anwendung zurückgegeben. Dies kann verschiedene Probleme verursachen, wenn die Anwendung nicht codiert wurde, um Unicode-Daten zu behandeln. Die gleichen Probleme können mit dem Datentyp **uniqueidentifier** (SQL_GUID) auftreten.  
  
 **Text**-, **ntext**-und **Image** -Daten sind in der Regel zu groß, um in eine einzelne Programm Variable zu passen, und werden in der Regel mit **SQLGetData** anstelle von **SQLBindCol**verarbeitet. Bei der Verwendung von Server Cursorn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird der Native Client-ODBC-Treiber so optimiert, dass die Daten für ungebundene **Text**-, **ntext**-oder **Image** -Spalten zum Zeitpunkt der Zeilen Abruf nicht übertragen werden. Die **Text**-, **ntext**-oder **Image** -Daten werden erst dann vom Server abgerufen, wenn die Anwendung **SQLGetData** für die Spalte ausgibt.  
  
 Diese Optimierung kann auf Anwendungen angewendet werden, sodass keine Text-, **ntext**-oder **Image** -Daten angezeigt werden, während ein Benutzer einen **Bildlauf**nach oben oder unten durchführt. Nachdem der Benutzer eine Zeile ausgewählt hat, kann die Anwendung **SQLGetData** aufrufen, um die **Text**-, **ntext**-oder **Image** -Daten abzurufen. Dadurch wird die Übertragung von **Text**-, **ntext**-oder **Image** -Daten für alle Zeilen, die der Benutzer nicht ausgewählt hat, und die Übertragung sehr großer Datenmengen gespart.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verarbeitungsergebnisse &#40;ODBC-&#41;](../../relational-databases/native-client-odbc-results/processing-results-odbc.md)  
  
  
