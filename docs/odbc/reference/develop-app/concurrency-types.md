---
title: Parallelitätstypen | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- transactions [ODBC], concurrency control
- concurrency control [ODBC]
- locking concurrency control [ODBC]
- optimistic concurrency [ODBC]
- read-only concurrency control [ODBC]
ms.assetid: 46762ae5-17dd-4777-968e-58156f470fe1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 642301d09c5aa189276db534e58aca0c5e00e3ce
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299100"
---
# <a name="concurrency-types"></a>Parallelitätstypen
Um das Problem der reduzierten Parallelität in Cursorn zu lösen, stellt ODBC vier verschiedene Typen von Cursorparallelität bereit:  
  
-   **Schreibgeschützt** Der Cursor kann Daten lesen, aber keine Daten aktualisieren oder löschen. Dies ist der Standardparallelitätstyp. Obwohl das DBMS Zeilen sperren kann, um die wiederholbaren Lese- und Serialisierbaren Isolationsebenen zu erzwingen, kann es Lesesperren anstelle von Schreibsperren verwenden. Dies führt zu einer höheren Parallelität, da andere Transaktionen die Daten zumindest lesen können.  
  
-   **Verriegelung** Der Cursor verwendet die niedrigste Sperrebene, die erforderlich ist, um sicherzustellen, dass er Zeilen im Resultset aktualisieren oder löschen kann. Dies führt in der Regel zu sehr niedrigen Parallelitätsstufen, insbesondere auf den Ebenen "Wiederholbare Lese- und Serialisierbare Transaktionsisolation".  
  
-   **Optimistische Parallelität mit Zeilenversionen und optimistische Parallelität unter Verwendung von Werten** Der Cursor verwendet eine optimistische Parallelität: Er aktualisiert oder löscht Zeilen nur, wenn sie sich seit dem letzten Lesen nicht geändert haben. Um Änderungen zu erkennen, werden Zeilenversionen oder -werte verglichen. Es gibt keine Garantie, dass der Cursor eine Zeile aktualisieren oder löschen kann, aber die Parallelität ist viel höher als bei der Verwendung des Sperrens. Weitere Informationen finden Sie im folgenden Abschnitt [Optimistische Parallelität](../../../odbc/reference/develop-app/optimistic-concurrency.md).  
  
 Eine Anwendung gibt an, welchen Parallelitätstyp der Cursor mit dem Attribut SQL_ATTR_CONCURRENCY Anweisung verwenden soll. Um zu bestimmen, welche Typen unterstützt werden, ruft es **SQLGetInfo** mit der Option SQL_SCROLL_CONCURRENCY auf.
