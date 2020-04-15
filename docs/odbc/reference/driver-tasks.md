---
title: Treiberaufgaben | Microsoft Docs
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
ms.openlocfilehash: 1b30df63a3c955d2ed074ab13649ea55c21a6da7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81294200"
---
# <a name="driver-tasks"></a>Treiberaufgaben
Zu den spezifischen Aufgaben, die von Treibern ausgeführt werden, gehören:  
  
-   Herstellen einer Verbindung mit der Datenquelle und Trennen der Verbindung mit der Datenquelle.  
  
-   Überprüfen auf Funktionsfehler, die nicht vom Treiber-Manager überprüft wurden.  
  
-   Initiierung von Transaktionen; dies ist für die Anwendung transparent.  
  
-   Senden von SQL-Anweisungen an die Datenquelle zur Ausführung. Der Treiber muss ODBC SQL in DBMS-spezifischeSQL ändern. Dies ist häufig auf das Ersetzen von Von ODBC definierten Escapeklauseln durch DBMS-spezifische SQL beschränkt.  
  
-   Senden von Daten an die Datenquelle und Abrufen von Daten aus der Datenquelle, einschließlich der Konvertierung von Datentypen, wie von der Anwendung angegeben.  
  
-   Zuordnen von DBMS-spezifischen Fehlern zu ODBC SQLSTATEs.
