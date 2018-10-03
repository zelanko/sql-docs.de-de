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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 509dd17efeeb982c51938d7a18fad99a2e84ba5b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47794178"
---
# <a name="testing-interoperable-applications"></a>Testen von interoperablen Anwendungen
Testen von interoperablen Anwendungen ist bestenfalls ein zeitraubender Geschäfts- und im schlimmsten Fall nicht möglich, da auf dem Markt ständig neue Treiber angezeigt werden. Eine angemessene Maß an Tests ist jedoch möglich. Anwendungen mit niedrigen darf maximal Interoperabilität müssen nur für Treiber getestet werden, die sie unterstützen garantiert. Sie müssen jedoch vollständig für diese Treiber getestet werden.  
  
 Hochgradig interoperabel Anwendungen können nicht für alle Treiber praktisch getestet werden. Am besten geeignet, die meisten Anwendungsentwickler durchführen können, ist vollständig für eine kleine Anzahl von Treibern und cursorily für einige weitere Test. Getestete Treiber sollte die am häufigsten verwendeten Treiber für die am häufigsten verwendeten DBMS in der Anwendung Markt sind: Wenn der Markt allen DBMS behandelt, sollten die Treiber für Desktop- und Server-DBMS getestet werden.  
  
 Eines der Probleme beim Testen der ODBC-Anwendungen ist die Anzahl von Komponenten beteiligt: die Anwendung selbst, der Treiber-Manager, der Treiber, die DBMS und möglicherweise Netzwerksoftware oder Gateways. Anwendungen können sie leichter zu Fehlern zu verfolgen, indem Sie senden die Fehlermeldungen, die von ODBC-Funktionen über **SQLGetDiagField** und **SQLGetDiagRec**. Diese Nachrichten identifizieren, den Hersteller und die Komponente, in denen Fehler auftreten. Weitere Informationen finden Sie unter [Diagnose](../../../odbc/reference/develop-app/diagnostics.md).
