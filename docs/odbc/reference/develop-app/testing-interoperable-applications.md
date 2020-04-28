---
title: Testen von interoperablen Anwendungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], testing interoperable applications
- testing interoperable applications [ODBC]
ms.assetid: 489083cb-8430-40be-9ef2-d75b9a2eea88
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c1d43c7aad2501591c497475f6c250ac33712aa7
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81307741"
---
# <a name="testing-interoperable-applications"></a>Testen von interoperablen Anwendungen
Das Testen von interoperablen Anwendungen ist am besten ein zeitaufwändiges Geschäft und im schlimmsten Fall nicht möglich, da neue Treiber ständig auf dem Markt erscheinen. Es ist jedoch ein angemessener Grad an Tests möglich. Anwendungen mit eingeschränkter oder niedriger Interoperabilität müssen nur mit den Treibern getestet werden, die Sie unterstützen. Allerdings müssen Sie für diese Treiber vollständig getestet werden.  
  
 Hochgradig interoperable Anwendungen können nicht praktisch für alle Treiber getestet werden. Die meisten Anwendungsentwickler können dies tun, indem Sie sie vollständig mit einer kleinen Anzahl von Treibern testen und sich mit mehreren weiteren Treibern in einigen weiteren Fällen durchführen. Getestete Treiber sollten die beliebtesten Treiber für den beliebtesten DBMSs auf dem Markt der Anwendung enthalten. Wenn der Markt alle DBMSs abdeckt, sollten Treiber für Desktop-und Server-DBMSs getestet werden.  
  
 Eines der Probleme beim Testen von ODBC-Anwendungen ist die Anzahl der beteiligten Komponenten: die Anwendung selbst, der Treiber-Manager, der Treiber, das DBMS und möglicherweise Netzwerk Software oder Gateways. Anwendungen können das Nachverfolgen von Fehlern vereinfachen, indem Sie die Fehlermeldungen, die von ODBC-Funktionen zurückgegeben werden, über **SQLGetDiagField** und **SQLGetDiagRec**veröffentlichen. Diese Nachrichten identifizieren den Hersteller und die Komponente, in denen Fehler auftreten. Weitere Informationen finden Sie unter [Diagnostics](../../../odbc/reference/develop-app/diagnostics.md).
