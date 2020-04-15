---
title: Zeit- und Datumsfunktionen (Visual FoxPro ODBC-Treiber) | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 86260f8e7245bed15122d4dbfc4649131674e17f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303061"
---
# <a name="time-and-date-functions-visual-foxpro-odbc-driver"></a>Zeit- und Datumsfunktionen (Visual FoxPro-ODBC-Treiber)
In der folgenden Tabelle sind ODBC-Zeit- und Datumsfunktionen aufgeführt, die vom Visual FoxPro ODBC-Treiber unterstützt werden. Wenn sich die Visual FoxPro-Grammatik für dieselbe Funktion von der ODBC-Syntax unterscheidet, wird das Visual FoxPro-Äquivalent aufgelistet.  
  
|ODBC-Grammatik|Visuelle FoxPro-Grammatik|  
|------------------|---------------------------|  
|CURDATE *( )*|DATUM *( )*|  
|CURTIME *( )*|ZEIT *( )*|  
|DAYNAME *(date_exp)*|CDOW *(date_exp)*|  
|DAYOFMONTH(*date_exp)*|TAG *( )*|  
|HOUR *(time_exp)*||  
|MINUTE *(time_exp)*||  
|MONAT *(time_exp)*||  
|MONATNAME *(date_exp)*|CMONTH *(date_exp)*|  
|JETZT *( )*|*DATUMSZEIT ( )*|  
|ZWEITE *(time_exp)*|SEC *(time_exp)*|  
|WOCHE *(date_exp)*||  
|JAHR *(date_exp)*||  
  
 Die folgenden Uhrzeit- und Datumsfunktionen werden nicht unterstützt:  
  
 DAYOFYEAR *(date_exp)*  
  
 QUARTER *(date_exp)*  
  
 TIMESTAMPADD *(Intervall, integer_exp, timestamp_exp)*  
  
 TIMESTAMPDIFF *(Intervall, timestamp_exp1, timestamp_exp2)*  
  
## <a name="odbc-escape-sequences"></a>ODBC-Escapesequenzen  
 Der Treiber unterstützt auch die ODBC-Escape-Sequenz für Datums- und Zeitstempeldaten. Die Escape-Klausel-Syntax lautet wie folgt:  
  
```  
--(*vendor(Microsoft),product(ODBC) d 'value' *)-  
--(*vendor(Microsoft),product(ODBC) ts ''value' *)-  
```  
  
 In dieser Syntax gibt **d** an, dass *der Wert* ein Datum im *yyyy-mm-dd-Format* ist, und **ts** gibt an, dass *der Wert* ein Zeitstempel im *yyyy-mm-dd hh:mm:ss*[ist.* f...*] Format. Die Kurzschriftsyntax für Datums- und Zeitstempeldaten lautet wie folgt:  
  
```  
{d 'value'}  
{ts 'value'}  
```  
  
 Beispielsweise aktualisiert jede der folgenden Anweisungen die ALLTYPES-Tabelle mithilfe der Datums- und Zeitstempel-Kurzschriftsyntax in einem unterstützten SQL UPDATE-Befehl:  
  
```  
UPDATE alltypes  
   SET DAT_COL={d'1968-04-28'}  
   WHERE KEY=111  
  
UPDATE alltypes  
   SET DTI_COL={ts'1968-04-28 12:00:00'}  
   WHERE KEY=111  
```  
  
## <a name="remarks"></a>Bemerkungen  
 Weitere Informationen zu Escape-Sequenzen finden Sie unter [Escape-Sequenzen in ODBC](../../odbc/reference/develop-app/escape-sequences-in-odbc.md) in der *ODBC-Programmiererreferenz*.
