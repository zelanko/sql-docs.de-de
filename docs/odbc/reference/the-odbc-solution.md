---
title: Die ODBC-Lösung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC [ODBC], database access
- SQL [ODBC], database access
- database access [ODBC]
- standardizing database access [ODBC], using ODBC
ms.assetid: 34b80790-e010-4b90-8eaa-03189f5d8986
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5adf32800f4c2bc2b4a0874ca7efc22f04ffd110
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63200474"
---
# <a name="the-odbc-solution"></a>Die ODBC-Lösung
Klicken Sie dann die Frage ist wie ODBC Zugriff auf die Datenbank standardisieren? Es gibt zwei architektonische Anforderungen:  
  
-   Anwendungen müssen mehrere DBMS-Systeme mithilfe den gleiche Quellcode ohne erneute Kompilierung oder des erneuten Bindens zugreifen können.  
  
-   Anwendungen müssen mehrere DBMS gleichzeitig zugreifen können.  
  
 Und es ist eine weitere Frage, die aufgrund von Marketplace-Reality:  
  
-   Die DBMS-Funktionen sollten ODBC verfügbar machen? Nur Funktionen, die häufig auf allen DBMS oder jede Funktion, die in jeder DBMS verfügbar ist?  
  
 ODBC löst diese Probleme auf folgende Weise:  
  
-   **ODBC ist ein Call-Level-Interface.** Zur Lösung des Problems wie Anwendungen mehrere DBMS-Systeme, die mit dem gleichen Quellcode zugreifen, werden in ODBC ein standard-CLI definiert. Diese enthält alle Funktionen in die CLI-Spezifikationen von Open Group und ISO/IEC und bietet zusätzliche Funktionen, die häufig von Anwendungen benötigt werden.  
  
     Eine andere Bibliothek oder Treiber verwenden, muss für jede DBMS, die ODBC unterstützt. Der Treiber implementiert die Funktionen der ODBC-API. Um einen anderen Treiber verwenden, muss die Anwendung nicht neu kompiliert oder erneut verknüpft werden soll. Die Anwendung wird stattdessen einfach wird der neuen Treiber geladen, und der Ruft die Funktionen in es. Um mehrere DBMS gleichzeitig zugreifen zu können, lädt die Anwendung mehrere Treiber. Wie der Treiber unterstützt werden, ist betriebssystemspezifisch. Beispielsweise sind die Treiber auf dem Betriebssystem Microsoft® Windows®, Dynamic Link Libraries (DLLs).  
  
-   **ODBC definiert eine standard-SQL-Grammatik.** Zusätzlich zu einer standard Call-Level-Interface definiert ODBC eine standard-SQL-Grammatik. Diese Grammatik basiert auf der Open Group SQL CAE-Spezifikation. Unterschiede zwischen den zwei Grammatiken sind kleinere und hauptsächlich aufgrund der Unterschiede zwischen der SQL-Grammatik, die erforderlichen eingebettet werden soll, SQL (Open Group) und eine CLI (ODBC). Es gibt auch einige Erweiterungen der Grammatik gängiger Sprachfunktionen, die nicht durch die Open Group-Grammatik abgedeckt verfügbar zu machen.  
  
     Anwendungen können mithilfe von ODBC oder DBMS-spezifische Grammatik Anweisungen senden. Wenn eine Anweisung ODBC-Grammatik, die sich von DBMS-spezifische Grammatik ist verwendet, konvertiert der Treiber es vor dem Senden an die Datenquelle an. Solche Konvertierungen sind jedoch nur selten, da die meisten DBMS-Systeme bereits standard-SQL-Grammatik verwenden.  
  
