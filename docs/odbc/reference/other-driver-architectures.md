---
title: Andere Treiberarchitekturen | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81280530"
---
# <a name="other-driver-architectures"></a>Andere Treiberarchitekturen
Einige ODBC-Treiber entsprechen nicht strikt der zuvor beschriebenen Architektur. Dies kann daran liegen, dass die Fahrer andere Aufgaben als die eines herkömmlichen ODBC-Treibers erfüllen oder keine Treiber im normalen Sinne sind.  
  
## <a name="driver-as-a-middle-component"></a>Treiber als mittlere Komponente  
 Der ODBC-Treiber kann sich zwischen dem Treiber-Manager und einem oder mehreren anderen ODBC-Treibern befinden. Wenn der Treiber in der Mitte in der Lage ist, mit mehreren Datenquellen zu arbeiten, fungiert er als Dispatcher von ODBC-Aufrufen (oder entsprechend übersetzten Aufrufen) an andere Module, die tatsächlich auf die Datenquellen zugreifen. In dieser Architektur übernimmt der Treiber in der Mitte einen Teil der Rolle eines Treiber-Managers.  
  
 Ein weiteres Beispiel für diese Art von Treiber ist ein Spionageprogramm für ODBC, das ODBC-Funktionen abfängt und kopiert, die zwischen dem Treiber-Manager und dem Treiber gesendet werden. Diese Ebene kann verwendet werden, um entweder einen Treiber oder eine Anwendung zu emulieren. Für den Treiber-Manager scheint der Layer der Treiber zu sein. für den Treiber scheint der Layer der Treiber-Manager zu sein.  
  
## <a name="heterogeneous-join-engines"></a>Heterogene Join-Engines  
 Einige ODBC-Treiber basieren auf einer Abfrage-Engine zum Ausführen heterogener Verknüpfungen. In einer Architektur eines heterogenen Join-Moduls (siehe folgende Abbildung) wird der Treiber der Anwendung als Treiber angezeigt, aber in einer anderen Instanz des Treiber-Managers als Anwendung. Dieser Treiber verarbeitet eine heterogene Verknüpfung aus der Anwendung, indem separate SQL-Anweisungen in Treibern für jede verbundene Datenbank aufgerufen werden.  
  
 ![Architektur einer heterogenen Join-Engine](../../odbc/reference/media/fig3-4.gif "abb. 3-4")  
  
 Diese Architektur stellt eine gemeinsame Schnittstelle für den Zugriff der Anwendung auf Daten aus verschiedenen Datenbanken bereit. Es kann eine allgemeine Möglichkeit zum Abrufen von Metadaten verwenden, z. B. Informationen zu speziellen Spalten (Zeilenbezeichner), und es kann allgemeine Katalogfunktionen aufrufen, um Datenwörterbuchinformationen abzurufen. Durch Aufrufen der ODBC-Funktion **SQLStatistics**kann die Anwendung beispielsweise Informationen über die Indizes in den zu verknüpfenden Tabellen abrufen, auch wenn sich die Tabellen in zwei separaten Datenbanken befinden. Der Abfrageprozessor muss sich keine Gedanken darüber machen, wie die Datenbanken Metadaten speichern.  
  
 Die Anwendung hat auch Standardzugriff auf Datentypen. ODBC definiert gängige SQL-Datentypen, denen DBMS-spezifische Datentypen zugeordnet sind. Eine Anwendung kann **SQLGetTypeInfo** aufrufen, um Informationen zu Datentypen in verschiedenen Datenbanken abzurufen.  
  
 Wenn die Anwendung eine heterogene Join-Anweisung generiert, analysiert der Abfrageprozessor in dieser Architektur die SQL-Anweisung und generiert dann separate SQL-Anweisungen für jede Datenbank, die verknüpft werden soll. Durch die Verwendung von Metadaten zu jedem Treiber kann der Abfrageprozessor die effizienteste und intelligenteste Verknüpfung ermitteln. Wenn die Anweisung z. B. zwei Tabellen in einer Datenbank mit einer Tabelle in einer anderen Datenbank verknüpft, kann der Abfrageprozessor die beiden Tabellen in der einen Datenbank verknüpfen, bevor er das Ergebnis mit der Tabelle aus der anderen Datenbank verknüpft.  
  
## <a name="odbc-on-the-server"></a>ODBC auf dem Server  
 ODBC-Treiber können auf einem Server installiert werden, sodass sie von Anwendungen auf einem beliebigen Clientcomputer verwendet werden können. In dieser Architektur (siehe folgende Abbildung) sind auf jedem Client ein Treiber-Manager und ein einzelner ODBC-Treiber installiert, und auf dem Server sind ein weiterer Treiber-Manager und eine Reihe von ODBC-Treibern installiert. Dadurch kann jeder Client auf eine Vielzahl von Treibern zugreifen, die auf dem Server verwendet und verwaltet werden.  
  
 ![Architektur der ODBC-Treiber auf einem Server](../../odbc/reference/media/fig3-5.gif "FIG3-5")  
  
 Ein Vorteil dieser Architektur ist die effiziente Softwarewartung und -konfiguration. Treiber müssen nur an einem Ort aktualisiert werden: auf dem Server. Durch die Verwendung von Systemdatenquellen können Datenquellen auf dem Server für die Verwendung durch alle Clients definiert werden. Die Datenquellen müssen nicht auf dem Client definiert werden. Das Verbindungspooling kann verwendet werden, um den Prozess zu optimieren, durch den Clients eine Verbindung mit Datenquellen herstellen.  
  
 Der Treiber auf dem Client ist in der Regel ein sehr kleiner Treiber, der den Driver Manager-Aufruf an den Server überträgt. Sein Platzbedarf kann deutlich kleiner sein als die voll funktionsfähigen ODBC-Treiber auf dem Server. In dieser Architektur können Clientressourcen freigegeben werden, wenn der Server über mehr Rechenleistung verfügt. Darüber hinaus können die Effizienz und Sicherheit des gesamten Systems durch die Installation von Backup-Servern und die Durchführung eines Lastenausgleichs zur Optimierung der Servernutzung verbessert werden.
