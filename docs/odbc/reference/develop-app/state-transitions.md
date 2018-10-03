---
title: Statusübergänge | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- state transitions [ODBC]
- unallocated state [ODBC]
- handles [ODBC], state transitions
- allocated state [ODBC]
- connection state [ODBC]
ms.assetid: fc741611-6535-43cc-8156-6d897d04664e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 30c1db4f850e6f181757d974ae74bb475b0cc5cc
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47767721"
---
# <a name="state-transitions"></a>Statusübergänge
ODBC definiert diskrete *Zustände* für jede Umgebung, jede Verbindung und jede Anweisung. Z. B. die Umgebung verfügt über drei mögliche Zustände: verfügbaren (in dem keine Umgebung zugeordnet ist), zugewiesenem (in der eine Umgebung wird zugeordnet, jedoch keine Verbindungen zugeordnet sind) und (in der Umgebung und eine oder mehrere Verbindungen sind Verbindung zugeordnet). Verbindungen haben sieben möglichen Status; -Anweisungen verfügen über 13 mögliche Zustände.  
  
 Ein Element verschiebt wie von seinem Handle identifiziert von einem Zustand, wenn die Anwendung eine bestimmte Funktion oder Funktionen aufruft, und das Handle für das Element übergibt. Diese Bewegung wird aufgerufen, eine *Status Übergang*. Z. B. Zuordnen eines Umgebungshandles mit **SQLAllocHandle** verschiebt Sie die Umgebung aus nicht zugeordnet, in zugeordneten und Freigeben dieses Handle mit **SQLFreeHandle** wird zugeordnet zu zurückgegeben Nicht zugeordnet ist. ODBC definiert eine begrenzte Anzahl von zulässigen Statusübergänge, die eine andere Möglichkeit, der besagt, dass Funktionen in einer bestimmten Reihenfolge aufgerufen werden müssen.  
  
 Einige Funktionen, z. B. **SQLGetConnectAttr**, wirken sich nicht Zustand überhaupt. Andere Funktionen wirken sich auf den Zustand eines einzelnen Elements. Z. B. **SQLDisconnect** verschiebt eine Verbindung aus eine Verbindung zu einem Status "Allocated". Einige Funktionen wird schließlich den Status der mehr als ein Element auswirken. Z. B. Zuordnen eines Verbindungshandles mit **SQLAllocHandle** bewegt sich eine Verbindung aus einer nicht zugeordnet, die ein Status "Allocated" und die Umgebung über eine zugeordnete in einen Verbindungszustand.  
  
 Wenn eine Anwendung eine Funktion außerhalb der Reihenfolge aufruft, gibt die Funktion eine *Status-Übergang-Fehler*. Wenn Sie eine Umgebung in einen Verbindungszustand und die Anwendung ist z. B. Aufrufe **SQLFreeHandle** mit diesem Umgebungshandle **SQLFreeHandle** SQLSTATE HY010 zurückgibt (Funktion Sequenzfehler), Da sie aufgerufen werden kann nur verwendet werden, wenn die Umgebung in einem Zustand zugeordnet ist. Durch definieren dies als ein ungültiger Statusübergang, hindert ODBC-die Anwendung aus die Umgebung freigegeben, während aktive Verbindungen.  
  
 Einige Statusübergänge sind sich der Entwurf von ODBC. Beispielsweise ist es nicht möglich, ein Verbindungshandle zuordnen ohne zuerst ein Umgebungshandle zuzuordnen, da die Funktion, die ein Verbindungshandle weist ein Umgebungshandle erforderlich ist. Andere Zustandsübergänge werden durch den Treiber-Manager und die Treiber erzwungen. Z. B. **SQLExecute** führt eine vorbereitete Anweisung. Wenn an das Anweisungshandle übergeben es ist nicht im vorbereiteten Status, **SQLExecute** SQLSTATE HY010 zurückgibt (Sequenzfehler funktionieren).  
  
 Statusübergänge sind aus Sicht der Anwendung, in der Regel einfach: zulässige Statusübergänge sind tendenziell gehen Hand in Hand mit den eine gut geschriebene Anwendung. Statusübergänge sind komplexer für den Treiber-Manager und die Treiber, da sie den Zustand der Umgebung, jede Verbindung und jede Anweisung nachverfolgen müssen. Die meisten dieser Arbeit ist möglich, vom Treiber-Manager. Die meisten Aufgaben, die vom Treiber durchgeführt werden muss, tritt bei Anweisungen mit ausstehende Ergebnisse.  
  
 Teil 1 und 2 dieses Handbuchs ("Introduction to ODBC" und "Entwickeln von Anwendungen und Treiber") tendenziell keine Statusübergänge explizit zu erwähnen. Stattdessen beschreiben sie die Reihenfolge, in der Funktionen aufgerufen werden müssen. "Ausführen von Anweisungen" gibt z. B. an, dass eine Anweisung vorbereitet werden muss, mit **SQLPrepare** , bevor sie mit ausgeführt werden kann **SQLExecute**. Eine vollständige Beschreibung der Zustände und Zustandsübergänge, einschließlich die Übergänge vom Treiber-Manager überprüft werden, und die vom Treiber, überprüft werden müssen finden Sie unter [Anhang B: ODBC-Übergang-Statustabellen](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).
