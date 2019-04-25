---
title: Zeit- und Datumsfunktionen (Visual FoxPro-ODBC-Treiber) | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: cf8e7552faf9567dab25ee3dc5b7b293034faef0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62632770"
---
# <a name="time-and-date-functions-visual-foxpro-odbc-driver"></a>Zeit- und Datumsfunktionen (Visual FoxPro-ODBC-Treiber)
In der folgende Tabelle werden die ODBC-Datum und die Funktionen von der Visual FoxPro-ODBC-Treiber unterstützt werden. Wenn die Visual FoxPro-Grammatik für die gleiche Funktion aus der ODBC-Syntax unterscheidet, wird der Visual FoxPro-Äquivalent aufgeführt.  
  
|ODBC-Grammatik|Visual FoxPro-Grammatik|  
|------------------|---------------------------|  
|CURDATE *( )*|DATE *( )*|  
|CURTIME *( )*|TIME *( )*|  
|DAYNAME *(date_exp)*|CDOW *(date_exp)*|  
|DAYOFMONTH(*date_exp)*|DAY *( )*|  
|HOUR *(time_exp)*||  
|MINUTE *(time_exp)*||  
|MONTH *(time_exp)*||  
|MONTHNAME *(date_exp)*|CMONTH *(date_exp)*|  
|NOW *( )*|DATETIME *( )*|  
|SECOND *(time_exp)*|SEC *(time_exp)*|  
|WEEK *(date_exp)*||  
|YEAR *(date_exp)*||  
  
 Die folgenden Funktionen für Datum und Uhrzeit werden nicht unterstützt:  
  
 DAYOFYEAR *(date_exp)*  
  
 QUARTER *(date_exp)*  
  
 TIMESTAMPADD *("Intervall", "Integer_exp", "Timestamp_exp")*  
  
 TIMESTAMPDIFF *(Intervall, timestamp_exp1 timestamp_exp2)*  
  
## <a name="odbc-escape-sequences"></a>ODBC-Escapesequenzen  
 Der Treiber unterstützt auch die ODBC-Escapesequenz für Datums- und Zeitstempel. Die Escape-Klausel-Syntax lautet wie folgt aus:  
  
```  
--(*vendor(Microsoft),product(ODBC) d 'value' *)-  
--(*vendor(Microsoft),product(ODBC) ts ''value' *)-  
```  
  
 In dieser Syntax **d** gibt an, dass *Wert* ein Datum in der *jjjj-mm-tt* Format und **ts** gibt an, dass *Wert*  ist ein Zeitstempel in der *jjjj-mm-tt hh: mm:*[.*f...*] Format. Die Kurzschreibweise der Syntax für Datums- und Zeitstempel lautet wie folgt aus:  
  
```  
{d 'value'}  
{ts 'value'}  
```  
  
 Jede der folgenden Aussagen aktualisiert z. B. die ALLTYPES-Tabelle mithilfe der Datums- und Zeitstempel Kurzschreibweise der Syntax in einem unterstützten SQL UPDATE-Befehl:  
  
```  
UPDATE alltypes  
   SET DAT_COL={d'1968-04-28'}  
   WHERE KEY=111  
  
UPDATE alltypes  
   SET DTI_COL={ts'1968-04-28 12:00:00'}  
   WHERE KEY=111  
```  
  
## <a name="remarks"></a>Hinweise  
 Weitere Informationen zu Escapesequenzen finden Sie unter [Escapesequenzen in ODBC](../../odbc/reference/develop-app/escape-sequences-in-odbc.md) in die *ODBC Programmer's Reference*.
