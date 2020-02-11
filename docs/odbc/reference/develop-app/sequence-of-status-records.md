---
title: Sequenz von Status Datensätzen | Microsoft-Dokumentation
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
ms.openlocfilehash: 67eac22a630305f32f141ea18861e5638445f19b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68094349"
---
# <a name="sequence-of-status-records"></a>Sequenz der Statusdatensätze
Wenn mindestens zwei Statusdaten Sätze zurückgegeben werden, werden Sie vom Treiber-Manager und vom Treiber gemäß den folgenden Regeln eingestuft. Der Datensatz mit dem höchsten Rang ist der erste Datensatz. Die Quelle eines Datensatzes (Treiber-Manager, Treiber, Gateway usw.) wird bei der Rangfolge von Datensätzen nicht berücksichtigt.  
  
-   **Fehler** Status Datensätze, in denen Fehler beschrieben werden, haben den höchsten Rang. Datensätze, die auf einen Transaktionsfehler oder einen möglichen Transaktionsfehler hinweisen, verursachen alle anderen Datensätze. Wenn zwei oder mehr Datensätze denselben Fehlerzustand beschreiben, werden von Sqlstates, die durch die Open Group CLI-Spezifikation (Klassen 03 bis Hz) definiert werden, ODBC-definierte und Treiber definierte Sqlstates überstehen.  
  
-   Von der **Implementierung definierte Datenwerte** Status Datensätze, die vom Treiber definierte No-Data-Werte (Klasse 02) beschreiben, haben den zweiten höchsten Rang.  
  
-   **Warnungen** Status Datensätze, die Warnungen (Class 01) beschreiben, haben den niedrigsten Rang. Wenn zwei oder mehr Datensätze dieselbe Warnungs Bedingung beschreiben, wird die Warnung Sqlstates, die von der Open Group CLI-Spezifikation definiert wird, für ODBC-definierte und Treiber definierte Sqlstates angezeigt.  
  
 Wenn zwei oder mehr Datensätze mit dem höchsten Rang vorhanden sind, ist nicht definiert, welcher Datensatz der erste Datensatz ist. Die Reihenfolge aller anderen Datensätze ist nicht definiert. Insbesondere, da Warnungen vor Fehlern angezeigt werden können, sollten Anwendungen alle Statusdaten Sätze überprüfen, wenn eine Funktion einen anderen Wert als SQL_SUCCESS zurückgibt.
