---
title: Andere Treiberarchitekturen | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fd051d018cb6f53b8c08110e26bc66910e3ca4c5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63045525"
---
# <a name="other-driver-architectures"></a>Andere Treiberarchitekturen
Einige ODBC-Treiber entsprechen nicht unbedingt an der Architektur, die zuvor beschriebenen. Dies kann sein, da die Treiber durchführen, außer denen eines herkömmlichen ODBC-Treibers Aufgaben sind oder nicht Treiber normale insofern.  
  
## <a name="driver-as-a-middle-component"></a>Treiber als mittlere-Komponente  
 Der ODBC-Treiber kann zwischen der Treiber-Manager und eine oder mehrere andere ODBC-Treiber befinden. Wenn der Treiber in der Mitte mit mehreren Datenquellen funktionsfähig ist, fungiert er als Verteiler von ODBC-Aufrufe (oder entsprechend übersetzten) an andere Module, die tatsächlich die Datenquellen zugreifen. In dieser Architektur nimmt der Treiber in der Mitte auf einigen der Rolle des Treiber-Managers.  
  
 Ein weiteres Beispiel für diese Art der Treiber ist ein Spy-Programm für ODBC, der abfängt und kopiert ODBC-Funktionen, die zwischen der Treiber-Manager und den Treiber gesendet werden. Diese Ebene kann verwendet werden, um entweder einen Treiber oder eine Anwendung zu emulieren. Auf der Treiber-Manager, erscheint die Ebene der ODBC-Treiber. an den Treiber wird die Ebene der Treiber-Manager.  
  
## <a name="heterogeneous-join-engines"></a>Heterogenen Join-Engines  
 Einige ODBC-Treiber baut auf eine Abfrage-Engine zum Ausführen von heterogenen Joins. In einer Architektur eines heterogenen joinmoduls (siehe die folgende Abbildung), der Treiber für die Anwendung angezeigt wird, wie ein Treiber jedoch zu einer anderen Instanz des Treiber-Managers als Anwendung angezeigt wird. Dieser Treiber verarbeitet einen heterogenen Join von der Anwendung durch Aufrufen von unterschiedlichen SQL-Anweisungen im Treiber für jede verknüpfte Datenbank.  
  
 ![Architektur eines heterogenen joinmoduls](../../odbc/reference/media/fig3-4.gif "fig3-4")  
  
 Diese Architektur bietet eine allgemeine Schnittstelle für die Anwendung auf Daten aus verschiedenen Datenbanken zugreifen. Eine allgemeine Möglichkeit zum Abrufen von Metadaten, z. B. Informationen zur spezielle Spalten (Zeilen-IDs), kann verwendet werden, und können allgemeine Katalogfunktionen zum Abrufen von Informationen zu Wörterbuch aufrufen. Durch Aufrufen der ODBC-Funktion **SQLStatistics**, z. B. kann die Anwendung Informationen zu den Indizes in den Tabellen verknüpft werden, abrufen, selbst wenn die Tabellen auf zwei separate Datenbanken sind. Der Abfrageprozessor muss nicht kümmern, wie in die Datenbanken zum Speichern von Metadaten.  
  
 Die Anwendung verfügt außerdem über Zugriff auf die standard-Datentypen. ODBC definiert allgemeine SQL-Datentypen, denen die die DBMS-spezifische Datentypen zugeordnet sind. Kann eine Anwendung aufrufen **SQLGetTypeInfo** zum Abrufen von Informationen zu Datentypen in unterschiedlichen Datenbanken.  
  
 Wenn die Anwendung eine heterogenen Join-Anweisung generiert, wird der Abfrageprozessor in dieser Architektur analysiert die SQL-Anweisung, und klicken Sie dann generiert separate SQL-Anweisungen für jede Datenbank verknüpft werden sollen. Mithilfe von Metadaten zu jedem Treiber kann der Abfrageprozessor den Join am effizientesten, intelligenten bestimmen. Z. B. wenn die Anweisung zwei Tabellen in einer Datenbank mit einer Tabelle auf eine andere Datenbank verknüpft werden, kann der Abfrageprozessor Verknüpfen der beiden Tabellen in einer Datenbank vor dem Verknüpfen des Ergebnis mit der Tabelle aus der anderen Datenbank.  
  
## <a name="odbc-on-the-server"></a>ODBC auf dem Server  
 ODBC-Treiber können auf einem Server installiert werden, damit sie von Anwendungen auf einer Reihe von Clientcomputern verwendet werden können. In dieser Architektur (siehe die folgende Abbildung), einen Treiber-Manager und einen einzelnen ODBC-Treiber werden installiert, auf jedem Client und einem anderen Treiber-Manager und eine Reihe von ODBC-Treiber auf dem Server installiert sind. Dadurch wird jeder Clientzugriff auf eine Vielzahl von Treibern auf dem Server verwaltet und verwendet.  
  
 ![Architektur der ODBC-Treiber auf einem Server](../../odbc/reference/media/fig3-5.gif "FIG3-5")  
  
 Ein Vorteil dieser Architektur ist effizient Softwarewartung und Konfiguration. Treiber müssen nur an einem Ort aktualisiert werden: auf dem Server. Mithilfe von System-Datenquellen können die Datenquellen auf dem Server für die Verwendung von allen Clients definiert werden. Die Datenquellen müssen nicht auf dem Client definiert werden. Verbindungspooling kann verwendet werden, um den Prozess zu optimieren, mit dem Clients eine Verbindung mit Datenquellen herstellen.  
  
 Der Treiber auf dem Client ist in der Regel eine sehr kleine Treiber, der der Treiber-Manager-Aufrufs an den Server zu übertragen. Der Platzbedarf kann erheblich kleiner als die voll funktionsfähige ODBC-Treiber auf dem Server sein. In dieser Architektur können Client-Ressourcen freigegeben werden, wenn der Server mehr rechenleistung verfügt. Darüber hinaus können der Effizienz und Sicherheit des gesamten Systems verbessert werden, von der backup-Server installieren und ausführen, den Lastenausgleich zum Optimieren der Serververwendung.
