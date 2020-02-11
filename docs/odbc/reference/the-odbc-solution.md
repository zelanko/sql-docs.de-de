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
ms.openlocfilehash: e6992e084c210cea1b95157744addfd40180fccb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68039339"
---
# <a name="the-odbc-solution"></a>Die ODBC-Lösung
Die Frage ist dann, wie kann ODBC den Datenbankzugriff standardisieren? Es gibt zwei architektonische Anforderungen:  
  
-   Anwendungen müssen in der Lage sein, auf mehrere DBMSs zuzugreifen, indem Sie denselben Quellcode verwenden, ohne neu kompilieren oder neu verknüpfen zu müssen.  
  
-   Anwendungen müssen gleichzeitig auf mehrere DBMSs zugreifen können.  
  
 Und aufgrund der Marketplace-Realität gibt es eine weitere Frage:  
  
-   Welche DBMS-Features sollten von ODBC verfügbar gemacht werden? Nur Features, die für alle DBMSs oder alle Features gelten, die in einem beliebigen DBMS verfügbar sind?  
  
 ODBC löst diese Probleme wie folgt:  
  
-   **ODBC ist eine Schnittstelle auf Aufrufebene.** Um das Problem zu lösen, wie Anwendungen mithilfe desselben Quellcodes auf mehrere DBMSs zugreifen, definiert ODBC eine Standard-CLI. Diese enthält alle Funktionen in den CLI-Spezifikationen von Open Group und ISO/IEC und stellt zusätzliche Funktionen bereit, die häufig von Anwendungen benötigt werden.  
  
     Eine andere Bibliothek bzw. ein anderer Treiber ist für jedes DBMS erforderlich, das ODBC unterstützt. Der Treiber implementiert die Funktionen in der ODBC-API. Um einen anderen Treiber zu verwenden, muss die Anwendung nicht neu kompiliert oder erneut verknüpft werden. Stattdessen lädt die Anwendung einfach den neuen Treiber und ruft die darin aufgerufenen Funktionen auf. Um gleichzeitig auf mehrere DBMSs zuzugreifen, lädt die Anwendung mehrere Treiber. Unterstützte Treiber sind betriebssystemspezifisch. Beispielsweise handelt es sich bei den Treibern auf dem Betriebssystem Microsoft® Windows® um DLLs (Dynamic-Link Libraries).  
  
-   **ODBC definiert eine Standard-SQL-Grammatik.** Zusätzlich zu einer Standardschnittstelle auf der callsebene definiert ODBC eine Standard-SQL-Grammatik. Diese Grammatik basiert auf der SQL-CAE-Spezifikation für Open Group. Unterschiede zwischen den beiden Grammatiken sind geringfügig und in erster Linie aufgrund der Unterschiede zwischen der SQL-Grammatik, die von eingebetteten SQL-(Open Group) und einer CLI (ODBC) benötigt wird. Es gibt auch einige Erweiterungen der Grammatik, um häufig verfügbare sprach Features verfügbar zu machen, die nicht von der Open Group-Grammatik abgedeckt werden.  
  
     Anwendungen können mithilfe der ODBC-oder DBMS-spezifischen Grammatik Anweisungen übermitteln. Wenn eine Anweisung ODBC-Grammatik verwendet, die sich von der DBMS-spezifischen Grammatik unterscheidet, konvertiert der Treiber Sie, bevor Sie an die Datenquelle gesendet wird. Solche Konvertierungen sind jedoch selten, da die meisten DBMSs bereits standardmäßige SQL-Grammatik verwenden.  
  
