---
title: Berücksichtigen von datenbankfeatures, die verwendet werden sollen | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a9d966781def1c3eab6a9568eab07ab591326171
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299010"
---
# <a name="considering-database-features-to-use"></a>Erwägen der zu verwendenden Datenbankfunktionen
Nachdem die grundlegende Ebene der Interoperabilität bekannt ist, müssen die von der Anwendung verwendeten Datenbankfeatures berücksichtigt werden. Welche SQL-Anweisungen wird die Anwendung z. B. ausführen? Wird die Anwendung scrollbare Cursor verwenden? Transaktionen? Verfahren? Lange Daten? Ideen darüber, welche Features möglicherweise nicht von allen DBMS unterstützt werden, finden Sie in den Funktionsbeschreibungen [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md), [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)und [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md) sowie [In Anhang C: SQL Grammar](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md). Die von einer Anwendung benötigten Funktionen können einige DBMS aus der Liste der Ziel-DBMS entfernen. Sie können auch zeigen, dass die Anwendung leicht auf viele DBMS abzielen kann.  
  
 Wenn die erforderlichen Funktionen beispielsweise einfach sind, können sie in der Regel mit einem hohen Maß an Interoperabilität implementiert werden. Eine Anwendung, die eine einfache **SELECT-Anweisung** ausführt und Ergebnisse mit einem Vorwärts-Cursor abruft, ist aufgrund ihrer Einfachheit wahrscheinlich sehr interoperabel: Fast alle Treiber und DBMS unterstützen die erforderliche Funktionalität.  
  
 Wenn die erforderlichen Features jedoch komplexer sind, z. B. scrollbare Cursor, positionierte Aktualisierungs- und Löschanweisungen und Prozeduren, müssen häufig Kompromisse vorgenommen werden. Es gibt mehrere Möglichkeiten:  
  
-   **Geringere Interoperabilität, mehr Funktionen.** Die Anwendung enthält die Funktionen, funktioniert aber nur mit DBMS, die sie unterstützen.  
  
-   **Höhere Interoperabilität, weniger Funktionen.** Die Anwendung löscht die Funktionen, funktioniert aber mit mehr DBMS.  
  
-   **Höhere Interoperabilität, optionale Funktionen.** Die Anwendung enthält die Funktionen, stellt sie jedoch nur mit den DBMS zur Verfügung, die sie unterstützen.  
  
-   **Höhere Interoperabilität, mehr Funktionen.** Die Anwendung verwendet die Features mit DBMS, die sie unterstützen und emuliert sie für DBMS, die dies nicht tun.  
  
 Die ersten beiden Fälle sind relativ einfach zu implementieren, da die Features entweder mit allen unterstützten DBMS oder mit keinem verwendet werden. Die beiden letztgenannten Fälle sind dagegen komplexer. In beiden Fällen muss überprüft werden, ob das DBMS die Features unterstützt, und im letzten Fall eine potenziell große Menge an Code schreiben, um diese Features zu emulieren. Daher erfordern diese Systeme wahrscheinlich mehr Entwicklungszeit und können zur Laufzeit langsamer sein.  
  
 Betrachten Sie eine generische Abfrageanwendung, die eine Verbindung mit einer einzelnen Datenquelle herstellen kann. Die Anwendung akzeptiert eine Abfrage des Benutzers und zeigt die Ergebnisse in einem Fenster an. Angenommen, diese Anwendung verfügt über eine Funktion, mit der Benutzer die Ergebnisse mehrerer Abfragen gleichzeitig anzeigen können. Das heißt, sie können eine Abfrage ausführen und einige der Ergebnisse betrachten, eine andere Abfrage ausführen und einige ihrer Ergebnisse betrachten und dann zur ersten Abfrage zurückkehren. Dies stellt ein Interoperabilitätsproblem dar, da einige Treiber nur eine einzelne aktive Anweisung unterstützen.  
  
 Die Anwendung hat eine Reihe von Optionen, basierend auf dem, was der Treiber für die SQL_MAX_CONCURRENT_ACTIVITIES Option in **SQLGetInfo**zurückgibt:  
  
-   **Unterstützen Sie immer mehrere Abfragen.** Nach dem Herstellen einer Verbindung mit einem Treiber überprüft die Anwendung die Anzahl der aktiven Anweisungen. Wenn der Treiber nur eine aktive Anweisung unterstützt, schließt die Anwendung die Verbindung und informiert den Benutzer, dass der Treiber die erforderliche Funktionalität nicht unterstützt. Die Anwendung ist einfach zu implementieren und verfügt über volle Funktionalität, weist jedoch eine geringere Interoperabilität auf.  
  
-   **Unterstützen Sie niemals mehrere Abfragen.** Die Anwendung löscht die Funktion vollständig. Es ist einfach zu implementieren und verfügt über eine hohe Interoperabilität, verfügt aber über weniger Funktionalität.  
  
-   **Unterstützen Sie mehrere Abfragen nur, wenn der Treiber dies tut.** Nach dem Herstellen einer Verbindung mit einem Treiber überprüft die Anwendung die Anzahl der aktiven Anweisungen. Die Anwendung ermöglicht es dem Benutzer, eine neue Anweisung zu starten, wenn eine nur aktiv ist, wenn der Treiber mehrere aktive Anweisungen unterstützt. Die Anwendung verfügt über eine höhere Funktionalität und Interoperabilität, ist jedoch schwieriger zu implementieren.  
  
-   **Unterstützen Sie immer mehrere Abfragen und emulieren Sie sie bei Bedarf.** Nach dem Herstellen einer Verbindung mit einem Treiber überprüft die Anwendung die Anzahl der aktiven Anweisungen. Die Anwendung ermöglicht es dem Benutzer immer, eine neue Anweisung zu starten, wenn eine bereits aktiv ist. Wenn der Treiber nur eine aktive Anweisung unterstützt, öffnet die Anwendung eine zusätzliche Verbindung zu diesem Treiber und führt die neue Anweisung für diese Verbindung aus. Die Anwendung verfügt über volle Funktionalität und hohe Interoperabilität, ist jedoch schwieriger zu implementieren.
