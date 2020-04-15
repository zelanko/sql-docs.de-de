---
title: Testen von interoperablen Anwendungen | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307741"
---
# <a name="testing-interoperable-applications"></a>Testen von interoperablen Anwendungen
Das Testen interoperabler Anwendungen ist bestenfalls ein zeitaufwändiges Geschäft und schlimmstenfalls unmöglich, da ständig neue Treiber auf dem Markt erscheinen. Ein angemessenes Prüfmaß ist jedoch möglich. Anwendungen mit eingeschränkter oder geringer Interoperabilität müssen nur anhand der Treiber getestet werden, die sie garantiert unterstützen. Sie müssen jedoch vollständig gegen diese Treiber getestet werden.  
  
 Hochinteroperabilitätsanwendungen können nicht praktisch an allen Treibern getestet werden. Das Beste, was die meisten Anwendungsentwickler tun können, ist, sie vollständig gegen eine kleine Anzahl von Treibern und cursorig gegen mehrere weitere zu testen. Getestete Treiber sollten die beliebtesten Treiber für die beliebtesten DBMS auf dem Markt der Anwendung enthalten. Wenn der Markt alle DBMS abdeckt, sollten Treiber für Desktop- und Server-DBMS getestet werden.  
  
 Eines der Probleme beim Testen von ODBC-Anwendungen ist die Anzahl der beteiligten Komponenten: die Anwendung selbst, der Treiber-Manager, der Treiber, das DBMS und möglicherweise Netzwerksoftware oder Gateways. Anwendungen können das Nachverfolgen von Fehlern vereinfachen, indem sie die von ODBC-Funktionen zurückgegebenen Fehlermeldungen über **SQLGetDiagField** und **SQLGetDiagRec**veröffentlichen. Diese Meldungen identifizieren den Hersteller und die Komponente, in der Fehler auftreten. Weitere Informationen finden Sie unter [Diagnose](../../../odbc/reference/develop-app/diagnostics.md).
