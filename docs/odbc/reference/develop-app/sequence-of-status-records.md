---
title: Sequenz der Statusdatensätze | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 17a88095611a5f551708f3950359063317368757
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62465918"
---
# <a name="sequence-of-status-records"></a>Sequenz der Statusdatensätze
Wenn zwei oder mehr Statusdatensätze zurückgegeben werden, Ihre Rangordnung der Treiber-Manager und die Treiber nach den folgenden Regeln. Der Datensatz mit den höchsten Rang ist der erste Datensatz. Die Quelle eines Datensatzes (Treiber-Manager, Treiber, Gateway, usw.) wird nicht berücksichtigt, wenn Datensätze Rangfolge.  
  
-   **Fehler** Statusdatensätze, die Fehler beschreiben, weisen den höchsten Rang. Zwischen Fehlerdatensätze outrank Datensätze, die ein Fehlschlagen der Transaktion oder möglichen Transaktionsfehler angeben für alle anderen Datensätze. Wenn zwei oder mehr Datensätze über die gleiche fehlerbedingung beschreiben, outrank SQLSTATEs, die durch die Open Group-CLI-Spezifikation (Klassen 03 über HZ) definiert die ODBC-definierten und treiberdefinierten SQLSTATEs.  
  
-   **Keine Datenwerte Implementierung definierten** Statusdatensätze, die beschreiben, treiberdefinierten keine Datenwerte (Klasse 02) haben die zweite höchsten Rang.  
  
-   **Warnungen** Status-Datensätze, die beschreiben, Warnungen (01-Klasse) sind den niedrigsten Rang. Wenn zwei oder mehr Datensätze die gleichen warnungsbedingung, durch die Open Group-CLI-Spezifikation definiert SQLSTATEs Warnung beschreiben outrank ODBC-definierten und treiberdefinierten SQLSTATEs.  
  
 Wenn zwei oder mehr Datensätze mit den höchsten Rang vorhanden sind, ist nicht definiert, welcher Datensatz den ersten Datensatz ist. Die Reihenfolge der alle anderen Datensätze ist nicht definiert. Insbesondere, da Warnungen vor Fehlern angezeigt werden können, sollten Anwendungen alle Statusdatensätze überprüfen, wenn eine Funktion einen anderen Wert als SQL_SUCCESS zurückgibt.
