---
title: Parallelitätstypen | Microsoft-Dokumentation
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68083184"
---
# <a name="concurrency-types"></a>Parallelitätstypen
Um das Problem der reduzierter Parallelität in Cursorn zu beheben, stellt die ODBC vier verschiedene Typen von Cursorparallelität:  
  
-   **Nur-Lese** des Cursors Daten lesen, aber nicht aktualisieren oder Löschen von Daten kann. Dies ist der Standardtyp für die Parallelität. Obwohl das DBMS Zeilen, um die Repeatable Read- und Serializable-Isolation Levels erzwingen sperren kann, können sie Lesesperren anstelle Schreibsperren verwenden. Dies führt zu höhere Parallelität zu erzielen, da die Daten mindestens von anderen Transaktionen lesen können.  
  
-   **Sperren** der Cursor verwendet die niedrigste Ebene von Sperren erforderlich, um sicherzustellen, dass sie später aktualisieren oder Löschen von Zeilen im Resultset. Dies führt in der Regel sehr niedrigen Parallelitätsstufen, insbesondere auf die Transaktionsisolationsstufen Repeatable Read und Serializable.  
  
-   **Optimistische Parallelität, die mithilfe von Zeilenversionen und vollständige Parallelität mit Werten** der Cursor verwendet die vollständigen Parallelität: Aktualisieren oder Löschen von Zeilen nur dann, wenn diese nicht geändert wurden, seit sie zuletzt gelesen wurden. Um die Änderungen zu erkennen, werden Zeilenversionen oder Werte verglichen. Es gibt keine Garantie, dass der Cursor wird in der Lage, aktualisieren oder Löschen einer Zeile sein, aber die Parallelität ist wesentlich höher als bei der Sperre verwendet wird. Weitere Informationen finden Sie unter den folgenden Abschnitt [optimistische Parallelität](../../../odbc/reference/develop-app/optimistic-concurrency.md).  
  
 Eine Anwendung gibt an, welche Art von Parallelität den Cursor, mit der SQL_ATTR_CONCURRENCY-Anweisungsattribut verwendet werden sollen. Um zu bestimmen, welche Typen unterstützt werden, ruft **SQLGetInfo** mit der Option SQL_SCROLL_CONCURRENCY.
