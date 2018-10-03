---
title: Datums- und Zeitformate | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- time data types [Integration Services]
- fast parse [Integration Services]
- date data types
- date and time formats for fast parse
ms.assetid: bed6e2c1-791a-4fa1-b29f-cbfdd1fa8d39
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d84f3158b41f2cff79572ad7a65c3033a4d2ca77
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48112742"
---
# <a name="date-and-time-formats"></a>Datums- und Zeitformate
  Die schnelle Analyse stellt schnelle, einfache Routinen zum Analysieren von Daten bereit. Die schnelle Analyse unterstützt die folgenden Formate für Datums- und Zeitdatentypen.  
  
## <a name="date-data-types"></a>Datumsdatentypen  
 Die schnelle Analyse unterstützt die folgenden Zeichenfolgenformate für Datumsdaten:  
  
-   Datumsformate, die führende Leerstellen einschließen. Beispielsweise ist der Wert " 2004- 02-03" gültig.  
  
-   ISO 8601-Formate, wie in der folgenden Tabelle aufgeführt:  
  
    |Format|Description|  
    |------------|-----------------|  
    |YYYYMMDD<br /><br /> YYYY-MM-DD|Basisformate und erweiterte Formate für eine vierstellige Jahresangabe, eine zweistellige Monatsangabe und eine zweistellige Tagesangabe. Beim erweiterten Format werden die Datumsteile durch einen Bindestrich (-) getrennt.|  
    |YYYY-MM|Basisformate und erweiterte Formate mit reduzierter Genauigkeit für eine vierstellige Jahresangabe und eine zweistellige Monatsangabe. Beim erweiterten Format werden die Datumsteile durch einen Bindestrich (-) getrennt.|  
    |YYYY|Das Format mit reduzierter Genauigkeit ist eine vierstellige Jahresangabe.|  
  
 Die schnelle Analyse unterstützt die folgenden Formate für Datumsdaten nicht:  
  
-   Alphabetische Monatswerte. Beispielsweise ist das Datumsformat Oct-31-2003 ungültig.  
  
-   Mehrdeutige Formate wie z. B. DD-MM-YYYY und MM-DD-YYYY. Beispielsweise sind die Datumsangaben 03-04-1995 und 04-03-1995 ungültig.  
  
-   Grundlegende und erweiterte abgeschnittene Formate für ein vierstelliges Kalenderjahr und einen dreistelligen Tag innerhalb eines Jahres: YYYYDDD und YYYY-DDD.  
  
-   Grundlegende und erweiterte Formate für ein vierstelliges Jahr, eine zweistellige Zahl für die Woche des Jahres und eine einstellige Zahl für den Tag der Woche: YYYYWwwD und YYYY-Www-D.  
  
-   Grundlegende und erweiterte abgeschnittene Formate für ein Jahr und eine Wochenangabe, für ein vierstelliges Jahr und eine zweistellige Zahl für die Woche: YYYWww und YYYY-Www.  
  
 Die schnelle Analyse gibt die Daten als DT_DBDATE aus. Datumswerte in abgeschnittenen Formaten werden aufgefüllt. Beispielsweise wird YYYY zu YYYY0101.  
  
 Weitere Informationen finden Sie unter [Integration Services Datentypen](data-flow/integration-services-data-types.md).  
  
## <a name="time-data-type"></a>Zeitdatentyp  
 Die schnelle Analyse unterstützt die folgenden Zeichenfolgenformate für Zeitdaten:  
  
-   Zeitformate, die führende Leerstellen einschließen. Beispielsweise ist der Wert " 10:24" gültig.  
  
-   24-Stunden-Format. Die schnelle Analyse unterstützt die Angabe von AM (Vormittag) und PM (Nachmittag) nicht.  
  
-   ISO 8601-Zeitformate, wie in der folgenden Tabelle aufgeführt:  
  
    |Format|Description|  
    |------------|-----------------|  
    |HHMISS<br /><br /> HH:MI:SS|Basisformate und erweiterte Formate für eine zweistellige Stundenangabe, eine zweistellige Minutenangabe und eine zweistellige Sekundenangabe. Beim erweiterten Format werden die Zeitteile durch einen Doppelpunkt (:) getrennt.|  
    |HHMI<br /><br /> HH:MI|Basisformate und erweiterte abgeschnittene Formate für eine zweistellige Stundenangabe und eine zweistellige Minutenangabe. Beim erweiterten Format werden die Zeitteile durch einen Doppelpunkt (:) getrennt.|  
    |HH|Das abgeschnittene Format für eine zweistellige Stundenangabe.|  
    |00:00:00<br /><br /> 000000<br /><br /> 0000<br /><br /> 00<br /><br /> 240000<br /><br /> 24:00:00<br /><br /> 2400<br /><br /> 24|Das Format für Mitternacht.|  
  
