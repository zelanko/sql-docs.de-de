---
title: Regeln für Konvertierungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- numeric data type [ODBC], literals
- conversions with numeric literals [ODBC]
- numeric literals [ODBC]
- literals [ODBC], numeric
ms.assetid: 89f846a3-001d-496a-9843-ac9c38dc1762
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c49177d62fffc3b3b5c47a25bf3fb421d7564245
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305086"
---
# <a name="rules-for-conversions"></a>Regeln für Konvertierungen
Die Regeln in diesem Abschnitt gelten für Konvertierungen, die numerische Literale einschließen. Für diese Regeln sind die folgenden Begriffe definiert:  
  
-   *Speicherzuweisung:* Beim Senden von Daten an eine Tabellenspalte in einer-Datenbank. Dies tritt bei Aufrufen von **SQLExecute**, **SQLExecDirect**und **SQLSetPos**auf. Während der Speicherzuweisung bezieht sich "target" auf eine Daten Bank Spalte, und "Source" bezieht sich auf Daten in Anwendungs Puffern.  
  
-   *Abruf Zuweisung:* Beim Abrufen von Daten aus der Datenbank in Anwendungs Puffer. Dies tritt bei Aufrufen von **SQLFetch**, **SQLGetData**, **SQLFetchScroll**und **SQLSetPos**auf. Während der Abruf Zuweisung bezieht sich "target" auf die Anwendungs Puffer, und "Quelle" bezieht sich auf die Daten Bank Spalte.  
  
-   *CS:* Der Wert in der zeichenquelle.  
  
-   *NT:* Der Wert im numerischen Ziel.  
  
-   *NS:* Der Wert in der numerischen Quelle.  
  
-   *CT:* Der Wert im Zeichen Ziel.  
  
-   Genauigkeit eines exakten numerischen Literals: die Anzahl der enthaltenen Ziffern.  
  
-   Die Skala eines exakten numerischen Literals: die Anzahl der Ziffern rechts neben dem ausgedrückten oder impliziten Zeitraum.  
  
-   Die Genauigkeit eines ungefähren numerischen Literals: die Genauigkeit der Mantisse.  
  
## <a name="character-source-to-numeric-target"></a>Zeichenquelle zum numerischen Ziel  
 Im folgenden werden die Regeln für die Umstellung von einer zeichenquelle (CS) in ein numerisches Ziel (NT) aufgeführt:  
  
1.  Ersetzen Sie CS durch den Wert, der durch Entfernen aller führenden oder nachfolgenden Leerzeichen in CS abgerufen wird. Wenn CS keine gültige *numerische Literale*ist, wird SQLSTATE 22018 (ungültiger Zeichen Wert für Umwandlungs Spezifikation) zurückgegeben.  
  
2.  Ersetzen Sie CS durch den Wert, den Sie erhalten haben, indem Sie führende Nullen vor dem Dezimaltrennzeichen, nachfolgende Nullen nach dem Dezimaltrennzeichen oder beides entfernen.  
  
3.  Konvertieren von CS in NT. Wenn die Konvertierung zu einem Verlust signifikanter Ziffern führt, wird SQLSTATE 22003 (numerischer Wert außerhalb des gültigen Bereichs) zurückgegeben. Wenn die Konvertierung zu einem Verlust nicht signifikanter Ziffern führt, wird SQLSTATE 01s07 (Bruchteil der Bruchteil) zurückgegeben.  
  
## <a name="numeric-source-to-character-target"></a>Numerische Quelle zum Zeichen Ziel  
 Im folgenden werden die Regeln für die Umstellung von einer numerischen Quelle (NS) in ein Zeichen Ziel (CT) aufgeführt:  
  
1.  LT ist die Länge in Zeichen von CT. Bei der Abruf Zuweisung entspricht lt der Länge des Puffers in Zeichen abzüglich der Anzahl von Bytes im NULL-Beendigungs Zeichen für diesen Zeichensatz.  
  
2.  Denen  
  
    -   Wenn NS ein genauer numerischer Typ ist, lassen Sie den Wert für die kürzeste Zeichenfolge, die der Definition von *Exact-numeric-Literale* entspricht, damit identisch sein, dass die Skala von "YP" mit der Skala von NS identisch ist, und der interpretierte Wert von "YP" ist der absolute Wert von "NS".  
  
    -   Wenn NS ein Ungefährer numerischer Typ ist, lassen Sie die folgende Zeichenfolge aus:  
  
         Schreibweise:  
  
         Wenn NS gleich 0 ist, ist der Wert 0.  
  
         Let ysn ist die kürzeste Zeichenfolge, die der Definition von Exact-*numeric-Literale* entspricht und deren interpretierter Wert der absolute Wert von NS ist. Wenn die Länge von ysn kleiner als der (*Precision* + 1) des Datentyps NS ist, lassen Sie den Wert von "typiysn".  
  
         Andernfalls ist "YP" die kürzeste Zeichenfolge, die der Definition des *ungefähren numerischen Literals* entspricht, dessen interpretierter Wert der absolute Wert von NS ist und dessen *Mantisse* aus einer einzelnen *Ziffer* , die nicht "0" ist, gefolgt von einem *Zeitraum* und einer *Ganzzahl ohne*Vorzeichen besteht.  
  
3.  Schreibweise:  
  
    -   Wenn NS kleiner als 0 ist, lassen Sie die folgenden Schritte durchführen:  
  
         "-"  &#124;&#124; YP  
  
         wobei ' &#124;&#124; ' der Operator für die Zeichen folgen Verkettung ist.  
  
         Andernfalls ist Y gleich.  
  
4.  Die Länge in Zeichen Y.  
  
5.  Schreibweise:  
  
    -   Wenn der Wert lt ist, wird CT auf Y festgelegt.  
  
    -   Wenn ly kleiner als lt ist, wird CT auf der rechten Seite durch die entsprechende Anzahl von Leerzeichen auf Y erweitert festgelegt.  
  
         Andernfalls (ly > lt) kopieren Sie die ersten lt-Zeichen von Y in CT.  
  
         Schreibweise:  
  
         Wenn es sich um eine Speicherzuweisung handelt, geben Sie den Fehler SQLSTATE 22001 (String Data, Right-truncated) zurück.  
  
         Wenn dies eine Abruf Zuweisung ist, wird die Warnung SQLSTATE 01004 (String Data, Right-truncated) zurückgegeben. Wenn der Kopiervorgang zum Verlust von Bruch Ziffern führt (außer nachfolgende Nullen), wird der Treiber definiert, ob einer der folgenden Punkte zutrifft:  
  
         (1) der Treiber verkürzt die Zeichenfolge in Y auf eine geeignete Skala (die ebenfalls NULL sein kann) und schreibt das Ergebnis in CT.  
  
         (2) der Treiber rundet die Zeichenfolge in Y auf eine entsprechende Skala (die ebenfalls NULL sein kann) und schreibt das Ergebnis in CT.  
  
         (3) der Treiber wird weder abgeschnitten noch gerundet, sondern kopiert lediglich die ersten lt-Zeichen von Y in CT.
