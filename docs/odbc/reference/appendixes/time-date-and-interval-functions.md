---
title: Uhrzeit-, Datums-und Intervall Funktionen | Microsoft-Dokumentation
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68070084"
---
# <a name="time-date-and-interval-functions"></a>Uhrzeit-, Datums- und Intervallfunktionen
In der folgenden Tabelle sind die Zeit-und Datumsfunktionen aufgelistet, die im ODBC-skalarfunktionssatz enthalten sind. Eine Anwendung kann ermitteln, welche Zeit-und Datumsfunktionen von einem Treiber unterstützt werden, indem **SQLGetInfo** mit dem *Informationstyp* SQL_TIMEDATE_FUNCTIONS aufgerufen wird.  
  
 Argumente, die als *timestamp_exp* bezeichnet werden, können der Name einer Spalte, das Ergebnis einer anderen Skalarfunktion oder ein *ODBC-Time-Escape*, *ODBC-Date-Escape*oder *ODBC-Timestamp-Escape*sein, wobei der zugrunde liegende Datentyp als SQL_CHAR, SQL_VARCHAR, SQL_TYPE_TIME, SQL_TYPE_DATE oder SQL_TYPE_TIMESTAMP dargestellt werden kann.  
  
 Argumente, die als *date_exp* bezeichnet werden, können der Name einer Spalte, das Ergebnis einer anderen Skalarfunktion oder ein *ODBC-Date-Escape* oder *ODBC-Timestamp-Escape*sein, wobei der zugrunde liegende Datentyp als SQL_CHAR, SQL_VARCHAR, SQL_TYPE_DATE oder SQL_TYPE_TIMESTAMP dargestellt werden könnte.  
  
 Argumente, die als *time_exp* bezeichnet werden, können der Name einer Spalte, das Ergebnis einer anderen Skalarfunktion oder ein *ODBC-Time-Escape* oder *ODBC-Timestamp-Escape*sein, wobei der zugrunde liegende Datentyp als SQL_CHAR, SQL_VARCHAR, SQL_TYPE_TIME oder SQL_TYPE_TIMESTAMP dargestellt werden kann.  
  
 Die Skalarfunktionen CURRENT_DATE, CURRENT_TIME und CURRENT_TIMESTAMP timedate wurden in ODBC 3,0 hinzugefügt, um Sie an SQL-92 auszurichten.  
  