-   Zeitformate, die eine Zeitzone angeben, wie in der folgenden Tabelle aufgeführt:  
  
    |Format|Description|  
    |------------|-----------------|  
    |+HH:MI<br /><br /> +HHMI|Basisformate und erweiterte Formate, die die Anzahl von Stunden und Minuten angeben, die zur koordinierten Weltzeit (UTC) addiert werden, um die lokale Zeit zu ermitteln.|  
    |-HH:MI<br /><br /> -HHMI|Basisformate und erweiterte Formate, die die Anzahl von Stunden und Minuten angeben, die von der koordinierten Weltzeit (UTC) subtrahiert werden, um die lokale Zeit zu ermitteln.|  
    |+HH|Abgeschnittene Formate, die die Anzahl von Stunden angeben, die zur koordinierten Weltzeit (UTC) addiert werden, um die lokale Zeit zu ermitteln.|  
    |-HH|Abgeschnittene Formate, die die Anzahl von Stunden angeben, die von der koordinierten Weltzeit (UTC) subtrahiert werden, um die lokale Zeit zu ermitteln.|  
    |Z|Ein Wert von 0, der angibt, dass die Zeit in UTC dargestellt wird.|  
  
     Die Formate für alle Zeit- und Datums-/Zeitdaten können ein Zeitzonenelement enthalten. Das System ignoriert jedoch den Zeitzonenwert, außer wenn die Daten vom Typ DT_DBTIMESTAMPOFFSET sind. Weitere Informationen finden Sie unter [Integration Services Datentypen](data-flow/integration-services-data-types.md).  
  
     Bei Formaten, die ein Zeitzonenelement enthalten, gibt es kein Leerzeichen zwischen dem Zeitelement und dem Zeitzonenelement, wie das folgende Beispiel zeigt:  
  
     HH:MI:SS[+HH:MI]  
  
     Die Klammern im vorherigen Beispiel geben an, dass der Zeitzonenwert optional ist.  
  
-   Zeitformate, die einen Dezimalbruch enthalten, wie in der folgenden Tabelle aufgeführt:  
  
    |Format|Description|  
    |------------|-----------------|  
    |HH[.nnnnnnn]|n ist ein Wert zwischen 0 und 9999999, der einen Stundenbruchteil darstellt. Die Klammern geben an, dass dieser Wert optional ist.<br /><br /> Beispielsweise steht der Wert 12.750 für 12:45.|  
    |HHMI[.nnnnnnn]<br /><br /> HH:MI[.nnnnnnn]|n ist ein Wert zwischen 0 und 9999999, der einen Minutenbruchteil darstellt. Die Klammern geben an, dass dieser Wert optional ist.<br /><br /> Beispielsweise steht der Wert 1220.500 für 12:20:30.|  
    |HHMISS[.nnnnnnn]<br /><br /> HH:MI:SS[.nnnnnnn]|n ist ein Wert zwischen 0 und 9999999, der einen Sekundenbruchteil darstellt. Die Klammern geben an, dass dieser Wert optional ist.<br /><br /> Beispielsweise steht der Wert 122040.250 für 12:20:40.15.|  
  
    > [!NOTE]  
    >  Als Trennzeichen für den Bruchteilwert kann bei den Zeitformaten der vorherigen Tabelle ein Punkt oder ein Komma verwendet werden.  
  
-   Zeitwerte, die eine Schaltsekunde enthalten, wie in den folgenden Beispielen gezeigt:  
  
     23:59:60[.0000000]  
  
     235960[.0000000]  
  
 Die schnelle Analyse gibt die Zeichenfolgen als DT_DBTIME und DT_DBTIME2 aus. Zeitwerte in abgeschnittenen Formaten werden aufgefüllt. Beispielsweise wird HH:MI als HH:MM:00.000 ausgegeben.  
  
 Weitere Informationen finden Sie unter [Integration Services Datentypen](data-flow/integration-services-data-types.md).  
  
## <a name="datetime-data-type"></a>Datums-/Zeitdatentyp  
 Die schnelle Analyse unterstützt die folgenden Zeichenfolgenformate für Datums-/Zeitdaten:  
  
-   Zeitformate, die führende Leerstellen enthalten. Beispielsweise ist der Wert "  2003-01-10T203910" gültig.  
  
-   Kombinationen gültiger Datumsformate und gültiger Zeitformate, getrennt durch ein groß geschriebenes T, und gültige Zeitzonenformate, beispielsweise YYYYMMDDT[HHMISS][+HH:MI]. Die Zeit- und Zeitzonenwerte sind nicht erforderlich. Beispielsweise ist "2003-10-14" gültig.  
  
 Die schnelle Analyse unterstützt keine Zeitintervalle. Beispielsweise kann ein Zeitintervall, das durch ein Startdatum und ein Enddatum und eine Zeitangabe im Format YYYYMMDDThhmmss/YYYYMMDDThhmmss identifiziert wird, nicht analysiert werden.  
  
 Die schnelle Analyse gibt die Zeichenfolgen als DT_DATE, DT_DBTIMESTAMP, DT_DBTIMESTAMP2 und DT_DBTIMESTAMPOFFSET aus. Datums-/Zeitwerte in abgeschnittenen Formaten werden aufgefüllt. In der folgenden Tabelle werden die Werte aufgeführt, die für fehlende Datums- und Zeitteile hinzugefügt werden.  
  
|Datums-/Zeitteil|Auffüllung|  
|---------------------|-------------|  
|Sekunden|00 hinzufügen.|  
|Minuten|00:00 hinzufügen.|  
|Hour|00:00:00 hinzufügen.|  
|Day|01 für den Tag des Monats hinzufügen.|  
|Month|01 für den Monat des Jahres hinzufügen.|  
  
 Weitere Informationen finden Sie unter [Integration Services Datentypen](data-flow/integration-services-data-types.md).  
  
  
