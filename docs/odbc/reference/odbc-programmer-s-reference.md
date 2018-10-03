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
ms.openlocfilehash: 7fc5177fda3562efe4561f9d165629419f8a629b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47850923"
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
  
-   Datenbanksprache – "SQL" mit der Integrität Verbesserung, ANSI, 1989 ANSI x 3.135-1989.  
  
-   Datenbanksprache – SQL: X3H2 mit ANSI und ISO/IEC JTC1/SC21/WG3 9075:1992 (SQL-92).  
  
-   Öffnen Sie die, die Datenverwaltung: Structured Query Language (SQL), Version 2 (die Open Group 1996).  
  
 Zusätzlich zu Standards und Handbücher für SQL-herstellerspezifisches, beschreiben viele Bücher SQL, einschließlich:  
  
-   Datum, J. c, mit Darwen, Hugh: *eine Anleitung für die SQL-Standard* (Addison-Wesley, 1993).  
  
-   Emerson, Stefan L., Darnovsky, Marcy und Bowman, Judith S.: *die praktische SQL Handbook* (Addison-Wesley, 1989).  
  
-   Groff, James r und Weinberg, Paul N.: *mithilfe von SQL* (Osborne McGraw-Hill, 1990).  
  
-   Gruber, Martin: *Grundlegendes zum SQL* (Sybex, 1990).  
  
-   Hursch, Jack L. und J. die Carolyn: *SQL, die strukturierte Abfragesprache* (Registerkarte Bücher, 1988).  
  
-   Melton, Jim und Simon "," Alan r: *Grundlegendes zu den neuen SQL: eine vollständige Anleitung* (Morgan Kaufmann Publishers, 1993).  
  
-   Pascal-Schreibweise, Fabian: *SQL und relationalen Grundlagen* (M & T Bücher, 1990).  
  
-   Trimble, J. Harvey, Jr. und Chappell, David: *eine visuelle Einführung in SQL* (Wiley, 1989).  
  
-   Van der Lans, Rick F.: *Einführung in SQL* (Addison-Wesley, 1988).  
  
-   Vang, Soren: *SQL und relationalen Datenbanken* (Microtrend Bücher, 1990).  
  
-   Viescas, John: *Kurzreferenz für SQL* (Microsoft Corporation, 1989).  
  
 Weitere Informationen zu Transaction processing, onlinetransaktionsverarbeitung finden Sie unter:  
  
-   Grau, J. n und Reuter, Andreas: *Transaction Processing: Concepts and Techniques* (Morgan Kaufmann Publishers, 1993).  
  
-   Hackathorn, Richard d: *Enterprise-Datenbankkonnektivität* (Wiley & Sons, 1993).  
  
 Weitere Informationen zur Call-Level-Schnittstellen sind die folgenden Standards verfügbar:  
  
-   Open Group *Datenverwaltung: SQL-Aufruf Ebene (Befehlszeilenschnittstelle), C451* (Open Group 1995).  
  
-   ISO/IEC 9075-3:1995, Call-Level-Interface (SQL/CLI).  
  
 Weitere Informationen zu ODBC sind eine Reihe von Büchern zur Verfügung, darunter:  
  
-   Geiger, Kyle: *in ODBC* (Microsoft Press®, 1995).  
  
-   Gryphon "," Robert "," Charpentier "," Luc "," Oelschlager "," Jon "," Shoemaker, Andrew, Cross, Jim, "und" Lilley, Albert W.: *mithilfe von ODBC 2* (Que, 1994).  
  
-   Johnston, Tom und Osborne, kennzeichnen: *ODBC-Developers Guide* (Howard W. Sams & Unternehmens, 1994).  
  
-   Nord, Ken: *Windows Multi-DBMS-Programmierung: mithilfe C++, Visual Basic, ODBC, OLE 2 und Tools für DBMS-Projekte* (Wiley John & Sons, Inc., 1995).  
  
-   Stegman, Michael O., Signore, Robert und Creamer, John: *der ODBC-Lösung, eine offene Datenbankverbindung in verteilten Umgebungen* (McGraw-Hill, 1995).  
  
-   Welch, Keith: *mithilfe von ODBC 2* (Que, 1994).  
  
-   Wittling, Bill: *Selbststudium ODBC in 21 Tage* (Howard W. Sams & Unternehmens, 1994).
