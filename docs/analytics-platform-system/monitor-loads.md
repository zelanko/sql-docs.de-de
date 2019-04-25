---
title: Überwachen von Lasten für Parallel Data Warehouse | Microsoft-Dokumentation
description: Überwachen Sie aktive und kürzlich vorgenommene lädt mithilfe der Analytics Platform System (APS)-Verwaltungskonsole oder Parallel Data Warehouse (PDW)-Systemsichten."
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: cb840c64c2235a2f3902c45633aa5471655482dc
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62639963"
---
# <a name="monitor-loads-into-parallel-data-warehouse"></a>Monitor wird in Parallel Data Warehouse geladen.
Überwachen Sie aktive und kürzlich vorgenommene [Dwloader](dwloader.md) lädt mithilfe der Verwaltungskonsole für Analytics Platform System (APS) oder Parallel Data Warehouse (PDW) [Systemsichten](https://azure.microsoft.com/documentation/articles/sql-data-warehouse-reference-tsql-system-views/). 
  
> [!TIP]  
> Mithilfe von INSERT-Anweisungen oder Business Intelligence-Tools, die SQL-Anweisungen verwenden, um den Ladevorgang durchzuführen, werden einige Lasten initiiert. 

<!-- MISSING LINKS
To monitor this type of load, see [Monitoring Active Queries](monitor-active-queries.md).  
-->
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
Unabhängig von der Methode, die zum Überwachen der Auslastung verwendet wird muss die Anmeldung den Zugriff auf die zugrunde liegenden Datenquellen Berechtigung. 

<!-- MISSING LINKS
For the permissions to grant, see "Use All of the Admin Console" in [Grant Permissions to Use the Admin Console](grant-permissions-admin-console.md). 

--> 
  
## <a name="monitoring-loads"></a>Überwachen der Auslastung  
In den folgenden Abschnitten wird beschrieben, wie Lasten zu überwachen.  
  
### <a name="to-monitor-loads-by-using-the-admin-console"></a>Lädt mit der Admin-Konsole überwachen  
  
1.  Melden Sie sich bei der Verwaltungskonsole. <!-- MISSING LINKS See [Monitor the Appliance by Using the Admin Console;](monitor-admin-console.md) for instructions. --> 
  
2.  Klicken Sie auf die im oberen Menü auf **lädt**. Sie sehen eine sortierbare Tabelle, die mit allen aktuellen und aktiver Ladevorgänge sowie zusätzliche Informationen wie gibt an, ob der Ladevorgang abgeschlossen ist oder noch aktiv ist. Klicken Sie auf die Spaltenüberschriften, um die Zeilen sortieren.  
  
3.  Um zusätzliche Details für eine bestimmte Auslastung anzuzeigen, klicken Sie auf der Last **ID** in der linken Spalte. In der Detailansicht sehen Sie auf die einzelnen Schritte des Ladevorgangs wird ausgeführt.  
  
Diese Systemsichten Informationen finden Sie die Metadaten über die Last, die in der Verwaltungskonsole angezeigt wird:  
  
-   [sys.dm_pdw_exec_requests](../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md)  
  
-   [sys.pdw_loader_run_stages](https://msdn.microsoft.com/library/mt203879.aspx)  
  
-   [sys.pdw_loader_backup_runs](../relational-databases/system-catalog-views/sys-pdw-loader-backup-runs-transact-sql.md)  
  
-   [sys.pdw_loader_backup_run_details](../relational-databases/system-catalog-views/sys-pdw-loader-backup-run-details-transact-sql.md)  
  
### <a name="to-monitor-loads-by-using-system-views"></a>Lädt mithilfe von Systemansichten überwachen  
Führen Sie die folgenden Schritte aus, um aktive und kürzlich vorgenommene lädt mithilfe von SQL Server-PDW-Ansichten zu überwachen. Für jede Systemsicht, die verwendet wird finden Sie unter der Dokumentation für diese Sicht Informationen für die Spalten und die möglichen Werte, die von der Sicht zurückgegeben.  
  
1.  Suchen der `request_id` für das Laden in die [dm_pdw_exec_requests](../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md) Ansicht durch Suchen der Loader-Befehlszeile in die `command` Spalte für diese Ansicht.  
  
    Beispielsweise gibt der folgende Befehl zurück, die Befehlstext und aktueller Status, sowie die `request_id`.  
  
    ```sql  
    SELECT request_id, status, command FROM sys.dm_pdw_exec_requests;  
    ```  
  
2.  Verwenden der `request_id` zum Abrufen zusätzlicher Informationen für das Laden mithilfe der [sys.pdw_loader_run_stages](../relational-databases/system-catalog-views/sys-pdw-loader-run-stages-transact-sql.md) , und [sys.pdw_loader_backup_run_details](../relational-databases/system-catalog-views/sys-pdw-loader-backup-run-details-transact-sql.md) Ansichten. Z. B. die folgende Abfrage gibt die `run_id` und Informationen zu den Start, Ende und Dauer, wie oft die Last sowie Fehler und Informationen über die Anzahl der verarbeiteten Zeilen:  
  
    ```sql  
    SELECT lbr.run_id,   
    er.submit_time, er.end_time, er.total_elapsed_time, er.error_id, lbr.rows_processed, lbr.rows_rejected, lbr.rows_inserted   
    FROM sys.dm_pdw_exec_requests er   
    LEFT OUTER JOIN   
    sys.pdw_loader_backup_runs lbr   
    ON (er.request_id=lbr.requst_id)   
    WHERE er.request_id='12738';  
    ```  
  
<!-- MISSING LINKS

## See Also  
[Common metadata query examples](metadata-query-examples.md)
-->  
  
