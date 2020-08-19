---
description: Hinweise zur Threadsicherheit für API-Funktionen (ODBC-Treiber für Oracle)
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
ms.openlocfilehash: 8c7da346832e2682caa02bdbdae91a1133a9cbaa
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88449082"
---
# <a name="thread-safety-notes-on-api-functions-odbc-driver-for-oracle"></a>Hinweise zur Threadsicherheit für API-Funktionen (ODBC-Treiber für Oracle)
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den von Oracle bereitgestellten ODBC-Treiber.  
  
 Der Microsoft ODBC-Treiber für Oracle ist Thread sicher. Oracle lässt jedoch nicht mehrere gleichzeitige Anweisungen für eine einzelne Verbindung zu. Der Treiber erzwingt diese Einschränkung. Anders ausgedrückt: in Multithreadanwendungen blockiert der Treiber, obwohl jeder Thread jederzeit den ODBC-Treiber für Oracle abrufen kann, alle anderen Threads des Treibers auf derselben Verbindung, bis der ursprüngliche Thread den Treiber verlässt.  
  
 Der Treiber wird nicht blockiert, wenn zwei Anweisungen für zwei unterschiedliche Verbindungen vorhanden sind. Wenn jedoch eine einzelne Verbindung mit zwei-Anweisungen besteht, besteht die Möglichkeit der Blockierung.