|Funktion|BESCHREIBUNG|  
|--------------|-----------------|  
|**CURRENT_DATE ()** (ODBC 3,0)|Gibt das aktuelle Datum zurück.|  
|**CURRENT_TIME [(** *Zeit Genauigkeit* **)]** (ODBC 3,0)|Gibt die aktuelle lokale Zeit zurück. Das *Zeit Genauigkeits* Argument bestimmt die Sekunden Genauigkeit des zurückgegebenen Werts.|  
|**CURRENT_TIMESTAMP**<br /> **[(** *Zeitstempel Genauigkeit* **)]** (ODBC 3,0)|Gibt das aktuelle lokale Datum und die lokale Uhrzeit als Zeitstempel-Wert zurück. Das *timestamp-Precision-* Argument bestimmt die Sekunden Genauigkeit des zurückgegebenen Zeitstempels.|  
|**CurrDate ()** (ODBC 1,0)|Gibt das aktuelle Datum zurück.|  
|**Geschweibzeit ()** (ODBC 1,0)|Gibt die aktuelle lokale Zeit zurück.|  
|**DAYNAME (** *date_exp* **)** (ODBC 2,0)|Gibt eine Zeichenfolge zurück, die den Datenquellen spezifischen Namen des Tages enthält (z. b. Sonntag bis Samstag oder Sun). bis Sa. für eine Datenquelle, die Englisch oder Sonntag bis Samstag für eine Datenquelle verwendet, die Deutsch verwendet, für den Tages Teil *date_exp*.|  
|**Dayosmonth (** *date_exp* **)** (ODBC 1,0)|Gibt den Tag des Monats zurück, basierend auf dem month-Feld in *date_exp* als ganzzahliger Wert im Bereich von 1-31.|  
|**Dayobweek (** *date_exp* **)** (ODBC 1,0)|Gibt den Wochentag auf der Grundlage des Wochen Felds in *date_exp* als ganzzahliger Wert im Bereich von 1-7 zurück, wobei 1 für Sonntag steht.|  
|**Dayosyear (** *date_exp* **)** (ODBC 1,0)|Gibt den Tag des Jahres zurück, basierend auf dem Feld "Year" in *date_exp* als ganzzahliger Wert im Bereich von 1-366.|  
|**Extract (** *extract-Field from* *extract-Source* **)** (ODBC 3,0)|Gibt den *extract-Field-* Teil des *extract-Source*-Werts zurück. Das *extract-Source-* Argument ist ein DateTime-oder Interval-Ausdruck. Das *extract-Field-* Argument kann eines der folgenden Schlüsselwörter sein:<br /><br /> Jahr Monat Tag Stunde Minute Sekunde<br /><br /> Die Genauigkeit des zurückgegebenen Werts ist von der Implementierung definiert. Die Skala ist 0, es sei denn, es ist ein zweites angegeben. in diesem Fall ist die Skala nicht kleiner als die Genauigkeit der Sekundenbruchteile des *Extraktions Quell* Felds.|  
|**Stunde (** *time_exp* **)** (ODBC 1,0)|Gibt die Stunde zurück, die auf dem Stunden Feld in *time_exp* als ganzzahliger Wert im Bereich von 0-23 basiert.|  
|**Minute (** *time_exp* **)** (ODBC 1,0)|Gibt die Minute zurück, die auf dem Minuten Feld in *time_exp* als ganzzahliger Wert im Bereich von 0-59 basiert.|  
|**Monat (** *date_exp* **)** (ODBC 1,0)|Gibt den Monat auf der Grundlage des Monats Felds in *date_exp* als ganzzahligen Wert im Bereich von 1-12 zurück.|  
|**MonthName (** *date_exp* **)** (ODBC 2,0)|Gibt eine Zeichenfolge zurück, die den Datenquellen spezifischen Namen des Monats enthält (z. b. Januar bis Dezember oder Jan. bis Dec. für eine Datenquelle, die Englisch verwendet, bzw. Januar bis Dezember für eine Datenquelle, die Deutsch verwendet) für den Monats Teil *date_exp*.|  
|**Now ()** (ODBC 1,0)|Gibt das aktuelle Datum und die aktuelle Uhrzeit als Zeitstempel-Wert zurück.|  
|**Quartal (** *date_exp* **)** (ODBC 1,0)|Gibt das Quartal in *date_exp* als ganzzahliger Wert im Bereich von 1-4 zurück, wobei 1 den 1. Januar bis zum 31. März darstellt.|  
|**Second (** *time_exp* **)** (ODBC 1,0)|Gibt die zweite auf der Grundlage des zweiten Felds in *time_exp* als ganzzahliger Wert im Bereich von 0-59 zurück.|
|**Timestampadd (** *Intervall*, *integer_exp* *timestamp_exp* **)** (ODBC 2,0)|Gibt den Zeitstempel zurück, der berechnet wird, indem *integer_exp* Intervalle des Typs *Interval* *timestamp_exp*hinzugefügt werden. Gültige Werte für *Interval* sind die folgenden Schlüsselwörter:<br /><br /> SQL_TSI_FRAC_SECOND<br /><br /> SQL_TSI_SECOND<br /><br /> SQL_TSI_MINUTE<br /><br /> SQL_TSI_HOUR<br /><br /> SQL_TSI_DAY<br /><br /> SQL_TSI_WEEK<br /><br /> SQL_TSI_MONTH<br /><br /> SQL_TSI_QUARTER<br /><br /> SQL_TSI_YEAR<br /><br /> , wenn Sekundenbruchteile in Milliardstel einer Sekunde ausgedrückt werden. Die folgende SQL-Anweisung gibt z. b. den Namen der einzelnen Mitarbeiter und das einjährige Jahres Datum zurück:<br /><br /> `SELECT NAME, {fn  TIMESTAMPADD(SQL_TSI_YEAR, 1, HIRE_DATE)} FROM  EMPLOYEES`<br /><br /> Wenn *timestamp_exp* ein Uhrzeitwert ist und das *Intervall* Tage, Wochen, Monate, Quartale oder Jahre angibt, wird der Datums Teil *timestamp_exp* auf das aktuelle Datum festgelegt, bevor der resultierende Zeitstempel berechnet wird.<br /><br /> Wenn *timestamp_exp* ein Datumswert und ein *Intervall* Sekundenbruchteile, Sekunden, Minuten oder Stunden angibt, wird der Uhrzeit Teil von *timestamp_exp* vor der Berechnung des resultierenden Zeitstempels auf 0 festgelegt.<br /><br /> Eine Anwendung bestimmt, welche Intervalle eine Datenquelle unterstützt, indem **SQLGetInfo** mit der Option SQL_TIMEDATE_ADD_INTERVALS aufgerufen wird.|  
|**Timestampdiff (** *Interval*, *timestamp_exp1* *timestamp_exp2* **)** (ODBC 2,0)|Gibt die ganzzahlige Anzahl von Intervallen des *typintervalls* zurück, um *timestamp_exp2* größer als *timestamp_exp1*ist. Gültige Werte für *Interval* sind die folgenden Schlüsselwörter:<br /><br /> SQL_TSI_FRAC_SECOND<br /><br /> SQL_TSI_SECOND<br /><br /> SQL_TSI_MINUTE<br /><br /> SQL_TSI_HOUR<br /><br /> SQL_TSI_DAY<br /><br /> SQL_TSI_WEEK<br /><br /> SQL_TSI_MONTH<br /><br /> SQL_TSI_QUARTER<br /><br /> SQL_TSI_YEAR<br /><br /> , wenn Sekundenbruchteile in Milliardstel einer Sekunde ausgedrückt werden. Die folgende SQL-Anweisung gibt z. b. den Namen jedes Mitarbeiters und die Anzahl der Jahre zurück, die er verwendet hat:<br /><br /> `SELECT NAME, {fn  TIMESTAMPDIFF(SQL_TSI_YEAR, {fn CURDATE()}, HIRE_DATE)} FROM EMPLOYEES`<br /><br /> Wenn ein Zeitstempel-Ausdruck ein Uhrzeitwert ist und das *Intervall* Tage, Wochen, Monate, Quartale oder Jahre angibt, wird der Datums Teil dieses Zeitstempels auf das aktuelle Datum festgelegt, bevor der Unterschied zwischen den Zeitstempeln berechnet wird.<br /><br /> Wenn ein Zeitstempel-Ausdruck ein Datumswert und ein *Intervall* Sekundenbruchteile, Sekunden, Minuten oder Stunden angibt, wird der Uhrzeit Teil dieses Zeitstempels auf 0 festgelegt, bevor der Unterschied zwischen den Zeitstempeln berechnet wird.<br /><br /> Eine Anwendung bestimmt, welche Intervalle eine Datenquelle unterstützt, indem **SQLGetInfo** mit der Option SQL_TIMEDATE_DIFF_INTERVALS aufgerufen wird.|  
|**Woche (** *date_exp* **)** (ODBC 1,0)|Gibt die Woche des Jahres zurück, die auf dem Wochen Feld in *date_exp* als ganzzahliger Wert im Bereich von 1-53 basiert.|  
|**Jahr (** *date_exp* **)** (ODBC 1,0)|Gibt das Jahr zurück, das auf dem Feld "Year" in *date_exp* als ganzzahliger Wert basiert. Der Bereich ist Datenquellen abhängig.|
