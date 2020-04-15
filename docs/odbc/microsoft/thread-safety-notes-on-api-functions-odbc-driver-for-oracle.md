---
title: Threadsicherheitshinweise zu API-Funktionen (ODBC-Treiber für Oracle) | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303071"
---
# <a name="thread-safety-notes-on-api-functions-odbc-driver-for-oracle"></a>Hinweise zur Threadsicherheit für API-Funktionen (ODBC-Treiber für Oracle)
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Windows-Version entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den von Oracle bereitgestellten ODBC-Treiber.  
  
 Der Microsoft ODBC-Treiber für Oracle ist threadsicher. Oracle lässt jedoch mehrere gleichzeitige Anweisungen für eine einzelne Verbindung nicht zu. Der Treiber erzwingt diese Einschränkung. Mit anderen Worten, in Multithreadanwendungen, obwohl jeder Thread jederzeit den ODBC-Treiber für Oracle aufrufen kann, blockiert der Treiber jeden anderen Thread vom Treiber auf derselben Verbindung, bis der ursprüngliche Thread den Treiber verlässt.  
  
 Der Treiber blockiert nicht, wenn zwei Anweisungen für zwei verschiedene Verbindungen vorhanden sind. Wenn jedoch eine einzige Verbindung mit zwei Anweisungen besteht, besteht das Potenzial zum Blockieren.
