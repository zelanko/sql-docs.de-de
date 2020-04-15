---
title: Die ODBC-Lösung | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2b35883ff4d621f0ecc092020ad744455281dd63
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81286753"
---
# <a name="the-odbc-solution"></a>Die ODBC-Lösung
Die Frage ist also, wie ODBC den Datenbankzugriff standardisiert? Es gibt zwei architektonische Anforderungen:  
  
-   Anwendungen müssen mit demselben Quellcode auf mehrere DBMS zugreifen können, ohne erneut zu kompilieren oder neu zu verknüpfen.  
  
-   Anwendungen müssen gleichzeitig auf mehrere DBMS zugreifen können.  
  
 Und es gibt noch eine Frage, aufgrund der Marktrealität:  
  
-   Welche DBMS-Funktionen sollte ODBC verfügbar machen? Nur Funktionen, die allen DBMS gemeinsam sind, oder eines Features, das in einem DBMS verfügbar ist?  
  
 ODBC löst diese Probleme auf folgende Weise:  
  
-   **ODBC ist eine Schnittstelle auf Aufrufebene.** Um das Problem zu lösen, wie Anwendungen mit demselben Quellcode auf mehrere DBMS zugreifen, definiert ODBC eine Standard-CLI. Dies enthält alle Funktionen in den CLI-Spezifikationen von Open Group und ISO/IEC und bietet zusätzliche Funktionen, die häufig von Anwendungen benötigt werden.  
  
     Für jedes DBMS, das ODBC unterstützt, ist eine andere Bibliothek oder ein anderer Treiber erforderlich. Der Treiber implementiert die Funktionen in der ODBC-API. Um einen anderen Treiber verwenden zu können, muss die Anwendung nicht neu kompiliert oder neu verknüpft werden. Stattdessen lädt die Anwendung einfach den neuen Treiber und ruft die darin eingebauten Funktionen auf. Um gleichzeitig auf mehrere DBMS zuzugreifen, lädt die Anwendung mehrere Treiber. Die Unterstützung von Treibern ist betriebssystemspezifisch. Auf dem Betriebssystem Microsoft® Windows® sind Treiber beispielsweise DLLs (Dynamic Link Libraries).  
  
-   **ODBC definiert eine SQL-Standardgrammatik.** Zusätzlich zu einer Standardschnittstelle auf Aufrufebene definiert ODBC eine Standard-SQL-Grammatik. Diese Grammatik basiert auf der Open Group SQL CAE-Spezifikation. Die Unterschiede zwischen den beiden Grammatiken sind geringfügig und in erster Linie auf die Unterschiede zwischen der SQL-Grammatik, die von embedded SQL (Open Group) und einer CLI (ODBC) benötigt wird. Es gibt auch einige Erweiterungen der Grammatik, um allgemein verfügbare Sprachfeatures verfügbar zu machen, die nicht von der Open Group-Grammatik abgedeckt werden.  
  
     Anwendungen können Anweisungen mit ODBC- oder DBMS-spezifischer Grammatik übermitteln. Wenn eine Anweisung eine ODBC-Grammatik verwendet, die sich von der DBMS-spezifischen Grammatik unterscheidet, konvertiert der Treiber sie, bevor sie an die Datenquelle gesendet wird. Solche Konvertierungen sind jedoch selten, da die meisten DBMS bereits Standard-SQL-Grammatik verwenden.  
  
