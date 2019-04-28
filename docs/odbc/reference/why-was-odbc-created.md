---
title: Warum wurde ODBC erstellt? | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC [ODBC], about ODBC
ms.assetid: ba6eb993-316b-4650-bab8-d76583c00e53
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 871919554975f04fae0aeaa1b8e6ec684c6650a4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62714147"
---
# <a name="why-was-odbc-created"></a>Warum wurde ODBC erstellt?
In der Vergangenheit verwendet Unternehmen eines einzelnen DBMS. Jeglicher Datenbankzugriff erfolgte durch die Front-End des Systems oder über Anwendungen, die ausschließlich mit dem System die Arbeit. Jedoch gestartet, weil die Verwendung von Computern wuchsen und weitere Computerhardware und-Software verfügbar sind, Unternehmen zum Abrufen der verschiedenen DBMS. Die Gründe wurden viele: Personen, die gekauft, kostengünstigste, was am schnellsten, was sich bereits wussten, was neueste auf dem Markt, was am besten für eine einzelne Anwendung gearbeitet. Andere Gründe wurden neuorganisationen und Fusionen verwendet, bei denen aufwies Abteilungen, die bisher von einer einzelnen DBMS jetzt mehrere.  
  
 Das Problem wächst mit dem Aufkommen der PCs noch komplizierter. Diese Computer auf einem Host von Tools für Abfragen, analysieren und Anzeigen von Daten, zusammen mit einer Anzahl von preiswerten, leicht zu bedienende Datenbanken gebracht wird. Von nun an einem einzigen Unternehmen setzten häufig voraus, Daten, die einer Vielzahl von Desktops, Servern und Minicomputer verteilt und in einer Vielzahl von nicht kompatiblen Datenbanken gespeicherten zugegriffen werden, indem eine große Anzahl von verschiedenen Tools, die einige davon auf alle Daten abgerufen werden konnten.  
  
 Die letzte Hürde kam mit der Einführung von Client-/servercomputerumgebung, die versucht, die optimale Nutzung von Computerressourcen. Kostengünstige PCs (die Clients) auf dem Desktop befinden, und geben Sie sowohl ein grafisches Front-End auf die Daten und eine Reihe von kostengünstige Tools, z. B. Tabellen, Diagrammen, Programme und Bericht-Generatoren. Hosten von Minicomputer und Mainframe-Computer (dem Server) der DBMS-Systeme, in dem sie ihre rechenleistung und einen zentralen Ort verwenden können, um schnelle, koordinierten Zugriff auf Daten bereitzustellen. Klicken Sie dann wie wurde die Front-End-Software mit den Back-End-Datenbanken verbunden werden?  
  
 Ein ähnliches Problem konfrontiert, unabhängige Softwarehersteller (ISVs). Anbieter, die Schreiben von Datenbanksoftware für Minicomputer und Mainframes mussten in der Regel schreiben eine Version einer Anwendung für jede DBMS oder Schreiben von DBMS-spezifischen Code für jede DBMS, die sie zugreifen möchten. Software für Computer, die zum Schreiben von Anbietern musste Data Access-Routinen für jede unterschiedliche DBMS zu schreiben, mit denen sie arbeiten möchten. Dies bedeutete häufig eine große Menge von Ressourcen für das Schreiben und verwalten, für den Datenzugriff Routinen anstelle von Anwendungen und Anwendungen wurden häufig verkauft werden, nicht auf die Qualität, jedoch auf, ob sie Daten in einem bestimmten DBMS zugreifen können aufgewendet wurden.  
  
 Beide Sätze von Entwicklern benötigt wurde eine Möglichkeit zum Zugreifen auf Daten in verschiedenen DBMS-Systeme. Die Gruppe Mainframe- und Minicomputer benötigt eine Möglichkeit zum Zusammenführen von Daten aus verschiedenen DBMS-Systeme in einer einzelnen Anwendung, während die PC-Gruppe erforderlich sind, diese Funktion als auch eine Möglichkeit, eine einzelne Anwendung schreiben, die unabhängig von der alle ein DBMS. Kurz gesagt, benötigt beide Gruppen eine interoperable Möglichkeit für den Datenzugriff werden; Sie benötigt die datenbankverbindung öffnen.
