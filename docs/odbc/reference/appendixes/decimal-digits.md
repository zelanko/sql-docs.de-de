---
title: Dezimalstellen | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f7b9a69941364b32e6b43d79f2d092511fd61f22
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63240994"
---
# <a name="decimal-digits"></a>Dezimalstellen
Die *Dezimalstellen* decimal und numeric-Daten-Typen als die maximale Anzahl von Ziffern rechts vom Dezimaltrennzeichen und die Skalierung der Daten definiert ist. Für die ungefähre Anzahl Gleitkomma-Spalten oder Parameter sind keine Dezimalstellen definiert, da die Anzahl der Ziffern rechts neben dem Dezimalzeichen nicht festgelegt ist. Für "DateTime" oder das Intervall-Daten, die eine Komponente für Sekunden enthält, wird als die Anzahl der Ziffern rechts vom Dezimaltrennzeichen in die Sekundenkomponente der Daten die Dezimalstellen definiert.  
  
 Für die Datentypen SQL_DECIMAL und SQL_NUMERIC ist die maximale Dezimalstellen in der Regel identisch mit der maximalen Genauigkeit. Einige Datenquellen verursachen jedoch einen separaten Grenzwert für die maximalen Dezimalstellen. Um zu bestimmen, die minimalen und maximalen Skalierungen, die für einen Datentyp zulässig, eine Anwendung ruft **SQLGetTypeInfo**.  
  
 Die Dezimalstellen für jeden präzise SQL-Datentyp definiert wird angezeigt, in der folgenden Tabelle.  
  
|SQL-Typ|Dezimalstellen|  
|--------------|--------------------|  
|Alle Zeichen- und Binärtypen [a]|–|  
|SQL_DECIMAL<br />SQL_NUMERIC|Die festgelegte Anzahl von Ziffern rechts vom Dezimaltrennzeichen an. Die Dezimalstellen einer Spalte, die als NUMERIC(10,3) definiert ist z. B. 3. Dies kann eine negative Zahl zum Speichern von sehr großen Zahlen unterstützt werden, ohne mit der Exponentialschreibweise sein; Beispielsweise könnte "12000" als "12" mit einer Skala von-3 gespeichert werden.|  
|Exakte numerische Typen als SQL_DECIMAL und SQL_NUMERIC [a]|0|  
|Alle ungefähre Datentypen [a]|–|  
|SQL_TYPE_DATE und alle Intervalltypen mit keine Sekundenkomponente [a]|–|  
|Alle Datetime-Typen mit Ausnahme von SQL_TYPE_DATE und alle Interval-Datentypen zu einer Sekundenkomponente in|Die Anzahl der Ziffern rechts vom Dezimaltrennzeichen in der Sekundenteil des Werts (Sekundenbruchteile). Diese Zahl darf nicht negativ sein.|  
|SQL_GUID|–|  
  
 [a] die *DecimalDigits* Argument **SQLBindParameter** wird für diesen Datentyp ignoriert.  
  
 Die zurückgegebenen Werte für die Dezimalstellen entsprechen nicht den Werten in jeder ein Deskriptorfeld. Die Werte können entweder die SQL_DESC_SCALE oder SQL_DESC_PRECISION Felds, je nach Datentyp, stammen, wie in der folgenden Tabelle gezeigt.  
  
|SQL-Typ|Für Deskriptorfeld<br /><br /> Dezimalstellen|  
|--------------|----------------------------------------------------------|  
|Alle Zeichen- und Binärtypen|–|  
|Alle exakte numerische Typen|SCALE|  
|SQL_BIT|–|  
|Alle ungefähren numerischen Typen|–|  
|Alle Datetime-Typen|PRECISION|  
|Alle Interval-Datentypen zu einer Sekundenkomponente in|PRECISION|  
|Alle Intervalltypen mit keine Komponente für Sekunden|–|
