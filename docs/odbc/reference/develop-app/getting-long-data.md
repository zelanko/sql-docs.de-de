---
title: Erhalten von langen Daten | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81298990"
---
# <a name="getting-long-data"></a>Abrufen von Long-Daten
DBMSs definiert *lange Daten* als beliebige Zeichen oder Binärdaten über eine bestimmte Größe, z. b. 255 Zeichen. Diese Daten können klein genug sein, um in einem einzelnen Puffer gespeichert zu werden, z. b. eine Teilebeschreibung von mehreren tausend Zeichen. Allerdings kann es zu lange dauern, bis Sie im Arbeitsspeicher gespeichert werden, z. b. lange Textdokumente oder Bitmaps. Da solche Daten nicht in einem einzelnen Puffer gespeichert werden können, werden Sie in Teilen mit **SQLGetData** aus dem Treiber abgerufen, nachdem die anderen Daten in der Zeile abgerufen wurden.  
  
> [!NOTE]  
>  Eine Anwendung kann tatsächlich beliebige Datentypen mit **SQLGetData**abrufen, nicht nur mit langen Daten, obwohl nur Zeichen-und Binärdaten in Teilen abgerufen werden können. Wenn die Daten jedoch klein genug für einen einzelnen Puffer sind, gibt es im Allgemeinen keinen Grund, **SQLGetData**zu verwenden. Es ist viel einfacher, einen Puffer an die Spalte zu binden, und der Treiber kann die Daten im Puffer zurückgeben lassen.  
  
 Zum Abrufen von Long-Daten aus einer Spalte Ruft eine Anwendung zuerst **SQLFetchScroll** oder **SQLFetch** auf, um zu einer Zeile zu wechseln und die Daten für gebundene Spalten abzurufen. Die Anwendung ruft dann **SQLGetData**auf. **SQLGetData** hat dieselben Argumente wie **SQLBindCol**: ein Anweisungs Handle. eine Spaltennummer. der C-Datentyp, die Adresse und die Byte Länge einer Anwendungsvariablen; und die Adresse eines Längen-/Indikatorpuffers. Beide Funktionen verfügen über dieselben Argumente, da Sie im Wesentlichen dieselbe Aufgabe ausführen: Sie beschreiben beide eine Anwendungs Variable für den Treiber und geben an, dass die Daten für eine bestimmte Spalte in der Variablen zurückgegeben werden sollen. Die Hauptunterschiede bestehen darin, dass **SQLGetData** aufgerufen wird, nachdem eine Zeile abgerufen wurde (was manchmal auch als *späte Bindung* bezeichnet wird) und dass die von **SQLGetData** angegebene Bindung nur für die Dauer des Aufrufs gilt.  
  
 In Bezug auf eine einzelne Spalte verhält sich **SQLGetData** wie **SQLFetch**: die Daten für die Spalte werden abgerufen, in den Typ der Anwendungsvariablen konvertiert und in der Variablen zurückgegeben. Außerdem wird die Byte Länge der Daten im Längen-/Indikatorpuffer zurückgegeben. Weitere Informationen zur Rückgabe von Daten durch **SQLFetch** finden Sie unter [Abrufen einer Daten Zeile](../../../odbc/reference/develop-app/fetching-a-row-of-data.md).  
  
 **SQLGetData** unterscheidet sich in einer wichtigen Hinsicht von **SQLFetch** . Wenn Sie mehr als einmal nacheinander für die gleiche Spalte aufgerufen wird, gibt jeder Aufruf einen aufeinander folgenden Teil der Daten zurück. Jeder-Befehl mit Ausnahme des letzten Aufrufes wird SQL_SUCCESS_WITH_INFO und SQLSTATE 01004 (Zeichen folgen Daten, rechts abgeschnitten) zurückgegeben. der letzte-Rückruf gibt SQL_SUCCESS zurück. Auf diese Weise wird **SQLGetData** zum Abrufen von Long-Daten in Teilen verwendet. Wenn keine weiteren Daten zurückgegeben werden können, gibt **SQLGetData** SQL_NO_DATA zurück. Die Anwendung ist dafür verantwortlich, die langen Daten zu platzieren. Dies kann bedeuten, dass die Teile der Daten verkettet werden. Jeder Teil ist NULL-terminiert. die Anwendung muss das NULL-Terminierungs Zeichen entfernen, wenn die Teile verkettet werden. Das Abrufen von Daten in Teilen kann sowohl für Lesezeichen mit variabler Länge als auch für andere lange Daten erfolgen. Der Wert, der im Längen-/Indikatorpuffer zurückgegeben wird, sinkt bei jedem-Rückruf durch die Anzahl der Bytes, die im vorherigen-Vorgang zurückgegeben wurden, obwohl der Treiber häufig nicht in der Lage ist, die Menge der verfügbaren Daten zu ermitteln und eine Byte Länge von SQL_NO_TOTAL zurückzugeben. Beispiel:  
  
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
  
 Es gibt mehrere Einschränkungen bei der Verwendung von **SQLGetData**. Allgemeine Spalten, auf die mit **SQLGetData**zugegriffen wird:  
  
-   Der Zugriff auf muss in der Reihenfolge der Erhöhung der Spaltennummer erfolgen (aufgrund der Art und Weise, wie die Spalten eines Resultsets aus der Datenquelle gelesen werden). Es ist z. b. ein Fehler, **SQLGetData** für Spalte 5 aufzurufen und ihn dann für Spalte 4 aufzurufen.  
  
-   Kann nicht gebunden werden.  
  
-   Muss eine höhere Spaltennummer als die letzte gebundene Spalte aufweisen. Wenn die letzte gebundene Spalte beispielsweise Column 3 lautet, ist es ein Fehler, **SQLGetData** für Spalte 2 aufzurufen. Aus diesem Grund sollten Anwendungen sicherstellen, dass lange Datenspalten am Ende der SELECT-Liste platziert werden.  
  
-   Kann nicht verwendet werden, wenn **SQLFetch** oder **SQLFetchScroll** aufgerufen wurde, um mehr als eine Zeile abzurufen. Weitere Informationen finden Sie unter [Verwenden von Blockcursorn](../../../odbc/reference/develop-app/using-block-cursors.md).  
  
 Einige Treiber erzwingen diese Einschränkungen nicht. Bei interoperablen Anwendungen muss entweder angenommen werden, dass Sie vorhanden sind, oder es wird festgelegt, welche Einschränkungen nicht durch den Aufruf von **SQLGetInfo** mit der Option SQL_GETDATA_EXTENSIONS  
  
 Wenn die Anwendung nicht alle Daten in einer Zeichen-oder Binärdaten Spalte benötigt, kann der Netzwerk Datenverkehr in DBMS-basierten Treibern verringert werden, indem das SQL_ATTR_MAX_LENGTH-Anweisungs Attribut festgelegt wird, bevor die Anweisung ausgeführt wird. Dies schränkt die Anzahl der Daten Bytes ein, die für ein beliebiges Zeichen oder eine binäre Spalte zurückgegeben werden. Angenommen, eine Spalte enthält lange Textdokumente. Eine Anwendung, die die Tabelle durchsucht, in der diese Spalte enthalten ist, muss möglicherweise nur die erste Seite jedes Dokuments anzeigen. Obwohl dieses Anweisungs Attribut im Treiber simuliert werden kann, gibt es keinen Grund dafür. Insbesondere, wenn eine Anwendung Zeichen-oder Binärdaten Abschneiden will, sollte ein kleiner Puffer an die Spalte mit **SQLBindCol** gebunden werden, und der Treiber kann die Daten abschneiden.