-   **ODBC bietet einen Treiber-Manager zum Verwalten des gleichzeitigen Zugriffs auf mehrere DBMSs.** Obwohl die Verwendung von Treibern das Problem des gleichzeitigen Zugriffs auf mehrere DBMSs löst, kann der Code dafür komplex sein. Anwendungen, die für die Arbeit mit allen Treibern entwickelt wurden, können nicht statisch mit Treibern verknüpft werden. Stattdessen müssen Sie Treiber zur Laufzeit laden und die darin genannten Funktionen über eine Tabelle von Funktions Zeigern abrufen. Die Situation wird komplexer, wenn die Anwendung mehrere Treiber gleichzeitig verwendet.  
  
     ODBC stellt einen Treiber-Manager bereit, anstatt jede Anwendung zu erzwingen. Der Treiber-Manager implementiert alle ODBC-Funktionen (größtenteils als Pass-Through-Aufrufe von ODBC-Funktionen in Treibern) und ist statisch mit der Anwendung verknüpft oder von der Anwendung zur Laufzeit geladen. Daher ruft die Anwendung ODBC-Funktionen im Treiber-Manager im Treiber-Manager und nicht in einem Zeiger in jedem Treiber auf.  
  
     Wenn eine Anwendung einen bestimmten Treiber benötigt, fordert Sie zuerst ein Verbindungs Handle zum Identifizieren des Treibers an und fordert dann an, dass der Treiber-Manager den Treiber lädt. Der Treiber-Manager lädt den Treiber und speichert die Adresse der einzelnen Funktionen des Treibers. Um eine ODBC-Funktion im Treiber aufzurufen, ruft die Anwendung diese Funktion im Treiber-Manager auf und übergibt das Verbindungs Handle für den Treiber. Der Treiber-Manager ruft dann die Funktion mithilfe der zuvor gespeicherten Adresse auf.  
  
-   **ODBC stellt eine beträchtliche Anzahl von DBMS-Features zur Verfügung, erfordert jedoch keine Treiber, um Sie zu unterstützen.** Wenn ODBC nur Features verfügbar macht, die allen DBMSs gemeinsam sind, wäre es von geringem Nutzen. der Grund, warum viele verschiedene DBMSs heute vorhanden sind, besteht darin, dass Sie über unterschiedliche Funktionen verfügen. Wenn ODBC jedes Feature verfügbar macht, das in einem beliebigen DBMS verfügbar ist, wäre es für Treiber nicht möglich, zu implementieren.  
  
     ODBC macht stattdessen eine beträchtliche Anzahl von Features verfügbar, da mehr als von den meisten DBMSs unterstützt werden, aber Treiber benötigen, um nur eine Teilmenge dieser Features zu implementieren. Treiber implementieren die verbleibenden Features nur dann, wenn Sie vom zugrunde liegenden DBMS unterstützt werden, oder wenn Sie sich für eine Emulierung entscheiden. Daher können Anwendungen so geschrieben werden, dass die Features eines einzelnen DBMS, wie vom Treiber für dieses DBMS verfügbar gemacht, genutzt werden können, um nur die Features zu nutzen, die von allen DBMSs verwendet werden, oder um die Unterstützung einer bestimmten Funktion zu überprüfen und entsprechend zu reagieren.  
  
     Damit eine Anwendung ermitteln kann, welche Funktionen von einem Treiber und DBMS unterstützt werden, bietet ODBC zwei Funktionen (**SQLGetInfo** und **SQLGetFunctions**), die allgemeine Informationen über die Treiber-und DBMS-Funktionen und eine Liste der vom Treiber unterstützten Funktionen zurückgeben. ODBC definiert auch API-und SQL-Grammatik-Konformitätsstufen, die eine breite Palette von Features angeben, die vom Treiber unterstützt werden. Weitere Informationen finden Sie unter [Konformitätsstufen](../../odbc/reference/develop-app/conformance-levels.md).  
  
     Beachten Sie, dass ODBC eine gemeinsame Schnittstelle für alle Features definiert, die es verfügbar macht. Aus diesem Grund enthalten Anwendungen featurespezifischen Code, nicht DBMS-spezifischen Code und können alle Treiber verwenden, die diese Features verfügbar machen. Ein Vorteil besteht darin, dass Anwendungen nicht aktualisiert werden müssen, wenn die von einem DBMS unterstützten Funktionen verbessert werden. Stattdessen verwendet die Anwendung bei der Installation eines aktualisierten Treibers automatisch die Features, da der zugehörige Code Funktions spezifisch und nicht Treiber spezifisch oder DBMS-spezifisch ist.
