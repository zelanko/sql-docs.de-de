---
title: Einschränkungen des Gregorianischen Kalenders | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f88842c7426e17af1fdc0533b8b97e2c559de237
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81284760"
---
# <a name="constraints-of-the-gregorian-calendar"></a>Einschränkungen des gregorianischen Kalenders
Datums- und Datumszeitdatentypen sowie die nachfolgenden Felder von Intervalldatentypen müssen den Einschränkungen des Gregorianischen Kalenders entsprechen. Diese Einschränkungen lauten wie folgt:  
  
-   Der Wert des Monatsfelds muss zwischen 1 und 12 liegen, einschließlich.  
  
-   Der Wert des Felds "Tag" muss im Bereich von 1 bis zur Anzahl der Tage im Monat liegen. Die Anzahl der Tage im Monat wird anhand der Werte der Felder "Jahr" und "Monate" ermittelt und kann 28, 29, 30 oder 31 betragen. (Die Anzahl der Tage im Monat kann auch davon abhängen, ob es sich um ein Schaltjahr handelt.)  
  
-   Der Wert des Stundenfelds muss zwischen 0 und 23 liegen, einschließlich.  
  
-   Der Wert des Minutenfelds muss zwischen 0 und 59 liegen, einschließlich.  
  
-   Für das Nachspiel Sekunden der Intervalldatentypen muss der Wert des Sekundenfelds zwischen 0 und 59,9(n) liegen, *einschließlich,* wobei n die Anzahl der Ziffern in der Sekundengenauigkeit ist.*n*  
  
-   Für das Feld "Nachsekunden" der Datetime-Datentypen muss der Wert des Sekundenfelds zwischen 0 und 61,9(*n*) liegen, einschließlich, wobei *n* die Anzahl der "9"-Ziffern angibt und der Wert von *n* die Sekundengenauigkeit ist. (Der Sekundenbereich erlaubt bis zu zwei Schaltsekunden, um die Synchronisation der Siderealzeit aufrechtzuerhalten.)
