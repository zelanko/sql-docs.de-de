---
title: Anwendungen | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f15b5e8eb6eb7c63ab771030f0c31e8c9ff92724
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68135676"
---
# <a name="applications"></a>Anwendungen
Ein *Anwendung* ist ein Programm, das die ODBC-API für den Datenzugriff aufruft. Obwohl viele Arten von Anwendungen möglich sind, fallen in drei Kategorien, die als Beispiele in diesem Handbuch verwendet werden.  
  
-   **Allgemeiner Anwendungen** diese auch als eingeschweißte Anwendungen oder Standardanwendungen bezeichnet werden. Allgemeine Anwendungen dienen zum mit einer Vielzahl von verschiedenen DBMS zu arbeiten. Beispiele: ein Arbeitsblatt oder Statistiken-Paket, das ODBC verwendet wird, zum Importieren von Daten zur weiteren Analyse und ein Textverarbeitungsprogramm, die ODBC verwendet, um eine Adressenliste aus einer Datenbank zu erhalten.  
  
     Eine wichtige Unterkategorie der generischen Anwendungen ist anwendungsentwicklungsumgebungen, z. B. PowerBuilder oder Microsoft® Visual Basic®. Obwohl die Anwendungen, die mit diesen Umgebungen erstellt wahrscheinlich nur mit einer einzelnen DBMS funktioniert, muss die Umgebung selbst arbeiten mit mehreren DBMS.  
  
     Was alle generische Anwendungen gemeinsam haben werden, dass sie zwischen DBMS hochgradig interoperabel sind und sie ODBC relativ allgemein zu verwenden müssen. Weitere Informationen zur Kompatibilität finden Sie unter [Auswählen einer Ebene die Interoperabilität von](../../odbc/reference/develop-app/choosing-a-level-of-interoperability.md).  
  
-   **Vertikale Anwendungen** vertikale Anwendungen führen Sie einen einzelnen Typ, der Aufgaben, z. B. Bestellungen eingeben oder Produktionskalender Daten, nachverfolgung von und Arbeiten mit einem Datenbankschema, die vom Entwickler der Anwendung gesteuert wird. Für einen bestimmten Kunden funktioniert die Anwendung mit einem einzelnen DBMS. Ein kleines Unternehmen verwenden z. B. die Anwendung bei dBase, während ein großes Unternehmen mit Oracle verwendet werden kann.  
  
     Die Anwendung verwendet ODBC auf diese Weise, dass die Anwendung nicht an alle ein DBMS, gebunden ist, obwohl es an eine begrenzte Anzahl von Datenbank-Managementsysteme gebunden werden kann, die ähnliche Funktionalität bereitstellen. Der Anwendungsentwickler kann daher die Anwendung unabhängig vom DBMS verkaufen. Vertikale Anwendungen sind interoperabel, wenn sie entwickelt wurden, aber manchmal angepasst, sodass noninteroperable Code enthalten, wenn der Kunde ein DBMS ausgewählt wurde.  
  
-   **Benutzerdefinierte Anwendungen** benutzerdefinierten Anwendungen werden verwendet, um eine bestimmte Aufgabe in einem einzelnen Unternehmen durchzuführen. Beispielsweise kann eine Anwendung in einem großen Unternehmen sammeln Daten aus mehreren Abteilungen (von denen jeder einen unterschiedlichen DBMS verwendet) und einen einzigen Bericht erstellen. ODBC wird verwendet, da dies eine allgemeine Schnittstelle und erspart Programmierer erfahren, mehrere Schnittstellen. Solche Anwendungen können in der Regel nicht zusammen und in bestimmten DBMS und Zieltreiber geschrieben werden.  
  
 Eine Reihe von Aufgaben gelten für alle Anwendungen, unabhängig davon, wie sie ODBC verwenden. Zusammen definieren sie hauptsächlich den Fluss einer ODBC-Anwendung. Die Aufgaben sind:  
  
-   Auswahl einer Datenquelle und eine Verbindung hergestellt wird.  
  
-   Senden eine SQL-Anweisung für die Ausführung an.  
  
-   Abrufen von Ergebnissen (sofern vorhanden).  
  
-   Verarbeiten von Fehlern.  
  
-   Ein Commit oder Rollback der Transaktion, die die SQL-Anweisung einschließen.  
  
-   Trennen die Datenquelle aus.  
  
 Da die meisten Datenzugriffe mit SQL ausgeführt wird, werden die primäre Aufgabe, die für die Anwendungen die ODBC verwendet SQL-Anweisungen zu senden und Abrufen der Ergebnisse (sofern vorhanden), das durch diese Anweisungen generiert werden. Andere Aufgaben, die für die Anwendungen die ODBC verwendet enthalten bestimmen, auf Treiber Funktionen anpassen, und Durchsuchen des Katalogs für die Datenbank.
