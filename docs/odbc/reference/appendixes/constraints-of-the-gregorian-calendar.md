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
manager: craigg
ms.openlocfilehash: 30fbdd17e7ec5eb970948e1c7133020081222614
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47847928"
---
# <a name="constraints-of-the-gregorian-calendar"></a>Einschränkungen des gregorianischen Kalenders
Date und Datetime-Datentypen und die nachfolgende Felder der Interval-Datentypen, müssen die Einschränkungen des gregorianischen Kalenders entsprechen. Diese Einschränkungen lauten wie folgt aus:  
  
-   Der Wert des Felds Monat muss zwischen 1 und 12 einschließlich sein.  
  
-   Der Wert des Felds Tag muss im Bereich von 1 bis zur Anzahl der Tage im Monat sein. Die Anzahl der Tage im Monat, die von den Werten der Felder Jahr und Monate bestimmt ist und 28, 29, 30 oder 31. (Die Anzahl der Tage im Monat kann auch davon abhängen, ob es sich um ein Schaltjahr ist.)  
  
-   Der Wert des Felds Stunde muss zwischen 0 und einschließlich 23 sein.  
  
-   Der Wert des Felds Minute muss zwischen 0 und einschließlich 59 liegen.  
  
-   Der Wert im Sekundenfeld muss für die nachfolgende Wert im Sekundenfeld der Interval-Datentypen, zwischen 0 und einen Anteil von 59,9 (*n*), einschließlich, in denen *n* ist die Anzahl der Ziffern in der Genauigkeit in Sekundenbruchteilen.  
  
-   Der Wert im Sekundenfeld muss für die nachfolgende Wert im Sekundenfeld der Datetime-Datentypen, zwischen 0 und 61.9 (*n*), einschließlich, in dem *n* gibt die Anzahl der Ziffern mit "9" und den Wert der *n*  ist die Genauigkeit der Bruchteile von Sekunden. (Der Bereich von Sekunden kann bis zu zwei Schaltsekunden, um die Synchronisierung siderischen Zeit aufrechtzuerhalten.)
