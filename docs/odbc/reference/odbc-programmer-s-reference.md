---
title: ODBC Programmierer&#39;s Referenz | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6a9ca32627b9703465dcfca554fdc32ae01442e7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81280510"
---
# <a name="odbc-programmer39s-reference"></a>ODBC Programmer&#39;s Referenz
Die *Referenz des ODBC-Programmierers* enthält die folgenden Abschnitte.  
  
-   [Was ist neu in ODBC 3.8](../../odbc/reference/what-s-new-in-odbc-3-8.md) listet die neuen ODBC-Funktionen, die in der Windows 8 SDK hinzugefügt wurden.  
  
-   [Beispiel ODBC-Programm](../../odbc/reference/sample-odbc-program.md) präsentiert ein Beispiel ODBC-Programm.  
  
-   [Die Einführung in ODBC](../../odbc/reference/introduction-to-odbc.md) enthält eine kurze Historie von Structured Query Language und ODBC sowie konzeptionelle Informationen zur ODBC-Schnittstelle.  
  
-   [Das Entwickeln von Anwendungen](../../odbc/reference/develop-app/developing-applications.md) enthält Informationen zum Entwickeln von Anwendungen, die die ODBC-Schnittstelle verwenden, und Treiber, die sie implementieren.  
  
-   [Die Installation und Konfiguration der ODBC-Software](../../odbc/reference/install/installing-and-configuring-the-odbc-software.md) enthält Informationen zur Installation und eine DLL-Funktionsreferenz für setup.  
  
-   [Die Entwicklung eines ODBC-Treibers](../../odbc/reference/develop-driver/developing-an-odbc-driver.md) enthält Informationen zum Schreiben eines Treibers.  
  
-   [API Reference](../../odbc/reference/syntax/odbc-reference.md) enthält Syntax- und semantische Informationen für alle ODBC-Funktionen.  
  
-   [ODBC-Anhänge](../../odbc/reference/appendixes/odbc-appendixes.md) enthalten technische Details und Referenztabellen für ODBC-Fehlercodes, Datentypen und SQL-Grammatik.  
  
## <a name="working-with-the-odbc-documentation"></a>Arbeiten mit der ODBC-Dokumentation  
 Die ODBC-Schnittstelle dient zur Verwendung mit der Programmiersprache C. Die Verwendung der ODBC-Schnittstelle umfasst drei Bereiche: SQL-Anweisungen, ODBC-Funktionsaufrufe und C-Programmierung. In dieser Dokumentation wird Folgendes vorausgesetzt:  
  
-   Kenntnisse der Programmiersprache C.  
  
-   Allgemeines DBMS-Wissen und vertraut mit SQL.  
  
 Die folgenden typografischen Konventionen werden verwendet.  
  
|Format|Syntaxelemente|  
|------------|--------------|  
|WÄHLEN * VON|Großbuchstaben geben SQL-Anweisungen, Makronamen und Begriffe an, die auf Befehlsebene des Betriebssystems verwendet werden.|  
|`RETCODE SQLFetch(hdbc)`|Die Monospace-Schriftart wird für Beispielbefehlszeilen und Programmcode verwendet.|  
|*Argument*|Kursive Wörter geben programmgesteuerte Argumente, Informationen an, die der Benutzer oder die Anwendung bereitstellen muss, oder Wortbetonung.|  
|**SQLEndTran**|Der Fetttyp gibt an, dass die Syntax genau wie gezeigt eingegeben werden muss, einschließlich Funktionsnamen.|  
|&#124;|Ein vertikaler Balken trennt zwei sich gegenseitig ausschließende Optionen in einer Syntaxzeile.|  
|...|Eine Auslassungspunkte gibt an, dass Argumente mehrmals wiederholt werden können.|  
|. . .|Eine Spalte mit drei Punkten zeigt die Fortsetzung der vorherigen Codezeilen an.|  
  
