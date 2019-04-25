---
title: Vollständige Parallelität | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fa80ff3359e3bbbed9e28044cce7514006c40f10
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62446212"
---
# <a name="optimistic-concurrency"></a>Optimistische Nebenläufigkeit
*Vollständige Parallelität* Name abgeleitet wird, von der optimistischen Annahme, dass Konflikte zwischen Transaktionen nur selten auftreten werden, als ein Konflikt aufgetreten sind wird, wenn eine andere Transaktion aktualisiert oder eine Zeile von Daten zwischen dem Zeitpunkt löscht, er wird gelesen, nach der aktuellen Transaktion und der Uhrzeit wird aktualisiert oder gelöscht. Dies ist das Gegenteil von *pessimistische Parallelität* oder Sperren in der Entwickler der Anwendung ist der Auffassung, dass solche Konflikte üblich sind.  
  
 Bei der vollständigen Parallelität, bleibt eine Zeile nicht gesperrt, bis die Zeit, die zum Aktualisieren oder löschen es kommt. An diesem Punkt wird die Zeile gebundenes und überprüft, um festzustellen, ob es seit dem letzten Lesen geändert wurde. Wenn die Zeile geändert hat, wird die Update- oder Delete schlägt fehl und wiederholt werden muss.  
  
 Um zu bestimmen, ob eine Zeile geändert wurde, wird die neue Version mit einer zwischengespeicherten Version der Zeile verglichen. Diese Prüfung kann auf die Zeilenversion, z. B. die Timestamp-Spalte in SQL Server oder die Werte der einzelnen Spalten in der Zeile basieren. Viele Datenbankmanagementsysteme unterstützt Zeilenversionen nicht.  
  
 Vollständige Parallelität kann von der Datenquelle oder die Anwendung implementiert werden. In beiden Fällen sollte die Anwendung eine niedrige Transaktionsisolationsstufe beispielsweise Read Committed verwenden; mit einer höheren Ebene negiert die erhöhte Parallelität durch vollständige Parallelität erzielt.  
  
 Wenn vollständige Parallelität von der Datenquelle implementiert wird, legt die Anwendung das Anweisungsattribut SQL_ATTR_CONCURRENCY SQL_CONCUR_ROWVER oder SQL_CONCUR_VALUES fest. Zum Aktualisieren oder Löschen einer Zeile, führt er ein positioniertes Update oder Delete-Anweisung oder Aufrufe **SQLSetPos** genau wie von pessimistischen Parallelität; gibt das Treiber oder die Datenquelle SQLSTATE 01001 (Konflikt beim Cursorvorgang) an, wenn die Fehler bei der Update- oder Delete aufgrund einen Konflikt.  
  
 Wenn die Anwendung selbst auf vollständigen Parallelität implementiert, wird das SQL_ATTR_CONCURRENCY-Anweisungsattribut auf SQL_CONCUR_READ_ONLY, eine Zeile zu lesen. Wenn es die Zeilenversionen verglichen werden und die Zeilenversionsspalte ist nicht bekannt, ruft es **SQLSpecialColumns** SQL_ROWVER Optional können Sie den Namen dieser Spalte zu bestimmen.  
  
 Die Anwendung aktualisiert oder löscht die Zeile durch das Erhöhen der Parallelität auf SQL_CONCUR_LOCK fest (um Schreibzugriff auf die Zeile zu erhalten) und Ausführen einer **UPDATE** oder **löschen** -Anweisung mit einer **, in denen**  -Klausel, die gibt die Version oder die Werte der zeilenupdates hatte, wenn die Anwendung, die sie lesen. Wenn die Zeile seit damals geändert hat, schlägt die Anweisung fehl. Wenn die **, in denen** Klausel wird die Zeile nicht eindeutig identifiziert, die Anweisung kann auch aktualisieren oder löschen Sie die anderen Zeilen; Zeilenversionen immer eindeutig identifiziert Zeilen, aber Zeilenwerte Zeilen eindeutig zu identifizieren, nur dann, wenn sie den Primärschlüssel enthalten.
