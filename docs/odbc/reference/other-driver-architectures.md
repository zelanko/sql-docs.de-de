---
title: Weitere Treiber Architekturen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- drivers [ODBC], heterogeneous join engines
- drivers [ODBC], ODBC on the server
- ODBC architecture [ODBC], drivers
- heterogeneous join engines[ODBC]
- drivers [ODBC], middle component
ms.assetid: 1cad06ee-5940-4361-8d01-7d850db1dd66
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ae047fe8014b806d3bda8b0513521b4ddda072a7
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81280530"
---
# <a name="other-driver-architectures"></a>Andere Treiberarchitekturen
Einige ODBC-Treiber entsprechen nicht strikt der zuvor beschriebenen Architektur. Dies kann daran liegen, dass die Treiber andere Aufgaben als die eines herkömmlichen ODBC-Treibers ausführen oder keine Treiber im normalen Sinn sind.  
  
## <a name="driver-as-a-middle-component"></a>Treiber als mittlere Komponente  
 Der ODBC-Treiber kann sich zwischen dem Treiber-Manager und einem oder mehreren anderen ODBC-Treibern befinden. Wenn der Treiber in der Mitte mit mehreren Datenquellen arbeiten kann, fungiert er als Verteiler von ODBC-aufrufen (oder entsprechend übersetzte Aufrufe) für andere Module, die tatsächlich auf die Datenquellen zugreifen. In dieser Architektur nimmt der Treiber in der Mitte einen Teil der Rolle eines Treiber-Managers an.  
  
 Ein weiteres Beispiel für diese Art von Treibern ist ein Spy-Programm für ODBC, das ODBC-Funktionen abfängt und kopiert, die zwischen dem Treiber-Manager und dem Treiber gesendet werden. Diese Ebene kann zum Emulieren eines Treibers oder einer Anwendung verwendet werden. Für den Treiber-Manager scheint die Ebene der Treiber zu sein. für den Treiber scheint die Ebene der Treiber-Manager zu sein.  
  
## <a name="heterogeneous-join-engines"></a>Heterogene joinengines  
 Einige ODBC-Treiber basieren auf einer Abfrage-Engine zum Ausführen heterogener Joins. In einer Architektur eines heterogenen joinmoduls (siehe folgende Abbildung) wird der Treiber für die Anwendung als Treiber angezeigt, wird jedoch in einer anderen Instanz des Treiber-Managers als Anwendung angezeigt. Dieser Treiber verarbeitet einen heterogenen Join aus der Anwendung, indem für jede verknüpfte Datenbank separate SQL-Anweisungen in Treibern aufgerufen werden.  
  
 ![Architektur einer heterogenen Join-Engine](../../odbc/reference/media/fig3-4.gif "Fig3-4")  
  
 Diese Architektur stellt eine allgemeine Schnittstelle für die Anwendung für den Zugriff auf Daten aus unterschiedlichen Datenbanken bereit. Es kann eine gängige Methode zum Abrufen von Metadaten verwenden, z. b. Informationen zu speziellen Spalten (Zeilen Bezeichner), und es kann allgemeine Katalog Funktionen aufrufen, um Daten Wörterbuch Informationen abzurufen. Durch Aufrufen der ODBC-Funktion **SQLStatistics**kann die Anwendung beispielsweise Informationen zu den Indizes in den Tabellen abrufen, die verknüpft werden sollen, selbst wenn sich die Tabellen in zwei separaten Datenbanken befinden. Der Abfrage Prozessor muss sich keine Gedanken darüber machen, wie die Datenbanken Metadaten speichern.  
  
 Die Anwendung verfügt auch über Standard Zugriff auf Datentypen. ODBC definiert allgemeine SQL-Datentypen, denen DBMS-spezifische Datentypen zugeordnet sind. Eine Anwendung kann **SQLGetTypeInfo** aufrufen, um Informationen zu Datentypen in verschiedenen Datenbanken abzurufen.  
  
 Wenn die Anwendung eine heterogene JOIN-Anweisung generiert, analysiert der Abfrage Prozessor in dieser Architektur die SQL-Anweisung und generiert dann separate SQL-Anweisungen für jede Datenbank, die verknüpft werden soll. Durch die Verwendung von Metadaten zu den einzelnen Treibern kann der Abfrage Prozessor den effizientesten, intelligenten Join ermitteln. Wenn die Anweisung z. b. zwei Tabellen in einer Datenbank mit einer Tabelle in einer anderen Datenbank verknüpft, kann der Abfrage Prozessor die beiden Tabellen in einer Datenbank verknüpfen, bevor das Ergebnis mit der Tabelle aus der anderen Datenbank verknüpft wird.  
  
## <a name="odbc-on-the-server"></a>ODBC auf dem Server  
 ODBC-Treiber können auf einem Server installiert werden, damit Sie von Anwendungen auf einer beliebigen Reihe von Client Computern verwendet werden können. In dieser Architektur (siehe folgende Abbildung) werden ein Treiber-Manager und ein einzelner ODBC-Treiber auf jedem Client installiert, und es werden ein weiterer Treiber-Manager und eine Reihe von ODBC-Treibern auf dem Server installiert. Dies ermöglicht jedem Client den Zugriff auf eine Vielzahl von Treibern, die auf dem Server verwendet und gewartet werden.  
  
 ![Architektur der ODBC-Treiber auf einem Server](../../odbc/reference/media/fig3-5.gif "FIG3-5")  
  
 Ein Vorteil dieser Architektur ist die effiziente Softwarewartung und-Konfiguration. Treiber müssen nur an einem Ort aktualisiert werden: auf dem Server. Mithilfe von Systemdaten Quellen können Datenquellen auf dem Server für die Verwendung durch alle Clients definiert werden. Die Datenquellen müssen nicht auf dem Client definiert werden. Das Verbindungspooling kann verwendet werden, um den Prozess zu optimieren, mit dem Clients eine Verbindung mit Datenquellen herstellen.  
  
 Der Treiber auf dem Client ist normalerweise ein sehr kleiner Treiber, der den Treiber-Manager-Rückruf an den Server überträgt. Der Speicherbedarf kann erheblich geringer sein als die voll funktionstüchtigen ODBC-Treiber auf dem Server. In dieser Architektur können Client Ressourcen freigegeben werden, wenn der Server über mehr Rechenleistung verfügt. Außerdem kann die Effizienz und Sicherheit des gesamten Systems verbessert werden, indem Sicherungs Server installiert und ein Lastenausgleich durchgeführt wird, um die Servernutzung zu optimieren.
