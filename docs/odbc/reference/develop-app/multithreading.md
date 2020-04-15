---
title: Multithreading | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302415"
---
# <a name="multithreading"></a>Multithreading
Bei Multithreadbetriebssystemen müssen Treiber threadsicher sein. Das heißt, es muss für Anwendungen möglich sein, dasselbe Handle für mehr als einen Thread zu verwenden. Wie dies erreicht wird, ist treiberspezifisch, und es ist wahrscheinlich, dass Treiber alle Versuche serialisieren, gleichzeitig dasselbe Handle auf zwei verschiedenen Threads zu verwenden.  
  
 Anwendungen verwenden häufig mehrere Threads anstelle der asynchronen Verarbeitung. Die Anwendung erstellt einen separaten Thread, ruft eine ODBC-Funktion darauf auf und setzt dann die Verarbeitung auf dem Hauptthread fort. Anstatt die asynchrone Funktion kontinuierlich abwählen zu müssen, wie dies bei der Verwendung des SQL_ATTR_ASYNC_ENABLE Anweisungsattributs der Fall ist, kann die Anwendung den neu erstellten Thread einfach beenden lassen.  
  
 Funktionen, die ein Anweisungshandle akzeptieren und für einen Thread ausgeführt werden, können abgebrochen werden, indem **SQLCancel** mit demselben Anweisungshandle aus einem anderen Thread aufgerufen wird. Obwohl Treiber die Verwendung von **SQLCancel** nicht auf diese Weise serialisieren sollten, gibt es keine Garantie dafür, dass der Aufruf von **SQLCancel** die Funktion, die auf dem anderen Thread ausgeführt wird, tatsächlich abbricht.