-   **ODBC bietet es sich um einen Treiber-Manager zum Verwalten von gleichzeitigen Zugriffs auf mehrere DBMS.** Obwohl die Verwendung der Treiber das Problem des Zugriffs auf mehrere DBMS gleichzeitig löst, kann der erforderliche Code sieht komplex sein. Anwendungen, die entwickelt wurden, funktionieren mit allen Treibern können nicht statisch, keine Treiber verknüpft werden. Sie müssen stattdessen zur Laufzeit Laden von Treibern und rufen Sie die Funktionen in der sie über eine Tabelle von Funktionszeigern. Es wird die Situation komplexer, wenn die Anwendung mehrere Treiber gleichzeitig verwendet.  
  
     ODBC bietet, sodass jede Anwendung dazu, einen Treiber-Manager. Der Treiber-Manager alle ODBC-Funktionen – meistens als Pass-Through-Aufrufe an ODBC-Treiber - Funktionen implementiert und statisch mit der Anwendung verknüpft oder von der Anwendung zur Laufzeit geladen werden. Daher ruft die Anwendung ODBC-Funktionen anhand des Namens im Treiber-Manager und nicht durch Zeiger in jeden Treiber.  
  
     Wenn eine Anwendung einen bestimmten Treiber benötigt, fordert sie zunächst ein Verbindungshandle zur Identifizierung der Treiber und anschließend fordert an, dass der Treiber-Manager den Treiber zu laden. Der Treiber-Manager wird der Treiber geladen und die Adresse für jede Funktion in der Treiber. Zum Aufrufen einer ODBC-Funktion in der Treiber die Anwendung ruft diese Funktion im Treiber-Manager und das Verbindungshandle für den Treiber übergeben. Der Treiber-Manager ruft die Funktion klicken Sie dann mit der Adresse, die sie zuvor gespeichert.  
  
-   **ODBC-Treiber zur Unterstützung aller nicht erfordert jedoch stellt eine erhebliche Anzahl von DBMS-Funktionen.** Wenn ODBC nur Funktionen verfügbar, die gemeinsam auf allen DBMS sind gemacht, wäre es jedoch von geringem Nutzen sein. Damit viele verschiedene DBMS-Systeme heute existieren, ist der Grund schließlich, dass sie unterschiedliche Funktionen aufweisen. Wenn ODBC jedes Feature verfügbar, die in jeder DBMS verfügbar ist gemacht, wäre es unmöglich, dass der Treiber implementiert.  
  
     Stattdessen ODBC stellt eine erhebliche Anzahl von Funktionen – mehr als die von den meisten DBMS - Microsoft Intune erfordert jedoch Treiber, um nur eine Teilmenge der Funktionen zu implementieren. Treiber implementieren Sie die übrigen Funktionen nur, wenn sie von der zugrunde liegenden DBMS unterstützt werden, oder wenn sie diese emulieren möchten. Daher können Anwendungen geschrieben werden, um die Features von einer einzelnen DBMS auszunutzen, verfügbar gemacht, durch den Treiber für dieses DBMS verwaltet, verwenden Sie nur die Funktionen, die von allen DBMS verwendet oder das für die Unterstützung einer bestimmten Funktion überprüfen und entsprechend reagieren.  
  
     Damit eine Anwendung bestimmen kann, welche Treiber features und DBMS unterstützen, handelt es sich bei ODBC bietet zwei Funktionen (**SQLGetInfo** und **SQLGetFunctions**), die allgemeine Informationen zu den Treiber und das DBMS zurückgeben Funktionen und eine Liste der Funktionen der Treiber unterstützt. ODBC definiert auch-API und SQL-Grammatik-Konformitätsgrad, die große Bereiche von Funktionen, die vom Treiber unterstützt angeben. Weitere Informationen finden Sie unter [Übereinstimmungsebenen](../../odbc/reference/develop-app/conformance-levels.md).  
  
     Es ist wichtig zu beachten, dass ODBC eine allgemeine Schnittstelle für alle Funktionen definiert, die sie verfügbar macht. Aus diesem Grund werden Anwendungen funktionsspezifischen Code, nicht mit speziellen DBMS-Code enthalten und können alle Treiber, die diese Funktionen verfügbar zu machen. Ein Vorteil besteht darin, dass Anwendungen müssen nicht aktualisiert werden, wenn die von einem DBMS unterstützten Funktionen erweitert werden; Stattdessen bei der Installation eines aktualisierten Treibers verwendet die Anwendung automatisch die da der Code featurespezifische, nicht treiberspezifische oder DBMS-spezifische ist.
