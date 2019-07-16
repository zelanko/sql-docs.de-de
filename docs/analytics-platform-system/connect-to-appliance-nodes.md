---
title: Herstellen einer Verbindung Appliance Knoten - Analytics Platform System mit | Microsoft-Dokumentation
description: Dieser Artikel beschreibt die verschiedenen Möglichkeiten für die Verbindung für jeden Knoten in der Analytics Platform System Appliance.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: ae40d38768f081ea6c439c40059065d695ebee23
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67961087"
---
# <a name="connect-to-appliance-nodes-in-analytics-platform-system"></a>Verbindung mit applianceknoten in Analytics Platform System
Dieser Artikel beschreibt die verschiedenen Möglichkeiten für die Verbindung für jeden Knoten in der Analytics Platform System Appliance.  
  
## <a name="connecting-with-hadoop"></a>Herstellen einer Verbindung mit Hadoop  
Bitten Sie vor der Verwendung von Hadoop mit SQL Server PDW Ihre applianceadministrator, um die Java-Laufzeitumgebung in SQL Server PDW zu installieren. Anweisungen hierzu finden Sie unter [Konfigurieren von PolyBase-Konnektivität für externe Daten &#40;Analytics Platform System&#41; ](configure-polybase-connectivity-to-external-data.md) in der Appliance-Handbuch.  
  
## <a name="ConnectingToIndividualNodes"></a>Herstellen einer Verbindung mit Applianceknoten  
Der Knoten der Appliance erfolgt direkt nur unter bestimmten Verwendungsszenarios und nach bestimmten Benutzertypen. Die folgende Tabelle enthält jeder Knoten der Appliance und die Szenarien, die unter denen Benutzer direkt auf diesen Knoten die Verbindung herstellen.  
  
<!-- MISSING LINKS For information on the purpose of each node, see [Understanding SQL Server PDW &#40;SQL Server PDW&#41;](../sqlpdw/understanding-sql-server-pdw-sql-server-pdw.md).  -->  

> [!WARNING]  
> Datenbank oder Tabelle auf das Steuerelement oder Compute-Knoten ohne explizite Zustimmung des Produktteams oder APS Kunden Support-Team ändert möglicherweise Ihre APS-Appliance nicht mehr unterstützt wird gerendert.
  
|||  
|-|-|  
|**Node**|**Zugriffsszenarien**|  
|Steuerknoten|Verwenden Sie einen Webbrowser, um die Verwaltungskonsole zugreifen, der auf dem steuerknoten ausgeführt wird. Weitere Informationen finden Sie unter [Überwachen der Appliance mithilfe der Verwaltungskonsole &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md).<br /><br />Alle Client-Anwendungen und Tools eine Verbindung herstellen, mit dem Steuerungsknoten, unabhängig davon, ob die Verbindung Ethernet oder InfiniBand verwenden wird.<br /><br />Verwenden Sie zum Konfigurieren einer Ethernet-Verbindungs mit dem Steuerungsknoten Steuerelement Knoten-Cluster-IP-Adresse und Port **17001**. Z. B. "192.168.0.1,17001".<br /><br />Verwenden Sie zum Konfigurieren einer InfiniBand-Verbindungs mit dem Steuerungsknoten  <strong>*Appliance_domain*-SQLCTL01</strong> und Port **17001**. Mithilfe von  <strong>*Appliance_domain*-SQLCTL01</strong>, der Appliance DNS-Server wird zur verbinden, mit dem Server mit dem aktiven InfiniBand-Netzwerk. Zum Konfigurieren des Servers nicht zur Appliance gehört Verwendung finden Sie unter [InfiniBand-Netzwerkadapter konfigurieren](configure-infiniband-network-adapters.md).<br /><br />Der applianceadministrator verbindet sich mit den Steuerelementknoten aus, um Verwaltungsvorgänge auszuführen. Beispielsweise führt der applianceadministrator die folgenden Vorgänge aus den Steuerelementknoten aus:<br /><br />Konfigurieren von Analytics Platform System mit der **dwconfig.exe** -Konfigurationstool.|  
|Computeknoten|Compute-Knoten-Verbindungen vom steuerknoten weitergeleitet werden. Die IP-Adressen von Compute-Knoten werden nie als Parameter in der Application-Befehle eingegeben.<br /><br />Für das Laden, Sicherung, Remotetabellenkopie, "und" Hadoop "," SQL Server PDW Daten senden oder empfangen direkt parallel zwischen den Compute-Knoten und nicht zur Appliance gehört Knoten oder Server. Diese Anwendungen Verbinden mit SQL Server PDW durch Herstellen einer Verbindung mit dem Steuerungsknoten und leitet dann der Steuerelementknoten aus SQL Server PDW zum Herstellen der Kommunikation zwischen den Compute-Knoten und dem Server nicht zur Appliance gehört.<br /><br />Beispielsweise finden Sie diese Vorgänge parallel mit direkte Verbindungen mit den Compute-Knoten statt:<br /><br />Laden vom Server geladen, in SQL Server PDW.<br /><br />Sichern einer Datenbank von SQL Server PDW zum Sicherungsserver.<br /><br />Wiederherstellen einer Datenbank aus dem backup-Server in SQL Server PDW.<br /><br />Abfragen von Hadoop-Daten aus SQL Server PDW.<br /><br />Exportieren von Daten aus SQL Server PDW zu einer externen Hadoop-Tabelle.<br /><br />Kopieren einer SQL Server-PDW-Tabelle mit einer SMP-SQL Server-Remotedatenbank an.|  
  
## <a name="connecting-to-the-ethernet-and-infiniband-networks"></a>Verbindung mit dem Ethernet und InfiniBand-Netzwerke  
Remote-Server können über entweder die Appliance InfiniBand-Netzwerk oder über das Ethernet-Netzwerk verbinden. Für die Verbesserung der Leistung, laden die Server, Server-Sicherung und -Servern empfangen von Daten über **CREATE REMOTE TABLE AS SELECT** -Anweisungen in der Regel übertragen von Daten über das Gerät InfiniBand-Netzwerk.  
  
Sie können die zu Ihrer eigenen Kunden Arbeitsgruppe oder Domäne gehören nicht zur Appliance gehört-Server konfigurieren und verwenden Sie dann Ihre eigenen Netzwerk des Kunden für die Verbindung mit diesen Servern und Übertragen von Daten auf diese. Nicht zur Appliance gehört-Servern, die an das InfiniBand-Gerät verbunden sind haben, die Möglichkeit zum Übertragen von Daten über das Gerät InfiniBand-Netzwerk miteinander; Achten Sie darauf, dabei, da sie die Leistung von SQL Server PDW verlangsamen kann.  
  
Diese Anweisung fügt z. B. Anmeldeinformationen für das Netzwerk zum Ausführen von Sicherungen über InfiniBand auf einen Sicherungsserver, der über ein InfiniBand IP-Adresse 192.168.0.1 verfügt. Die Domäne der Anwendung ist *Mypdw*, und die Anweisung vom backup-Server ausgeführt wird. Bevor Sie diese Anweisung ausführen, müssen Sie in Ihren eigenen Parametern an eingeben.  
  
```  
sqlcmd -S "mypdw-sqlctl01,17001" -U sa -P password -I -Q "exec sp_pdw_add_network_credentials '192.168.0.1', 'mypdw\Administrator', 'password'"  
```  
  
Beispielsweise startet ein Befehl Laden durch Folgendes:  
  
```  
dwloader -S mypdw-SQLCTL01  
```  
  
<!-- MISSING LINKS ## See Also  
[Configure an External Windows System To Receive Remote Table Copies Using InfiniBand &#40;SQL Server PDW&#41;](../sqlpdw/configure-an-external-windows-system-to-receive-remote-table-copies-using-infiniband-sql-server-pdw.md)  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
