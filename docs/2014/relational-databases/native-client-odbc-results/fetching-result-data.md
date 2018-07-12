---
title: Abrufen von Ergebnisdaten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
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
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2228bb8fcbc7237fabfb0239c62f512b9a223d28
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37408209"
---
# <a name="fetching-result-data"></a>Abrufen von Ergebnisdaten
  Eine ODBC-Anwendung bietet drei Optionen zum Abrufen von Ergebnisdaten.  
  
 Die erste Option basiert auf [SQLBindCol](../native-client-odbc-api/sqlbindcol.md). Vor dem Abrufen des Resultsets verwendet die Anwendung **SQLBindCol** jede Spalte im Resultset an eine Programmvariable zu binden. Nachdem die Spalten gebunden wurden, Zeit überträgt der Treiber, die die Daten der aktuellen Zeile in der Variablen an die Resultsetspalten jede Ruft die Anwendung **SQLFetch** oder [SQLFetchScroll](../native-client-odbc-api/sqlfetchscroll.md). Der Treiber führt Datenkonvertierungen durch, wenn die Resultsetspalte und die Programmvariable verschiedene Datentypen aufweisen. Wenn die Anwendung SQL_ATTR_ROW_ARRAY_SIZE größer als 1 festgelegt wurde, kann bindet, bindet es Ergebnisspalten an Arrays von Variablen, die alle bei jedem Aufruf gefüllt werden **SQLFetchScroll**.  
  
 Die zweite Option basiert auf [SQLGetData](../native-client-odbc-api/sqlgetdata.md). Die Anwendung verwendet keine **SQLBindCol** Ergebnis binden Resultsetspalten an Programmvariablen. Nach jedem Anruf **SQLFetch**, die Anwendung ruft **SQLGetData** einmal für jede Spalte im Ergebnis festgelegt. **SQLGetData** weist den Treiber an den Daten aus einer bestimmten Resultsetspalte in eine spezielle Programmvariable zu übertragen, und gibt an, die Datentypen der Spalte und der Variablen. Dies ermöglicht es dem Treiber, Daten zu konvertieren, wenn die Datentypen der Ergebnisspalte und der Programmvariablen nicht übereinstimmen. **Text**, **Ntext**, und **Image** Spalten sind in der Regel zu groß für eine Programmvariable, aber immer noch mit abgerufen werden können **SQLGetData**. Wenn die **Text**, **Ntext**, oder **Image** Daten in der Ergebnisspalte ist größer als die Programmvariable, **SQLGetData** SQL_SUCCESS_ zurückgibt WITH_INFO und SQLSTATE 01004 (Zeichenfolgendaten, rechts abgeschnitten). Aufeinander folgende Aufrufe von **SQLGetData** aufeinanderfolgende Datenabschnitte Zurückgeben der **Text** oder **Image** Daten. Wenn das Ende der Daten erreicht ist, **SQLGetData** gibt SQL_SUCCESS zurück. Jeder Abruf gibt einen Satz von Zeilen oder ein Rowset zurück, wenn SQL_ATTR_ROW_ARRAY_SIZE größer als 1 ist. Vor der Verwendung von **SQLGetData**, müssen Sie zunächst mithilfe **SQLSetPos** an einer bestimmten Zeile im Rowset als aktuelle Zeile.  
  
 Die dritte Option ist die Verwendung der eine Mischung aus **SQLBindCol** und **SQLGetData**. Eine Anwendung könnte beispielsweise die ersten zehn Spalten eines Resultsets binden und rufen Sie dann bei jedem Abruf **SQLGetData** dreimal, um die Daten aus drei ungebundenen Spalten abzurufen. Dies wird in der Regel verwendet werden, wenn ein Resultset eine oder mehrere enthält **Text** oder **Image** Spalten.  
  
 Abhängig von den Cursoroptionen für das Resultset auf festgelegt, eine Anwendung kann auch mithilfe der Bildlauf Optionen der **SQLFetchScroll** rund um das Resultset zu scrollen.  
  
 Übermäßige Verwendung von **SQLBindCol** zum Binden einer Resultsetspalte an eine Programmvariable ist teuer da **SQLBindCol** bewirkt, dass einen ODBC-Treiber, um Speicher zu belegen. Beim Binden einer Ergebnisspalte einer Variablen, dass die Bindung bleibt wirksam, bis Sie entweder Sie rufen die [SQLFreeHandle](../native-client-odbc-api/sqlfreehandle.md) um das Anweisungshandle oder ein Aufruf freizugeben [SQLFreeStmt](../native-client-odbc-api/sqlfreestmt.md) mit *fOption* auf SQL_UNBIND gesetzt ist. Die Bindungen werden nicht automatisch rückgängig gemacht, wenn die Anweisung abgeschlossen ist.  
  
 Diese Logik ermöglicht Ihnen das effektive Ausführen derselben SELECT-Anweisung mehrere Male mit verschiedenen Parametern. Da das Resultset dieselbe Struktur beibehält, Sie können das Resultset einmal binden, verarbeiten Sie alle SELECT-Anweisungen, rufen Sie anschließend **SQLFreeStmt** mit *fOption* auf SQL_UNBIND gesetzt ist nach der letzten Ausführung. Sie sollten nicht aufrufen, **SQLBindCol** zum Binden der Spalten in einem Resultset erst nach Aufrufen von **SQLFreeStmt** mit *fOption* auf SQL_UNBIND festgelegt, um alle vorherigen Bindungen freizugeben.  
  
 Bei Verwendung **SQLBindCol**, können Sie entweder Zeilen- oder spaltenbezogene Bindung. Zeilenbezogene Bindungen sind etwas schneller als spaltenbezogene Bindungen.  
  
 Sie können **SQLGetData** zum Abrufen von Daten auf Basis von Spalten anstelle von Binden von Resultsetspalten Resultsetspalten mit **SQLBindCol**. Wenn ein Resultset auf nur ein paar Zeilen umfasst, **SQLGetData** anstelle von **SQLBindCol** schneller ist, andernfalls **SQLBindCol** bietet die beste Leistung. Wenn Sie immer nicht die Daten in den gleichen Satz von Variablen einfügen, verwenden Sie **SQLGetData** anstatt ständig neue Bindungen auszuführen. Sie können nur **SQLGetData** für Spalten, in der Auswahlliste sind, nachdem alle Spalten gebunden sind **SQLBindCol**. Die Spalte muss auch angezeigt werden, nach allen Spalten, die Sie bereits, auf dem verwendet haben **SQLGetData**.  
  
 Die ODBC-Funktionen, beim Verschieben von Daten in oder aus Programmvariablen, z. B. **SQLGetData**, **SQLBindCol**, und [SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md), unterstützen die implizite Datentypen die Konvertierung. Wenn beispielsweise eine Anwendung eine Spalte mit ganzen Zahlen an eine Zeichenfolgen-Programmvariable bindet, konvertiert der Treiber automatisch die Daten aus einer ganzen Zahl in ein Zeichen, bevor sie in der Programmvariablen abgelegt werden.  
  
 Datenkonvertierungen in Anwendungen sollten reduziert werden. Nur wenn eine Datenkonvertierung für die von der Anwendung durchgeführte Verarbeitung erforderlich ist, sollten Anwendungen Spalten und Parameter an Programmvariablen desselben Datentyps binden. Wenn die Daten von einem Typ in einen anderen konvertiert werden müssen, ist es effektiver, wenn der Treiber die Konvertierung durchführt, anstatt dies in der Anwendung durchzuführen. Der ODBC-Treiber für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client überträgt normalerweise einfach Daten direkt aus den Netzwerkpuffern an die Variablen der Anwendung. Wenn Sie die Datenkonvertierung durch den Treiber anfordern, zwingt dies den Treiber, die Daten zu puffern und CPU-Zyklen für das Konvertieren der Daten zu verwenden.  
  
 Programmvariablen sollten groß genug zum Speichern von Daten aus einer Spalte, außer im übertragen werden **Text**, **Ntext**, und **Image** Daten. Wenn eine Anwendung versucht, Resultsetdaten abzurufen und in einer Variablen abzulegen, die für die Aufnahme dieser Daten zu klein ist, generiert der Treiber eine Warnung. Dies zwingt den Treiber, Speicher für die Meldung zu belegen, und sowohl der Treiber als auch die Anwendung müssen CPU-Zyklen für die Verarbeitung der Meldung und die Durchführung der Fehlerbehandlung aufwenden. Die Anwendung sollte entweder eine Variable zuordnen, die groß genug ist, die abgerufenen Daten aufzunehmen, oder die SUBSTRING-Funktion in der Auswahlliste verwenden, um die Größe der Spalte im Resultset zu reduzieren.  
  
 Beim Verwenden von SQL_C_DEFAULT zur Angabe des Typs der C-Variablen müssen Sie mit Bedacht vorgehen. SQL_C_DEFAULT gibt an, dass der Typ der C-Variablen mit dem SQL-Datentyp der Spalte oder des Parameters übereinstimmt. Wenn SQL_C_DEFAULT für angegeben, wird ein **Ntext**, **Nchar**, oder **Nvarchar** Spalte Unicode-Daten an die Anwendung zurückgegeben werden. Dies kann verschiedene Probleme verursachen, wenn die Anwendung nicht codiert wurde, um Unicode-Daten zu behandeln. Ist möglich, die dieselbe Art von Problemen mit der **Uniqueidentifier** (SQL_GUID)-Datentyp.  
  
 **Text**, **Ntext**, und **Image** Daten ist in der Regel zu groß für eine einzige Programmvariable und wird in der Regel mit verarbeitet **SQLGetData** anstelle von **SQLBindCol**. Wenn Servercursor verwendet die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber wurde optimiert, um überträgt keine Daten für ungebundene **Text**, **Ntext**, oder **Image** Spalten in der Zeitpunkt, zu der Zeile abgerufen wird. Die **Text**, **Ntext**, oder **Image** Daten werden erst die Anwendungsprobleme nicht tatsächlich vom Server abgerufen **SQLGetData** für die die Spalte.  
  
 Diese Optimierung kann auf Anwendungen angewendet werden, damit keine **Text**, **Ntext**, oder **Image** Daten werden angezeigt, während ein Benutzer nach oben oder unten einen Cursor einen Bildlauf ist. Nachdem der Benutzer eine Zeile ausgewählt hat, kann die Anwendung aufrufen **SQLGetData** zum Abrufen der **Text**, **Ntext**, oder **Image** Daten. Dies spart übertragen die **Text**, **Ntext**, oder **Image** Daten für alle Zeilen der Benutzer wird nicht ausgewählt und kann die Übertragung sehr großer Mengen an Daten speichern.  
  
## <a name="see-also"></a>Siehe auch  
 [Verarbeiten von Ergebnissen &#40;ODBC&#41;](processing-results-odbc.md)  
  
  
