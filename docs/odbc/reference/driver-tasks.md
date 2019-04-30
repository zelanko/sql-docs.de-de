---
title: Treiber-Aufgaben | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC architecture [ODBC], drivers
- drivers [ODBC], tasks
ms.assetid: 184c795a-c2e8-4d20-9902-12e60b2f0e45
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ee695c62fc60b2ebb0ae9bb33ef9008ba617b49a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63254147"
---
# <a name="driver-tasks"></a>Treiberaufgaben
Bestimmte Aufgaben, die vom Treiber ausgeführt:  
  
-   Herstellen einer Verbindung mit und Trennen von der Datenquelle.  
  
-   Überprüfung auf Funktionsfehler, die vom Treiber-Manager nicht aktiviert.  
  
-   Initiierenden-Transaktionen Dies ist für die Anwendung transparent.  
  
-   SQL-Anweisungen an die Datenquelle für die Ausführung wird übermittelt. Der Treiber muss mit DBMS-spezifische SQL ODBC-SQL ändern; Dies ist häufig auf, und Ersetzen Sie dabei Escape-Klauseln, die von ODBC mit speziellen DBMS-SQL definiert.  
  
-   Senden von Daten zu und Abrufen von Daten aus der Datenquelle, einschließlich der Konvertierung von Datentypen, wie von der Anwendung angegeben.  
  
-   Zuordnen von DBMS-spezifische Fehler zu ODBC SQLSTATEs.
