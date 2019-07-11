---
title: Ablaufverfolgungsdatei | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- trace files [ODBC]
- tracing options [ODBC], trace files
ms.assetid: ec97f949-126f-40a2-b67e-e74520a524cb
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8138a0cef3a28d31242a74162f0024e28e8b8fe9
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2019
ms.locfileid: "67793931"
---
# <a name="trace-file"></a>Ablaufverfolgungsdatei
Eine Anwendung gibt der Datei entweder durch Festlegen der **TraceFile** Schlüsselwort im Registrierungseintrag Odbc.ini oder durch Aufrufen von **SQLSetConnectAttr** mit das SQL_ATTR_TRACEFILE-Verbindungsattribut. Wenn die Datei nicht vorhanden ist, wenn die Ablaufverfolgung aktiviert ist, wird der Treiber-Manager die Datei erstellt. Jede Anwendung müssen eigene dedizierte Ablaufverfolgungsdatei, um Konflikte zu vermeiden. Eine Anwendung kann mehr als eine Ablaufverfolgungsdatei verwenden; Setup-Programm von der Anwendung bieten den Benutzer eine Auswahl von Ablaufverfolgungsdateien. Wenn die Ablaufverfolgung dynamisch aktiviert ist, kann eine Anwendung auch Ablaufverfolgungsergebnisse, anstatt die Protokollierung zur Ablaufverfolgungsdatei anzeigen.  
  
 Die Ablaufverfolgungsdatei enthält ein Protokoll der einzelnen ODBC-Funktionsaufruf mit den Datentypen und Werte für alle Argumente. Protokolliert alle Eingabefunktionen und alle zurückgegebene Funktionen mit Rückgabecodes und Fehlerzustände protokolliert.  
  
 In ODBC *3.x*, Parameter, Verbindungsfunktionen werden nicht bereitgestellt, um die Ablaufverfolgung-DLL.
