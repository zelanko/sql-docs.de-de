---
title: Optimistische Parallelität | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81282484"
---
# <a name="optimistic-concurrency"></a>Optimistische Nebenläufigkeit
Die *optimistische* Parallelität leitet den Namen von der vollständigen Annahme ab, dass Konflikte zwischen Transaktionen selten auftreten. Es ist ein Konflikt aufgetreten, wenn eine andere Transaktion eine Daten Zeile zwischen dem Zeitpunkt, zu dem Sie von der aktuellen Transaktion gelesen wird, und dem Zeitpunkt, zu dem Sie aktualisiert oder gelöscht wird, aktualisiert oder gelöscht hat. Dies ist das Gegenteil der *pessimistischen* Parallelität oder Sperrung, bei der der Anwendungsentwickler der Meinung ist, dass derartige Kollisionen üblich sind.  
  
 In optimistischer Parallelität wird eine Zeile bis zum Aktualisieren oder Löschen der Zeit gesperrt. An diesem Punkt wird die Zeile erneut angezeigt und geprüft, ob Sie seit dem letzten Lesen geändert wurde. Wenn die Zeile geändert wurde, schlägt die Aktualisierung oder Löschung fehl und muss erneut versucht werden.  
  
 Um zu ermitteln, ob eine Zeile geändert wurde, wird die neue Version anhand einer zwischengespeicherten Version der Zeile überprüft. Diese Überprüfung kann auf der Zeilen Version basieren, wie z. b. der Zeitstempel-Spalte in SQL Server oder den Werten der einzelnen Spalten in der Zeile. Viele DBMSs unterstützen keine Zeilen Versionen.  
  
 Die optimistische Parallelität kann von der Datenquelle oder der Anwendung implementiert werden. In jedem Fall sollte die Anwendung eine niedrige Transaktions Isolationsstufe verwenden, z. b. Read Commit. die Verwendung einer höheren Ebene negiert die erhöhte Parallelität, die durch die Verwendung optimistischer Parallelität erzielt wurde.  
  
 Wenn die vollständige Parallelität durch die Datenquelle implementiert wird, legt die Anwendung das SQL_ATTR_CONCURRENCY-Anweisungs Attribut auf SQL_CONCUR_ROWVER oder SQL_CONCUR_VALUES fest. Um eine Zeile zu aktualisieren oder zu löschen, führt Sie eine positionierte UPDATE-oder DELETE-Anweisung aus oder ruft **SQLSetPos** genauso wie bei der pessimistischen Parallelität auf. der Treiber oder die Datenquelle gibt SQLSTATE 01001 (Cursor Vorgangs Konflikt) zurück, wenn die Aktualisierung oder der Löschvorgang aufgrund eines Konflikts fehlschlägt.  
  
 Wenn die Anwendung selbst vollständige Parallelität implementiert, legt Sie das Attribut SQL_ATTR_CONCURRENCY Anweisung auf SQL_CONCUR_READ_ONLY fest, um eine Zeile zu lesen. Wenn die Zeilen Versionen verglichen werden und die Spalte Zeilen Version nicht bekannt ist, wird **SQLSpecialColumns** mit der Option SQL_ROWVER aufgerufen, um den Namen dieser Spalte zu bestimmen.  
  
 Die Anwendung aktualisiert oder löscht die Zeile durch Erhöhen der Parallelität auf SQL_CONCUR_LOCK (um Schreibzugriff auf die Zeile zu erhalten) und durch Ausführen einer **Update** -oder **Delete** -Anweisung mit einer **Where** -Klausel, die die Version oder die Werte der Zeile angibt, wenn Sie von der Anwendung gelesen wurde. Wenn sich die Zeile seitdem geändert hat, schlägt die Anweisung fehl. Wenn die Zeile von der **Where** -Klausel nicht eindeutig identifiziert wird, kann die Anweisung auch andere Zeilen aktualisieren oder löschen. Zeilen Versionen identifizieren immer eindeutig Zeilen, aber Zeilen Werte identifizieren nur Zeilen eindeutig, wenn Sie den Primärschlüssel enthalten.