-   **ODBC stellt einen Treiber-Manager zur Verfügung, um den gleichzeitigen Zugriff auf mehrere DBMS zu verwalten.** Obwohl die Verwendung von Treibern das Problem des gleichzeitigen Zugriffs auf mehrere DBMS löst, kann der Code dazu komplex sein. Anwendungen, die für die Arbeit mit allen Treibern entwickelt wurden, können nicht statisch mit Treibern verknüpft werden. Stattdessen müssen sie Treiber zur Laufzeit laden und die darin eingebauten Funktionen über eine Tabelle mit Funktionszeigern aufrufen. Die Situation wird komplexer, wenn die Anwendung mehrere Treiber gleichzeitig verwendet.  
  
     Anstatt jede Anwendung dazu zu zwingen, stellt ODBC einen Treiber-Manager bereit. Der Treiber-Manager implementiert alle ODBC-Funktionen - meist als Pass-Through-Aufrufe an ODBC-Funktionen in Treibern - und ist statisch mit der Anwendung verknüpft oder zur Laufzeit von der Anwendung geladen. Daher ruft die Anwendung ODBC-Funktionen mit Namen im Treiber-Manager auf und nicht per Zeiger in jedem Treiber.  
  
     Wenn eine Anwendung einen bestimmten Treiber benötigt, fordert sie zunächst ein Verbindungshandle an, mit dem der Treiber identifiziert werden soll, und fordert dann an, dass der Treiber-Manager den Treiber lädt. Der Treiber-Manager lädt den Treiber und speichert die Adresse jeder Funktion im Treiber. Um eine ODBC-Funktion im Treiber aufzurufen, ruft die Anwendung diese Funktion im Treiber-Manager auf und übergibt das Verbindungshandle für den Treiber. Der Treiber-Manager ruft dann die Funktion auf, indem er die zuvor gespeicherte Adresse verwendet.  
  
-   **ODBC macht eine erhebliche Anzahl von DBMS-Funktionen verfügbar, erfordert jedoch keine Treiber, die sie alle unterstützen.** Wenn ODBC nur Features verfügbar gemacht, die allen DBMS gemeinsam sind, würde dies wenig nützen. Schließlich gibt es heute so viele verschiedene DBMS, weil sie unterschiedliche Eigenschaften haben. Wenn ODBC jedes Feature verfügbar macht, das in jedem DBMS verfügbar ist, wäre es für Treiber unmöglich zu implementieren.  
  
     Stattdessen macht ODBC eine erhebliche Anzahl von Features verfügbar - mehr als von den meisten DBMS unterstützt werden -, erfordert jedoch, dass Treiber nur eine Teilmenge dieser Features implementieren. Treiber implementieren die verbleibenden Features nur, wenn sie vom zugrunde liegenden DBMS unterstützt werden oder wenn sie sie emulieren möchten. So können Anwendungen geschrieben werden, um die Funktionen eines einzelnen DBMS zu nutzen, wie sie vom Treiber für dieses DBMS verfügbar gemacht werden, nur die Funktionen zu verwenden, die von allen DBMS verwendet werden, oder um die Unterstützung eines bestimmten Features zu überprüfen und entsprechend zu reagieren.  
  
     Damit eine Anwendung bestimmen kann, welche Funktionen ein Treiber und EINE DBMS-Unterstützung sind, stellt ODBC zwei Funktionen bereit (**SQLGetInfo** und **SQLGetFunctions**), die allgemeine Informationen über den Treiber und die DBMS-Funktionen sowie eine Liste der vom Treiber unterstützten Funktionen zurückgeben. ODBC definiert auch API- und SQL-Grammatikkonformitätsebenen, die große Bereiche von Features angeben, die vom Treiber unterstützt werden. Weitere Informationen finden Sie unter [Konformitätsstufen](../../odbc/reference/develop-app/conformance-levels.md).  
  
     Es ist wichtig, sich daran zu erinnern, dass ODBC eine gemeinsame Schnittstelle für alle Features definiert, die es verfügbar macht. Aus diesem Grund enthalten Anwendungen funktionsspezifischen Code, nicht DBMS-spezifischen Code, und können alle Treiber verwenden, die diese Features verfügbar machen. Ein Vorteil besteht darin, dass Anwendungen nicht aktualisiert werden müssen, wenn die von einem DBMS unterstützten Funktionen verbessert werden. Wenn stattdessen ein aktualisierter Treiber installiert wird, verwendet die Anwendung die Features automatisch, da ihr Code funktions- und nicht treiberspezifisch oder DBMS-spezifisch ist.
