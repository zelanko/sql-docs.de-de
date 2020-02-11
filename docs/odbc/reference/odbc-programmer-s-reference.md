---
title: ODBC-Programmierer&#39;s-Referenz | Microsoft-Dokumentation
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
ms.openlocfilehash: fd729956ee7bb1fccf7a8fceb7a435042df4df7e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68111193"
---
# <a name="odbc-programmer39s-reference"></a>ODBC-Programmierer&#39;s-Referenz
Die *ODBC-Programmier Referenz* enthält die folgenden Abschnitte.  
  
-   [Neues in ODBC 3,8](../../odbc/reference/what-s-new-in-odbc-3-8.md) listet die neuen ODBC-Funktionen auf, die im Windows 8-SDK hinzugefügt wurden.  
  
-   Das [ODBC-Beispielprogramm](../../odbc/reference/sample-odbc-program.md) stellt ein ODBC-Beispielprogramm dar.  
  
-   Die [Einführung in ODBC](../../odbc/reference/introduction-to-odbc.md) bietet einen kurzen Überblick über strukturierte Abfragesprache und ODBC sowie konzeptionelle Informationen zur ODBC-Schnittstelle.  
  
-   Das [entwickeln von Anwendungen](../../odbc/reference/develop-app/developing-applications.md) enthält Informationen zum Entwickeln von Anwendungen, die die ODBC-Schnittstelle verwenden, und Treiber, die Sie implementieren.  
  
-   Die [Installation und Konfiguration von ODBC-Software](../../odbc/reference/install/installing-and-configuring-the-odbc-software.md) enthält Informationen zur Installation und eine DLL-Funktionsreferenz für Setup.  
  
-   [Die Entwicklung eines ODBC-Treibers](../../odbc/reference/develop-driver/developing-an-odbc-driver.md) enthält Informationen zum Schreiben eines Treibers.  
  
-   Die [API-Referenz](../../odbc/reference/syntax/odbc-reference.md) enthält Syntax-und Semantik Informationen für alle ODBC-Funktionen.  
  
-   [ODBC-Appendixes](../../odbc/reference/appendixes/odbc-appendixes.md) enthalten technische Details und Referenztabellen für ODBC-Fehlercodes,-Datentypen und SQL-Grammatik.  
  
## <a name="working-with-the-odbc-documentation"></a>Arbeiten mit der ODBC-Dokumentation  
 Die ODBC-Schnittstelle ist für die Verwendung mit der Programmiersprache C konzipiert. Die Verwendung der ODBC-Schnittstelle umfasst drei Bereiche: SQL-Anweisungen, ODBC-Funktionsaufrufe und C-Programmierung. In dieser Dokumentation wird Folgendes vorausgesetzt:  
  
-   Ein Funktions Wissen der Programmiersprache C.  
  
-   Allgemeines DBMS-wissen und eine Vertrautheit mit SQL.  
  
 Die folgenden typografischen Konventionen werden verwendet.  
  
|Format|Syntaxelemente|  
|------------|--------------|  
|Select * from|Großbuchstaben geben SQL-Anweisungen, Makronamen und Begriffe an, die auf der Betriebssystem-Befehls Ebene verwendet werden.|  
|`RETCODE SQLFetch(hdbc)`|Die Schriftart fest breiten wird für Beispiel Befehlszeilen und Programmcode verwendet.|  
|*gestritten*|Kursiv formatierte Wörter zeigen programmgesteuerte Argumente, Informationen an, die der Benutzer oder die Anwendung bereitstellen muss, oder die Wort Betonung.|  
|**SQLEndTran**|Der Typ "Bold" gibt an, dass die Syntax genau wie gezeigt eingegeben werden muss, einschließlich der Funktionsnamen.|  
|&#124;|Ein vertikaler Strich trennt zwei sich gegenseitig ausschließende Optionen in einer Syntax Zeile.|  
|...|Ein Ellipsen Wert gibt an, dass Argumente mehrmals wiederholt werden können.|  
|. . .|Eine Spalte mit drei Punkten gibt die Fortsetzung vorheriger Codezeilen an.|  
  
## <a name="about-the-code-examples"></a>Informationen zu den Code Beispielen  
 Die Codebeispiele in diesem Handbuch dienen nur zu Illustrations Zwecken. Da Sie in erster Linie für die Veranschaulichung von ODBC-Prinzipien geschrieben werden, wurde die Effizienz manchmal im Interesse der Klarheit eingestellt. Darüber hinaus wurden vollständige Code Abschnitte aus Gründen der Übersichtlichkeit ausgelassen. Hierzu gehören die Definitionen von nicht-ODBC-Funktionen (die Funktionen, deren Namen nicht mit "SQL" beginnen) und die meisten Fehlerbehandlung.  
  
 Alle Codebeispiele verwenden ANSI-Zeichen folgen und das gleiche Datenbankschema, das am Anfang der [Katalog Funktionen](../../odbc/reference/develop-app/catalog-functions.md)angezeigt wird.  
  
