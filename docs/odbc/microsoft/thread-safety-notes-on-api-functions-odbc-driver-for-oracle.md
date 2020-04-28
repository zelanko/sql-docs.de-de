---
title: Hinweise zur Thread Sicherheit bei API-Funktionen (ODBC-Treiber für Oracle) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], threading
- threading options [ODBC]
- multiple concurrent statements [ODBC]
ms.assetid: f0c9bdfd-f79d-4088-9ecb-afcd8ca7fb73
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 489f0e99ea53d419ff94dddfeb22e37573abb874
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81303071"
---
# <a name="thread-safety-notes-on-api-functions-odbc-driver-for-oracle"></a>Hinweise zur Threadsicherheit für API-Funktionen (ODBC-Treiber für Oracle)
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den von Oracle bereitgestellten ODBC-Treiber.  
  
 Der Microsoft ODBC-Treiber für Oracle ist Thread sicher. Oracle lässt jedoch nicht mehrere gleichzeitige Anweisungen für eine einzelne Verbindung zu. Der Treiber erzwingt diese Einschränkung. Anders ausgedrückt: in Multithreadanwendungen blockiert der Treiber, obwohl jeder Thread jederzeit den ODBC-Treiber für Oracle abrufen kann, alle anderen Threads des Treibers auf derselben Verbindung, bis der ursprüngliche Thread den Treiber verlässt.  
  
 Der Treiber wird nicht blockiert, wenn zwei Anweisungen für zwei unterschiedliche Verbindungen vorhanden sind. Wenn jedoch eine einzelne Verbindung mit zwei-Anweisungen besteht, besteht die Möglichkeit der Blockierung.
