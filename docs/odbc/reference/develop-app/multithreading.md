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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1a16262d562ca2088f38cd863a6f44e537e65d40
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63254208"
---
# <a name="multithreading"></a>Multithreading
Bei multithread-Betriebssystemen müssen der Treiber threadsicher sein. D. h. muss es möglich, dass Anwendungen in mehr als einem Thread dasselbe Handle zu verwenden sein. Wie dies erreicht wird, ist treiberspezifisch, und ist es wahrscheinlich, dass der Treiber alle Versuche, verwenden Sie dasselbe Handle gleichzeitig in zwei verschiedenen Threads serialisiert werden.  
  
 Anwendungen werden häufig mehrere Threads verwenden, anstatt die asynchrone Verarbeitung. Die Anwendung einen separaten Thread erstellt, ruft eine ODBC-Funktion auf und Verarbeitung auf dem Hauptthread fortgesetzt. Anstatt die asynchrone Funktion, ständig abruft wie der Fall ist, wenn das Attribut des SQL_ATTR_ASYNC_ENABLE-Anweisung verwendet wird, können die Anwendung einfach den neu erstellten Thread abgeschlossen.  
  
 Funktionen, die ein Anweisungshandle akzeptieren und in einem einzelnen Thread ausgeführt werden können abgebrochen werden, durch den Aufruf **SQLCancel** aus einem anderen Thread mit der gleichen Anweisung zu verarbeiten. Obwohl der Treiber die Verwendung von nicht serialisieren soll **SQLCancel** auf diese Weise besteht keine Garantie, dass der Aufruf **SQLCancel** die Funktion, die auf dem anderen Thread ausgeführt wird, wird tatsächlich abgebrochen.
