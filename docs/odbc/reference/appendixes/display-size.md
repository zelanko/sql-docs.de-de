---
title: Anzeigegröße | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2c7d4a14a6afc2d716e85e687cbae1a202a596d7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47751098"
---
# <a name="display-size"></a>Anzeigegröße
Die Größe einer Spalte ist die maximale Anzahl von Zeichen, die zum Anzeigen von Daten in Form von Zeichen erforderlich sind. In der folgende Tabelle definiert die Größe für jede ODBC-SQL-Datentyp.  
  
|SQL-Typ-ID|Anzeigegröße|  
|-------------------------|------------------|  
|Alle Typen mit Zeichen [a]|Die definierten (bei festen Typen) oder (für Variablentypen) maximale Anzahl von Zeichen, die zum Anzeigen der Daten in Form von Zeichen erforderlich.|  
|SQL_DECIMAL SQL_NUMERIC|Die Genauigkeit der Spalte plus 2 (eine Anmeldung, *Genauigkeit* Ziffern und ein Dezimaltrennzeichen). Beispielsweise ist die Größe einer Spalte, die als NUMERIC(10,3) definiert 12.|  
|SQL_BIT|1 (1 Ziffer).|  
|SQL_TINYINT|4, wenn Sie signiert (eine Anmeldung und 3 Ziffern) oder 3 bei einem unsignierten (3 Ziffern).|  
|SQL_SMALLINT|6, wenn Sie signiert (eine Anmeldung und 5 Ziffern) oder 5 Falls (5-stellig) ohne Vorzeichen.|  
|SQL_INTEGER|11 Wenn (eine Anmeldung und 10-Ziffern) signiert oder 10 bei einem unsignierten (10 Ziffern).|  
|SQL_BIGINT|20 (eine Anmeldung und 19 Ziffern, wenn angemeldet oder 20 Ziffern bei einem unsignierten).|  
|SQL_REAL|14 (ein Zeichen, 7 Ziffern, einem Dezimaltrennzeichen, der Buchstabe *E*, ein Zeichen und 2 Ziffern).|  
|SQL_FLOAT SQL_DOUBLE|24 (ein Zeichen, 15 Dezimalstellen, ein Dezimaltrennzeichen, der Buchstabe *E*, ein Zeichen und 3 Ziffern).|  
|[A] alle binären Typen|Die definiert oder (für Variablentypen) maximale Länge der Spalte x 2. (Jedes binäre Byte wird durch eine hexadezimale Zahl mit 2 Stellen dargestellt.)|  
|SQL_TYPE_DATE|10 (ein Datum im Format *jjjj-mm-tt*).|  
|SQL_TYPE_TIME|8 (eine Uhrzeit im Format *hh: mm:*)<br /><br /> - oder -<br /><br /> 9 + *s* (eine Uhrzeit im Format *hh: mm:*[: ss. fff...], wobei *s* ist die Genauigkeit der Sekundenbruchteile).|  
|SQL_TYPE_TIMESTAMP|19 (für den Zeitstempel in der *jjjj-mm-tt hh: mm:* Format)<br /><br /> - oder -<br /><br /> 20 + *s* (für den Zeitstempel in der *jjjj-mm-tt hh: mm:*[: ss. fff...]-Format, in denen *s* ist die Genauigkeit der Sekundenbruchteile).|  
|Alle Interval-Datentypen|Finden Sie unter [Länge des Datentyps Interval](../../../odbc/reference/appendixes/interval-data-type-length.md).|  
|SQL_GUID|36 (die Anzahl der Zeichen in der *Aaaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee* Format|  
  
 [a] Wenn der Treiber die Spalte oder Parameter die Länge von Variablentypen nicht bestimmen kann, gibt er SQL_NO_TOTAL zurück.
