---
title: Zeit-und Datumsfunktionen (Visual FoxPro-ODBC-Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC date functions [ODBC]
- Visual FoxPro ODBC driver [ODBC], time and date functions
- FoxPro ODBC driver [ODBC], time and date functions
- time and date functions [ODBC]
- ODBC time and date functions [ODBC]
- date functions [ODBC]
ms.assetid: c1fb63b7-af50-45d6-8dec-ae6ea7119527
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 537af13edf943e27a634d3a8ba4f0f85c645251f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67912402"
---
# <a name="time-and-date-functions-visual-foxpro-odbc-driver"></a>Zeit- und Datumsfunktionen (Visual FoxPro-ODBC-Treiber)
In der folgenden Tabelle sind die vom Visual FoxPro-ODBC-Treiber unterstützten ODBC-Zeit-und Datumsfunktionen aufgeführt. Wenn die Visual FoxPro-Grammatik für dieselbe Funktion von der ODBC-Syntax abweicht, wird die Entsprechung von Visual FoxPro aufgeführt.  
  
|ODBC-Grammatik|Visual FoxPro-Grammatik|  
|------------------|---------------------------|  
|CurrDate *()*|Date *()*|  
|Cursor Zeit *()*|Zeit *()*|  
|DAYNAME *(date_exp)*|CDOW *(date_exp)*|  
|Dayosmonth (*date_exp)*|Tag *()*|  
|Stunde *(time_exp)*||  
|Minute *(time_exp)*||  
|Monat *(time_exp)*||  
|MonthName *(date_exp)*|Cmonth *(date_exp)*|  
|Jetzt *()*|DateTime *()*|  
|Sekunde *(time_exp)*|Sek.*(time_exp)*|  
|Woche *(date_exp)*||  
|Jahr *(date_exp)*||  
  
 Die folgenden Zeit-und Datumsfunktionen werden nicht unterstützt:  
  
 Dayosyear *(date_exp)*  
  
 Quartal *(date_exp)*  
  
 Timestampadd *(Intervall, integer_exp timestamp_exp)*  
  
 Timestampdiff *(Intervall, timestamp_exp1 timestamp_exp2)*  
  
## <a name="odbc-escape-sequences"></a>ODBC-Escapesequenzen  
 Der Treiber unterstützt auch die ODBC-Escapesequenz für Datums-und Zeitstempel Daten. Die Syntax der Escape-Klausel lautet wie folgt:  
  
```  
--(*vendor(Microsoft),product(ODBC) d 'value' *)-  
--(*vendor(Microsoft),product(ODBC) ts ''value' *)-  
```  
  
 In dieser Syntax gibt **d** an, dass der *Wert* ein Datum im Format *yyyy-mm-dd* ist, und **TS** gibt an, dass der *Wert* ein Zeitstempel in *yyyy-mm-dd hh: mm: SS*[ist.* f...*] Ges. Die Kurzform-Syntax für Datums-und Zeitstempel Daten lautet wie folgt:  
  
```  
{d 'value'}  
{ts 'value'}  
```  
  
 Jede der folgenden Anweisungen aktualisiert z. b. die alltypes-Tabelle mit der Kurzzeit-Syntax date und Zeitstempel in einem unterstützten SQL Update-Befehl:  
  
```  
UPDATE alltypes  
   SET DAT_COL={d'1968-04-28'}  
   WHERE KEY=111  
  
UPDATE alltypes  
   SET DTI_COL={ts'1968-04-28 12:00:00'}  
   WHERE KEY=111  
```  
  
## <a name="remarks"></a>Bemerkungen  
 Weitere Informationen zu Escapesequenzen finden Sie unter Escapesequenzen [in ODBC](../../odbc/reference/develop-app/escape-sequences-in-odbc.md) in der *ODBC Programmer es Reference*.
