---
title: Abrufen von Long-Daten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- long data [ODBC]
- fetches [ODBC], long data
- result sets [ODBC], fetching
- SQLGetData function [ODBC], getting long data
- retrieving long data [ODBC]
ms.assetid: 6ccb44bc-8695-4bad-91af-363ef22bdb85
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 49f0023f726dd4bb290ffba1018ce2608800dd90
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68216359"
---
# <a name="getting-long-data"></a>Abrufen von Long-Daten
Definieren eines DBMS *long-Daten* als beliebiges Zeichen oder Binärdaten über eine bestimmte Größe, wie z. B. 255 Zeichen lang sein. Diese Daten möglicherweise klein genug, um in einem einzigen Puffer, z. B. eine Beschreibung für den mehrere Tausend Zeichen gespeichert werden. Allerdings kann es zu lange im Arbeitsspeicher, z. B. langer Text-Dateien oder Bitmaps gespeichert sein. Da solche Daten nicht in einem einzigen Puffer gespeichert werden können, wird sie abgerufen, Webparts mit dem Treiber **SQLGetData** nach die anderen Daten in die Zeile abgerufen wurde.  
  
> [!NOTE]  
>  Eine Anwendung kann eigentlich jeden Datentyp mit abrufen **SQLGetData**, Daten, nicht nur lange, obwohl nur Zeichen- und Binärdaten in Teilen abgerufen werden können. Wenn die Daten klein genug, um in einen einzelnen Puffer zu passen, gibt es ist jedoch im Allgemeinen kein Grund für die Verwendung **SQLGetData**. Es ist viel einfacher, binden einen Puffer an die Spalte und des Treibers die Daten im Puffer zurück.  
  
 Zum Abrufen von long-Daten aus einer Spalte Ruft eine Anwendung zuerst **SQLFetchScroll** oder **SQLFetch** in eine Zeile verschieben, und die Daten für die gebundenen Spalten abzurufen. Die Anwendung ruft dann **SQLGetData**. **SQLGetData** hat die gleichen Argumente wie **SQLBindCol**: ein Anweisungshandle; eine Spaltennummer; der C Typ, Adresse und Byte Datenlänge einer Anwendungsvariablen; und die Adresse des ein Längen-/Indikatorpuffer. Beide Funktionen haben die gleichen Argumenten, da sie im Wesentlichen die gleiche Aufgabe ausführen: Beide eine Anwendungsvariablen an den Treiber zu beschreiben und anzugeben, dass die Daten für eine bestimmte Spalte in der Variablen zurückgegeben werden sollen. Die Hauptunterschiede sind, die **SQLGetData** wird aufgerufen, nachdem eine Zeile abgerufen wird (und wird manchmal als *späte Bindung* aus diesem Grund) und dass die Bindung von angegebene **SQLGetData**  so lange beibehalten wird nur für die Dauer des Aufrufs.  
  
 Im Hinblick auf eine einzelne Spalte **SQLGetData** verhält sich wie **SQLFetch**: Ruft die Daten für die Spalte ab, konvertiert sie in den Typ der Anwendungsvariablen und wird in dieser Variablen zurückgegeben. Es gibt auch die Bytelänge der Daten in den Längen-/Indikatorpuffer zurück. Weitere Informationen dazu, wie **SQLFetch** gibt Daten finden Sie unter [Abrufen einer Zeile mit Daten](../../../odbc/reference/develop-app/fetching-a-row-of-data.md).  
  
 **SQLGetData** unterscheidet sich von **SQLFetch** in einen letzten wichtigen Aspekt. Wenn sie mehrmals hintereinander für dieselbe Spalte aufgerufen wird, gibt jeden Aufruf eine aufeinander folgende zusammen mit den Daten zurück. Jeder Aufruf außer dem letzten Aufruf gibt SQL_SUCCESS_WITH_INFO und SQLSTATE 01004 (Zeichenfolgendaten, rechts abgeschnitten); der letzte Aufruf gibt SQL_SUCCESS zurück. Dies ist wie **SQLGetData** dient zum Abrufen von long-Daten in Teilen. Wenn keine weiteren Daten zurückgeben, **SQLGetData** SQL_NO_DATA zurückgibt. Die Anwendung ist verantwortlich für das die langen Daten zusammenstellen, das kann bedeuten, dass die Teile der Daten verketten. Jeder Teil ist die Null-terminierte; die Anwendung muss die Null-Terminierungszeichen entfernen, wenn die Teile zu verketten. Abrufen von Daten in Webparts auch variabler Länge, die Lesezeichen wie bei anderen long-Daten möglich. Der Wert, der in den Puffer Längenindikator/nimmt ab, bei jedem Aufruf durch die Anzahl der Bytes zurückgegeben, die in den vorherigen Aufruf zurückgegeben wird, obwohl es üblich, dass der Treiber möglicherweise nicht ist auf die Menge der verfügbaren Daten ermitteln und eine Bytelänge von SQL_NO_TOTAL zurück. Zum Beispiel:  
  