## <a name="recommended-reading"></a>Empfohlene Lektüre  
 Weitere Informationen zu SQL finden Sie in den folgenden Standards:  
  
-   Datenbanksprache-SQL mit Integritäts Erweiterung, ANSI, 1989 ANSI x 3.135-1989.  
  
-   Datenbanksprache-SQL: ANSI X3H2 und ISO/IEC JTC1/SC21/WG3 9075:1992 (SQL-92).  
  
-   Open Group, Datenverwaltung: strukturierte Abfragesprache (SQL), Version 2 (die geöffnete Gruppe, 1996).  
  
 Zusätzlich zu den Standard-und herstellerspezifischen SQL-Leitfäden beschreiben viele Bücher SQL, einschließlich:  
  
-   Date, C. J., with Darwen, Hugh: *ein Leitfaden zum SQL-Standard* (Addison-Wesley, 1993).  
  
-   Emerson, Sandra L., darnovsky, Marcy und Bowman, Judith S.: *das praktische SQL-Handbuch* (Addison-Wesley, 1989).  
  
-   Groff, James R. und Weinberg, Paul N.: *using SQL* (Osborne McGraw-Hill, 1990).  
  
-   Gruber, Martin: Grundlegendes zu *SQL* (Sybex, 1990).  
  
-   Hursch, Jack L. und Carolyn J.: *SQL, die strukturierte Abfragesprache* (Registerkarten Bücher, 1988).  
  
-   Melton, Jim und Simon, Alan R.: Grundlegendes *zum neuen SQL: A Complete Guide* (Morgan Kaufmann Publisher, 1993).  
  
-   Pascal, Fabian: *SQL und relationale Grundlagen* (M & T Books, 1990).  
  
-   Trimble, J. Harvey, Jr. und Chappell, David: *eine visuelle Einführung in SQL* (Wiley, 1989).  
  
-   Van der LANs, Rick F.: *Einführung in SQL* (Addison-Wesley, 1988).  
  
-   Vang, Soren: *SQL-und relationale Datenbanken* (mikrotrend-Bücher, 1990).  
  
-   Viescas, John: *Kurzübersicht zu SQL* (Microsoft Corp., 1989).  
  
 Weitere Informationen zur Transaktionsverarbeitung finden Sie unter:  
  
-   Grau, J. N. und Reuter, Andreas: *Transaktionsverarbeitung: Konzepte und Techniken* (Morgan Kaufmann Publisher, 1993).  
  
-   Hackathorn, Richard D.: *Enterprise Database Connectivity* (Wiley & Sons, 1993).  
  
 Weitere Informationen zu Schnittstellen auf Aufrufebene finden Sie in den folgenden Standards:  
  
-   Open Group, *Datenverwaltung: SQL-Befehlsebenen-Schnittstelle (CLI), C451* (Open Group, 1995).  
  
-   ISO/IEC 9075-3:1995, Schnittstelle auf Callcenter (SQL/CLI).  
  
 Weitere Informationen zu ODBC finden Sie unter den folgenden Themen:  
  
-   Geiger, Kyle: *innerhalb von ODBC* (Microsoft Press®, 1995).  
  
-   Gryphon, Robert, chartztier, Luc, Oelschlager, Jon, Shoemaker, Andrew, Cross, Jim und Lilley, Albert W.: *Using ODBC 2* (que, 1994).  
  
-   Johnston, Tom und Osborne, Mark: *ODBC-Entwicklerhandbuch* (Howard W. Sams & Company, 1994).  
  
-   Nord, Ken: *Windows Multi-DBMS Programming: Using C++, Visual Basic, ODBC, OLE 2 und Tools for DBMS projects* (John Wiley & Sons, Inc., 1995).  
  
-   Stegman, Michael O., Signore, Robert und Creamer, John: *die ODBC-Lösung, Open Database Connectivity in verteilten Umgebungen* (McGraw-Hill, 1995).  
  
-   Welch Keith: *Verwendung von ODBC 2* (que, 1994).  
  
-   Whiting, Rechnung: *vermitteln Sie ODBC in zwanzig Tagen* (Howard W. Sams & Company, 1994).
