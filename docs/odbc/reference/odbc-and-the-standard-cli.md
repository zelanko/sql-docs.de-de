---
title: ODBC und die Standard-CLI | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC [ODBC], CLI
- CLI [ODBC]
- CLI [ODBC], about CLI
- call-level interface [ODBC]
- call-level interface [ODBC], about call-level interface
ms.assetid: 79b9c268-16ac-4b80-b451-f9dcd8c02ca4
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5222282bce2acf49cc6a144667ddd691528b3693
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67944846"
---
# <a name="odbc-and-the-standard-cli"></a>ODBC und die Standard-CLI
ODBC richtet mit den folgenden Spezifikationen und Standards, die mit der Call-Level-Interface (CLI) zu behandeln. (Die ODBC-Funktionen sind eine Obermenge aller dieser Standards.)  
  
-   Die Open Group CAE-Spezifikation "Datenverwaltung: SQL-Call-Level-Interface (CLI)"  
  
-   ISO/IEC 9075-3:1995 (E)-Call-Level-Interface (SQL/CLI)  
  
 Aufgrund dieser Ausrichtung gilt Folgendes:  
  
-   Eine Anwendung geschrieben, um die Open Group und ISO-CLI-Spezifikationen funktioniert mit einer ODBC- *3.x* Treiber oder eine Standards kompatible beim Kompilieren mit der ODBC-Treiber *3.x* Header-Dateien und verknüpft mit ODBC *3.x* Bibliotheken, und wenn sie den Zugriff auf den über die ODBC-Treiber erhält *3.x* -Treiber-Manager.  
  
-   Mit einer ODBC-Treiber geschrieben, um die Open Group und ISO-CLI-Spezifikationen funktioniert *3.x* Anwendung oder eine Standards kompatible Anwendung, wenn die Kompilierung mit der ODBC *3.x* Header-Dateien und verknüpft mit dem ODBC- *3.x* Bibliotheken, und wenn die Anwendung erhält Zugriff auf den über die ODBC-Treiber *3.x* -Treiber-Manager. (Weitere Informationen finden Sie unter [den Standards entsprechende Anwendungen und Treiber](../../odbc/reference/develop-app/standards-compliant-applications-and-drivers.md).  
  
 Der Konformitätsgrad des Core-Schnittstelle umfasst alle Features in der ISO-CLI und alle nonoptional Funktionen in der Open Group-CLI. Optionale Features der CLI öffnen Gruppe werden in höheren Ebenen der schnittstellenübereinstimmung Schnittstelle angezeigt. Da alle ODBC *3.x* Treiber sind erforderlich, um die Funktionen in der Konformitätsgrad des Core-Schnittstelle unterstützen, die folgende Bedingungen erfüllt sind:  
  
-   ODBC *3.x* Treiber unterstützt alle Funktionen, die von einer standardkonformen Anwendung verwendet.  
  
-   ODBC *3.x* -Anwendung mit nur die Funktionen in der ISO-CLI und die nonoptional Features der CLI Open Group funktioniert mit jeder standardkonformen Treiber.  
  
 Zusätzlich zu den Call-Level-Interface-Spezifikationen enthalten, die in den ISO/IEC und Open Group-CLI-Standards implementiert ODBC die folgenden Features. (Einige dieser Features war in Versionen von ODBC, bevor Sie ODBC *3.x*.)  
  
-   Mehrzeilige Abrufvorgänge durch einen einzelnen Funktionsaufruf  
  
-   Binden an ein Array von Parametern  
  
-   Lesezeichenunterstützung einschließlich Abrufen nach Lesezeichen, variabler Länge, Lesezeichen und Bulk aktualisieren und Löschen von Lesezeichen-Vorgänge für nicht zusammenhängende Zeilen  
  
-   Zeilenweises binden  
  
-   Binden von offsets  
  
-   Unterstützung für Batches von SQL-Anweisungen, die entweder in einer gespeicherten Prozedur oder als eine Folge von SQL-Anweisungen ausgeführt, die über **SQLExecute** oder **SQLExecDirect**  
  
-   Cursor für genaue oder Ungefähre Zeilenanzahl  
  
-   Update und Delete-Vorgänge im Batchmodus Updates und löschungen durch Funktionsaufruf positioniert (**SQLSetPos**)  
  
-   Katalogfunktionen, die Informationen aus dem Informationsschema ohne die Notwendigkeit zur Unterstützung von Informationsschemasichten extrahieren  
  
-   Escapesequenzen für äußere Joins, Skalarfunktionen, Datetime-Literale, Intervall-Literale und gespeicherten Prozeduren  
  
-   Codepage-Übersetzung Bibliotheken  
  
-   Berichterstellung von ANSI-Konformitätsgrad und SQL-Unterstützung des Treibers  
  
-   Bei Bedarf automatische Auffüllung des IPD  
  
-   Erweiterte Diagnose und die Zeilen- und Parameter-Status-arrays  
  
-   "DateTime", Intervall, numerische/Decimal- und 64-Bit-Ganzzahl-Puffer Anwendungstypen  
  
-   Asynchrone Ausführung  
  
-   Unterstützung für gespeicherte Prozeduren,-Escapesequenzen, einschließlich Ausgabe Parameterbindungsmechanismen und Katalogfunktionen  
  
-   Verbindungs-Erweiterungen, einschließlich der Unterstützung für-Verbindungsattributen und das Attribut durchsuchen
