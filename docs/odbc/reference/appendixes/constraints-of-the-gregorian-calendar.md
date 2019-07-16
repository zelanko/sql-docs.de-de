---
title: Einschränkungen des gregorianischen Kalenders | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], Gregorian calendar
- Gregorian calendar [ODBC]
ms.assetid: 70667410-c582-4369-8e06-9d98e21cd2bf
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9f67d313f5a1261dba1f88e9ef3a70d30c1cd503
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68019185"
---
# <a name="constraints-of-the-gregorian-calendar"></a>Einschränkungen des gregorianischen Kalenders
Date und Datetime-Datentypen und die nachfolgende Felder der Interval-Datentypen, müssen die Einschränkungen des gregorianischen Kalenders entsprechen. Diese Einschränkungen lauten wie folgt aus:  
  
-   Der Wert des Felds Monat muss zwischen 1 und 12 einschließlich sein.  
  
-   Der Wert des Felds Tag muss im Bereich von 1 bis zur Anzahl der Tage im Monat sein. Die Anzahl der Tage im Monat, die von den Werten der Felder Jahr und Monate bestimmt ist und 28, 29, 30 oder 31. (Die Anzahl der Tage im Monat kann auch davon abhängen, ob es sich um ein Schaltjahr ist.)  
  
-   Der Wert des Felds Stunde muss zwischen 0 und einschließlich 23 sein.  
  
-   Der Wert des Felds Minute muss zwischen 0 und einschließlich 59 liegen.  
  
-   Der Wert im Sekundenfeld muss für die nachfolgende Wert im Sekundenfeld der Interval-Datentypen, zwischen 0 und einen Anteil von 59,9 (*n*), einschließlich, in denen *n* ist die Anzahl der Ziffern in der Genauigkeit in Sekundenbruchteilen.  
  
-   Der Wert im Sekundenfeld muss für die nachfolgende Wert im Sekundenfeld der Datetime-Datentypen, zwischen 0 und 61.9 (*n*), einschließlich, in dem *n* gibt die Anzahl der Ziffern mit "9" und den Wert der *n*  ist die Genauigkeit der Bruchteile von Sekunden. (Der Bereich von Sekunden kann bis zu zwei Schaltsekunden, um die Synchronisierung siderischen Zeit aufrechtzuerhalten.)
