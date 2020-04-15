---
title: Optimistische Parallelität | Microsoft Docs
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
- optimistic concurrency [ODBC]
ms.assetid: 9d71e09e-bc68-4c1f-9229-ed2a7be7d324
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 30eba3ea03b4c798a74a8cb928014b582846607b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81282484"
---
# <a name="optimistic-concurrency"></a>Optimistische Nebenläufigkeit
*Optimistische Parallelität* leitet ihren Namen von der optimistischen Annahme ab, dass Es selten zu Kollisionen zwischen Transaktionen kommen wird. Eine Kollision soll aufgetreten sein, wenn eine andere Transaktion eine Datenzeile zwischen dem Zeitpunkt, zu dem sie von der aktuellen Transaktion gelesen wird, und dem Zeitpunkt, zu dem sie aktualisiert oder gelöscht wird, aktualisiert oder gelöscht wird. Es ist das Gegenteil von *pessimistischer Parallelität* oder Sperrung, bei der der Anwendungsentwickler der Ansicht ist, dass solche Kollisionen an der Tagesordnung sind.  
  
 Bei optimistischer Parallelität bleibt eine Zeile entsperrt, bis die Zeit kommt, sie zu aktualisieren oder zu löschen. An diesem Punkt wird die Zeile erneut gelesen und überprüft, um festzustellen, ob sie seit dem letzten Lesen geändert wurde. Wenn sich die Zeile geändert hat, schlägt die Aktualisierung oder das Löschen fehl und muss erneut versucht werden.  
  
 Um festzustellen, ob eine Zeile geändert wurde, wird ihre neue Version mit einer zwischengespeicherten Version der Zeile abgeglichen. Diese Überprüfung kann auf der Zeilenversion basieren, z. B. der Zeitstempelspalte in SQL Server oder den Werten jeder Spalte in der Zeile. Viele DBMS unterstützen keine Zeilenversionen.  
  
 Optimistische Parallelität kann von der Datenquelle oder der Anwendung implementiert werden. In beiden Fällen sollte die Anwendung eine niedrige Transaktionsisolationsstufe verwenden, z. B. Read Committed. Die Verwendung einer höheren Ebene negiert die erhöhte Parallelität, die durch die Verwendung optimistischer Parallelität gewonnen wird.  
  
 Wenn die Quellquelle eine optimistische Parallelität implementiert, legt die Anwendung das Attribut SQL_ATTR_CONCURRENCY Anweisung auf SQL_CONCUR_ROWVER oder SQL_CONCUR_VALUES fest. Um eine Zeile zu aktualisieren oder zu löschen, führt sie eine positionierte Aktualisierungs- oder Löschanweisung aus oder ruft **SQLSetPos** auf, genau wie bei pessimistischer Parallelität. Der Treiber oder die Datenquelle gibt SQLSTATE 01001 (Cursor-Vorgangskonflikt) zurück, wenn die Aktualisierung oder löschung aufgrund einer Kollision fehlschlägt.  
  
 Wenn die Anwendung selbst eine optimistische Parallelität implementiert, legt sie das Attribut SQL_ATTR_CONCURRENCY Anweisung auf SQL_CONCUR_READ_ONLY zum Lesen einer Zeile fest. Wenn zeilenversionen verglichen werden und die Zeilenversionsspalte nicht bekannt ist, ruft sie **SQLSpecialColumns** mit der Option SQL_ROWVER auf, um den Namen dieser Spalte zu bestimmen.  
  
 Die Anwendung aktualisiert oder löscht die Zeile, indem sie die Parallelität auf SQL_CONCUR_LOCK erhöht (um Schreibzugriff auf die Zeile zu erhalten) und eine **UPDATE-** oder **DELETE-Anweisung** mit einer **WHERE-Klausel** ausführt, die die Version oder die Werte angibt, die die Zeile beim Lesen der Zeile hatte. Wenn sich die Zeile seitdem geändert hat, schlägt die Anweisung fehl. Wenn die **WHERE-Klausel** die Zeile nicht eindeutig identifiziert, kann die Anweisung auch andere Zeilen aktualisieren oder löschen. Zeilenversionen identifizieren Zeilen immer eindeutig, Zeilenwerte jedoch nur dann eindeutig, wenn sie den Primärschlüssel enthalten.
