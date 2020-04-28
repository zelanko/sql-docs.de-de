---
title: Multithreading | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC drivers [ODBC], thread-safe
- thread-safe drivers [ODBC]
- multithreaded applications [ODBC]
ms.assetid: cdfebdf5-12ff-4e28-8055-41f49b77f664
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c10d1b401ac780d24184c4c2337199e99973e916
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81302415"
---
# <a name="multithreading"></a>Multithreading
Bei multithreadbetriebssystemen müssen Treiber Thread sicher sein. Das heißt, es muss möglich sein, dass Anwendungen das gleiche Handle für mehr als einen Thread verwenden können. Wie dies erreicht wird, ist Treiber spezifisch, und es ist wahrscheinlich, dass Treiber alle Versuche serialisieren, gleichzeitig denselben Handle für zwei verschiedene Threads zu verwenden.  
  
 Anwendungen verwenden häufig mehrere Threads anstelle der asynchronen Verarbeitung. Die Anwendung erstellt einen separaten Thread, ruft eine ODBC-Funktion darauf auf und setzt dann die Verarbeitung im Haupt Thread fort. Anstatt die asynchrone Funktion kontinuierlich abzufragen, wie es der Fall ist, wenn das SQL_ATTR_ASYNC_ENABLE-Anweisungs Attribut verwendet wird, kann die Anwendung den neu erstellten Thread einfach Fertigstellen lassen.  
  
 Funktionen, die ein Anweisungs Handle akzeptieren und in einem Thread ausgeführt werden, können durch Aufrufen von **SQLCancel** mit dem gleichen Anweisungs Handle von einem anderen Thread abgebrochen werden. Obwohl Treiber die Verwendung von **SQLCancel** nicht auf diese Weise serialisieren sollten, gibt es keine Garantie, dass das Aufrufen von **SQLCancel** tatsächlich die Funktion abbricht, die auf dem anderen Thread ausgeführt wird.
