---
title: Zeit-, Datums- und Intervallfunktionen | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: aec3d6b23383edcc9659ff884e8cd71b0595dae1
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302821"
---
# <a name="time-date-and-interval-functions"></a>Uhrzeit-, Datums- und Intervallfunktionen
In der folgenden Tabelle sind Zeit- und Datumsfunktionen aufgeführt, die im ODBC-Skalarfunktionssatz enthalten sind. Eine Anwendung kann bestimmen, welche Zeit- und Datumsfunktionen von einem Treiber unterstützt werden, indem **sie SQLGetInfo** mit einem *Informationstyp* von SQL_TIMEDATE_FUNCTIONS.  
  
 Argumente, die als *timestamp_exp* bezeichnet werden, können der Name einer Spalte, das Ergebnis einer anderen Skalarfunktion oder ein *ODBC-Time-Escape*, *ODBC-date-escape*oder *ODBC-timestamp-escape*sein, wobei der zugrunde liegende Datentyp als SQL_CHAR, SQL_VARCHAR, SQL_TYPE_TIME, SQL_TYPE_DATE oder SQL_TYPE_TIMESTAMP dargestellt werden könnte.  
  
 Argumente, die als *date_exp* bezeichnet werden, können der Name einer Spalte, das Ergebnis einer anderen Skalarfunktion oder ein *ODBC-Datumsescape-* oder *ODBC-Timestamp-Escape*sein, bei dem der zugrunde liegende Datentyp als SQL_CHAR, SQL_VARCHAR, SQL_TYPE_DATE oder SQL_TYPE_TIMESTAMP dargestellt werden könnte.  
  
 Argumente, die als *time_exp* bezeichnet werden, können der Name einer Spalte, das Ergebnis einer anderen Skalarfunktion oder ein *ODBC-Time-Escape* oder *ODBC-Timestamp-Escape*sein, bei dem der zugrunde liegende Datentyp als SQL_CHAR, SQL_VARCHAR, SQL_TYPE_TIME oder SQL_TYPE_TIMESTAMP dargestellt werden könnte.  
  
 Die CURRENT_DATE CURRENT_TIME und CURRENT_TIMESTAMP Skalarfunktionen für die Zeitzeit wurden in ODBC 3.0 hinzugefügt, um sql-92 auszurichten.  
  