```  
// Declare a binary buffer to retrieve 5000 bytes of data at a time.  
SQLCHAR       BinaryPtr[5000];  
SQLUINTEGER   PartID;  
SQLINTEGER    PartIDInd, BinaryLenOrInd, NumBytes;  
SQLRETURN     rc;   
SQLHSTMT      hstmt;  
  
// Create a result set containing the ID and picture of each part.  
SQLExecDirect(hstmt, "SELECT PartID, Picture FROM Pictures", SQL_NTS);  
  
// Bind PartID to the PartID column.  
SQLBindCol(hstmt, 1, SQL_C_ULONG, &PartID, 0, &PartIDInd);  
  
// Retrieve and display each row of data.  
while ((rc = SQLFetch(hstmt)) != SQL_NO_DATA) {  
   // Display the part ID and initialize the picture.  
   DisplayID(PartID, PartIDInd);  
   InitPicture();  
  
   // Retrieve the picture data in parts. Send each part and the number   
   // of bytes in each part to a function that displays it. The number   
   // of bytes is always 5000 if there were more than 5000 bytes   
   // available to return (cbBinaryBuffer > 5000). Code to check if   
   // rc equals SQL_ERROR or SQL_SUCCESS_WITH_INFO not shown.  
   while ((rc = SQLGetData(hstmt, 2, SQL_C_BINARY, BinaryPtr, sizeof(BinaryPtr),  
                           &BinaryLenOrInd)) != SQL_NO_DATA) {  
      NumBytes = (BinaryLenOrInd > 5000) || (BinaryLenOrInd == SQL_NO_TOTAL) ?  
                  5000 : BinaryLenOrInd;  
      DisplayNextPictPart(BinaryPtr, NumBytes);  
   }  
}  
  
// Close the cursor.  
SQLCloseCursor(hstmt);  
```  
  
 Es gibt mehrere Einschränkungen zur Verwendung von **SQLGetData**. Im allgemeinen Zugriff auf Spalten mit **SQLGetData**:  
  
-   Muss in der Reihenfolge zunehmender spaltenzahlfolge (aufgrund der Art und Weise, in die Spalten eines Resultsets aus einer Datenquelle gelesen werden) zugegriffen werden. Es ist beispielsweise ein Fehler aufgerufen **SQLGetData** für Spalte 5 und dann für die Spalte 4 aufgerufen wird.  
  
-   kann nicht gebunden werden.  
  
-   Sie müssen eine Spalte größer als der letzten gebundenen Spalte. Beispielsweise ist die letzte gebundene Spalte Spalte 3, ist es Fehler beim Aufrufen **SQLGetData** für die Spalte 2. Aus diesem Grund sollten Anwendungen, um lange Datenspalten am Ende der select-Liste zu platzieren sicherstellen.  
  
-   Kann nicht verwendet werden, wenn **SQLFetch** oder **SQLFetchScroll** war aufgerufen, um mehr als eine Zeile abzurufen. Weitere Informationen finden Sie unter [Verwenden von Blockcursorn](../../../odbc/reference/develop-app/using-block-cursors.md).  
  
 Einige Treiber erzwungen diese Einschränkungen nicht. Interoperable Anwendungen ausführen können sollten entweder annehmen, sie vorhanden ist oder bestimmen, welche Einschränkungen durch den Aufruf nicht erzwungen werden **SQLGetInfo** mit der Option SQL_GETDATA_EXTENSIONS.  
  
 Wenn die Anwendung nicht alle Daten in ein Zeichen oder eine Spalte mit binary-benötigt, können sie des Netzwerkdatenverkehrs im DBMS-basierten Treibern reduzieren, indem Sie das Anweisungsattribut SQL_ATTR_MAX_LENGTH vor der Ausführung der Anweisung festlegen. Dies schränkt die Anzahl der Datenbytes, die für alle Zeichen oder binary-Spalte zurückgegeben werden. Nehmen wir beispielsweise an, dass eine Spalte mit langen Textdokumente enthält. Eine Anwendung, die durchsucht die Tabelle, enthält diese Spalte möglicherweise nur die erste Seite der einzelnen Dokumente anzuzeigen. Obwohl dieses Anweisungsattribut im Treiber simuliert werden kann, besteht kein Grund dafür. Insbesondere, wenn eine Anwendung zum Abschneiden von Zeichen- oder Binärdaten darstellen Daten, sollten bindet, bindet es einen kleinen Puffer der Spalte mit **SQLBindCol** und lassen Sie den Treiber, die die Daten abgeschnitten.
