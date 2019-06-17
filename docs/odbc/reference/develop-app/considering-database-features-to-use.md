---
title: Erwägen die zu verwendenden Datenbankfunktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], database features
ms.assetid: 59760114-508e-46c5-81d2-8f2498c0d778
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b92eeb64b95d666b15c03c70d656d2309a63eabf
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63042186"
---
# <a name="considering-database-features-to-use"></a>Erwägen der zu verwendenden Datenbankfunktionen
Nachdem das grundlegende Maß an Interoperabilität bekannt ist, müssen die von der Anwendung verwendeten Funktionen der Datenbank berücksichtigt werden. Werden die Anwendung wird z. B. welche SQL-Anweisungen ausgeführt? Verwendet die Anwendung scrollfähige Cursor? Transaktionen? Verfahren? Long-Daten? Weitere Ideen darüber, welche Funktionen möglicherweise nicht von allen DBMS unterstützt wird, finden Sie unter den [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md), [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md), und [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md) Beschreibungen der Funktionen und [ Anhang C: SQL-Grammatik](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md). Die Funktionen, die von einer Anwendung benötigt möglicherweise einige DBMS-Systeme in der Liste der Ziel-DBMS vermieden. Sie können auch zeigen, dass die Anwendung viele Datenbankmanagementsysteme problemlos ausgeführt werden kann.  
  
 Z. B. wenn die erforderlichen Features einfach sind, können sie in der Regel mit einem hohen Grad an Interoperabilität implementiert werden. Eine Anwendung, die eine einfache führt **wählen** -Anweisung und ruft Ergebnisse mit einem Vorwärtscursor ist wahrscheinlich aufgrund seiner Einfachheit hochgradig interoperabel sein: Fast alle Treiber und DBMS-Systeme unterstützen die benötigten Funktionen.  
  
 Aber wenn die erforderlichen Features komplexer sein, z. B. scrollfähige Cursor, positioniertes Update und Delete-Anweisungen und Prozeduren sind, müssen vor-und Nachteile häufig vorgenommen werden. Es gibt mehrere Möglichkeiten:  
  
-   **Niedrigere Interoperabilität, mehr Funktionen.** Die Anwendung umfasst die Funktionen, aber funktioniert nur mit DBMS-Systeme, die sie unterstützen.  
  
-   **Höhere Interoperabilität, weniger Funktionen.** Die Anwendung fällt die Funktionen, aber funktioniert mit Weitere DBMS.  
  
-   **Höhere Interoperabilität, optionalen Features.** Die Anwendung umfasst die Funktionen jedoch nur für die DBMS-Systeme, die sie unterstützen Verfügung stellt.  
  
-   **Höhere Interoperabilität, mehr Funktionen.** Die Anwendung verwendet die Funktionen mit DBMS-Systeme, die sie unterstützen, und sie für die DBMS-Systeme, die nicht emuliert.  
  
 Die ersten beiden Fälle sind relativ einfach zu implementieren, da die Funktionen mit allen unterstützten DBMS oder mit keiner verwendet werden. Die beiden letztgenannten Fällen sind andererseits, komplexer. Es ist erforderlich, in beiden Fällen zu überprüfen, ob das DBMS die Funktionen unterstützt und im letzten Fall schreiben Sie eine potenziell große Menge an Code, um diese Funktionen emulieren. Diese Schemas wird daher wahrscheinlich Weitere Entwicklungszeit erfordern und zur Laufzeit möglicherweise langsamer.  
  
 Betrachten Sie eine generische Abfragen, die mit einer einzelnen Datenquelle verbinden können. Die Anwendung akzeptiert eine Abfrage des Benutzers und zeigt die Ergebnisse in einem Fenster. Jetzt nehmen wir an diese Anwendung verfügt über eine Funktion, die Benutzern ermöglicht, die Ergebnisse anzuzeigen abgefragt, mehrere gleichzeitig. D. h. können sie Ausführen einer Abfrage und sehen Sie sich einige der Ergebnisse, führen Sie eine andere Abfrage sehen Sie sich einige Ergebnisse des und dann an die erste Abfrage zurück. Dies stellt einen Interoperabilitätsfehler im Zusammenhang, da einige Treiber nur eine einzelne aktive Anweisung unterstützt.  
  
 Die Anwendung hat eine Reihe von Optionen, die basierend auf was der Treiber für die Option SQL_MAX_CONCURRENT_ACTIVITIES in gibt **SQLGetInfo**:  
  
-   **Immer unterstützt mehrere Abfragen.** Nach dem Herstellen einer Verbindung zu einem Treiber, überprüft die Anwendung die Anzahl aktiver Anweisungen an. Wenn der Treiber nur eine aktive Anweisung unterstützt, wird die Anwendung schließt die Verbindung und der Benutzer wird informiert, dass der Treiber nicht die erforderlichen Funktionen unterstützt. Die Anwendung ist einfach zu implementieren und verfügt über die vollständige Funktionalität jedoch niedriger Interoperabilität hat.  
  
-   **Unterstützen Sie nicht mehrere Abfragen.** Das Feature wird von die Anwendung vollständig gelöscht. Es ist einfach zu implementieren und hohe Interoperabilität ist jedoch weniger Funktionen verfügt.  
  
-   **Unterstützen Sie mehrere Abfragen, nur dann, wenn der Treiber führt.** Nach dem Herstellen einer Verbindung zu einem Treiber, überprüft die Anwendung die Anzahl aktiver Anweisungen an. Die Anwendung ermöglicht den Benutzer eine neue Anweisung gestartet wird, wenn eine bereits nur aktiviert ist, wenn der Treiber mehrere aktive Anweisungen unterstützt. Die Anwendung verfügt über höhere Funktionalität und Interoperabilität, aber es ist schwieriger zu implementieren.  
  
-   **Immer unterstützen Sie mehrere Abfragen, und emulieren sie bei Bedarf zu.** Nach dem Herstellen einer Verbindung zu einem Treiber, überprüft die Anwendung die Anzahl aktiver Anweisungen an. Die Anwendung immer ermöglicht den Benutzer eine neue Anweisung gestartet wird, wenn eine bereits aktiv ist. Wenn der Treiber nur eine aktive Anweisung unterstützt, wird die Anwendung eine zusätzliche Verbindung zu diesen Treiber geöffnet, und führt die neue Anweisung für diese Verbindung. Die Anwendung verfügt über vollständige Funktionalität und hohe Interoperabilität, aber es ist schwieriger zu implementieren.
