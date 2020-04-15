---
title: Anwendungen | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- off-the-shelf applications [ODBC]
- ODBC architecture [ODBC], applications
- shrink-wrapped applications [ODBC]
- application development [ODBC], types
- custom applications [ODBC]
- virtual applications [ODBC]
- generic applications [ODBC]
ms.assetid: 39d6461f-0d24-4b7d-a723-843ade15ad73
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9184986883f64bd082ca1db472d887609d3071bd
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306551"
---
# <a name="applications"></a>Anwendungen
Eine *Anwendung* ist ein Programm, das die ODBC-API aufruft, um auf Daten zuzugreifen. Obwohl viele Arten von Anwendungen möglich sind, lassen sich die meisten in drei Kategorien einteilen, die in diesem Handbuch als Beispiele verwendet werden.  
  
-   **Generische Anwendungen** Diese werden auch als schrumpfverpackte Anwendungen oder Standardanwendungen bezeichnet. Generische Anwendungen sind für die Arbeit mit einer Vielzahl unterschiedlicher DBMS konzipiert. Beispiele hierfür sind ein Tabellenkalkulations- oder Statistikpaket, das ODBC zum Importieren von Daten für weitere Analysen verwendet, und ein Textverarbeitungsprogramm, das ODBC verwendet, um eine Mailingliste aus einer Datenbank abzurufen.  
  
     Eine wichtige Unterkategorie generischer Anwendungen sind Anwendungsentwicklungsumgebungen wie PowerBuilder oder Microsoft® Visual Basic®. Obwohl die mit diesen Umgebungen erstellten Anwendungen wahrscheinlich nur mit einem einzelnen DBMS funktionieren, muss die Umgebung selbst mit mehreren DBMS arbeiten.  
  
     Allen generischen Anwendungen gemeinsam ist, dass sie unter DBMS sehr interoperabel sind und ODBC relativ allgemein verwenden müssen. Weitere Informationen zur Interoperabilität finden Sie unter [Auswählen eines Interoperabilitätsgrads](../../odbc/reference/develop-app/choosing-a-level-of-interoperability.md).  
  
-   **Vertikale Anwendungen** Vertikale Anwendungen führen einen einzelnen Aufgabentyp aus, z. B. Auftragserfassung oder Nachverfolgung von Fertigungsdaten, und arbeiten mit einem Datenbankschema, das vom Entwickler der Anwendung gesteuert wird. Für einen bestimmten Kunden arbeitet die Anwendung mit einem einzelnen DBMS. Beispielsweise kann ein kleines Unternehmen die Anwendung mit dBase verwenden, während ein großes Unternehmen sie mit Oracle verwenden kann.  
  
     Die Anwendung verwendet ODBC in einer Weise, dass die Anwendung nicht an ein DBMS gebunden ist, obwohl sie an eine begrenzte Anzahl von DBMS gebunden sein könnte, die ähnliche Funktionen bieten. Somit kann der Anwendungsentwickler die Anwendung unabhängig vom DBMS verkaufen. Vertikale Anwendungen sind interoperabel, wenn sie entwickelt werden, werden aber manchmal so geändert, dass sie nicht interoperablen Code enthalten, sobald der Kunde ein DBMS ausgewählt hat.  
  
-   **Benutzerdefinierte Anwendungen** Benutzerdefinierte Anwendungen werden verwendet, um eine bestimmte Aufgabe in einem einzigen Unternehmen auszuführen. Beispielsweise kann eine Anwendung in einem großen Unternehmen Verkaufsdaten aus mehreren Abteilungen (von denen jede ein anderes DBMS verwendet) sammeln und einen einzelnen Bericht erstellen. ODBC wird verwendet, weil es eine gemeinsame Schnittstelle ist und Programmierer davor bewahrt, mehrere Schnittstellen zu erlernen. Solche Anwendungen sind in der Regel nicht interoperabel und werden auf bestimmte DBMS und Treiber geschrieben.  
  
 Eine Reihe von Aufgaben sind allen Anwendungen gemeinsam, unabhängig davon, wie sie ODBC verwenden. Zusammengenommen definieren sie weitgehend den Fluss jeder ODBC-Anwendung. Die Aufgaben sind:  
  
-   Auswählen einer Datenquelle und Herstellen einer Verbindung mit ihr.  
  
-   Senden einer SQL-Anweisung zur Ausführung.  
  
-   Abrufen von Ergebnissen (falls vorhanden).  
  
-   Verarbeitungsfehler.  
  
-   Übertragen oder Zurückfahren der Transaktion, die die SQL-Anweisung einschließt.  
  
-   Trennen der Verbindung zur Datenquelle.  
  
 Da die meisten Datenzugriffsarbeiten mit SQL ausgeführt werden, besteht die primäre Aufgabe, für die Anwendungen ODBC verwenden, darin, SQL-Anweisungen zu übermitteln und die ergebnisse (falls vorhanden) abzurufen, die durch diese Anweisungen generiert werden. Weitere Aufgaben, für die Anwendungen ODBC verwenden, sind das Bestimmen und Anpassen der Treiberfunktionen und das Durchsuchen des Datenbankkatalogs.
