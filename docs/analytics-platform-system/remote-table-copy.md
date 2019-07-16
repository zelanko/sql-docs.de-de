---
title: Remotetabellenkopie - Parallel Data Warehouse | Microsoft-Dokumentation
description: Verwenden von remotetabellenkopie in Analytics Platform System Parallel Data Warehouse.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 28bd5deda25650d36467281ccbffa7b666f4c695
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67960203"
---
# <a name="remote-table-copy"></a>Remotetabellenkopie
Beschreibt, wie die remotetabellenkopie-Features, die zum Kopieren von Tabellen aus SQL Server-PDW-Datenbanken auf SMP-SQL Server-Remotedatenbanken (nicht zur Appliance gehört) verwenden. Verwenden Sie für SQL Server PDW remotetabellenkopie Hub- und Spoke-Szenarien ermöglicht.  
  
## <a name="BasicsPDE"></a>Grundlegendes zu Remotetabellenkopie für SQLServer PDW  
Remotetabellenkopie ist ein Feature von SQL Server PDW, die Hub- and -Spoke-Szenarien unterstützt, durch die Ergebnisse einer SQL-SELECT-Anweisung in eine Tabelle in einer SMP-Datenbank kopieren. Die remotetabellenkopie wird initiiert, mit der [CREATE REMOTE TABLE AS SELECT](../t-sql/statements/create-remote-table-as-select-parallel-data-warehouse.md) Anweisung.  
  
## <a name="BasicsPrerequisites"></a>Anforderungen für die Verwendung von Remotetabellenkopie  
Sie können die Remotetabelle kopieren, Kopieren von Tabellen aus SQL Server PDW mit einer SQL Server-Datenbank verwenden, wenn diese Bedingungen erfüllt sind:  
  
-   Die Zieldatenbank muss es sich um eine Instanz von Microsoft® SQL Server® sein, die auf einem System Microsoft Windows® ausgeführt wird, die mit der SQL Server-PDW-Appliance verbinden können, aber befindet sich nicht auf einem Server in der Appliance. Der Remotecomputer mit SQL Server kann in der SQL Server PDW mit InfiniBand-Netzwerk oder über das Ethernet-Netzwerk verbunden werden.  
  
-   Die zu kopierenden Daten muss ausgewählt werden, mithilfe einer einzelnen gültigen SQL Server PDW [wählen](../t-sql/queries/select-transact-sql.md) Anweisung.  
  
-   Der Zielserver muss ein Server sein, der nicht zur Appliance gehört. Daten können nicht direkt von einer Appliance kopiert werden, in eine andere mithilfe der Anweisungen in diesem Thema.  
  
-   Der Zielserver muss auf allen Knoten auf der Appliance Infiniband-Netzwerk zugreifen kann.  
  
## <a name="ConfigureRemote"></a>Konfigurieren Sie die Remotetabellenkopie  
Um remotetabellenkopie verwenden zu können, müssen Sie zu erwerben und konfigurieren Sie einen Windows-Server, konfigurieren Sie SQL Server auf dem Windows Server und Konfigurieren von SQL Server PDW. Verwenden Sie die folgenden Links, um diese drei Schritte ausführen.  
  
1.  [Konfigurieren eines externen Windows-Systems zum Empfangen von Remotetabellenkopien mit InfiniBand](configure-an-external-windows-system-to-receive-remote-table-copies-using-infiniband.md)  
  
2.  [Konfigurieren eines externen SMP-SQL-Servers zum Empfangen von Remotetabellenkopien](configure-an-external-smp-sql-server-to-receive-remote-table-copies.md)  
  
3.  [Konfigurieren von SQLServer PDW für Remotetabellenkopien](configure-sql-server-pdw-for-remote-table-copies.md)  
  
## <a name="PerformRemote"></a>Führen Sie eine Remotetabellenkopie  
Um eine remotetabellenkopie auszuführen, verwenden die [CREATE REMOTE TABLE AS SELECT](../t-sql/statements/create-remote-table-as-select-parallel-data-warehouse.md) SQL-Anweisung. Beispiele sind in das Thema CREATE REMOTE TABLE enthalten.  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
