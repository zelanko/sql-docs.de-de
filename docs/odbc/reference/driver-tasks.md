---
description: Treiberaufgaben
title: Treiber Aufgaben | Microsoft-Dokumentation
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 263f591592063a45fdd5afdca4efdd75b5b915b6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88339056"
---
# <a name="driver-tasks"></a>Treiberaufgaben
Bestimmte Aufgaben, die von Treibern ausgeführt werden, umfassen Folgendes:  
  
-   Verbindung mit der Datenquelle wird hergestellt, und die Verbindung wird getrennt.  
  
-   Es wird auf Funktionsfehler überprüft, die vom Treiber-Manager nicht überprüft werden.  
  
-   Initiieren von Transaktionen; Dies ist für die Anwendung transparent.  
  
-   SQL-Anweisungen werden zur Ausführung an die Datenquelle übermittelt. Der Treiber muss ODBC SQL in DBMS-spezifisches SQL ändern; Dies ist oft auf das Ersetzen von Escape-Klauseln beschränkt, die von ODBC durch DBMS-spezifische SQL definiert werden.  
  
-   Senden von Daten an und Abrufen von Daten aus der Datenquelle, einschließlich der Datentypen, wie von der Anwendung angegeben.  
  
-   Zuordnen von DBMS-spezifischen Fehlern zu ODBC Sqlstates.
