---
description: Anwendungen
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: dc811b075eb698e5127fc321406bf906012c6d12
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88386136"
---
# <a name="applications"></a>Anwendungen
Eine *Anwendung* ist ein Programm, das die ODBC-API aufruft, um auf Daten zuzugreifen. Obwohl viele Arten von Anwendungen möglich sind, sind die meisten in drei Kategorien unterteilt, die in diesem Handbuch als Beispiele verwendet werden.  
  
-   **Generische Anwendungen** Diese werden auch als verkleinerte Anwendungen oder externe Anwendungen bezeichnet. Generische Anwendungen sind für die Arbeit mit einer Vielzahl von unterschiedlichen DBMSs konzipiert. Beispiele hierfür sind ein tabellenkalkulationstabellen-oder Statistikpaket, das ODBC zum Importieren von Daten zur weiteren Analyse und ein Textverarbeitungs Tool verwendet, das ODBC verwendet, um eine Mailingliste aus einer Datenbank zu erhalten.  
  
     Eine wichtige Unterkategorie von generischen Anwendungen sind Anwendungsentwicklungsumgebungen wie PowerBuilder oder Microsoft® Visual Basic®. Obwohl die mit diesen Umgebungen erstellten Anwendungen wahrscheinlich nur mit einem einzelnen DBMS funktionieren, muss die Umgebung selbst mit mehreren DBMSs funktionieren.  
  
     Was alle generischen Anwendungen gemeinsam haben, besteht darin, dass Sie unter DBMSs hochgradig interoperabel sind und ODBC in einer relativ generischen Weise verwenden müssen. Weitere Informationen zur Interoperabilität finden Sie unter [Auswählen eines Interoperabilitäts Niveaus](../../odbc/reference/develop-app/choosing-a-level-of-interoperability.md).  
  
-   **Vertikale Anwendungen** Vertikale Anwendungen führen eine einzelne Art von Aufgabe aus, z. b. Bestell Eintrag oder Nachverfolgung von Produktionsdaten, und arbeiten mit einem Datenbankschema, das vom Entwickler der Anwendung gesteuert wird. Für einen bestimmten Kunden kann die Anwendung mit einem einzelnen DBMS verwendet werden. Beispielsweise kann ein kleines Unternehmen die Anwendung mit dBASE verwenden, während ein großes Unternehmen es mit Oracle verwenden könnte.  
  
     Die Anwendung verwendet ODBC so, dass die Anwendung nicht an ein DBMS gebunden ist, obwohl Sie möglicherweise an eine begrenzte Anzahl von DBMSs gebunden ist, die eine ähnliche Funktionalität bereitstellen. Der Anwendungsentwickler kann die Anwendung daher unabhängig vom DBMS verkaufen. Vertikale Anwendungen sind interoperabel, wenn Sie entwickelt werden, aber manchmal so geändert werden, dass Sie nicht interoperablen Code enthalten, wenn der Kunde ein DBMS ausgewählt hat.  
  
-   **Benutzerdefinierte Anwendungen** Benutzerdefinierte Anwendungen werden verwendet, um eine bestimmte Aufgabe in einem einzelnen Unternehmen auszuführen. Beispielsweise kann eine Anwendung in einem großen Unternehmen Umsatzdaten aus mehreren Abteilungen erfassen (von denen jeder ein anderes DBMS verwendet) und einen einzelnen Bericht erstellt. ODBC wird verwendet, da es sich um eine gängige Schnittstelle handelt und Programmierer daran gewöhnt sind, mehrere Schnittstellen erlernen zu müssen. Solche Anwendungen sind im Allgemeinen nicht interoperabel und werden in bestimmte DBMSs und Treiber geschrieben.  
  
 Eine Reihe von Aufgaben wird allen Anwendungen gemeinsam verwendet, unabhängig davon, wie Sie ODBC verwenden. Im wesentlichen definieren Sie den Fluss einer beliebigen ODBC-Anwendung. Die Aufgaben lauten:  
  
-   Wählen Sie eine Datenquelle aus, und verbinden Sie Sie.  
  
-   Eine SQL-Anweisung für die Ausführung wird übermittelt.  
  
-   Abrufen von Ergebnissen (sofern vorhanden).  
  
-   Verarbeitungsfehler.  
  
-   Commit oder Rollback der Transaktion, die die SQL-Anweisung einschließt.  
  
-   Die Verbindung mit der Datenquelle wird getrennt.  
  
 Da die meisten Datenzugriffs arbeiten mit SQL ausgeführt werden, ist der primäre Task, bei dem Anwendungen ODBC verwenden, SQL-Anweisungen zu übermitteln und die von diesen Anweisungen generierten Ergebnisse abzurufen. Andere Aufgaben, für die Anwendungen ODBC verwenden, umfassen das ermitteln und Anpassen von Treiberfunktionen und das Durchsuchen des Daten Bank Katalogs.
