---
title: Display-Größe | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307031"
---
# <a name="display-size"></a>Anzeigegröße
Die Anzeigegröße einer Spalte ist die maximale Anzahl von Zeichen, die zum Anzeigen von Daten in Zeichenform erforderlich sind. In der folgenden Tabelle wird die Anzeigegröße für jeden ODBC SQL-Datentyp definiert.  
  
|SQL-Typbezeichner|Anzeigegröße|  
|-------------------------|------------------|  
|Alle Zeichentypen[a]|Die definierte (für feste Typen) oder maximale Anzahl (für Variablentypen) Anzahl von Zeichen, die zum Anzeigen der Daten in Zeichenform erforderlich sind.|  
|SQL_DECIMAL SQL_NUMERIC|Die Genauigkeit der Spalte plus 2 (ein Vorzeichen, *Präzisionsziffern* und ein Dezimaltrennzeichen). Die Anzeigegröße einer Spalte, die als NUMERIC(10,3) definiert ist, beträgt beispielsweise 12.|  
|SQL_BIT|1 (1 Ziffer).|  
|SQL_TINYINT|4 wenn signiert (ein Zeichen und 3 Ziffern) oder 3, wenn nicht signiert (3 Ziffern).|  
|SQL_SMALLINT|6, wenn signiert (ein Zeichen und 5 Ziffern) oder 5, wenn nicht signiert (5 Ziffern).|  
|SQL_INTEGER|11 wenn signiert (ein Zeichen und 10 Ziffern) oder 10, wenn nicht signiert (10 Ziffern).|  
|SQL_BIGINT|20 (ein Zeichen und 19 Ziffern, wenn signiert oder 20 Ziffern, wenn nicht signiert).|  
|SQL_REAL|14 (ein Vorzeichen, 7 Ziffern, ein Dezimalkomma, der Buchstabe *E*, ein Zeichen und 2 Ziffern).|  
|SQL_FLOAT SQL_DOUBLE|24 (ein Vorzeichen, 15 Ziffern, ein Dezimalkomma, der Buchstabe *E*, ein Zeichen und 3 Ziffern).|  
|Alle binären Typen[a]|Die definierte oder maximale Länge (für variable Typen) der Spaltenzeiten 2. (Jedes binäre Byte wird durch eine zweistellige hexadezimale Zahl dargestellt.)|  
|SQL_TYPE_DATE|10 (ein Datum im Format *yyyy-mm-dd*).|  
|SQL_TYPE_TIME|8 (eine Uhrzeit im Format *hh:mm:ss*)<br /><br /> - oder -<br /><br /> 9 + *s* (eine Zeit im Format *hh:mm:ss*[.fff...], wobei *s* die Sekundengenauigkeit ist).|  
|SQL_TYPE_TIMESTAMP|19 (für einen Zeitstempel im *Yyyy-mm-dd hh:mm:ss-Format)*<br /><br /> - oder -<br /><br /> 20 + *s* (für einen Zeitstempel im *Yyyy-mm-dd hh:mm:ss*[.fff...]-Format, wobei *s* die Sekundengenauigkeit ist).|  
|Alle Intervalldatentypen|Siehe [Intervalldatentyplänge](../../../odbc/reference/appendixes/interval-data-type-length.md).|  
|SQL_GUID|36 (Anzahl der Zeichen im *Aaaaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeeee*|  
  
 [a] Wenn der Treiber die Spalten- oder Parameterlänge von Variablentypen nicht bestimmen kann, gibt er SQL_NO_TOTAL zurück.
