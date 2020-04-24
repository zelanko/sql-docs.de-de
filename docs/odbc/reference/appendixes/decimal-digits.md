---
title: Dezimalziffern | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- size of data types [ODBC]
- decimal digits of data types [ODBC]
- data types [ODBC], decimal digits
- SQL data types [ODBC], column characteristics
ms.assetid: 07f3d1fc-b4ee-4693-b342-330b2231b6d0
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4921a6162b6d711e657f223b5be5783dfa37bca8
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285160"
---
# <a name="decimal-digits"></a>Dezimalstellen
Die *Dezimalstellen* von Dezimal- und numerischen Datentypen werden als die maximale Anzahl von Ziffern rechts vom Dezimaltrennzeichen oder als Maßstab der Daten definiert. Bei ungefähren Gleitkommazahlenspalten oder Parametern ist der Maßstab nicht definiert, da die Anzahl der Ziffern rechts vom Dezimaltrennzeichen nicht festgelegt ist. Bei Datums- oder Intervalldaten, die eine Sekundenkomponente enthalten, werden die Dezimalstellen als die Anzahl der Ziffern rechts vom Dezimaltrennzeichen in der Sekundenkomponente der Daten definiert.  
  
 Bei den SQL_DECIMAL- und SQL_NUMERIC Datentypen entspricht die maximale Skalierung in der Regel der maximalen Genauigkeit. Einige Datenquellen legen jedoch eine separate Begrenzung für die maximale Skala fest. Um die für einen Datentyp zulässigen minimalen und maximalen Skalierungen zu bestimmen, ruft eine Anwendung **SQLGetTypeInfo**auf.  
  
 Die für jeden kurzen SQL-Datentyp definierten Dezimalstellen werden in der folgenden Tabelle angezeigt.  
  
|SQL-Typ|Dezimalzahlen|  
|--------------|--------------------|  
|Alle Zeichen- und Binärtypen[a]|–|  
|SQL_DECIMAL<br />SQL_NUMERIC|Die definierte Anzahl von Ziffern rechts vom Dezimaltrennzeichen. Der Maßstab einer Spalte, die als NUMERIC(10,3) definiert ist, ist z. B. 3. Dies kann eine negative Zahl sein, um die Speicherung sehr großer Zahlen ohne exponentielle Notation zu unterstützen. Beispielsweise könnte "12000" als "12" mit einer Skala von -3 gespeichert werden.|  
|Alle genauen numerischen Typen außer SQL_DECIMAL und SQL_NUMERIC[a]|0|  
|Alle ungefähren Datentypen[a]|–|  
|SQL_TYPE_DATE und alle Intervalltypen ohne Sekundenkomponente[a]|–|  
|Alle Datumszeittypen außer SQL_TYPE_DATE und alle Intervalltypen mit einer Sekundenkomponente|Die Anzahl der Ziffern rechts vom Dezimaltrennzeichen im Sekundenteil des Wertes (Bruchsekunden). Diese Zahl darf nicht negativ sein.|  
|SQL_GUID|–|  
  
 [a] Das *DecimalDigits-Argument* von **SQLBindParameter** wird für diesen Datentyp ignoriert.  
  
 Die für die Dezimalstellen zurückgegebenen Werte entsprechen nicht den Werten in einem Deskriptorfeld. Die Werte können je nach Datentyp entweder aus dem SQL_DESC_SCALE oder dem Feld SQL_DESC_PRECISION stammen, wie in der folgenden Tabelle dargestellt.  
  
|SQL-Typ|Deskriptorfeld entsprechend<br /><br /> Dezimalstellen|  
|--------------|----------------------------------------------------------|  
|Alle Zeichen- und Binärtypen|–|  
|Alle genauen numerischen Typen|SCALE|  
|SQL_BIT|–|  
|Alle ungefähren numerischen Typen|–|  
|Alle Datumszeittypen|PRECISION|  
|Alle Intervalltypen mit einer Sekundenkomponente|PRECISION|  
|Alle Intervalltypen ohne Sekundenkomponente|–|
