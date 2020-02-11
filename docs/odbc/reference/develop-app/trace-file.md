---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c94c3718c116b37eb198264887dfb4a319bd1dc3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67985149"
---
# <a name="trace-file"></a>Ablaufverfolgungsdatei
Eine Anwendung gibt die Ablauf Verfolgungs Datei entweder durch Festlegen des **Tracefile** -Schlüssel Worts im Registrierungs Eintrag "ODBC. ini" oder durch Aufrufen von **SQLSetConnectAttr** mit dem SQL_ATTR_TRACEFILE Connection-Attribut an. Wenn die Datei nicht vorhanden ist, wenn die Ablauf Verfolgung aktiviert ist, wird die Datei vom Treiber-Manager erstellt. Jede Anwendung sollte über eine eigene dedizierte Ablauf Verfolgungs Datei verfügen, um Konflikte zu vermeiden. Eine Anwendung kann mehr als eine Ablauf Verfolgungs Datei verwenden. Das Setup Programm einer Anwendung kann dem Benutzer die Auswahl von Ablauf Verfolgungs Dateien ermöglichen. Wenn die Ablauf Verfolgung dynamisch aktiviert ist, kann eine Anwendung auch Ablauf Verfolgungs Ergebnisse anzeigen, anstatt Sie in der Ablauf Verfolgungs Datei zu protokollieren.  
  
 Die Ablauf Verfolgungs Datei stellt ein Protokoll aller ODBC-Funktionsaufrufe mit den Datentypen und den Werten aller Argumente bereit. Es protokolliert alle Eingabefunktionen und protokolliert alle zurückgegebenen Funktionen mit Rückgabecodes und Fehlerzuständen.  
  
 In ODBC *3. x*werden Parameter für Verbindungsfunktionen nicht für die Trace-dll bereitgestellt.
