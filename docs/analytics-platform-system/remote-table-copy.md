---
title: Remotetabellenkopie
description: Verwenden der Remote Tabellen Kopie in Analytics Platform System parallel Data Warehouse.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: ecbbdced731e940de46dbde4a65adc486f602c2f
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "74400479"
---
# <a name="remote-table-copy"></a>Remote Tabellen Kopie
Beschreibt, wie Sie mit dem Feature "Remote-Tabellen Kopie" Tabellen aus SQL Server PDW-Datenbanken in Remote-(nicht-Appliance) SMP SQL Server-Datenbanken kopieren. Verwenden Sie die Remote Tabellen Kopie, um Hub-und sprach Szenarios für SQL Server PDW zu aktivieren.  
  
## <a name="understand-remote-table-copy-for-sql-server-pdw"></a><a name="BasicsPDE"></a>Grundlegendes zum Kopieren von Remote Tabellen für SQL Server PDW  
Die Remote Tabellen Kopie ist eine Funktion von SQL Server PDW, die Hub-und sprach Szenarios ermöglicht, indem die Ergebnisse einer SQL-SELECT-Anweisung in eine Tabelle in einer SMP-Datenbank kopiert werden. Die Remote Tabellen Kopie wird mit der [Create Remote Table As Select](../t-sql/statements/create-remote-table-as-select-parallel-data-warehouse.md) -Anweisung initiiert.  
  
## <a name="requirements-for-using-remote-table-copy"></a><a name="BasicsPrerequisites"></a>Anforderungen für die Verwendung der Remote Tabellen Kopie  
Wenn diese Bedingungen erfüllt sind, können Sie die Remote Tabellen Kopie zum Kopieren von Tabellen aus SQL Server PDW in eine SQL Server Datenbank verwenden:  
  
-   Die Zieldatenbank muss eine Instanz von Microsoft® SQL Server® sein, die auf einem Microsoft Windows®-System ausgeführt wird, das eine Verbindung mit der SQL Server PDW Appliance herstellen kann, sich aber nicht auf einem Server innerhalb des Geräts befindet. Der Remote SQL Server kann mit dem SQL Server PDW über das InfiniBand-Netzwerk oder über das Ethernet-Netzwerk verbunden werden.  
  
-   Die zu kopierenden Daten müssen mithilfe einer einzelnen gültigen SQL Server PDW [Select](../t-sql/queries/select-transact-sql.md) -Anweisung ausgewählt werden.  
  
-   Der Zielserver muss ein Server sein, der nicht zur Appliance gehört. Mithilfe der Anweisungen in diesem Thema können keine Daten direkt von einem Gerät in ein anderes kopiert werden.  
  
-   Der Zielserver muss für alle Knoten im InfiniBand-Netzwerk der Anwendung zugänglich sein.  
  
## <a name="configure-remote-table-copy"></a><a name="ConfigureRemote"></a>Remote Tabellen Kopie konfigurieren  
Zum Verwenden der Remote Tabellen Kopie müssen Sie einen Windows-Server erwerben und konfigurieren, SQL Server auf dem Windows-Server konfigurieren und SQL Server PDW konfigurieren. Verwenden Sie die folgenden Links, um diese drei Konfigurationsschritte auszuführen.  
  
1.  [Konfigurieren eines externen Windows-Systems zum Empfangen von Remote Tabellen Kopien mithilfe von InfiniBand](configure-an-external-windows-system-to-receive-remote-table-copies-using-infiniband.md)  
  
2.  [Konfigurieren eines externen SMP-SQL Server zum Empfangen von Remote Tabellen Kopien](configure-an-external-smp-sql-server-to-receive-remote-table-copies.md)  
  
3.  [Konfigurieren von SQL Server PDW für Remote Tabellen Kopien](configure-sql-server-pdw-for-remote-table-copies.md)  
  
## <a name="perform-a-remote-table-copy"></a><a name="PerformRemote"></a>Ausführen einer Remote Tabellen Kopie  
Verwenden Sie die [Create Remote Table As Select](../t-sql/statements/create-remote-table-as-select-parallel-data-warehouse.md) SQL-Anweisung, um eine Remote Tabellen Kopie auszuführen. Beispiele sind im Thema Create Remote Table enthalten.  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
