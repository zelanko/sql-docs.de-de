---
title: Uhrzeit-, Datums- und Intervallfunktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- functions [ODBC], time functions
- functions [ODBC], date functions
- interval functions [ODBC]
- functions [ODBC], interval functions
- time functions [ODBC]
- date functions [ODBC]
ms.assetid: bdf054a0-7aba-4e99-a34a-799917376fd5
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ae10946be501adb16fdda5fa9f053e389eea4bed
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68070084"
---
# <a name="time-date-and-interval-functions"></a>Uhrzeit-, Datums- und Intervallfunktionen
Die folgende Tabelle enthält Datum und Uhrzeit-Funktionen, die in der ODBC-Skalarfunktion Menge enthalten sind. Eine Anwendung kann bestimmen, welche Funktionen für Datum und die von einem Treiber unterstützt werden, durch den Aufruf **SQLGetInfo** mit einer *Informationstyp* von SQL_TIMEDATE_FUNCTIONS.  
  
 Argumente schulungsausgabe als *Timestamp_exp* kann der Name einer Spalte, die das Ergebnis einer anderen Skalarfunktion sein oder ein *ODBC-Zeit-Escapesequenz*, *ODBC-Datum-Escape*, oder *ODBC-Zeitstempel-Escapesequenz*, in denen der zugrunde liegende Datentyp als SQL_CHAR, SQL_VARCHAR, SQL_TYPE_TIME, SQL_TYPE_DATE oder SQL_TYPE_TIMESTAMP dargestellt werden kann.  
  
 Argumente schulungsausgabe als *"date_exp"* möglich, dass der Name einer Spalte, die das Ergebnis einer anderen skalaren Funktion, oder ein *ODBC-Datum-Escapesequenz* oder *ODBC-Zeitstempel-Escapesequenz*, wobei die der zugrunde liegende Datentyp kann als SQL_CHAR, SQL_VARCHAR, SQL_TYPE_DATE oder SQL_TYPE_TIMESTAMP dargestellt werden.  
  
 Argumente schulungsausgabe als *"time_exp"* kann der Name einer Spalte, die das Ergebnis einer anderen Skalarfunktion sein oder ein *ODBC-Zeit-Escapezeichen* oder *ODBC-Zeitstempel-Escape*, wobei die der zugrunde liegende Datentyp kann als SQL_CHAR, SQL_VARCHAR, SQL_TYPE_TIME und SQL_TYPE_TIMESTAMP dargestellt werden.  
  
 Die CURRENT_DATE CURRENT_TIME und CURRENT_TIMESTAMP timedate Skalarfunktionen ODBC 3.0 an einer Verbindung mit SQL-92 hinzugefügt wurden.  
  
