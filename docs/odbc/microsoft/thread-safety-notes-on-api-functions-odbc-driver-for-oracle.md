---
title: Threadsicherheit Hinweise auf API-Funktionen (ODBC-Treiber für Oracle) | Microsoft-Dokumentation
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67912435"
---
# <a name="thread-safety-notes-on-api-functions-odbc-driver-for-oracle"></a>Hinweise zur Threadsicherheit für API-Funktionen (ODBC-Treiber für Oracle)
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den ODBC-Treiber, die von Oracle bereitgestellt.  
  
 Der Microsoft ODBC-Treiber für Oracle ist threadsicher. Oracle lässt jedoch nicht mehrere gleichzeitige Anweisungen über eine einzelne Verbindung. Der Treiber erzwingt diese Einschränkung. Das heißt, obwohl jeder Thread zu jedem Zeitpunkt in der ODBC-Treiber für Oracle aufrufen kann blockiert, in Multithreadanwendungen, der Treiber keinem anderen Thread aus dem Treiber für die gleiche Verbindung bis der ursprüngliche Thread den Treiber verlässt.  
  
 Der Treiber wird nicht blockiert, wenn zwei Anweisungen für zwei unterschiedliche Verbindungen vorhanden sind. Allerdings ist es eine einzelne Verbindung mit zwei Anweisungen, besteht es die Möglichkeit zum Blockieren.
