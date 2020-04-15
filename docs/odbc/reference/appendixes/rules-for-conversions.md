---
title: Regeln für Conversions | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305086"
---
# <a name="rules-for-conversions"></a>Regeln für Konvertierungen
Die Regeln in diesem Abschnitt gelten für Konvertierungen mit numerischen Literalen. Für die Zwecke dieser Regeln werden die folgenden Begriffe definiert:  
  
-   *Speicherzuweisung:* Beim Senden von Daten in eine Tabellenspalte in einer Datenbank. Dies tritt bei Aufrufen von **SQLExecute**, **SQLExecDirect**und **SQLSetPos**auf. Während der Speicherzuweisung bezieht sich "target" auf eine Datenbankspalte und "Quelle" auf Daten in Anwendungspuffern.  
  
-   *Abrufauftrag:* Beim Abrufen von Daten aus der Datenbank in Anwendungspuffer. Dies tritt bei Aufrufen von **SQLFetch**, **SQLGetData**, **SQLFetchScroll**und **SQLSetPos**auf. Bei der Abrufzuweisung bezieht sich "target" auf die Anwendungspuffer und "Quelle" auf die Datenbankspalte.  
  
-   *CS:* Der Wert in der Zeichenquelle.  
  
-   *NT:* Der Wert im numerischen Ziel.  
  
-   *NS:* Der Wert in der numerischen Quelle.  
  
-   *CT:* Der Wert im Zeichenziel.  
  
-   Genauigkeit eines genauen numerischen Literals: die Anzahl der darin enthaltenen Ziffern.  
  
-   Die Skala eines genauen numerischen Literals: die Anzahl der Ziffern rechts neben dem ausgedrückten oder impliziten Punkt.  
  
-   Die Genauigkeit eines ungefähren numerischen Liters: die Genauigkeit seiner Mantisse.  
  
## <a name="character-source-to-numeric-target"></a>Zeichenquelle zu numerischem Ziel  
 Im Folgenden sind die Regeln für die Konvertierung von einer Zeichenquelle (CS) in ein numerisches Ziel (NT) enthalten:  
  
1.  Ersetzen Sie CS durch den erhaltenen Wert, indem Sie alle führenden oder nachgestellten Leerzeichen in CS entfernen. Wenn CS kein gültiges *numerisches Literal*ist, wird SQLSTATE 22018 (Ungültiger Zeichenwert für die Umwandlungsspezifikation) zurückgegeben.  
  
2.  Ersetzen Sie CS durch den erhaltenen Wert, indem Sie führende Nullen vor dem Dezimaltrennzeichen entfernen, Nullen nach dem Dezimaltrennzeichen oder beides nachfolgen.  
  
3.  Konvertieren Sie CS in NT. Wenn die Konvertierung zu einem Verlust signifikanter Ziffern führt, wird SQLSTATE 22003 (Numeric value a of range) zurückgegeben. Wenn die Konvertierung zum Verlust nicht signifikanter Ziffern führt, wird SQLSTATE 01S07 (Fractional-Abschneide) zurückgegeben.  
  
## <a name="numeric-source-to-character-target"></a>Numerische Quelle für Zeichenziel  
 Im Folgenden sind die Regeln für die Konvertierung von einer numerischen Quelle (NS) in ein Zeichenziel (CT) enthalten:  
  
1.  Lassen Sie LT die Länge in Zeichen von CT sein. Bei der Abrufzuweisung ist LT gleich der Länge des Puffers in Zeichen abzüglich der Anzahl der Bytes im Null-Beendigungszeichen für diesen Zeichensatz.  
  
2.  Fällen:  
  
    -   Wenn NS ein exakter numerischer Typ ist, lassen Sie YP die kürzeste Zeichenfolge gleich, die der Definition von *exact-numeric-literal* entspricht, so dass die Skala von YP mit der Skala von NS identisch ist und der interpretierte Wert von YP der absolute Wert von NS ist.  
  
    -   Wenn NS ein ungefährer numerischer Typ ist, lassen Sie YP wie folgt eine Zeichenfolge sein:  
  
         Schreibweise:  
  
         Wenn NS gleich 0 ist, ist YP 0.  
  
         Lassen Sie YSN die kürzeste Zeichenfolge sein, die der Definition von*exact-numerisch-literal* entspricht und deren interpretierter Wert der absolute Wert von NS ist. Wenn die Länge von YSN kleiner als die *(Genauigkeit* + 1) des Datentyps von NS ist, lassen Sie YP gleich YSN.  
  
         Andernfalls ist YP die kürzeste Zeichenfolge, die der Definition von *ungefähr-numerischem Literal* entspricht, dessen interpretierter Wert der absolute Wert von NS ist und dessen *Mandissa* aus einer einzelnen *Ziffer* besteht, die nicht '0' ist, gefolgt von einem *Punkt* und einer *unsignierten ganzzahligen*.  
  
3.  Schreibweise:  
  
    -   Wenn NS kleiner als 0 ist, lassen Sie Y das Ergebnis sein:  
  
         '-' &#124;&#124; YP  
  
         wobei '&#124;&#124;' der Zeichenfolgenverkettungsoperator ist.  
  
         Andernfalls lassen Sie Y gleich YP.  
  
4.  Lassen Sie LY die Länge in Zeichen von Y sein.  
  
5.  Schreibweise:  
  
    -   Wenn LY LT gleich ist, wird CT auf Y gesetzt.  
  
    -   Wenn LY kleiner als LT ist, wird CT auf Y auf der rechten Seite um eine entsprechende Anzahl von Leerzeichen erweitert.  
  
         Andernfalls (LY > LT) kopieren Sie die ersten LT-Zeichen von Y in CT.  
  
         Schreibweise:  
  
         Wenn es sich um eine Speicherzuweisung handelt, geben Sie den Fehler SQLSTATE 22001 zurück (Zeichenfolgendaten, rechts abgeschnitten).  
  
         Wenn es sich um eine Abrufzuweisung handelt, geben Sie die Warnung SQLSTATE 01004 (String-Daten, rechts abgeschnitten) zurück. Wenn die Kopie zum Verlust von Bruchziffern führt (außer nachfolgenden Nullen), wird der Treiber definiert, ob eine der folgenden Folgen auftritt:  
  
         (1) Der Treiber kürt die Zeichenfolge in Y auf eine entsprechende Skala (die auch Null sein kann) und schreibt das Ergebnis in CT.  
  
         (2) Der Treiber umrundet die Zeichenfolge in Y auf eine entsprechende Skala (die auch Null sein kann) und schreibt das Ergebnis in CT.  
  
         (3) Der Fahrer kürzt und dreht sich nicht, sondern kopiert nur die ersten LT-Zeichen von Y in CT.
