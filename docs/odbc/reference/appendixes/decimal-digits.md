---
title: Dezimalziffern | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81285160"
---
# <a name="decimal-digits"></a>Dezimalstellen
Die *Dezimal* stellen der Datentypen decimal und numeric werden als maximale Anzahl von Ziffern rechts vom Dezimaltrennzeichen oder der Skala der Daten definiert. Für ungefähre Spalten oder Parameter für Gleit Komma Zahlen ist die Skala nicht definiert, da die Anzahl der Ziffern rechts vom Dezimaltrennzeichen nicht korrigiert ist. Für DateTime-oder Interval-Daten, die eine Sekunden Komponente enthalten, werden die Dezimalziffern als die Anzahl der Ziffern rechts vom Dezimaltrennzeichen in der Komponente seconds der Daten definiert.  
  
 Bei den Datentypen SQL_DECIMAL und SQL_NUMERIC ist die maximale Skalierung in der Regel mit der maximalen Genauigkeit identisch. Einige Datenquellen erzwingen jedoch ein separates Limit für die maximale Skalierung. Um die minimale und maximale Skalierung zu ermitteln, die für einen Datentyp zulässig ist, ruft eine Anwendung **SQLGetTypeInfo**auf.  
  
 Die Dezimalstellen, die für jeden präzisen SQL-Datentyp definiert sind, sind in der folgenden Tabelle aufgeführt.  
  
|SQL-Typ|Dezimalzahlen|  
|--------------|--------------------|  
|Alle Zeichen-und Binär Typen [a]|Nicht zutreffend|  
|SQL_DECIMAL<br />SQL_NUMERIC|Die definierte Anzahl von Ziffern rechts vom Dezimaltrennzeichen. Beispielsweise ist die Skala einer Spalte, die als numerisch (10, 3) definiert ist, 3. Dies kann eine negative Zahl sein, um die Speicherung von sehr großen Zahlen ohne Exponentialnotation zu unterstützen. Beispielsweise könnte "12000" als "12" mit einer Skala von "-3" gespeichert werden.|  
|Alle exakten numerischen Typen außer SQL_DECIMAL und SQL_NUMERIC [a]|0|  
|Alle ungefähren Datentypen [a]|Nicht zutreffend|  
|SQL_TYPE_DATE und alle Intervall Typen ohne Sekunden Komponente [a]|Nicht zutreffend|  
|Alle DateTime-Typen außer SQL_TYPE_DATE und alle Intervall Typen mit einer seconds-Komponente|Die Anzahl der Ziffern auf der rechten Seite des Dezimal Trennzeichens im Sekunden Teil des Werts (Sekundenbruchteile). Diese Zahl darf nicht negativ sein.|  
|SQL_GUID|Nicht zutreffend|  
  
 [a] das *DecimalDigits* -Argument von **SQLBindParameter** wird für diesen Datentyp ignoriert.  
  
 Die Werte, die für die Dezimalstellen zurückgegeben werden, entsprechen nicht den Werten in einem Deskriptorfeld. Die Werte können je nach Datentyp entweder aus dem SQL_DESC_SCALE oder dem Feld SQL_DESC_PRECISION stammen, wie in der folgenden Tabelle dargestellt.  
  
|SQL-Typ|Deskriptorfeld, das entspricht<br /><br /> Dezimalstellen|  
|--------------|----------------------------------------------------------|  
|Alle Zeichen-und Binär Typen|Nicht zutreffend|  
|Alle exakten numerischen Typen|SCALE|  
|SQL_BIT|Nicht zutreffend|  
|Alle ungefähren numerischen Typen|Nicht zutreffend|  
|Alle DateTime-Typen|PRECISION|  
|Alle Intervall Typen mit einer Sekunden Komponente|PRECISION|  
|Alle Intervall Typen ohne Sekunden Komponente|Nicht zutreffend|
