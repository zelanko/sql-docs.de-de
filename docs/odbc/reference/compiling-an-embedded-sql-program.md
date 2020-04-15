---
title: Kompilieren eines Embedded SQL-Programms | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: eb801dc532009410055b67031b3e036cc6b9c3d0
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306531"
---
# <a name="compiling-an-embedded-sql-program"></a>Kompilieren eines eingebetteten SQL-Programms
Da ein eingebettetes SQL-Programm eine Mischung aus SQL- und Hostsprachenanweisungen enthält, kann es nicht direkt an einen Compiler für die Hostsprache übermittelt werden. Stattdessen wird es durch einen mehrstufigen Prozess kompiliert. Obwohl sich dieser Prozess von Produkt zu Produkt unterscheidet, sind die Schritte für alle Produkte in etwa gleich.  
  
 In dieser Abbildung werden die Schritte veranschaulicht, die zum Kompilieren eines eingebetteten SQL-Programms erforderlich sind.  
  
 ![Schritte zum Kompilieren eines eingebetteten SQL-Programms](../../odbc/reference/media/pr02.gif "pr02")  
  
 Beim Kompilieren eines eingebetteten SQL-Programms sind fünf Schritte erforderlich:  
  
1.  Das eingebettete SQL-Programm wird an den SQL-Vorcompiler, ein Programmiertool, übermittelt. Der Vorkompilierer scannt das Programm, findet die eingebetteten SQL-Anweisungen und verarbeitet sie. Für jede Programmiersprache, die vom DBMS unterstützt wird, ist ein anderer Vorkompilatierer erforderlich. DBMS-Produkte bieten in der Regel Vorkompilierer für eine oder mehrere Sprachen, einschließlich C, Pascal, COBOL, Fortran, Ada, PL/I und verschiedene Assemblysprachen.  
  
2.  Der Vorkompilierer erzeugt zwei Ausgabedateien. Die erste Datei ist die Quelldatei, die von den eingebetteten SQL-Anweisungen entfernt wurde. An ihrer Stelle ersetzt der Vorkompilierer Aufrufe proprietärer DBMS-Routinen, die die Laufzeitverbindung zwischen dem Programm und dem DBMS bereitstellen. In der Regel sind die Namen und die Aufrufensequenzen dieser Routinen nur dem Vorkompilator und dem DBMS bekannt. Sie stellen keine öffentliche Schnittstelle zum DBMS her. Die zweite Datei ist eine Kopie aller eingebetteten SQL-Anweisungen, die im Programm verwendet werden. Diese Datei wird manchmal als Datenbankanforderungsmodul oder DBRM bezeichnet.  
  
3.  Die Quelldateiausgabe des Vorkompilcompilers wird an den Standardcompiler für die Hostprogrammiersprache (z. B. einen C- oder COBOL-Compiler) übermittelt. Der Compiler verarbeitet den Quellcode und erzeugt Objektcode als Ausgabe. Beachten Sie, dass dieser Schritt nichts mit dem DBMS oder sql zu tun hat.  
  
4.  Der Linker akzeptiert die vom Compiler generierten Objektmodule, verknüpft sie mit verschiedenen Bibliotheksroutinen und erstellt ein ausführbares Programm. Zu den Bibliotheksroutinen, die mit dem ausführbaren Programm verknüpft sind, gehören die in Schritt 2 beschriebenen proprietären DBMS-Routinen.  
  
5.  Das vom Vorkompiler generierte Datenbankanforderungsmodul wird an ein spezielles Bindungsdienstprogramm gesendet. Dieses Dienstprogramm untersucht die SQL-Anweisungen, analysiert, validiert und optimiert sie und erstellt dann einen Zugriffsplan für jede Anweisung. Das Ergebnis ist ein kombinierter Zugriffsplan für das gesamte Programm, der eine ausführbare Version der eingebetteten SQL-Anweisungen darstellt. Das Bindungsdienstprogramm speichert den Plan in der Datenbank und weist ihm in der Regel den Namen des Anwendungsprogramms zu, das ihn verwenden wird. Ob dieser Schritt zur Kompilierungszeit oder Laufzeit erfolgt, hängt vom DBMS ab.  
  
 Beachten Sie, dass die Schritte zum Kompilieren eines eingebetteten SQL-Programms sehr eng mit den schritten korrelieren, die weiter oben in [Der Verarbeitung einer SQL-Anweisung](../../odbc/reference/processing-a-sql-statement.md)beschrieben wurden. Beachten Sie insbesondere, dass der Vorkompilierer die SQL-Anweisungen vom Hostsprachencode trennt und das Bindungsdienstprogramm die SQL-Anweisungen analysiert und überprüft und die Zugriffspläne erstellt. In DBMS, bei denen Schritt 5 zur Kompilierungszeit stattfindet, finden die ersten vier Schritte zur Verarbeitung einer SQL-Anweisung zur Kompilierungszeit statt, während der letzte Schritt (Ausführung) zur Laufzeit erfolgt. Dies hat den Effekt, dass Abfrageausführung in solchen DBMS sehr schnell.
