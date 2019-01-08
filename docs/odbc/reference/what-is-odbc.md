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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cc9c7a3d9f75e1863d90b16986234e0036229d01
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52540439"
---
# <a name="what-is-odbc"></a>Was ist ODBC?
Viele Missverständnisse über ODBC befinden sich in der IT-Welt. Für den Endbenutzer ist es ein Symbol in der Microsoft® Windows®-Systemsteuerung. Um den Anwendungsprogrammierer ist es eine Bibliothek mit der Data Access-Routinen. Für viele andere ist es die Antwort auf alle Datenbank-Access-Probleme, die jemals gestaltete.  
  
 Zuallererst ist ODBC eine Spezifikation für eine Datenbank-API. Diese API ist unabhängig von einem DBMS oder Betriebssystem. Obwohl dieses Handbuchs C verwendet wird, ist der ODBC-API sprachunabhängig. Der ODBC-API basiert auf den CLI-Spezifikationen von Open Group und ISO/IEC. ODBC 3. *x* vollständig implementiert beide dieser Spezifikationen - frühere Versionen von ODBC basieren auf den vorläufigen Versionen dieser Spezifikationen, aber sie nicht vollständig implementiert – und bietet Features, die häufig von Entwicklern bildschirmbasierte benötigt. Datenbank-Clientanwendungen, beispielsweise scrollfähige Cursor.  
  
 Die Funktionen der ODBC-API werden von Entwicklern mit speziellen DBMS-Treibern implementiert. Anwendungen werden die Funktionen in diesen Treibern, den Zugriff auf Daten in einer DBMS-unabhängige Weise aufrufen. Eine Treiber-Manager verwaltet die Kommunikation zwischen Anwendungen und Treiber.  
  
 Obwohl Microsoft bietet einen Treibermanager für Computer unter Microsoft Windows® 95 und höher geschrieben hat mehrere ODBC-Treiber und ruft ODBC-Funktionen von einigen Anwendungen, jeder ODBC-Anwendungen und Treiber schreiben kann. In der Tat die überwiegende Mehrheit der ODBC-Anwendungen und Treiber zur Verfügung stehen heute wurden von anderen Unternehmen als Microsoft. Darüber hinaus sind ODBC-Treiber und Anwendungen auf die Macintosh® und eine Vielzahl von UNIX-Plattformen vorhanden.  
  
 Die um Anwendungs- und Treiberinstallation Entwickler zu unterstützen, bietet Microsoft eine ODBC-Software Development Kit (SDK) für Computer unter Windows 95 und höher bietet, die der Treiber-Manager, Installationsprogramm-DLL, Tools für Tests und Beispielanwendungen. Microsoft hat mit Visigenic Software so portieren Sie diese SDKs für Macintosh und eine Vielzahl von UNIX-Plattformen in einem Team verwendet.  
  
 Es ist wichtig zu verstehen, dass ODBC Datenbankfunktionen verfügbar, ergänzen sie nicht entwickelt wurde. Daher sollten Anwendungsentwickler erwarten nicht, dass eine einfache Datenbank in eine ausgestattete relationale Datenbank-Engine mithilfe von ODBC plötzlich transformiert wird. Noch Treiber Writer erwartet, Implementieren von Funktionen, die in der zugrunde liegenden Datenbank nicht gefunden. Eine Ausnahme ist die Entwickler, die Treiber zu schreiben, die direkt auf Daten (z. B. in einer Xbase-Datei) zugreifen müssen, eine Datenbank-Engine zu schreiben, die mindestens die minimale SQL-Funktionen unterstützt. Eine weitere Ausnahme, die die ODBC-Komponente des Windows SDK, war früher in der Microsoft Data Access Components (MDAC) SDK enthalten, bietet eine Cursorbibliothek, die scrollbare Cursor für Treiber simuliert, die ein gewisses Maß an Funktionalität zu implementieren.  
  
 Anwendungen, die ODBC verwenden, sind für alle datenbankübergreifenden-Funktionalität verantwortlich sind. Z. B. ODBC ist keines heterogenen joinmoduls, noch ein Prozessors der verteilten Transaktion. Jedoch, da es sich um DBMS unabhängig ist, können sie verwendet werden solche datenbankübergreifende Tools erstellen.
