---
title: ODBC-Programmierer&#39;s Verweis | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC [ODBC], reference
ms.assetid: b33c3c43-ae66-44a3-be17-9cd82624dd96
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c83a7de609d200da2957a65b9325d031eda49780
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63273040"
---
# <a name="odbc-programmer39s-reference"></a>ODBC-Programmierer&#39;s-Referenz
Die *ODBC Programmer's Reference* enthält die folgenden Abschnitte.  
  
-   [Neuigkeiten in ODBC 3.8](../../odbc/reference/what-s-new-in-odbc-3-8.md) werden die neuen ODBC-Features, die in Windows 8 SDK hinzugefügt wurden.  
  
-   [ODBC-Beispielprogramm](../../odbc/reference/sample-odbc-program.md) enthält ein ODBC-Beispielprogramm.  
  
-   [Einführung in ODBC](../../odbc/reference/introduction-to-odbc.md) bietet eine kurze Geschichte Structured Query Language und ODBC sowie grundlegende Informationen über die ODBC-Schnittstelle.  
  
-   [Entwickeln von Anwendungen](../../odbc/reference/develop-app/developing-applications.md) enthält Informationen zum Entwickeln von Anwendungen, die die ODBC-Schnittstelle und Treiber, die ihn implementieren.  
  
-   [Installieren und Konfigurieren von ODBC-Software](../../odbc/reference/install/installing-and-configuring-the-odbc-software.md) enthält Informationen zu Installation und ein Setup-DLL-Funktionsreferenz.  
  
-   [Entwickeln einen ODBC-Treiber](../../odbc/reference/develop-driver/developing-an-odbc-driver.md) enthält Informationen zum Schreiben von einem Treiber.  
  
-   [API-Referenz](../../odbc/reference/syntax/odbc-reference.md) enthält Syntax und die semantischen Informationen für alle ODBC-Funktionen.  
  
-   [ODBC-Anhänge](../../odbc/reference/appendixes/odbc-appendixes.md) enthalten technische Details und verweisen auf Tabellen für ODBC-Fehlercodes, Datentypen und SQL-Grammatik.  
  
## <a name="working-with-the-odbc-documentation"></a>Arbeiten mit der ODBC-Dokumentation  
 Die ODBC-Schnittstelle dient zur Verwendung mit der Programmiersprache C. Verwenden der ODBC-Schnittstelle umfasst drei Bereiche: SQL-Anweisungen, ODBC-Funktionsaufrufe und C-Programmierung. In dieser Dokumentation wird Folgendes vorausgesetzt:  
  
-   Kenntnisse der Programmiersprache C.  
  
-   Allgemeine DBMS-Kenntnisse und Vertrautheit mit SQL.  
  
 Die folgenden typografischen Konventionen dienen.  
  
|Format|Syntaxelemente|  
|------------|--------------|  
|WÄHLEN SIE * AUS|Großbuchstaben geben SQL-Anweisungen, Makronamen und Begriffe, die auf der Ebene Betriebssystembefehl verwendet.|  
|`RETCODE SQLFetch(hdbc)`|Die Festbreitenschriftart dient für Beispielbefehlszeilen und Programmcode.|  
|*argument*|Kursiv Wörter zeigen die programmgesteuerte Argumente, von dem Benutzer oder die Anwendung muss, oder word Betonung an.|  
|**SQLEndTran**|Fett bedeutet, dass die Syntax genau wie dargestellt, einschließlich Funktionsnamen, eingegeben werden muss.|  
|&#124;|Eine vertikale Leiste trennt zwei sich gegenseitig ausschließende Optionen in einer Syntaxzeile.|  
|...|Ein Auslassungszeichen weisen darauf hin, dass Argumente mehrmals wiederholt werden können.|  
|. . .|Eine Spalte mit den drei Punkten gibt die Fortsetzung des vorherigen Codezeilen an.|  
  
## <a name="about-the-code-examples"></a>Informationen zu den Codebeispielen  
 Die Codebeispiele in diesem Handbuch dienen lediglich zur Veranschaulichung. Da sie, in erster Linie zum ODBC-Prinzipien veranschaulichen geschrieben werden, wurde Effizienz manchmal reserviert aus Gründen der Übersichtlichkeit festgelegt. Darüber hinaus wurden ganze Bereiche des Codes in einigen Fällen aus Gründen der Übersichtlichkeit ausgelassen. Dazu gehören die Definitionen von nicht-ODBC-Funktionen (diese Funktionen, deren Namen nicht mit "SQL" beginnen) und die meisten Fehlerbehandlung.  
  
 Alle Codebeispiele zu verwenden, ANSI-Zeichenfolgen und das gleiche Datenbankschema, die am Anfang angezeigt wird [Katalogfunktionen](../../odbc/reference/develop-app/catalog-functions.md).  
  
