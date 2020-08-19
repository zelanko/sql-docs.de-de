---
description: Call-Level-Interface
title: Schnittstellen auf der callsebene | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], CLI
- CLI [ODBC], using CLI
- sending SQL statements to DBMS [ODBC]
- SQL [ODBC], CLI
- call-level interface [ODBC], using call-level interface
ms.assetid: 42257bb6-0bf1-4533-a4ef-4a6dd2aecb18
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ad1e89f945dbb739c4c20103fc2330cbf4e562b5
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88448958"
---
# <a name="call-level-interfaces"></a>Call-Level-Interface
Das abschließende Verfahren zum Senden von SQL-Anweisungen an das DBMS erfolgt über eine Schnittstelle auf Callcenter (Callcenter). Eine Schnittstelle auf Aufruf Ebene stellt eine Bibliothek von DBMS-Funktionen bereit, die vom Anwendungsprogramm aufgerufen werden können. Anstatt SQL mit einer anderen Programmiersprache zu vermischen, ähnelt eine Schnittstelle auf Aufruf Ebene den Routine Bibliotheken, die die meisten Programmierer verwenden, wie z. b. Zeichen folgen-, e/a-oder mathematische Bibliotheken in C. Beachten Sie, dass DBMSs, der eingebettete SQL-Unterstützung unterstützt, bereits über eine Schnittstelle auf Aufruf Ebene verfügt. Diese Aufrufe sind jedoch nicht dokumentiert und können ohne vorherige Ankündigung geändert werden.  
  
 Schnittstellen auf Aufrufebene werden häufig in Client/Server-Architekturen verwendet, in denen sich das Anwendungsprogramm (der-Client) auf einem Computer und das DBMS (der-Server) auf einem anderen Computer befindet. Die Anwendung ruft CLI-Funktionen auf dem lokalen System auf, und diese Aufrufe werden zur Verarbeitung über das Netzwerk an das DBMS gesendet.  
  
 Eine Schnittstelle auf Aufruf Ebene ähnelt der dynamischen SQL-Anweisung, da SQL-Anweisungen zur Verarbeitung zur Laufzeit an das DBMS übermittelt werden, unterscheidet sich jedoch von eingebettetem SQL als Ganzes darin, dass keine eingebetteten SQL-Anweisungen vorhanden sind und kein vorkompilierten erforderlich ist.  
  
 Die Verwendung einer Schnittstelle auf Aufrufebene umfasst in der Regel die folgenden Schritte:  
  
1.  Die Anwendung ruft eine CLI-Funktion auf, um eine Verbindung mit dem DBMS herzustellen.  
  
2.  Die Anwendung erstellt eine SQL-Anweisung und platziert Sie in einem Puffer. Anschließend wird eine oder mehrere CLI-Funktionen aufgerufen, um die Anweisung zur Vorbereitung und Ausführung an das DBMS zu senden.  
  
3.  Wenn die Anweisung eine SELECT-Anweisung ist, ruft die Anwendung eine CLI-Funktion auf, um die Ergebnisse in Anwendungs Puffern zurückzugeben. In der Regel gibt diese Funktion jeweils eine Zeile oder eine Spalte mit Daten zurück.  
  
4.  Die Anwendung ruft eine CLI-Funktion auf, um die Verbindung mit dem DBMS zu trennen.
