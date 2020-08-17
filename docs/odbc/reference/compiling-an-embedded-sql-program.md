---
description: Kompilieren eines eingebetteten SQL-Programms
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5065d50bd9ae23cc7db8a2310b13792b461da2a5
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88386076"
---
# <a name="compiling-an-embedded-sql-program"></a>Kompilieren eines eingebetteten SQL-Programms
Da ein eingebettetes SQL-Programm eine Mischung aus SQL-und Host Sprachanweisungen enthält, kann es nicht direkt an einen Compiler für die Host Sprache übermittelt werden. Stattdessen wird Sie durch einen Prozess mit mehreren Schritten kompiliert. Obwohl sich dieser Prozess von Produkt zu Produkt unterscheidet, sind die Schritte für alle Produkte ungefähr identisch.  
  
 Diese Abbildung zeigt die Schritte, die zum Kompilieren eines eingebetteten SQL-Programms erforderlich sind.  
  
 ![Schritte zum Kompilieren eines eingebetteten SQL-Programms](../../odbc/reference/media/pr02.gif "pr02")  
  
 Zum Kompilieren eines eingebetteten SQL-Programms sind fünf Schritte erforderlich:  
  
1.  Das eingebettete SQL-Programm wird an den SQL-präcompiler, ein Programmier Tool, übermittelt. Der Vorcompiler scannt das Programm, sucht die eingebetteten SQL-Anweisungen und verarbeitet sie. Ein anderer vorkompilierten ist für jede vom DBMS unterstützte Programmiersprache erforderlich. DBMS-Produkte bieten in der Regel präcompiler für eine oder mehrere Sprachen, u.a. C, Pascal, COBOL, Fortran, Ada, PL/I und verschiedene Assemblysprachen.  
  
2.  Der vorkompilierten erzeugt zwei Ausgabedateien. Die erste Datei ist die Quelldatei, die von den eingebetteten SQL-Anweisungen entfernt wurde. An dieser Stelle ersetzt der vorkompilierten Aufrufe an proprietäre DBMS-Routinen, die den Lauf Zeit Link zwischen dem Programm und dem DBMS bereitstellen. In der Regel sind die Namen und die Aufruf Sequenzen dieser Routinen nur dem vorkompilierten und dem DBMS bekannt. Sie sind keine öffentliche Schnittstelle für das DBMS. Die zweite Datei ist eine Kopie aller eingebetteten SQL-Anweisungen, die im Programm verwendet werden. Diese Datei wird manchmal als Daten Bank Anforderungs Modul oder DBRM bezeichnet.  
  
3.  Die Quelldatei Ausgabe des precompilers wird an den Standard Compiler für die Host Programmiersprache (z. b. einen C-oder COBOL-Compiler) übermittelt. Der Compiler verarbeitet den Quellcode und erzeugt den Objektcode als Ausgabe. Beachten Sie, dass dieser Schritt nichts mit dem DBMS oder mit SQL zu tun hat.  
  
4.  Der Linker akzeptiert die vom Compiler generierten Objekt Module, verknüpft Sie mit verschiedenen Bibliotheks Routinen und erstellt ein ausführbares Programm. Die mit dem ausführbaren Programm verknüpften Bibliotheks Routinen enthalten die proprietären DBMS-Routinen, die in Schritt 2 beschrieben werden.  
  
5.  Das vom vorkompilierten generierte Daten Bank Anforderungs Modul wird an ein spezielles Bindungs Dienstprogramm übermittelt. Dieses Hilfsprogramm untersucht die SQL-Anweisungen, analysiert, validiert und optimiert Sie und erstellt dann einen Zugriffs Plan für jede Anweisung. Das Ergebnis ist ein kombinierter Zugriffs Plan für das gesamte Programm, das eine ausführbare Version der eingebetteten SQL-Anweisungen darstellt. Das Bindungs Hilfsprogramm speichert den Plan in der Datenbank und weist in der Regel den Namen des Anwendungsprogramms zu, von dem es verwendet wird. Ob dieser Schritt zur Kompilierzeit oder zur Laufzeit stattfindet, hängt vom DBMS ab.  
  
 Beachten Sie, dass die Schritte, die zum Kompilieren eines eingebetteten SQL-Programms verwendet werden, sehr eng mit den zuvor in [Verarbeiten einer SQL-Anweisung](../../odbc/reference/processing-a-sql-statement.md)beschriebenen Schritten korrelieren. Beachten Sie insbesondere, dass der vorkompilierten die SQL-Anweisungen vom Host Sprachcode trennt und das Bindungs Programm die SQL-Anweisungen analysiert und überprüft und die Zugriffs Pläne erstellt. In DBMSs, in dem Schritt 5 zur Kompilierzeit stattfindet, werden die ersten vier Schritte zum Verarbeiten einer SQL-Anweisung zur Kompilierzeit stattfinden, während der letzte Schritt (Ausführung) zur Laufzeit stattfindet. Dies hat den Effekt, dass die Abfrage Ausführung in derartigen DBMSs sehr schnell ist.
