---
title: Parallelitäts Typen | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 63d7c7dce51fe4f514232cfd0d5ae2e5abeb5b70
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68083184"
---
# <a name="concurrency-types"></a>Parallelitätstypen
Um das Problem der reduzierten Parallelität in Cursorn zu beheben, macht ODBC vier verschiedene Arten von Cursor Parallelität verfügbar:  
  
-   **** Schreibgeschützt Der Cursor kann Daten lesen, aber keine Daten aktualisieren oder löschen. Dies ist der Standard Parallelitäts Typ. Obwohl das DBMS Zeilen sperren kann, um die wiederholbaren Lese-und serialisierbaren Isolations Stufen zu erzwingen, kann es Lese Sperren anstelle von Schreib Sperren verwenden. Dies führt zu einer höheren Parallelität, da andere Transaktionen die Daten zumindest lesen können.  
  
-   **Sperren** Der Cursor verwendet die niedrigste erforderliche Sperrungs Ebene, um sicherzustellen, dass er Zeilen im Resultset aktualisieren oder löschen kann. Dies führt in der Regel zu sehr niedrigen Parallelitäts Stufen, insbesondere bei wiederholbaren Lese-und serialisierbaren Transaktions Isolations Stufen.  
  
-   **Optimistische Parallelität mithilfe von Zeilen Versionen und optimistischer** Parallelität mithilfe von Werten Der Cursor verwendet vollständige Parallelität: er aktualisiert oder löscht nur Zeilen, wenn Sie sich seit dem letzten Lesevorgang nicht geändert haben. Zum Erkennen von Änderungen werden Zeilen Versionen oder-Werte verglichen. Es gibt keine Garantie, dass der Cursor eine Zeile aktualisieren oder löschen kann, aber die Parallelität ist weitaus höher als bei der Verwendung von Sperren. Weitere Informationen finden Sie im folgenden Abschnitt [optimistische](../../../odbc/reference/develop-app/optimistic-concurrency.md)Parallelität.  
  
 Eine Anwendung gibt an, welche Art von Parallelität der Cursor mit dem SQL_ATTR_CONCURRENCY-Anweisungs Attribut verwenden soll. Um zu ermitteln, welche Typen unterstützt werden, ruft Sie **SQLGetInfo** mit der SQL_SCROLL_CONCURRENCY-Option auf.
