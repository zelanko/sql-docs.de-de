---
title: Reihenfolge der Statusdatensätze | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], diagnostic records
- status records [ODBC]
- diagnostic records [ODBC]
ms.assetid: 0e0436cc-230f-44b0-b373-04a57e83ee76
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bb26731a85d1d6313658fe9c24a32167b351d2d9
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304171"
---
# <a name="sequence-of-status-records"></a>Sequenz der Statusdatensätze
Wenn zwei oder mehr Statusdatensätze zurückgegeben werden, ordnen der Treiber-Manager und der Treiber sie nach den folgenden Regeln ein. Der Rekord mit dem höchsten Rang ist der erste Datensatz. Die Quelle eines Datensatzes (Treiber-Manager, Treiber, Gateway usw.) wird beim Rangieren von Datensätzen nicht berücksichtigt.  
  
-   **Fehler** Statusdatensätze, die Fehler beschreiben, haben den höchsten Rang. Unter Den Fehlerdatensätzen übersteigen Datensätze, die auf einen Transaktionsfehler oder einen möglichen Transaktionsfehler hinweisen, alle anderen Datensätze. Wenn zwei oder mehr Datensätze dieselbe Fehlerbedingung beschreiben, übertreffen SQLSTATEs, die durch die OPEN Group CLI-Spezifikation (Klassen 03 bis HZ) definiert werden, ODBC-definierte und treiberdefinierte SQLSTATEs.  
  
-   **Implementierungsdefinierte Keine Datenwerte** Statusdatensätze, die treiberdefinierte No Data-Werte (Klasse 02) beschreiben, haben den zweithöchsten Rang.  
  
-   **Warnungen** Statusdatensätze, die Warnungen beschreiben (Klasse 01), haben den niedrigsten Rang. Wenn zwei oder mehr Datensätze dieselbe Warnbedingung beschreiben, übertrifft die Warnung SQLSTATEs, die durch die CLI-Spezifikation "Open Group" definiert wurden, ODBC-definierte und treiberdefinierte SQLSTATEs.  
  
 Wenn zwei oder mehr Datensätze mit dem höchsten Rang vorhanden sind, ist nicht definiert, welcher Datensatz der erste Datensatz ist. Die Reihenfolge aller anderen Datensätze ist nicht definiert. Da Warnungen vor Fehlern angezeigt werden können, sollten Anwendungen insbesondere alle Statusdatensätze überprüfen, wenn eine Funktion einen anderen Wert als SQL_SUCCESS zurückgibt.
