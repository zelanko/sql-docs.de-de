---
title: Anzeige Größe | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- display size of data types [ODBC]
- size of data types [ODBC]
- data types [ODBC], display size
- SQL data types [ODBC], column characteristics
ms.assetid: 9f7f766f-2492-463c-aab7-f2476e222042
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 578bf0cbdf2dd1dbd06dd4a248f4efa5eb839916
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81307031"
---
# <a name="display-size"></a>Anzeigegröße
Die Anzeige Größe einer Spalte ist die maximale Anzahl von Zeichen, die zum Anzeigen von Daten im Zeichenformat benötigt werden. In der folgenden Tabelle wird die Anzeige Größe für jeden ODBC SQL-Datentyp definiert.  
  
|SQL-Typbezeichner|Anzeigegröße|  
|-------------------------|------------------|  
|Alle Zeichen Typen [a]|Der definierte (für festgelegte Typen) oder die maximale Anzahl von Zeichen (für Variablen Typen), die zum Anzeigen der Daten im Zeichenformat erforderlich sind.|  
|SQL_DECIMAL SQL_NUMERIC|Die Genauigkeit der Spalte plus 2 (ein Zeichen, *Genauigkeits* Ziffern und ein Dezimaltrennzeichen). Beispielsweise ist die Anzeige Größe einer Spalte, die als numerisch (10, 3) definiert ist, 12.|  
|SQL_BIT|1 (1 Ziffer).|  
|SQL_TINYINT|4, wenn signiert (ein Vorzeichen und 3 Ziffern) oder 3, wenn kein Vorzeichen (3 Ziffern) ist.|  
|SQL_SMALLINT|6, wenn signiert (ein Vorzeichen und 5 Ziffern) oder 5, wenn kein Vorzeichen (5 Ziffern) ist.|  
|SQL_INTEGER|11, wenn signiert (ein-und 10-Ziffern) oder 10, wenn kein Vorzeichen (10 Ziffern) ist.|  
|SQL_BIGINT|20 (ein Vorzeichen und 19 Ziffern, wenn signiert oder 20 Ziffern, wenn nicht signiert).|  
|SQL_REAL|14 (ein Zeichen, 7 Ziffern, ein Dezimaltrennzeichen, der Buchstabe *E*, ein Vorzeichen und zwei Ziffern).|  
|SQL_FLOAT SQL_DOUBLE|24 (ein Vorzeichen, 15 Ziffern, ein Dezimaltrennzeichen, der Buchstabe *E*, ein Vorzeichen und 3 Ziffern).|  
|Alle binären Typen [a]|Die definierte oder maximale Länge (für Variablen Typen) der Spalte 2. (Jedes binäre Byte wird durch eine zweistellige hexadezimal Zahl dargestellt.)|  
|SQL_TYPE_DATE|10 (ein Datum im Format *yyyy-mm-dd*).|  
|SQL_TYPE_TIME|8 (eine Uhrzeit im Format *hh: mm: SS*)<br /><br /> - oder -<br /><br /> 9 + *s* (eine Uhrzeit im Format *hh: mm: SS*[. fff...], wobei *s* für die Genauigkeit der Sekundenbruchteile steht).|  
|SQL_TYPE_TIMESTAMP|19 (für einen Zeitstempel im Format *yyyy-mm-dd hh: mm: SS* )<br /><br /> - oder -<br /><br /> 20 + *s* (für einen Zeitstempel im Format *yyyy-mm-dd hh: mm: SS*[. fff...], wobei *s* für die Genauigkeit der Sekundenbruchteile steht).|  
|Alle Intervall Datentypen|Siehe [Intervall Datentyp Länge](../../../odbc/reference/appendixes/interval-data-type-length.md).|  
|SQL_GUID|36 (die Anzahl der Zeichen im *aaaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee* -Format|  
  
 [a] Wenn der Treiber die Spalten-oder Parameter Länge von Variablen Typen nicht bestimmen kann, wird SQL_NO_TOTAL zurückgegeben.
