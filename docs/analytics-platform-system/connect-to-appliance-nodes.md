---
title: Verbindung mit Anwendungs Knoten herstellen
description: In diesem Artikel werden die verschiedenen Möglichkeiten zum Herstellen einer Verbindung mit den einzelnen Knoten des Analytics Platform System Appliance erläutert.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: e1182d174e3281fda944c0b6490b114d4b6f2244
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "74401243"
---
# <a name="connect-to-appliance-nodes-in-analytics-platform-system"></a>Herstellen einer Verbindung mit Geräteknoten in Analytics Platform System
In diesem Artikel werden die verschiedenen Möglichkeiten zum Herstellen einer Verbindung mit den einzelnen Knoten des Analytics Platform System Appliance erläutert.  
  
## <a name="connecting-with-hadoop"></a>Herstellen einer Verbindung mit Hadoop  
Bevor Sie Hadoop mit SQL Server PDW verwenden, bitten Sie den Geräte Administrator, die Java Runtime Environment auf SQL Server PDW zu installieren. Anweisungen hierzu finden [Sie unter Konfigurieren der polybase-Konnektivität mit externen Daten &#40;Analytics Platform System&#41;](configure-polybase-connectivity-to-external-data.md) im Handbuch Appliance Operations.  
  
## <a name="connecting-to-appliance-nodes"></a><a name="ConnectingToIndividualNodes"></a>Herstellen einer Verbindung mit Anwendungs Knoten  
Der Zugriff auf jeden applicenknoten erfolgt direkt in bestimmten Verwendungs Szenarios und bestimmten Benutzer Typen. In der folgenden Tabelle werden die einzelnen Geräteknoten und die Szenarien aufgelistet, unter denen Benutzer direkt eine Verbindung mit diesem Knoten herstellen.  
  
<!-- MISSING LINKS For information on the purpose of each node, see [Understanding SQL Server PDW &#40;SQL Server PDW&#41;](../sqlpdw/understanding-sql-server-pdw-sql-server-pdw.md).  -->  

> [!WARNING]  
> Das Ändern von Datenbank-oder Tabelleneinstellungen auf Steuerungs-oder Computeknoten ohne explizite Zustimmung des Produktteams oder APS-Kundensupport Teams kann ihre APS-Appliance nicht mehr unterstützen.
  
|||  
|-|-|  
|**Node**|**Zugriffs Szenarien**|  
|Steuerknoten|Verwenden Sie einen Webbrowser, um auf die Verwaltungskonsole zuzugreifen, die auf dem Steuer Knoten ausgeführt wird. Weitere Informationen finden Sie unter [Überwachen der Appliance mithilfe der Verwaltungskonsole &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md).<br /><br />Alle Client Anwendungen und Tools stellen eine Verbindung mit dem Steuer Knoten her, unabhängig davon, ob die Verbindung Ethernet oder InfiniBand verwendet.<br /><br />Um eine Ethernet-Verbindung mit dem Steuerungs Knoten zu konfigurieren, verwenden Sie die IP-Adresse und den Port **17001**des Kontroll Knoten Clusters. Beispiel: "192.168.0.1, 17001".<br /><br />Zum Konfigurieren einer InfiniBand-Verbindung mit dem Steuer Knoten verwenden Sie <strong> *appliance_domain*-SQLCTL01</strong> und Port **17001**. Wenn Sie <strong> *appliance_domain*-SQLCTL01</strong>verwenden, verbindet der DNS-Server der Appliance Ihren Server mit dem aktiven InfiniBand-Netzwerk. Informationen zum Konfigurieren des nicht-Appliance-Servers für die Verwendung finden Sie unter [Konfigurieren von InfiniBand-Netzwerkadaptern](configure-infiniband-network-adapters.md).<br /><br />Der Geräte Administrator stellt eine Verbindung mit dem Steuerungs Knoten her, um Verwaltungsvorgänge auszuführen. Der applianceadministrator führt z. b. die folgenden Vorgänge über den Steuer Knoten aus:<br /><br />Konfigurieren Sie das Analytics Platform System mit dem Konfigurationstool " **dwconfig. exe** ".|  
|Computeknoten|Computeknotenverbindungen werden vom Steuer Knoten gesteuert. Die IP-Adressen von Computeknoten werden nie als Parameter in Anwendungs Befehle eingegeben.<br /><br />Beim Laden, bei der Sicherung, bei der Remote Tabellen Kopie und bei Hadoop werden von SQL Server PDW Daten direkt zwischen den Computeknoten und den nicht Appliance-Knoten oder-Servern gesendet oder empfangen. Diese Anwendungen stellen eine Verbindung mit SQL Server PDW her, indem Sie eine Verbindung mit dem Steuerungs Knoten herstellen, und der Steuerungs Knoten leitet SQL Server PDW an, um die Kommunikation zwischen den Computeknoten und dem nicht-Appliance-Server herzustellen.<br /><br />Diese Datenübertragungs Vorgänge erfolgen beispielsweise parallel mit direkten Verbindungen zu den Computeknoten:<br /><br />Laden vom Lade Server in SQL Server PDW.<br /><br />Sichern einer Datenbank vom SQL Server PDW auf dem Sicherungs Server.<br /><br />Wiederherstellen einer Datenbank vom Sicherungs Server in SQL Server PDW.<br /><br />Abfragen von Hadoop-Daten aus SQL Server PDW.<br /><br />Exportieren von Daten aus SQL Server PDW in eine externe Hadoop-Tabelle.<br /><br />Kopieren einer SQL Server PDW Tabelle in eine Remote-SMP-SQL Server Datenbank.|  
  
## <a name="connecting-to-the-ethernet-and-infiniband-networks"></a>Herstellen einer Verbindung mit dem Ethernet-und InfiniBand-Netzwerk  
Remote Server können entweder über das Gerät InfiniBand-Netzwerk oder über das Ethernet-Netzwerk eine Verbindung herstellen. Aus Leistungsgründen werden durch das Laden von Servern, Sicherungs Servern und Servern, die Daten über **Create Remote Table As Select** -Anweisungen empfangen, normalerweise Daten über das InfiniBand-Netzwerkgerät übertragen.  
  
Sie können nicht-Geräteserver so konfigurieren, dass Sie zu ihrer eigenen Kunden Arbeitsgruppe oder Domäne gehören, und dann Ihr eigenes Kundennetzwerk verwenden, um eine Verbindung mit diesen Servern herzustellen und Daten an diese zu übertragen. Außerdem haben nicht-Geräteserver, die mit dem Gerät InfiniBand verbunden sind, die Möglichkeit, Daten über das InfiniBand-Netzwerk der Anwendung zu übertragen. seien Sie vorsichtig damit, da die Leistung von SQL Server PDW verlangsamt werden kann.  
  
Diese Anweisung fügt z. b. Netzwerk Anmelde Informationen zum Durchführen von Sicherungen über InfiniBand zu einem Sicherungs Server mit einer InfiniBand-IP-Adresse 192.168.0.1 hinzu. Die Appliance-Domäne ist *mypdw*, und die-Anweisung wird vom Backup-Server ausgeführt. Vor dem Ausführen dieser Anweisung müssen Sie Ihre eigenen Parameter eingeben.  
  
```  
sqlcmd -S "mypdw-sqlctl01,17001" -U sa -P password -I -Q "exec sp_pdw_add_network_credentials '192.168.0.1', 'mypdw\Administrator', 'password'"  
```  
  
Beispielsweise wird ein Lade Befehl mit folgendem Befehl gestartet:  
  
```  
dwloader -S mypdw-SQLCTL01  
```  
  
<!-- MISSING LINKS ## See Also  
[Configure an External Windows System To Receive Remote Table Copies Using InfiniBand &#40;SQL Server PDW&#41;](../sqlpdw/configure-an-external-windows-system-to-receive-remote-table-copies-using-infiniband-sql-server-pdw.md)  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
