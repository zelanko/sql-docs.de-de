---
description: Ablaufverfolgungsdatei
title: Ablauf Verfolgungs Datei | Microsoft-Dokumentation
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ba45e44baaba68d1c203e83a25c9db305642e6d2
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88487493"
---
# <a name="trace-file"></a>Ablaufverfolgungsdatei
Eine Anwendung gibt die Ablauf Verfolgungs Datei an, indem entweder das **Tracefile** -Schlüsselwort im Registrierungs Eintrag Odbc.ini festgelegt wird oder durch Aufrufen von **SQLSetConnectAttr** mit dem SQL_ATTR_TRACEFILE-Verbindungs Attribut. Wenn die Datei nicht vorhanden ist, wenn die Ablauf Verfolgung aktiviert ist, wird die Datei vom Treiber-Manager erstellt. Jede Anwendung sollte über eine eigene dedizierte Ablauf Verfolgungs Datei verfügen, um Konflikte zu vermeiden. Eine Anwendung kann mehr als eine Ablauf Verfolgungs Datei verwenden. Das Setup Programm einer Anwendung kann dem Benutzer die Auswahl von Ablauf Verfolgungs Dateien ermöglichen. Wenn die Ablauf Verfolgung dynamisch aktiviert ist, kann eine Anwendung auch Ablauf Verfolgungs Ergebnisse anzeigen, anstatt Sie in der Ablauf Verfolgungs Datei zu protokollieren.  
  
 Die Ablauf Verfolgungs Datei stellt ein Protokoll aller ODBC-Funktionsaufrufe mit den Datentypen und den Werten aller Argumente bereit. Es protokolliert alle Eingabefunktionen und protokolliert alle zurückgegebenen Funktionen mit Rückgabecodes und Fehlerzuständen.  
  
 In ODBC *3. x*werden Parameter für Verbindungsfunktionen nicht für die Trace-dll bereitgestellt.
