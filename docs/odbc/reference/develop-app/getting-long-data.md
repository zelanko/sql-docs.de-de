---
title: Erhalten langer Daten | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: da901c22eb26af063397b4af184179ebe5c75924
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298990"
---
# <a name="getting-long-data"></a>Abrufen von Long-Daten
DBMS definieren *lange Daten* als beliebige Zeichen- oder Binärdaten über eine bestimmte Größe, z. B. 255 Zeichen. Diese Daten können klein genug sein, um in einem einzelnen Puffer gespeichert zu werden, z. B. eine Teilbeschreibung von mehreren tausend Zeichen. Es kann jedoch zu lange dauern, um im Arbeitsspeicher gespeichert zu werden, z. B. lange Textdokumente oder Bitmaps. Da solche Daten nicht in einem einzelnen Puffer gespeichert werden können, werden sie in Teilen mit **SQLGetData** vom Treiber abgerufen, nachdem die anderen Daten in der Zeile abgerufen wurden.  
  
> [!NOTE]  
>  Eine Anwendung kann tatsächlich jede Art von Daten mit **SQLGetData**abrufen, nicht nur lange Daten, obwohl nur Zeichen- und Binärdaten in Teilen abgerufen werden können. Wenn die Daten jedoch klein genug sind, um in einen einzelnen Puffer zu passen, gibt es im Allgemeinen keinen Grund, **SQLGetData**zu verwenden. Es ist viel einfacher, einen Puffer an die Spalte zu binden und den Treiber die Daten im Puffer zurückgeben zu lassen.  
  
 Um lange Daten aus einer Spalte abzurufen, ruft eine Anwendung zuerst **SQLFetchScroll** oder **SQLFetch** auf, um in eine Zeile zu wechseln und die Daten für gebundene Spalten abzurufen. Die Anwendung ruft dann **SQLGetData**auf. **SQLGetData** hat die gleichen Argumente wie **SQLBindCol**: ein Anweisungshandle; eine Spaltennummer; den C-Datentyp, die Adresse und die Bytelänge einer Anwendungsvariablen; und die Adresse eines Längen-/Indikatorpuffers. Beide Funktionen haben die gleichen Argumente, da sie im Wesentlichen die gleiche Aufgabe ausführen: Beide beschreiben eine Anwendungsvariable für den Treiber und geben an, dass die Daten für eine bestimmte Spalte in dieser Variablen zurückgegeben werden sollen. Die Hauptunterschiede bestehen darin, dass **SQLGetData** aufgerufen wird, nachdem eine Zeile abgerufen wurde (und aus diesem Grund manchmal als *späte Bindung* bezeichnet wird) und dass die von **SQLGetData** angegebene Bindung nur für die Dauer des Aufrufs gilt.  
  
 In Bezug auf eine einzelne Spalte verhält sich **SQLGetData** wie **SQLFetch:** Es ruft die Daten für die Spalte ab, konvertiert sie in den Typ der Anwendungsvariablen und gibt sie in dieser Variablen zurück. Außerdem wird die Bytelänge der Daten im Längen-/Indikatorpuffer zurückgegeben. Weitere Informationen dazu, wie **SQLFetch** Daten zurückgibt, finden Sie unter [Abrufen einer Datenzeile](../../../odbc/reference/develop-app/fetching-a-row-of-data.md).  
  
 **SQLGetData** unterscheidet sich in einer wichtigen Hinsicht von **SQLFetch.** Wenn er für dieselbe Spalte mehr als einmal nacheinander aufgerufen wird, gibt jeder Aufruf einen aufeinanderfolgenden Teil der Daten zurück. Jeder Aufruf mit Ausnahme des letzten Aufrufs gibt SQL_SUCCESS_WITH_INFO und SQLSTATE 01004 zurück (String-Daten, rechts abgeschnitten); Der letzte Anruf gibt SQL_SUCCESS zurück. Auf diese Weise wird **SQLGetData** verwendet, um lange Daten in Teilen abzurufen. Wenn keine weiteren Daten zurückgegeben werden können, gibt **SQLGetData** SQL_NO_DATA zurück. Die Anwendung ist für das Zusammensetzen der langen Daten verantwortlich, was bedeuten kann, dass die Teile der Daten verkettet werden. Jedes Teil ist null-beendet; Die Anwendung muss das Null-Beendigungszeichen entfernen, wenn die Teile verkettet werden. Das Abrufen von Daten in Teilen kann für Lesezeichen variabler Länge sowie für andere lange Daten erfolgen. Der im Längen-Indikator-Puffer zurückgegebene Wert verringert sich in jedem Aufruf um die Anzahl der Bytes, die beim vorherigen Aufruf zurückgegeben wurden, obwohl es üblich ist, dass der Treiber die Menge der verfügbaren Daten nicht ermitteln und eine Bytelänge von SQL_NO_TOTAL zurückgeben kann. Beispiel:  
  
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
  
 Es gibt mehrere Einschränkungen für die Verwendung von **SQLGetData**. Im Allgemeinen werden Spalten, auf die mit **SQLGetData**zugegriffen wird:  
  
-   Es muss in der Reihenfolge der steigenden Spaltennummer zugegriffen werden (aufgrund der Art und Weise, wie die Spalten eines Resultsets aus der Datenquelle gelesen werden). Beispielsweise ist es ein Fehler, **SQLGetData** für Spalte 5 aufzurufen und dann für Spalte 4 aufzurufen.  
  
-   Kann nicht gebunden werden.  
  
-   Es muss eine höhere Spaltennummer als die letzte gebundene Spalte haben. Wenn die letzte gebundene Spalte beispielsweise Spalte 3 ist, ist es ein Fehler, **SQLGetData** für Spalte 2 aufzurufen. Aus diesem Grund sollten Anwendungen sicherstellen, dass lange Datenspalten am Ende der Auswahlliste platziert werden.  
  
-   Kann nicht verwendet werden, wenn **SQLFetch** oder **SQLFetchScroll** aufgerufen wurden, um mehr als eine Zeile abzurufen. Weitere Informationen finden Sie unter [Verwenden von Blockcursors](../../../odbc/reference/develop-app/using-block-cursors.md).  
  
 Einige Treiber erzwingen diese Einschränkungen nicht. Interoperable Anwendungen sollten entweder davon ausgehen, dass sie vorhanden sind, oder bestimmen, welche Einschränkungen nicht erzwungen werden, indem **SQLGetInfo** mit der Option SQL_GETDATA_EXTENSIONS aufgerufen wird.  
  
 Wenn die Anwendung nicht alle Daten in einer Zeichen- oder Binärdatenspalte benötigt, kann sie den Netzwerkverkehr in DBMS-basierten Treibern reduzieren, indem das Attribut SQL_ATTR_MAX_LENGTH Anweisung vor der Ausführung der Anweisung gesetzt wird. Dadurch wird die Anzahl der Bytes von Daten eingeschränkt, die für ein beliebiges Zeichen oder eine binäre Spalte zurückgegeben werden. Angenommen, eine Spalte enthält lange Textdokumente. Eine Anwendung, die die Tabelle mit dieser Spalte durchsucht, muss möglicherweise nur die erste Seite jedes Dokuments anzeigen. Obwohl dieses Anweisungsattribut im Treiber simuliert werden kann, gibt es keinen Grund, dies zu tun. Wenn eine Anwendung Zeichen- oder Binärdaten abschneiden möchte, sollte sie insbesondere einen kleinen Puffer mit **SQLBindCol** an die Spalte binden und den Treiber die Daten abschneiden lassen.
