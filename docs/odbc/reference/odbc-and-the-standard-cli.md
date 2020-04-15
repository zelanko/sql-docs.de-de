---
title: ODBC und die Standard-CLI | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 56dc0ac73c77cbbb77943d2e9ba308796b259dbb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305141"
---
# <a name="odbc-and-the-standard-cli"></a>ODBC und die Standard-CLI
ODBC richtet sich nach den folgenden Spezifikationen und Standards, die sich mit der Call-Level Interface (CLI) befassen. (Die ODBC-Funktionen sind eine Obermenge jedes dieser Standards.)  
  
-   Die Open Group CAE-Spezifikation "Data Management: SQL Call-Level Interface (CLI)"  
  
-   ISO/IEC 9075-3:1995 (E) Call-Level-Schnittstelle (SQL/CLI)  
  
 Als Ergebnis dieser Ausrichtung sind die folgenden Punkte zutreffend:  
  
-   Eine Anwendung, die in die Open Group- und ISO CLI-Spezifikationen geschrieben wurde, funktioniert mit einem ODBC *3.x-Treiber* oder einem standardkonformen Treiber, wenn sie mit den ODBC *3.x-Headerdateien* kompiliert und mit ODBC *3.x-Bibliotheken* verknüpft wird und wenn sie über den ODBC *3.x-Treiber-Manager* Zugriff auf den Treiber erhält.  
  
-   Ein Treiber, der in die Open Group- und ISO CLI-Spezifikationen geschrieben wurde, funktioniert mit einer ODBC *3.x-Anwendung* oder einer standardkonformen Anwendung, wenn er mit den ODBC *3.x-Headerdateien* kompiliert und mit ODBC *3.x-Bibliotheken* verknüpft wird und wenn die Anwendung über den ODBC *3.x-Treiber-Manager* Zugriff auf den Treiber erhält. (Weitere Informationen finden Sie unter [Standardkonforme Anwendungen und Treiber](../../odbc/reference/develop-app/standards-compliant-applications-and-drivers.md).  
  
 Die Core-Schnittstellenkonformitätsstufe umfasst alle Funktionen in der ISO CLI und alle nicht optionalen Features in der Open Group CLI. Optionale Funktionen der Open Group CLI werden in höheren Schnittstellenkonformitätsstufen angezeigt. Da alle ODBC *3.x-Treiber* erforderlich sind, um die Features in der Core-Schnittstellenkonformitätsebene zu unterstützen, sind die folgenden Punkte zutreffend:  
  
-   Ein ODBC *3.x-Treiber* unterstützt alle Funktionen, die von einer standardkonformen Anwendung verwendet werden.  
  
-   Eine ODBC *3.x-Anwendung,* die nur die Funktionen in der ISO CLI und die nicht optionalen Funktionen der Open Group CLI verwendet, funktioniert mit jedem standardkonformen Treiber.  
  
 Zusätzlich zu den Schnittstellenspezifikationen auf Aufrufebene, die in den CLI-Standards ISO/IEC und Open Group enthalten sind, implementiert ODBC die folgenden Funktionen. (Einige dieser Funktionen existierten in Versionen von ODBC vor ODBC *3.x*.)  
  
-   Multirow-Abrufe durch einen einzelnen Funktionsaufruf  
  
-   Bindung an ein Array von Parametern  
  
-   Lesezeichenunterstützung, einschließlich Abrufen nach Lesezeichen, Lesezeichen variabler Länge und Massenaktualisierung und Löschung nach Lesezeichenoperationen in disontierenden Zeilen  
  
-   Row-wise-Bindung  
  
-   Bindungsversätze  
  
-   Unterstützung für Batches von SQL-Anweisungen, entweder in einer gespeicherten Prozedur oder als eine Sequenz von SQL-Anweisungen, die über **SQLExecute** oder **SQLExecDirect** ausgeführt werden  
  
-   Genaue oder ungefähre Cursorzeilenanzahl  
  
-   Positionierte Aktualisierungs- und Löschvorgänge sowie Batch-Aktualisierungen und -Löschvorgänge nach Funktionsaufruf (**SQLSetPos**)  
  
-   Katalogfunktionen, die Informationen aus dem Informationsschema extrahieren, ohne dass Informationen schemaansichten unterstützt werden müssen  
  
-   Escape-Sequenzen für äußere Verknüpfungen, Skalarfunktionen, Datetime-Literale, Intervallliterale und gespeicherte Prozeduren  
  
-   Codepage-Übersetzungsbibliotheken  
  
-   Melden der ANSI-Konformitätsstufe und sql-Unterstützung eines Treibers  
  
-   Automatische Aufanforderung der Implementierungsparameterdeskriptor  
  
-   Erweiterte Diagnose- und Zeilen- und Parameterstatus-Arrays  
  
-   Datetime-, Intervall-, Numerisch-/Dezimal- und 64-Bit-Ganzzahl-Anwendungspuffertypen  
  
-   Asynchrone Ausführung  
  
-   Unterstützung gespeicherter Prozeduren, einschließlich Escapesequenzen, Ausgabeparameterbindungsmechanismen und Katalogfunktionen  
  
-   Verbindungsverbesserungen, einschließlich Unterstützung für Verbindungsattribute und Attributsuche