|Funktion|Beschreibung|  
|--------------|-----------------|  
|**CURRENT_DATE ()** (ODBC 3.0)|Gibt das aktuelle Datum zurück.|  
|**CURRENT_TIME [(** *zeitgenauigkeit* **)]** (ODBC-Version 3.0)|Gibt die aktuelle lokale Zeit zurück. Die *zeitgenauigkeit* Argument bestimmt die Genauigkeit des zurückgegebenen Werts.|  
|**CURRENT_TIMESTAMP**<br /> **[(** *Zeitstempel mit Genauigkeit* **)]** (ODBC-Version 3.0)|Gibt die aktuelle lokale Datum und Ortszeit als einen Timestamp-Wert zurück. Die *Zeitstempel mit Genauigkeit* Argument bestimmt die Genauigkeit des zurückgegebenen Zeitstempels.|  
|**CURDATE ()** (ODBC 1.0)|Gibt das aktuelle Datum zurück.|  
|**CURTIME ()** (ODBC 1.0)|Gibt die aktuelle lokale Zeit zurück.|  
|**DAYNAME (** *"date_exp"* **)** (ODBC 2.0)|Gibt eine Zeichenfolge, die mit dem-spezifischen Namen des Tags (z. B. Sonntag bis Samstag oder so. bis Sa. für eine Datenquelle, die Englisch oder Sunday bis Saturday für eine Datenquelle verwendet, die Deutsch verwendet) für den Tagteil von *"date_exp"* .|  
|**DAYOFMONTH (** *"date_exp"* **)** (ODBC-1.0)|Gibt den Tag des Monats basierend auf dem Monatsfeld in *"date_exp"* als ganze Zahl im Bereich von 1 bis 31.|  
|**DAYOFWEEK (** *"date_exp"* **)** (ODBC-1.0)|Gibt den Tag der Woche, die basierend auf dem wochenfeld in *"date_exp"* als ganze Zahl im Bereich von 1 bis 7, wobei 1 steht für Sonntag.|  
|**DAYOFYEAR (** *"date_exp"* **)** (ODBC-1.0)|Gibt den Tag des Jahres basierend auf das Jahresfeld in *"date_exp"* als ganze Zahl im Bereich von 1-366.|  
|**EXTRAHIEREN (** *Extract-Feld FROM* *Extrakt-Quelle* **)** (ODBC-Version 3.0)|Gibt die *Extract-Feld* Teil der *Extrakt-Quelle*. Die *Extrakt-Quelle* -Argument ist ein Ausdruck, "DateTime" oder das Intervall. Die *Extract-Feld* Argument kann eine der folgenden Schlüsselwörter:<br /><br /> JAHR MONAT TAG STUNDE MINUTE, SEKUNDE<br /><br /> Die Genauigkeit des zurückgegebenen Werts ist implementierungsdefiniert. Die Skalierung ist 0, wenn die zweite angegeben wird, in diesem Fall ist die Skalierung nicht kleiner als die Genauigkeit der Sekundenbruchteile von der *Extrakt-Quelle* Feld.|  
|**Stunde (** *"time_exp"* **)** (ODBC-1.0)|Gibt die Stunde basierend auf dem Stundenfeld in *"time_exp"* als ganze Zahl im Bereich von 0 bis 23.|  
|**MINUTE (** *"time_exp"* **)** (ODBC-1.0)|Gibt die Minute basierend auf dem Minutenfeld in *"time_exp"* als ganze Zahl im Bereich von 0 bis 59.|  
|**Monat (** *"date_exp"* **)** (ODBC-1.0)|Gibt den Monat basierend auf dem Monatsfeld in *"date_exp"* als ganze Zahl im Bereich von 1 bis 12.|  
|**MONTHNAME (** *"date_exp"* **)** (ODBC 2.0)|Gibt eine Zeichenfolge, die mit dem-spezifischen Namen des Monats (z. B. Januar bis Dezember oder Januar bis Dezember für eine Datenquelle, die Englisch verwendet, oder January bis December für eine Datenquelle, die Deutsch verwendet) für den Monatsteil von *"date_exp"* .|  
|**(JETZT)** (ODBC 1.0)|Gibt das aktuelle Datum und Uhrzeit als einen Timestamp-Wert zurück.|  
|**Quartal (** *"date_exp"* **)** (ODBC-1.0)|Gibt das Quartal *"date_exp"* als ganze Zahl im Bereich von 1 bis 4, wobei 1 am 1. Januar bis 31. März darstellt.|  
|**ZWEITE (** *"time_exp"* **)** (ODBC-1.0)|Gibt die Sekunde basierend auf dem Sekundenfeld in *"time_exp"* als ganze Zahl im Bereich von 0 bis 59.|
|**TIMESTAMPADD (** *Intervall*, *Integer_exp*, *Timestamp_exp* **)** (ODBC 2.0)|Gibt den Zeitstempel, der durch Addition berechnet *Integer_exp* Intervalle des Typs *Intervall* zu *Timestamp_exp*. Gültige Werte für *Intervall* sind die folgenden Schlüsselwörter:<br /><br /> SQL_TSI_FRAC_SECOND<br /><br /> SQL_TSI_SECOND<br /><br /> SQL_TSI_MINUTE<br /><br /> SQL_TSI_HOUR<br /><br /> SQL_TSI_DAY<br /><br /> SQL_TSI_WEEK<br /><br /> SQL_TSI_MONTH<br /><br /> SQL_TSI_QUARTER<br /><br /> SQL_TSI_YEAR<br /><br /> in dem Bruchteile von Sekunden als milliardste Teil einer Sekunde ausgedrückt werden. Die folgende SQL-Anweisung gibt beispielsweise den Namen der einzelnen Mitarbeiter und seine 1-Jahres-Jahrestag zurück:<br /><br /> `SELECT NAME, {fn  TIMESTAMPADD(SQL_TSI_YEAR, 1, HIRE_DATE)} FROM  EMPLOYEES`<br /><br /> Wenn *Timestamp_exp* ist ein Uhrzeitwert und *Intervall* gibt an, Tage, Wochen, Monaten, Quartalen oder Jahren den Datumsteil des *Timestamp_exp* festgelegt ist, auf das aktuelle Datum vor den resultierenden Zeitstempel zu berechnen.<br /><br /> Wenn *Timestamp_exp* ist ein Datumswert und *Intervall* Sekundenbruchteile gibt Sekunden, Sekunden, Minuten oder Stunden, das Time-Teil eines *Timestamp_exp* auf 0 vor dem festgelegt wird den resultierenden Zeitstempel zu berechnen.<br /><br /> Eine Anwendung bestimmt die Intervalle, die eine Datenquelle unterstützt wird, durch den Aufruf **SQLGetInfo** mit der Option SQL_TIMEDATE_ADD_INTERVALS.|  
|**TIMESTAMPDIFF (** *Intervall*, *timestamp_exp1*, *timestamp_exp2* **)** (ODBC 2.0)|Gibt die ganze Zahl der Intervalle des Typs *Intervall* mit dem *timestamp_exp2* ist größer als *timestamp_exp1*. Gültige Werte für *Intervall* sind die folgenden Schlüsselwörter:<br /><br /> SQL_TSI_FRAC_SECOND<br /><br /> SQL_TSI_SECOND<br /><br /> SQL_TSI_MINUTE<br /><br /> SQL_TSI_HOUR<br /><br /> SQL_TSI_DAY<br /><br /> SQL_TSI_WEEK<br /><br /> SQL_TSI_MONTH<br /><br /> SQL_TSI_QUARTER<br /><br /> SQL_TSI_YEAR<br /><br /> in dem Bruchteile von Sekunden als milliardste Teil einer Sekunde ausgedrückt werden. Die folgende SQL-Anweisung gibt z. B. den Namen der einzelnen Mitarbeiter und die Anzahl der Jahre, die er entwickelt hat:<br /><br /> `SELECT NAME, {fn  TIMESTAMPDIFF(SQL_TSI_YEAR, {fn CURDATE()}, HIRE_DATE)} FROM EMPLOYEES`<br /><br /> Falls ein Timestamp-Ausdruck einen Zeitwert ist und *Intervall* gibt an, auf das aktuelle Datum vor dem Berechnen der Differenz zwischen den Zeitstempeln Tage, Wochen, Monaten, Quartalen oder Jahren den Datumsteil des jeweiligen Zeitstempel festgelegt ist.<br /><br /> Falls ein Timestamp-Ausdruck ein Date-Wert ist und *Intervall* Sekundenbruchteile gibt Sekunden, Sekunden, Minuten oder Stunden, wird der Uhrzeitteil des jeweiligen Zeitstempel auf 0 vor dem Berechnen der Differenz zwischen den Zeitstempeln festgelegt.<br /><br /> Eine Anwendung bestimmt die Intervalle, die eine Datenquelle unterstützt wird, durch den Aufruf **SQLGetInfo** mit der Option SQL_TIMEDATE_DIFF_INTERVALS.|  
|**Woche (** *"date_exp"* **)** (ODBC-1.0)|Gibt die Woche des Jahres basierend auf dem wochenfeld in *"date_exp"* als ganze Zahl im Bereich von 1-53.|  
|**Jahr (** *"date_exp"* **)** (ODBC-1.0)|Gibt das Jahr, basierend auf das Jahresfeld in zurück *"date_exp"* als ganze Zahl. Der Bereich ist datenquellenabhängig.|
