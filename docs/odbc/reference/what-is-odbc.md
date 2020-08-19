---
description: Was ist ODBC?
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
ms.openlocfilehash: 23badedad64ac836f07e3d9f7832fcfa6c33b0b9
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88428822"
---
# <a name="what-is-odbc"></a>Was ist ODBC?
Viele fehl Stimmungen zu ODBC sind in der Computing-Welt vorhanden. Für den Endbenutzer ist dies ein Symbol in der Systemsteuerung von Microsoft® Windows®. An den Anwendungsprogrammierer handelt es sich um eine Bibliothek mit Datenzugriffs Routinen. Vielen anderen ist dies die Antwort auf alle Datenbankzugriffs Probleme, die je vorgestellt wurden.  
  
 Vor allem ist ODBC eine Spezifikation für eine Datenbank-API. Diese API ist unabhängig von einem DBMS oder Betriebssystem. Obwohl in diesem manuellen C C verwendet wird, ist die ODBC-API sprachunabhängig. Die ODBC-API basiert auf den CLI-Spezifikationen von Open Group und ISO/IEC. ODBC 3. *x* implementiert beide Spezifikationen vollständig. frühere Versionen von ODBC basieren auf früheren Versionen dieser Spezifikationen, haben Sie jedoch nicht vollständig implementiert und fügen Features hinzu, die häufig von Entwicklern von bildschirmbasierten Datenbankanwendungen, wie z. b. scrollfähigen Cursorn, benötigt werden.  
  
 Die Funktionen in der ODBC-API werden von Entwicklern von DBMS-spezifischen Treibern implementiert. Anwendungen aufrufen die Funktionen in diesen Treibern, um auf Daten in einer DBMS-unabhängigen Weise zuzugreifen. Ein Treiber-Manager verwaltet die Kommunikation zwischen Anwendungen und Treibern.  
  
 Microsoft stellt zwar einen Treiber-Manager für Computer bereit, auf denen Microsoft Windows® 95 und höher ausgeführt wird, hat jedoch mehrere ODBC-Treiber geschrieben und ODBC-Funktionen aus einigen Anwendungen aufgerufen, und jeder kann ODBC-Anwendungen und-Treiber schreiben. Tatsächlich werden die meisten der heute verfügbaren ODBC-Anwendungen und-Treiber von anderen Unternehmen als Microsoft verfasst. Außerdem sind ODBC-Treiber und-Anwendungen auf dem Macintosh-® und eine Vielzahl von UNIX-Plattformen vorhanden.  
  
 Zur Unterstützung von Anwendungs-und Treiber Entwicklern bietet Microsoft ein ODBC Software Development Kit (SDK) für Computer unter Windows 95 und höher, die Treiber-Manager, Installationsprogramm-dll, Testtools und Beispielanwendungen bereitstellt. Microsoft hat sich mit der visigenen Software zusammengefasst, um diese sdche auf Macintosh und eine Vielzahl von UNIX-Plattformen zu portieren.  
  
 Es ist wichtig zu verstehen, dass ODBC für die Offenlegung von Datenbankfunktionen konzipiert ist, die Sie nicht ergänzen. Daher sollten Anwendungs Schreiber nicht erwarten, dass die Verwendung von ODBC eine einfache Datenbank plötzlich in eine relationale Datenbank-Engine mit vollem Funktionsumfang umwandelt. Ebenso erwarten Treiber Schreiber nicht, dass Funktionen implementiert werden, die in der zugrunde liegenden Datenbank nicht gefunden wurden. Eine Ausnahme hiervon besteht darin, dass Entwickler, die Treiber schreiben, die direkt auf Datei Daten zugreifen (z. b. Daten in einer xBase-Datei), eine Datenbank-Engine schreiben müssen, die mindestens minimale SQL-Funktionalität unterstützt. Eine weitere Ausnahme besteht darin, dass die ODBC-Komponente der Windows SDK, die zuvor im Microsoft Data Access Components (MDAC) SDK enthalten war, eine Cursor Bibliothek bereitstellt, die scrollfähige Cursor für Treiber simuliert, die eine bestimmte Funktionalitäts Ebene implementieren.  
  
 Anwendungen, die ODBC verwenden, sind für datenbankübergreifende Funktionen verantwortlich. ODBC ist beispielsweise keine heterogene joinengine, und es handelt sich nicht um einen verteilten Transaktionsprozessor. Da es jedoch DBMS-unabhängig ist, kann es verwendet werden, um solche datenbankübergreifende Tools zu erstellen.
