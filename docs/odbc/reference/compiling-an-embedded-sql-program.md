---
title: Kompilieren eines eingebetteten SQL-Programms | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL [ODBC], embedded SQL
- SQL statements [ODBC], embedded SQL
- compiling embedded SQL programs [ODBC]
- embedded SQL [ODBC]
ms.assetid: 9e94146a-5b80-4a01-b586-1e03ff05b9ac
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bc8133241ad0b76579e87164350a5c6fe2a39f2e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63186326"
---
# <a name="compiling-an-embedded-sql-program"></a>Kompilieren eines eingebetteten SQL-Programms
Da ein eingebettetes SQL-Programms eine Mischung aus SQL- und Host-Anweisungen enthält, kann es direkt an einen Compiler für die Hostsprache übermittelt werden. Stattdessen wird er durch einen Prozess mit mehreren kompiliert. Obwohl dieser Prozess vom jeweiligen Produkt im Detail variiert, sind die Schritte ungefähr gleich für alle Produkte.  
  
 Die folgende Abbildung zeigt die Schritte zum Kompilieren eines eingebetteten SQL-Programms.  
  
 ![Schritte zum Kompilieren eines eingebetteten SQL-Programms](../../odbc/reference/media/pr02.gif "pr02")  
  
 Fünf Schritte sind erforderlich, beim Kompilieren eines eingebetteten SQL-Programms:  
  
1.  Die eingebetteten SQL-Programms wird an der SQL-Precompiler eine Programmiertool übermittelt. Die vorkompilierten vom Programm gescannt, sucht die eingebettete SQL-Anweisungen und verarbeitet sie. Eine andere vorkompilierten ist erforderlich für jede Programmiersprache, die vom DBMS unterstützt. DBMS-Produkte stellen in der Regel Precompilers für eine oder mehrere Sprachen, darunter C, Pascal, COBOL, Fortran, Ada, PL / ich und verschiedene Sprachen der Assembly.  
  
2.  Die vorkompilierten erzeugt zwei Ausgabedateien an. Die erste Datei ist der Quelldatei, die eingebettete SQL-Anweisungen entfernt. An ihre Stelle ersetzt die vorkompilierten Aufrufe von proprietären DBMS-Routinen, die die Laufzeit-Verknüpfung zwischen dem Programm und das DBMS bereitstellen. Die Namen und die aufrufenden Sequenzen dieser Routinen sind in der Regel nur für den vorkompilierten und das DBMS bekannt; Sie sind sich nicht um eine öffentliche Schnittstelle für das DBMS. Die zweite Datei ist eine Kopie aller eingebettete SQL-Anweisungen in der Anwendung verwendet. Diese Datei ist ein Datenbank-Request-Modul oder DBRM bezeichnet.  
  
3.  Die Quelle-Datei der vorkompilierten Ausgabe wird an den standard-Compiler für die Host-Programmiersprache (z. B. eine C- oder COBOL-Compiler) übermittelt. Der Compiler verarbeitet den Quellcode und Objektcode als Ausgabe erzeugt. Beachten Sie, dass dieser Schritt nichts mit dem DBMS oder mit SQL zu tun hat.  
  
4.  Der Linker akzeptiert die Objektmodule, die vom Compiler generierte, verknüpft sie mit verschiedenen Bibliotheksroutinen und erzeugt ein ausführbares Programm. Die Bibliotheksroutinen verknüpft, in das ausführbare Programm enthalten die proprietären DBMS-Routinen, die in Schritt 2 beschrieben.  
  
5.  Das Datenbank-Anforderung-Modul von der vorkompilierten generiert wird mit einem speziellen Bindung-Hilfsprogramm übermittelt. Dieses Dienstprogramm überprüft die SQL-Anweisungen, analysiert, überprüft hat, und optimiert sie und erzeugt dann einen Plan Access for each-Anweisung. Das Ergebnis ist eine kombinierte Zugriffsplan für das gesamte Programm, eine ausführbare Version von der SQL-Anweisung darstellt. Das Hilfsprogramm für die Bindung speichert den Plan in der Datenbank, in der Regel der Name des Anwendungsprogramms, die sie verwenden zuweisen. Gibt an, ob dieser Schritt zur Kompilier- oder Laufzeit stattfindet, hängt von der DBMS ab.  
  
 Beachten Sie, die die Schritte zum Kompilieren eines eingebetteten SQL-Programms sehr eng mit den weiter oben beschriebenen Schritten korrelieren [Verarbeiten einer SQL-Anweisung](../../odbc/reference/processing-a-sql-statement.md). Beachten Sie insbesondere, dass der vorkompilierten, die SQL-Anweisungen aus der Sprachcode für den Host trennt, und das Hilfsprogramm für die Bindung analysiert und überprüft die SQL-Anweisungen und die Access-Pläne erstellt. In DBMS, in dem Schritt 5 zum Zeitpunkt der Kompilierung stattfindet, erfolgen die ersten vier Schritte der Verarbeitung einer SQL-Anweisung zum Zeitpunkt der Kompilierung, während der letzte Schritt (Ausführung) zur Laufzeit ausgeführt wird. Dies hat es sich um die Auswirkungen bei der Ausführung der Abfrage in eine solche sehr schnelle DBMS.