|Funktion|BESCHREIBUNG|  
|--------------|-----------------|  
|**CURRENT_DATE( )** (ODBC 3.0)|Gibt das aktuelle Datum zurück.|  
|**CURRENT_TIME[(** *Zeitgenauigkeit* **)]** (ODBC 3.0)|Gibt die aktuelle lokale Zeit zurück. Das *Argument für die Zeitgenauigkeit* bestimmt die Sekundengenauigkeit des zurückgegebenen Werts.|  
|**CURRENT_TIMESTAMP**<br /> **[(** *Zeitstempelgenauigkeit* **)]** (ODBC 3.0)|Gibt das aktuelle lokale Datum und die ortszeite Uhrzeit als Zeitstempelwert zurück. Das Argument *zeitstempelpräzision* bestimmt die Sekundengenauigkeit des zurückgegebenen Zeitstempels.|  
|**CURDATE( )** (ODBC 1.0)|Gibt das aktuelle Datum zurück.|  
|**CURTIME( )** (ODBC 1.0)|Gibt die aktuelle lokale Zeit zurück.|  
|**DAYNAME(** *date_exp* **)** (ODBC 2.0)|Gibt eine Zeichenfolge zurück, die den datenquellenspezifischen Namen des Tages enthält (z. B. Sonntag bis Samstag oder Sonne). bis Sa. für eine Datenquelle, die Englisch verwendet, oder Sonntag bis Samstag für eine Datenquelle, die Deutsch verwendet) für den Tagesteil von *date_exp*.|  
|**DAYOFMONTH(** *date_exp* **)** (ODBC 1.0)|Gibt den Tag des Monats basierend auf dem Feld "Monat" in *date_exp* als Ganzzahlwert im Bereich von 1-31 zurück.|  
|**DAYOFWEEK(** *date_exp* **)** (ODBC 1.0)|Gibt den Wochentag basierend auf dem Wochenfeld in *date_exp* als Ganzzahlwert im Bereich von 1-7 zurück, wobei 1 den Sonntag darstellt.|  
|**DAYOFYEAR(** *date_exp* **)** (ODBC 1.0)|Gibt den Tag des Jahres basierend auf dem Jahresfeld in *date_exp* als ganzzahligen Wert im Bereich von 1-366 zurück.|  
|**EXTRACT(** *Extraktfeld AUS* *Extraktquelle* **)** (ODBC 3.0)|Gibt den *Extraktfeldteil* der *Extraktquelle*zurück. Das *Argument "Extrakt-Quelle"* ist ein Datumszeit- oder Intervallausdruck. Das *Argument "Extraktfeld"* kann eines der folgenden Schlüsselwörter sein:<br /><br /> JAHR MONAT STUNDE MINUTE SEKUNDE SEKUNDE<br /><br /> Die Genauigkeit des zurückgegebenen Werts ist implementierungsdefiniert. Die Skala ist 0, es sei denn, SECOND wird angegeben, in diesem Fall ist die Skala nicht kleiner als die Sekundengenauigkeit des *Extrakt-Quellenfelds.*|  
|**HOUR(** *time_exp* **)** (ODBC 1.0)|Gibt die Stunde basierend auf dem Stundenfeld in *time_exp* als Ganzzahlwert im Bereich von 0-23 zurück.|  
|**MINUTE(** *time_exp* **)** (ODBC 1.0)|Gibt die Minute basierend auf dem Minutenfeld in *time_exp* als Ganzzahlwert im Bereich von 0-59 zurück.|  
|**MONAT(** *date_exp* **)** (ODBC 1.0)|Gibt den Monat basierend auf dem Feld "Monat" in *date_exp* als Ganzzahlwert im Bereich von 1-12 zurück.|  
|**MONATNAME(** *date_exp* **)** (ODBC 2.0)|Gibt eine Zeichenfolge zurück, die den datenquellenspezifischen Namen des Monats enthält (z. B. Januar bis Dezember oder Jan. bis Dez. für eine Datenquelle, die Englisch verwendet, oder Januar bis Dezember für eine Datenquelle, die Deutsch verwendet) für den Monatsteil *date_exp*.|  
|**JETZT ( )** (ODBC 1.0)|Gibt das aktuelle Datum und die aktuelle Uhrzeit als Zeitstempelwert zurück.|  
|**QUARTER(** *date_exp* **)** (ODBC 1.0)|Gibt das Quartal in *date_exp* als Ganzzahlwert im Bereich von 1-4 zurück, wobei 1 den 1. Januar bis zum 31. März darstellt.|  
|**ZWEITE(** *time_exp* **)** (ODBC 1.0)|Gibt das zweite Feld basierend auf dem zweiten Feld in *time_exp* als Ganzzahlwert im Bereich von 0-59 zurück.|
|**TIMESTAMPADD(** *Intervall*, *integer_exp*, *timestamp_exp* **)** (ODBC 2.0)|Gibt den Zeitstempel zurück, der durch Hinzufügen *integer_exp* Intervalle des *Typintervalls* zu *timestamp_exp*berechnet wird. Gültige *Intervallwerte* sind die folgenden Schlüsselwörter:<br /><br /> SQL_TSI_FRAC_SECOND<br /><br /> SQL_TSI_SECOND<br /><br /> SQL_TSI_MINUTE<br /><br /> SQL_TSI_HOUR<br /><br /> SQL_TSI_DAY<br /><br /> SQL_TSI_WEEK<br /><br /> SQL_TSI_MONTH<br /><br /> SQL_TSI_QUARTER<br /><br /> SQL_TSI_YEAR<br /><br /> wobei Bruchteilsekunden in Millimillimillistelsekunden ausgedrückt werden. Die folgende SQL-Anweisung gibt z. B. den Namen jedes Mitarbeiters und sein einjähriges Jubiläumsdatum zurück:<br /><br /> `SELECT NAME, {fn  TIMESTAMPADD(SQL_TSI_YEAR, 1, HIRE_DATE)} FROM  EMPLOYEES`<br /><br /> Wenn *timestamp_exp* ein Zeitwert und *ein Intervall* Tage, Wochen, Monate, Quartale oder Jahre angibt, wird der Datumsteil von *timestamp_exp* vor der Berechnung des resultierenden Zeitstempels auf das aktuelle Datum festgelegt.<br /><br /> Wenn *timestamp_exp* ein Datumswert ist und *das Intervall* Bruchsekunden, Sekunden, Minuten oder Stunden angibt, wird der Zeitteil von *timestamp_exp* vor der Berechnung des resultierenden Zeitstempels auf 0 festgelegt.<br /><br /> Eine Anwendung bestimmt, welche Intervalle eine Datenquelle unterstützt, indem **sie SQLGetInfo** mit der Option SQL_TIMEDATE_ADD_INTERVALS aufruft.|  
|**TIMESTAMPDIFF(** *Intervall*, *timestamp_exp1*, *timestamp_exp2* **)** (ODBC 2.0)|Gibt die ganze Zahl der Intervalle des *Typintervalls* zurück, um die *timestamp_exp2* größer als *timestamp_exp1*ist. Gültige *Intervallwerte* sind die folgenden Schlüsselwörter:<br /><br /> SQL_TSI_FRAC_SECOND<br /><br /> SQL_TSI_SECOND<br /><br /> SQL_TSI_MINUTE<br /><br /> SQL_TSI_HOUR<br /><br /> SQL_TSI_DAY<br /><br /> SQL_TSI_WEEK<br /><br /> SQL_TSI_MONTH<br /><br /> SQL_TSI_QUARTER<br /><br /> SQL_TSI_YEAR<br /><br /> wobei Bruchteilsekunden in Millimillimillistelsekunden ausgedrückt werden. Die folgende SQL-Anweisung gibt z. B. den Namen jedes Mitarbeiters und die Anzahl der Jahre zurück, in denen er beschäftigt wurde:<br /><br /> `SELECT NAME, {fn  TIMESTAMPDIFF(SQL_TSI_YEAR, {fn CURDATE()}, HIRE_DATE)} FROM EMPLOYEES`<br /><br /> Wenn ein Zeitstempelausdruck ein Zeitwert ist und *das Intervall* Tage, Wochen, Monate, Quartale oder Jahre angibt, wird der Datumsteil dieses Zeitstempels auf das aktuelle Datum festgelegt, bevor die Differenz zwischen den Zeitstempeln berechnet wird.<br /><br /> Wenn einer der Zeitstempelausdruckeins ein Datumswert ist und *das Intervall* Bruchsekunden, Sekunden, Minuten oder Stunden angibt, wird der Zeitteil dieses Zeitstempels auf 0 festgelegt, bevor die Differenz zwischen den Zeitstempeln berechnet wird.<br /><br /> Eine Anwendung bestimmt, welche Intervalle eine Datenquelle unterstützt, indem **sie SQLGetInfo** mit der Option SQL_TIMEDATE_DIFF_INTERVALS aufruft.|  
|**WOCHE(** *date_exp* **)** (ODBC 1.0)|Gibt die Woche des Jahres basierend auf dem Wochenfeld in *date_exp* als Ganzzahlwert im Bereich von 1-53 zurück.|  
|**JAHR(** *date_exp* **)** (ODBC 1.0)|Gibt das Jahr basierend auf dem Feld "Jahr" in *date_exp* als Ganzzahlwert zurück. Der Bereich ist datenquellenabhängig.|
