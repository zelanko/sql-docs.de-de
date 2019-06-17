---
title: Interoperabilität | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC]
- interoperability [ODBC], about interoperability
ms.assetid: 43b7c849-9d59-4002-9977-9e2c8730b859
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8d5e4fbee458bec88461d3e2945a466c848d3345
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62446487"
---
# <a name="interoperability"></a>Interoperabilität
*Interoperabilität* ist die Möglichkeit einer einzelnen Anwendung mit vielen verschiedenen DBMS-Systeme ausgeführt werden. Die Notwendigkeit zum Schreiben von generischer und interoperabler Anwendungen war eines der der wichtigsten Faktoren, die Sie für die Entwicklung von ODBC. Interoperabilität ist jedoch kein einfacher Pfad, gefolgt von "nicht kompatibel" auf "vollständig interoperabel." Der Pfad enthält zahlreiche Verzweigungen, und jedes erfordert Kompromisse zwischen Funktionen, Geschwindigkeit, Codekomplexität und Zeitpunkt der Entwicklung.  
  
 Das Schreiben einer interoperablen Anwendung umfasst mehrere Schritte:  
  
1.  Entscheiden, ob die Anwendung die ODBC verwendet werden.  
  
2.  Wählen ein Maß an Interoperabilität und entscheiden, welche vor-und Nachteile zum Erreichen dieser Ebene erforderlich sind.  
  
3.  Interoperable Code schreiben, und wie möglich vollständig testen.  
  
 Es sollte beachtet werden, dass Interoperabilität in erster Linie für die Domäne der Autor der Anwendung. Treiber dienen zum Arbeiten mit einem einzelnen DBMS und per Definition können nicht zusammen. Sie spielen eine Rolle in der Interoperabilität von richtig zu implementieren und Verfügbarmachen von ODBC über eine einzelne DBMS.  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Ist ODBC die Antwort?](../../../odbc/reference/develop-app/is-odbc-the-answer.md)  
  
-   [Auswählen einer Ebene der Interoperabilität](../../../odbc/reference/develop-app/choosing-a-level-of-interoperability.md)  
  
-   [Ermitteln der Ziel-DBMS und Zieltreiber](../../../odbc/reference/develop-app/determining-the-target-dbmss-and-drivers.md)  
  
-   [Erwägen der zu verwendenden Datenbankfunktionen](../../../odbc/reference/develop-app/considering-database-features-to-use.md)  
  
-   [Länge des Produktzyklus](../../../odbc/reference/develop-app/length-of-the-product-cycle.md)  
  
-   [Schreiben einer interoperablen Anwendung](../../../odbc/reference/develop-app/writing-an-interoperable-application.md)  
  
-   [Testen von interoperablen Anwendungen](../../../odbc/reference/develop-app/testing-interoperable-applications.md)