## <a name="about-the-code-examples"></a>Informationen zu den Codebeispielen  
 Die Codebeispiele in diesem Handbuch dienen nur zur Veranschaulichung. Da sie in erster Linie geschrieben wurden, um ODBC-Prinzipien zu demonstrieren, wurde Effizienz manchmal im Interesse der Klarheit beiseite geschoben. Darüber hinaus wurden manchmal ganze Codeabschnitte aus Gründen der Übersichtlichkeit weggelassen. Dazu gehören die Definitionen von Nicht-ODBC-Funktionen (die Funktionen, deren Namen nicht mit "SQL" beginnen) und die meisten Fehlerbehandlungen.  
  
 Alle Codebeispiele verwenden ANSI-Zeichenfolgen und dasselbe Datenbankschema, das am Anfang von [Catalog Functions](../../odbc/reference/develop-app/catalog-functions.md)angezeigt wird.  
  
## <a name="recommended-reading"></a>Empfohlene Lektüre  
 Weitere Informationen zu SQL finden Sie unter folgenden Standards:  
  
-   Datenbanksprache - SQL mit Integritätsverbesserung, ANSI, 1989 ANSI X3.135-1989.  
  
-   Datenbanksprache - SQL: ANSI X3H2 und ISO/IEC JTC1/SC21/WG3 9075:1992 (SQL-92).  
  
-   Open Group, Data Management: Structured Query Language (SQL), Version 2 (The Open Group, 1996).  
  
 Neben Standards und herstellerspezifischen SQL-Leitfäden beschreiben viele Bücher SQL, einschließlich:  
  
-   Date, C. J., mit Darwen, Hugh: *A Guide to the SQL Standard* (Addison-Wesley, 1993).  
  
-   Emerson, Sandra L., Darnovsky, Marcy, and Bowman, Judith S.: *The Practical SQL Handbook* (Addison-Wesley, 1989).  
  
-   Groff, James R. and Weinberg, Paul N.: *Using SQL* (Osborne McGraw-Hill, 1990).  
  
-   Martin Gruber: *Understanding SQL* (Sybex, 1990).  
  
-   Jack L. Hursch und Carolyn J.: *SQL, The Structured Query Language* (TAB Books, 1988).  
  
-   Alan R: *Understanding the New SQL: A Complete Guide* (Morgan Kaufmann Publishers, 1993).  
  
-   Pascal, Fabian: *SQL and Relational Basics* (M & T Books, 1990).  
  
-   Trimble, J. Harvey, Jr. und Chappell, David: *A Visual Introduction to SQL* (Wiley, 1989).  
  
-   Rick F. Van der Lans: *Introduction to SQL* (Addison-Wesley, 1988).  
  
-   Vang, Soren: *SQL and Relational Databases* (Microtrend Books, 1990).  
  
-   John: *Quick Reference Guide to SQL:* Viescas:  
  
 Weitere Informationen zur Transaktionsverarbeitung finden Sie unter:  
  
-   Gray, J. N. und Reuter, Andreas: *Transaction Processing: Concepts and Techniques* (Morgan Kaufmann Publishers, 1993).  
  
-   Richard D. Hackathorn: *Enterprise Database Connectivity* (Wiley & Sons, 1993).  
  
 Weitere Informationen zu Call-Level-Schnittstellen finden Sie unter folgenden Standards:  
  
-   Open Group, *Data Management: SQL Call Level Interface (CLI), C451* (Open Group, 1995).  
  
-   ISO/IEC 9075-3:1995, Schnittstelle auf Aufrufebene (SQL/CLI).  
  
 Für weitere Informationen über ODBC stehen eine Reihe von Büchern zur Verfügung, darunter:  
  
-   Kyle Geiger: *Inside ODBC* (Microsoft Press®, 1995).  
  
-   Gryphon, Robert, Charpentier, Luc, Oelschlager, Jon, Shoemaker, Andrew, Cross, Jim, and Lilley, Albert W.: *Using ODBC 2* (Que, 1994).  
  
-   Tom and Osborne Johnston, Mark: *ODBC Developers Guide* (Howard W. Sams & Company, 1994).  
  
-   North, Ken: *Windows Multi-DBMS Programming: Using C++, Visual Basic, ODBC, OLE 2 and Tools for DBMS Projects* (John Wiley & Sons, Inc., 1995).  
  
-   Stegman, Michael O., Signore, Robert, and Creamer, John: *The ODBC Solution, Open Database Connectivity in Distributed Environments* (McGraw-Hill, 1995).  
  
-   Keith Welch: *Using ODBC 2* (Que, 1994).  
  
-   Whiting, Bill: *Teach Yourself ODBC in Twenty-One Days* (Howard W. Sams & Company, 1994).
