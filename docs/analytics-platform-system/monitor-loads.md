---
title: Überwachen von Ladevorgängen
description: Überwachen Sie aktive und aktuelle Lasten mithilfe der Verwaltungskonsole von Analytics Platform System (APS) oder der System Sichten parallel Data Warehouse (PDW).
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: b284fdcef506924c26e452196db6e9518faa1351
ms.sourcegitcommit: d587a141351e59782c31229bccaa0bff2e869580
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/22/2019
ms.locfileid: "74400966"
---
# <a name="monitor-loads-into-parallel-data-warehouse"></a>Überwachen der Auslastung in parallele Data Warehouse
Überwachen Sie aktive und aktuelle ["dwloader-Lade](dwloader.md) Vorgänge mithilfe der Verwaltungskonsole von Analytics Platform System (APS) oder der [System Sichten](https://azure.microsoft.com/documentation/articles/sql-data-warehouse-reference-tsql-system-views/)parallel Data Warehouse (PDW). 
  
> [!TIP]  
> Einige Ladungen werden mithilfe von INSERT-Anweisungen oder Business Intelligence Tools initiiert, die SQL-Anweisungen verwenden, um die Auslastung auszuführen. 

<!-- MISSING LINKS
To monitor this type of load, see [Monitoring Active Queries](monitor-active-queries.md).  
-->
  
## <a name="prerequisites"></a>Voraussetzungen  
Unabhängig von der Methode, die zum Überwachen einer Last verwendet wird, muss die Anmeldung über die Berechtigung zum Zugriff auf die zugrunde liegenden Datenquellen verfügen. 

<!-- MISSING LINKS
For the permissions to grant, see "Use All of the Admin Console" in [Grant Permissions to Use the Admin Console](grant-permissions-admin-console.md). 

--> 
  
## <a name="monitoring-loads"></a>Überwachen von Lasten  
In den folgenden Abschnitten wird beschrieben, wie Ladungen überwacht werden.  
  
### <a name="to-monitor-loads-by-using-the-admin-console"></a>So überwachen Sie Ladevorgänge mithilfe der Verwaltungskonsole  
  
1.  Melden Sie sich bei der Verwaltungskonsole an. <!-- MISSING LINKS See [Monitor the Appliance by Using the Admin Console;](monitor-admin-console.md) for instructions. --> 
  
2.  Klicken Sie im oberen **Menü auf Laden**. Sie sehen eine sortierbare Tabelle mit allen aktuellen und aktiven Ladevorgängen sowie zusätzlichen Informationen, z. b. ob die Last abgeschlossen wurde oder noch aktiv ist. Klicken Sie auf die Spaltenüberschriften, um die Zeilen zu sortieren.  
  
3.  Klicken Sie in der linken Spalte auf die Load- **ID** , um weitere Details für eine bestimmte Auslastung anzuzeigen. In der Detailansicht können Sie den Fortschritt für jeden Schritt der Auslastung anzeigen.  
  
In diesen System Sichten finden Sie Informationen zu den Metadaten zu der Auslastung, die in der Verwaltungskonsole angezeigt wird:  
  
-   [sys. dm_pdw_exec_requests](../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md)  
  
-   [sys.pdw_loader_run_stages](https://msdn.microsoft.com/library/mt203879.aspx)  
  
-   [sys. pdw_loader_backup_runs](../relational-databases/system-catalog-views/sys-pdw-loader-backup-runs-transact-sql.md)  
  
-   [sys. pdw_loader_backup_run_details](../relational-databases/system-catalog-views/sys-pdw-loader-backup-run-details-transact-sql.md)  
  
### <a name="to-monitor-loads-by-using-system-views"></a>So überwachen Sie Ladungen mithilfe von System Sichten  
Führen Sie die folgenden Schritte aus, um aktive und aktuelle Lasten mithilfe SQL Server PDW Ansichten zu überwachen. Informationen zu den Spalten und möglichen Werten, die von der Sicht zurückgegeben werden, finden Sie in der Dokumentation für diese Ansicht.  
  
1.  Suchen Sie in der [sys. dm_pdw_exec_requests](../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md) -Sicht nach der Lade Befehlszeile in der- `command` Spalte für diese Ansicht. `request_id`  
  
    Der folgende Befehl gibt z. b. den Befehls Text und den aktuellen Status sowie `request_id`den zurück.  
  
    ```sql  
    SELECT request_id, status, command FROM sys.dm_pdw_exec_requests;  
    ```  
  
2.  Verwenden Sie `request_id` , um zusätzliche Informationen für die Last mithilfe der [sys. pdw_loader_run_stages](../relational-databases/system-catalog-views/sys-pdw-loader-run-stages-transact-sql.md) -und [sys. pdw_loader_backup_run_details](../relational-databases/system-catalog-views/sys-pdw-loader-backup-run-details-transact-sql.md) -Sichten abzurufen. Beispielsweise gibt die folgende Abfrage die `run_id` Informationen zu Beginn, Ende und Dauer der Auslastung sowie alle Fehler sowie Informationen zur Anzahl der verarbeiteten Zeilen zurück:  
  
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
  
