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
ms.openlocfilehash: c94c3718c116b37eb198264887dfb4a319bd1dc3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67985149"
---
# <a name="trace-file"></a>Ablaufverfolgungsdatei
Eine Anwendung gibt der Datei entweder durch Festlegen der **TraceFile** Schlüsselwort im Registrierungseintrag Odbc.ini oder durch Aufrufen von **SQLSetConnectAttr** mit das SQL_ATTR_TRACEFILE-Verbindungsattribut. Wenn die Datei nicht vorhanden ist, wenn die Ablaufverfolgung aktiviert ist, wird der Treiber-Manager die Datei erstellt. Jede Anwendung müssen eigene dedizierte Ablaufverfolgungsdatei, um Konflikte zu vermeiden. Eine Anwendung kann mehr als eine Ablaufverfolgungsdatei verwenden; Setup-Programm von der Anwendung bieten den Benutzer eine Auswahl von Ablaufverfolgungsdateien. Wenn die Ablaufverfolgung dynamisch aktiviert ist, kann eine Anwendung auch Ablaufverfolgungsergebnisse, anstatt die Protokollierung zur Ablaufverfolgungsdatei anzeigen.  
  
 Die Ablaufverfolgungsdatei enthält ein Protokoll der einzelnen ODBC-Funktionsaufruf mit den Datentypen und Werte für alle Argumente. Protokolliert alle Eingabefunktionen und alle zurückgegebene Funktionen mit Rückgabecodes und Fehlerzustände protokolliert.  
  
 In ODBC *3.x*, Parameter, Verbindungsfunktionen werden nicht bereitgestellt, um die Ablaufverfolgung-DLL.
