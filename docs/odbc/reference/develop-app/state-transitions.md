---
title: Zustandsübergänge | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3a480b7ff8953ef94f0efc4886a09731730a61b7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299693"
---
# <a name="state-transitions"></a>Statusübergänge
ODBC definiert diskrete *Zustände* für jede Umgebung, jede Verbindung und jede Anweisung. Die Umgebung weist beispielsweise drei mögliche Zustände auf: Nicht zugewiesen (in denen keine Umgebung zugewiesen ist), Zugewiesen (in der eine Umgebung zugewiesen, aber keine Verbindungen zugewiesen sind) und Verbindung (in der eine Umgebung und eine oder mehrere Verbindungen zugewiesen sind). Verbindungen haben sieben mögliche Zustände; Aussagen haben 13 mögliche Zustände.  
  
 Ein bestimmtes Element, wie durch sein Handle identifiziert, wird von einem Zustand in einen anderen verschoben, wenn die Anwendung eine bestimmte Funktion oder Funktionen aufruft und das Handle an dieses Element übergibt. Eine solche Bewegung wird als *Zustandsübergang*bezeichnet. Wenn Sie z. B. ein Umgebungshandle mit **SQLAllocHandle** zuweisen, wird die Umgebung von "Nicht zugewiesen" auf "Allocated" verschoben, und das Freiwerden dieses Handles mit **SQLFreeHandle** gibt es von "Zugeordnet" an "Nicht zugewiesen" zurück. ODBC definiert eine begrenzte Anzahl von rechtsstaatlichen Übergängen, was eine weitere Möglichkeit ist zu sagen, dass Funktionen in einer bestimmten Reihenfolge aufgerufen werden müssen.  
  
 Einige Funktionen, z. B. **SQLGetConnectAttr**, wirken sich überhaupt nicht auf den Status aus. Andere Funktionen wirken sich auf den Status eines einzelnen Elements aus. **SQLDisconnect** verschiebt z. B. eine Verbindung von einem Verbindungsstatus in einen Status "Zugeordnet". Schließlich wirken sich einige Funktionen auf den Zustand von mehr als einem Element aus. Wenn Sie z. B. ein Verbindungshandle mit **SQLAllocHandle** zuweisen, wird eine Verbindung von einem Nicht zugewiesenen in einen Status "Zugeordnet" verschoben und die Umgebung von einem Status "Zugeordnet" in einen Verbindungsstatus verschoben.  
  
 Wenn eine Anwendung eine Funktion aerrort, gibt die Funktion einen *Statusübergangsfehler*zurück. Wenn sich eine Umgebung beispielsweise im Verbindungsstatus befindet und die Anwendung **SQLFreeHandle** mit diesem Umgebungshandle aufruft, gibt **SQLFreeHandle** SQLSTATE HY010 (Funktionssequenzfehler) zurück, da sie nur aufgerufen werden kann, wenn sich die Umgebung im Status "Zugeordnet" befindet. Indem ODBC dies als ungültigen Zustandsübergang definiert, verhindert ODBC, dass die Anwendung die Umgebung freigibt, während aktive Verbindungen vorhanden sind.  
  
 Einige Zustandsübergänge sind dem Entwurf von ODBC inhärent. Beispielsweise ist es nicht möglich, ein Verbindungshandle zuzuweisen, ohne zuvor ein Umgebungshandle zuzuweisen, da die Funktion, die ein Verbindungshandle zuweist, ein Umgebungshandle erfordert. Andere Statusübergänge werden vom Treiber-Manager und den Treibern erzwungen. **SQLExecute** führt beispielsweise eine vorbereitete Anweisung aus. Wenn sich das an das Anweisungshandle übergebene Anweisungshandle nicht im Status Vorbereitet befindet, gibt **SQLExecute** SQLSTATE HY010 (Funktionssequenzfehler) zurück.  
  
 Aus Sicht der Anwendung sind Zustandsübergänge in der Regel einfach: Rechtszustandsübergänge gehen in der Regel Hand in Hand mit dem Fluss einer gut geschriebenen Anwendung. Zustandsübergänge sind für den Treiber-Manager und die Treiber komplexer, da sie den Zustand der Umgebung, jede Verbindung und jede Anweisung nachverfolgen müssen. Der größte Teil dieser Arbeit wird vom Treiber-Manager ausgeführt. die meiste Arbeit, die von Treibern ausgeführt werden muss, erfolgt mit Anweisungen mit ausstehenden Ergebnissen.  
  
 In den Teilen 1 und 2 dieses Handbuchs ("Einführung in ODBC" und "Entwickeln von Anwendungen und Treibern") werden Zustandsübergänge in der Regel nicht explizit erwähnt. Stattdessen beschreiben sie die Reihenfolge, in der Funktionen aufgerufen werden müssen. "Executing Statements" besagt beispielsweise, dass eine Anweisung mit **SQLPrepare** vorbereitet werden muss, bevor sie mit **SQLExecute**ausgeführt werden kann. Eine vollständige Beschreibung der Zustände und Zustandsübergänge, einschließlich der Übergänge, die vom Treiber-Manager überprüft werden und die von Treibern überprüft werden müssen, finden Sie in [Anhang B: ODBC-Statusübergangstabellen](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).
