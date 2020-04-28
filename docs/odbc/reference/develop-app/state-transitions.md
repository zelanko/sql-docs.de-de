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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3a480b7ff8953ef94f0efc4886a09731730a61b7
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299693"
---
# <a name="state-transitions"></a>Statusübergänge
ODBC definiert diskrete *Zustände* für jede Umgebung, jede Verbindung und jede Anweisung. Die Umgebung verfügt beispielsweise über drei mögliche Zustände: nicht zugeordnet (in der keine Umgebung zugeordnet ist), zugeordnet (in der eine Umgebung zugeordnet ist, aber keine Verbindungen zugeordnet sind) und Verbindung (in der eine Umgebung und eine oder mehrere Verbindungen zugeordnet werden). Verbindungen haben sieben mögliche Zustände. -Anweisungen haben 13 mögliche Zustände.  
  
 Ein bestimmtes Element, wie durch sein Handle identifiziert, wechselt von einem Zustand in einen anderen, wenn die Anwendung eine bestimmte Funktion oder Funktionen aufruft und das Handle an dieses Element übergibt. Diese Bewegung wird als *Zustandsübergang*bezeichnet. Wenn Sie z. b. ein Umgebungs Handle mit **sqlprovichandle** zuordnen, wird die Umgebung von der nicht zugeordneten zu zugeordneten verschoben, und durch das Freigeben dieses Handles mit **SQLFreeHandle** wird dieses von der Zuordnung zu nicht zugeordnet zurückgegeben. ODBC definiert eine begrenzte Anzahl gesetzlicher Zustandsübergänge. Dies ist eine andere Möglichkeit, zu sagen, dass Funktionen in einer bestimmten Reihenfolge aufgerufen werden müssen.  
  
 Einige Funktionen, z. b. **SQLGetConnectAttr**, wirken sich nicht auf den Status aus. Andere Funktionen beeinflussen den Zustand eines einzelnen Elements. Beispielsweise verschiebt **SQLDisconnect** eine Verbindung von einem Verbindungsstatus in einen zugewiesenen Zustand. Zum Schluss beeinflussen einige Funktionen den Status von mehr als einem Element. Wenn Sie z. b. ein Verbindungs Handle mit **sqlprovichandle** zuordnen, wird eine Verbindung von einem nicht zugeordneten zu einem zugewiesenen Zustand verschoben, und die Umgebung wird von einem zugeordneten zu einem Verbindungsstatus verschoben.  
  
 Wenn eine Anwendung eine Funktion außerhalb der Reihenfolge aufruft, gibt die Funktion einen *Status Übergangs Fehler*zurück. Wenn z. b. eine Umgebung einen Verbindungsstatus aufweist und die Anwendung **SQLFreeHandle** mit diesem Umgebungs Handle aufruft, gibt **SQLFreeHandle** SQLSTATE HY010 (Funktions Sequenz Fehler) zurück, da Sie nur aufgerufen werden kann, wenn die Umgebung einen zugewiesenen Zustand aufweist. Wenn Sie dies als ungültigen Status Übergang definieren, verhindert ODBC, dass die Anwendung die Umgebung freigibt, während aktive Verbindungen vorhanden sind.  
  
 Einige Zustandsübergänge sind im Entwurf von ODBC enthalten. Beispielsweise ist es nicht möglich, ein Verbindungs Handle zuzuordnen, ohne zuerst ein Umgebungs Handle zuzuordnen, da die Funktion, die ein Verbindungs Handle zuordnet, ein Umgebungs Handle erfordert. Andere Zustandsübergänge werden vom Treiber-Manager und den Treibern erzwungen. **SQLExecute** führt z. b. eine vorbereitete Anweisung aus. Wenn sich das an das Anweisungs Handle weiter gegebene Handle nicht in einem vorbereiteten Zustand befindet, gibt **SQLExecute** SQLSTATE HY010 (Funktions Sequenz Fehler) zurück.  
  
 Aus Sicht der Anwendung sind Zustandsübergänge in der Regel unkompliziert: zulässige Zustandsübergänge sind tendenziell Hand in Hand mit dem Ablauf einer gut geschriebenen Anwendung. Zustandsübergänge sind für den Treiber-Manager und die Treiber komplexer, da Sie den Zustand der Umgebung, jede Verbindung und jede Anweisung nachverfolgen müssen. Die meisten dieser Aufgaben werden vom Treiber-Manager ausgeführt. die meisten Aufgaben, die von Treibern ausgeführt werden müssen, treten mit Anweisungen mit ausstehenden Ergebnissen auf.  
  
 In den Teilen 1 und 2 dieses Handbuchs ("Einführung in ODBC" und "entwickeln von Anwendungen und Treibern") werden Zustandsübergänge tendenziell nicht explizit erwähnt. Stattdessen beschreiben Sie die Reihenfolge, in der Funktionen aufgerufen werden müssen. Beispielsweise gibt "ausführende Anweisungen" an, dass eine Anweisung mit **SQLPrepare** vorbereitet werden muss, bevor Sie mit **SQLExecute**ausgeführt werden kann. Eine umfassende Beschreibung der Zustände und Zustandsübergänge, einschließlich der Übergänge, die vom Treiber-Manager geprüft werden und die von Treibern geprüft werden müssen, finden Sie in [Anhang B: ODBC-Status Übergangs Tabellen](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).
