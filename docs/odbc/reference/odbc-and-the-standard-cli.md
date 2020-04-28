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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 56dc0ac73c77cbbb77943d2e9ba308796b259dbb
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305141"
---
# <a name="odbc-and-the-standard-cli"></a>ODBC und die Standard-CLI
ODBC richtet sich an die folgenden Spezifikationen und Standards, die mit der CLI (calllevel Interface) zu tun haben. (Bei den ODBC-Funktionen handelt es sich um eine supermenge der einzelnen Standards.)  
  
-   Die Open Group-CAE-Spezifikation "Datenverwaltung: SQL-Befehlszeilenschnittstelle (CLI)"  
  
-   ISO/IEC 9075-3:1995 (E)-Schnittstelle (SQL/CLI)  
  
 Als Ergebnis dieser Ausrichtung sind folgende Aktionen zutreffend:  
  
-   Eine Anwendung, die in die Spezifikationen "Open Group" und "ISO CLI" geschrieben wird, funktioniert mit einem ODBC *3. x* -Treiber oder einem Standard kompatiblen Treiber, wenn dieser mit den ODBC *3. x* -Header Dateien kompiliert und mit ODBC *3* . x-Bibliotheken verknüpft ist und wenn er über den ODBC *3. x* -Treiber-Manager Zugriff auf den Treiber erhält.  
  
-   Ein Treiber, der in die Open Group-und ISO CLI-Spezifikationen geschrieben wird, funktioniert mit einer ODBC *3. x* -Anwendung oder einer Standard kompatiblen Anwendung, wenn diese mit den ODBC *3. x* -Header Dateien kompiliert und mit ODBC *3* . x-Bibliotheken verknüpft ist, und wenn die Anwendung über den ODBC *3. x* -Treiber-Manager Zugriff auf den Treiber erhält. (Weitere Informationen finden Sie unter [Standards-kompatible Anwendungen und Treiber](../../odbc/reference/develop-app/standards-compliant-applications-and-drivers.md).  
  
 Der Standardwert für die Schnittstellen Konformität umfasst alle Features in der ISO-CLI und alle nicht optionalen Features in der Open-Group-CLI. Optionale Features der Open Group-CLI werden in höheren Schnittstellen Übereinstimmungs Ebenen angezeigt. Da alle ODBC *3. x* -Treiber erforderlich sind, um die Funktionen in der Kern Schnittstellen Konformität zu unterstützen, gilt Folgendes:  
  
-   Ein ODBC *3. x* -Treiber unterstützt alle Funktionen, die von einer Standard kompatiblen Anwendung verwendet werden.  
  
-   Eine ODBC *3. x* -Anwendung, die nur die Features in der ISO-CLI und die nicht optionalen Features der Open Group-CLI verwendet, funktioniert mit jedem Standard kompatiblen Treiber.  
  
 Zusätzlich zu den in den ISO/IEC-und Open Group CLI-Standards enthaltenen Schnittstellen Spezifikationen auf der Telefon Ebene implementiert ODBC die folgenden Funktionen. (Einige dieser Features waren in Versionen von ODBC vor ODBC *3. x*vorhanden.)  
  
-   Mehr zeiliges Abrufen durch einen einzelnen Funktions Aufrufsatz  
  
-   Binden an ein Array von Parametern  
  
-   Lesezeichen Unterstützung einschließlich Abruf durch Lesezeichen, Lesezeichen mit variabler Länge und Massen Aktualisierung und Löschung durch Lesezeichen Vorgänge in nicht zusammenhängenden Zeilen  
  
-   Zeilen weises binden  
  
-   Bindungs Offsets  
  
-   Unterstützung für Batches von SQL-Anweisungen, entweder in einer gespeicherten Prozedur oder als Sequenz von SQL-Anweisungen, die über **SQLExecute** oder **SQLExecDirect** ausgeführt werden.  
  
-   Genaue oder ungefähre Cursor Zeilen Anzahl  
  
-   Positionierte UPDATE-und DELETE-Vorgänge und Updates und Löschungen im Batch Modus nach Funktionsaufrufen (**SQLSetPos**)  
  
-   Katalog Funktionen, die Informationen aus dem Informations Schema extrahieren, ohne Informations Schema Sichten unterstützen zu müssen  
  
-   Escapesequenzen für äußere Joins, skalare Funktionen, datetime-Literale, intervallliterale und gespeicherte Prozeduren  
  
-   Codepage-Übersetzungs Bibliotheken  
  
-   Berichterstellung für ANSI-Konformität und SQL-Unterstützung eines Treibers  
  
-   Bedarfs gesteuerte automatische Auffüllung des Implementierungs Parameter Deskriptors  
  
-   Erweiterte Diagnose-und Zeilen-und Parameter Status Arrays  
  
-   DateTime-, Interval-, numeric/Decimal-und 64-Bit-ganzzahlige Anwendungs Puffer Typen  
  
-   Asynchrone Ausführung  
  
-   Unterstützung für gespeicherte Prozeduren, einschließlich Escapesequenzen, Bindungs Mechanismen für Ausgabeparameter und Katalog Funktionen  
  
-   Verbindungs Erweiterungen einschließlich Unterstützung für Verbindungs Attribute und Durchsuchen von Attributen
