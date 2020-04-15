---
title: Was ist ODBC? | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC [ODBC], about ODBC
ms.assetid: badf3a45-f941-44ae-a31d-393116f68a18
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ea0aa81188e5e58d3a66032af38700ece2d4e5b4
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81286500"
---
# <a name="what-is-odbc"></a>Was ist ODBC?
Viele Missverständnisse über ODBC gibt es in der Computerwelt. Für den Endbenutzer ist es ein Symbol in der Microsoft® Windows® Systemsteuerung. Für den Anwendungsprogrammierer ist es eine Bibliothek, die Datenzugriffsroutinen enthält. Für viele andere ist es die Antwort auf alle Datenbankzugriffsprobleme, die man sich jemals vorgestellt hat.  
  
 In erster Linie ist ODBC eine Spezifikation für eine Datenbank-API. Diese API ist unabhängig von einem DBMS oder Betriebssystem. Obwohl in diesem Handbuch C verwendet wird, ist die ODBC-API sprachunabhängig. Die ODBC-API basiert auf den CLI-Spezifikationen von Open Group und ISO/IEC. ODBC 3. *x* implementiert beide Spezifikationen vollständig - frühere Versionen von ODBC basierten auf vorläufigen Versionen dieser Spezifikationen, implementierten sie aber nicht vollständig - und fügt Funktionen hinzu, die häufig von Entwicklern von bildschirmbasierten Datenbankanwendungen benötigt werden, wie z. B. scrollbare Cursor.  
  
 Die Funktionen in der ODBC-API werden von Entwicklern von DBMS-spezifischen Treibern implementiert. Anwendungen rufen die Funktionen in diesen Treibern auf, um DBMS-unabhängig auf Daten zuzugreifen. Ein Treiber-Manager verwaltet die Kommunikation zwischen Anwendungen und Treibern.  
  
 Obwohl Microsoft einen Treiber-Manager für Computer mit Microsoft Windows® 95 und höher bereitstellt, mehrere ODBC-Treiber geschrieben hat und ODBC-Funktionen aus einigen seiner Anwendungen aufruft, kann jeder ODBC-Anwendungen und -Treiber schreiben. Tatsächlich wird die überwiegende Mehrheit der heute verfügbaren ODBC-Anwendungen und -Treiber von anderen Unternehmen als Microsoft geschrieben. Darüber hinaus gibt es ODBC-Treiber und -Anwendungen auf dem Macintosh® und einer Vielzahl von UNIX-Plattformen.  
  
 Um Anwendungs- und Treiberentwicklern zu helfen, bietet Microsoft ein ODBC Software Development Kit (SDK) für Computer mit Windows 95 und höher an, das den Treiber-Manager, die Installations-DLL, Testtools und Beispielanwendungen bereitstellt. Microsoft hat sich mit Visigenic Software zusammengetan, um diese SDKs auf dem Macintosh und einer Vielzahl von UNIX-Plattformen zu portieren.  
  
 Es ist wichtig zu verstehen, dass ODBC entwickelt wurde, um Datenbankfunktionen verfügbar zu machen, nicht sie zu ergänzen. Daher sollten Anwendungsautoren nicht erwarten, dass die Verwendung von ODBC plötzlich eine einfache Datenbank in eine voll funktionsfähige relationale Datenbank-Engine umwandelt. Es wird auch nicht erwartet, dass Treiberautoren Funktionen implementieren, die in der zugrunde liegenden Datenbank nicht gefunden werden. Eine Ausnahme bildet die Möglichkeit, dass Entwickler, die Treiber schreiben, die direkt auf Dateidaten zugreifen (z. B. Daten in einer Xbase-Datei), ein Datenbankmodul schreiben müssen, das mindestens minimale SQL-Funktionen unterstützt. Eine weitere Ausnahme ist, dass die ODBC-Komponente des Windows SDK, die zuvor im Microsoft Data Access Components (MDAC)-SDK enthalten war, eine Cursorbibliothek bereitstellt, die scrollbare Cursor für Treiber simuliert, die eine bestimmte Funktionalität implementieren.  
  
 Anwendungen, die ODBC verwenden, sind für alle datenbankübergreifenden Funktionen verantwortlich. BEISPIELSWEISE ist ODBC weder ein heterogenes Join-Modul noch ein verteilter Transaktionsprozessor. Da es jedoch DBMS-unabhängig ist, kann es verwendet werden, um solche datenbankübergreifenden Tools zu erstellen.
