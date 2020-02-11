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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 926b2285bcce9a28579fffc4004c5454b2837392
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67912435"
---
# <a name="thread-safety-notes-on-api-functions-odbc-driver-for-oracle"></a>Hinweise zur Threadsicherheit für API-Funktionen (ODBC-Treiber für Oracle)
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den von Oracle bereitgestellten ODBC-Treiber.  
  
 Der Microsoft ODBC-Treiber für Oracle ist Thread sicher. Oracle lässt jedoch nicht mehrere gleichzeitige Anweisungen für eine einzelne Verbindung zu. Der Treiber erzwingt diese Einschränkung. Anders ausgedrückt: in Multithreadanwendungen blockiert der Treiber, obwohl jeder Thread jederzeit den ODBC-Treiber für Oracle abrufen kann, alle anderen Threads des Treibers auf derselben Verbindung, bis der ursprüngliche Thread den Treiber verlässt.  
  
 Der Treiber wird nicht blockiert, wenn zwei Anweisungen für zwei unterschiedliche Verbindungen vorhanden sind. Wenn jedoch eine einzelne Verbindung mit zwei-Anweisungen besteht, besteht die Möglichkeit der Blockierung.