## <a name="recommended-reading"></a>Empfohlene Lektüre  
 Weitere Informationen zu SQL stehen die folgenden Standards:  
  
-   Language - SQL mit Integrität Verbesserung, ANSI, 1989 ANSI x 3.135-1989-Datenbank.  
  
-   Language - SQL-Datenbank: X3H2 mit ANSI und ISO/IEC JTC1/SC21/WG3 9075:1992 (SQL-92).  
  
-   Öffnen Sie die, die Datenverwaltung: Strukturierte Abfragesprache (SQL), Version 2 (die Open Group 1996).  
  
 Zusätzlich zu Standards und Handbücher für SQL-herstellerspezifisches, beschreiben viele Bücher SQL, einschließlich:  
  
-   Datum, J. c, mit Darwen, Hugh: *Eine Anleitung für die SQL-Standard* (Addison-Wesley, 1993).  
  
-   Emerson, Stefan L., Darnovsky, Marcy und Bowman, Judith S.: *The Practical SQL Handbook* (Addison-Wesley, 1989).  
  
-   Groff, James r und Weinberg, Paul N.: *Mithilfe von SQL* (Osborne McGraw-Hill, 1990).  
  
-   Gruber, Martin: *Grundlegendes zum SQL* (Sybex, 1990).  
  
-   Hursch, Jack L. and Carolyn J.: *SQL, die strukturierte Abfragesprache* (Registerkarte Bücher, 1988).  
  
-   Melton "," Jim "und" Simon "," Alan r ": *Grundlegendes zu neuen: Eine vollständige Anleitung* (Morgan Kaufmann Publishers, 1993).  
  
-   Pascal-Schreibweise, Fabian: *SQL und relationalen Grundlagen* (M & T Bücher, 1990).  
  
-   Trimble, J. Harvey, Jr. und Chappell, David: *Eine visuelle Einführung in SQL* (Wiley, 1989).  
  
-   Van der Lans, Rick F.: *Einführung in SQL* (Addison-Wesley, 1988).  
  
-   Vang, Soren: *SQL und relationalen Datenbanken* (Microtrend Bücher, 1990).  
  
-   Viescas, John: *Kurzübersicht zu SQL* (Microsoft Corporation, 1989).  
  
 Weitere Informationen zu Transaction processing, onlinetransaktionsverarbeitung finden Sie unter:  
  
-   Grau, J. n und Reuter, Andreas: *Verarbeitung von Transaktionen: Konzepte und Techniken* (Morgan Kaufmann Publishers, 1993).  
  
-   Hackathorn, Richard d: *Enterprise-Datenbankkonnektivität* (Wiley & Sons, 1993).  
  
 Weitere Informationen zur Call-Level-Schnittstellen sind die folgenden Standards verfügbar:  
  
-   Open Group *Datenverwaltung: SQL-Aufruf Ebene (Befehlszeilenschnittstelle), C451* (Open Group 1995).  
  
-   ISO/IEC 9075-3:1995, Call-Level-Interface (SQL/CLI).  
  
 Weitere Informationen zu ODBC sind eine Reihe von Büchern zur Verfügung, darunter:  
  
-   Geiger, Kyle: *Inside ODBC* (Microsoft Press®, 1995).  
  
-   Gryphon "," Robert "," Charpentier "," Luc "," Oelschlager "," Jon "," Shoemaker, Andrew, Cross, Jim, "und" Lilley, Albert W.: *Mithilfe von ODBC 2* (Que, 1994).  
  
-   Johnston, Tom und Osborne, zu markieren: *ODBC Developers Guide* (Howard W. Sams & Company, 1994).  
  
-   Nord, Ken: *Windows-Multi-DBMS-Programmierung: Using C++, Visual Basic, ODBC, OLE 2 and Tools for DBMS Projects* (John Wiley & Sons, Inc., 1995).  
  
-   Stegman, Michael O., Signore, Robert, and Creamer, John: *Der ODBC-Lösung, eine offene Datenbankverbindung in verteilten Umgebungen* (McGraw-Hill, 1995).  
  
-   Welch, Keith: *Mithilfe von ODBC 2* (Que, 1994).  
  
-   Wittling, Rechnung: *Bringen Sie sich selbst ODBC in 21 Tage* (Howard W. Sams & Unternehmens, 1994).
