---
description: Erwägen der zu verwendenden Datenbankfunktionen
title: Berücksichtigen der zu verwendenden Datenbankfunktionen | Microsoft-Dokumentation
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
ms.openlocfilehash: 2abaed3806514a161c5c506d8bad89b4d3b75153
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88465892"
---
# <a name="considering-database-features-to-use"></a>Erwägen der zu verwendenden Datenbankfunktionen
Nachdem der grundlegende Grad an Interoperabilität bekannt ist, müssen die von der Anwendung verwendeten Datenbankfunktionen berücksichtigt werden. Welche SQL-Anweisungen werden z. b. von der Anwendung ausgeführt? Verwendet die Anwendung scrollbare Cursor? Handel? Abläufen? Lange Daten? Ideen zu den Funktionen, die möglicherweise nicht von allen DBMSs unterstützt werden, finden Sie in den Beschreibungen der Funktionen [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md), [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)und [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md) und [Anhang C: SQL-Grammatik](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md). Die von einer Anwendung benötigten Features können einige DBMSs aus der Liste der Ziel-DBMSs entfernen. Sie können auch anzeigen, dass die Anwendung auf einfache Weise viele DBMSs als Ziel hat.  
  
 Wenn die erforderlichen Features z. b. einfach sind, können Sie in der Regel mit einem hohen Grad an Interoperabilität implementiert werden. Eine Anwendung, die eine einfache **Select** -Anweisung ausführt und Ergebnisse mit einem Vorwärts Cursor abruft, ist wahrscheinlich aufgrund ihrer Einfachheit sehr interoperabel: fast alle Treiber und DBMSs unterstützen die erforderliche Funktionalität.  
  
 Wenn die erforderlichen Funktionen jedoch komplexer sind, wie z. b. scrollfähige Cursor, positionierte UPDATE-und DELETE-Anweisungen und Prozeduren, müssen häufig Kompromisse ausgelöst werden. Es gibt mehrere Möglichkeiten:  
  
-   **Geringere Interoperabilität, weitere Features.** Die Anwendung umfasst die Features, funktioniert aber nur mit DBMSs, die Sie unterstützen.  
  
-   **Höhere Interoperabilität, weniger Features.** Die Anwendung löscht die Features, funktioniert jedoch mit mehr DBMSs.  
  
-   **Höhere Interoperabilität, optionale Features.** Die Anwendung umfasst die Features, stellt Sie jedoch nur mit den DBMSs zur Verfügung, die Sie unterstützen.  
  
-   **Höhere Interoperabilität, weitere Features.** Die Anwendung verwendet die Features mit DBMSs, die Sie unterstützen, und emuliert Sie für DBMSs, die dies nicht tun.  
  
 Die ersten beiden Fälle sind relativ einfach zu implementieren, da die Features entweder mit allen unterstützten DBMSs oder mit None verwendet werden. Die beiden letztgenannten Fälle sind hingegen komplexer. Es ist in beiden Fällen notwendig, zu überprüfen, ob das DBMS die Features unterstützt, und im letzten Fall, um eine potenziell große Menge Code zu schreiben, um diese Features zu emulieren. Diese Schemas erfordern daher wahrscheinlich mehr Entwicklungszeit und sind möglicherweise zur Laufzeit langsamer.  
  
 Stellen Sie sich eine generische Abfrageanwendung vor, die eine Verbindung mit einer einzelnen Datenquelle herstellen kann. Die Anwendung akzeptiert eine Abfrage vom Benutzer und zeigt die Ergebnisse in einem Fenster an. Angenommen, diese Anwendung verfügt über eine Funktion, die es Benutzern ermöglicht, die Ergebnisse mehrerer Abfragen gleichzeitig anzuzeigen. Das heißt, Sie können eine Abfrage ausführen und einige der Ergebnisse überprüfen, eine andere Abfrage ausführen und die Ergebnisse überprüfen und dann zur ersten Abfrage zurückkehren. Dies stellt ein Interoperabilitäts Problem dar, da einige Treiber nur eine einzige aktive Anweisung unterstützen.  
  
 Die Anwendung verfügt über eine Reihe von Optionen, die darauf basieren, was der Treiber für die SQL_MAX_CONCURRENT_ACTIVITIES-Option in **SQLGetInfo**zurückgibt:  
  
-   **Mehrere Abfragen werden immer unterstützt.** Nachdem eine Verbindung mit einem Treiber hergestellt wurde, überprüft die Anwendung die Anzahl der aktiven Anweisungen. Wenn der Treiber nur eine aktive Anweisung unterstützt, schließt die Anwendung die Verbindung und informiert den Benutzer darüber, dass der Treiber die erforderliche Funktionalität nicht unterstützt. Die Anwendung ist einfach zu implementieren und verfügt über eine vollständige Funktionalität, aber eine geringere Interoperabilität.  
  
-   **Mehrere Abfragen werden nie unterstützt.** Die Anwendung löscht das Feature vollständig. Es ist einfach zu implementieren und verfügt über eine hohe Interoperabilität, verfügt aber über weniger Funktionalität.  
  
-   **Unterstützen Sie mehrere Abfragen nur, wenn der Treiber dies tut.** Nachdem eine Verbindung mit einem Treiber hergestellt wurde, überprüft die Anwendung die Anzahl der aktiven Anweisungen. Die Anwendung ermöglicht dem Benutzer, eine neue Anweisung zu starten, wenn eine bereits aktive Anweisung ist, wenn der Treiber mehrere aktive Anweisungen unterstützt. Die Anwendung verfügt über eine höhere Funktionalität und Interoperabilität, ist jedoch schwieriger zu implementieren.  
  
-   **Unterstützen Sie immer mehrere Abfragen und emulieren Sie bei Bedarf.** Nachdem eine Verbindung mit einem Treiber hergestellt wurde, überprüft die Anwendung die Anzahl der aktiven Anweisungen. Die Anwendung ermöglicht dem Benutzer immer, eine neue Anweisung zu starten, wenn eine bereits aktiv ist. Wenn der Treiber nur eine aktive Anweisung unterstützt, öffnet die Anwendung eine zusätzliche Verbindung mit diesem Treiber und führt die neue Anweisung für diese Verbindung aus. Die Anwendung verfügt über vollständige Funktionalität und hohe Interoperabilität, ist jedoch schwieriger zu implementieren.
