---
title: Überwachen aktive Abfragen – Parallel Data Warehouse | Microsoft-Dokumentation
description: Verwenden Sie die Verwaltungskonsole und Parallel Data Warehouse-Systemsichten, um aktive Abfragen in Analytics Platform System überwachen.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 65d656b02ef0d726292a7d37aef565bf508d7662
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67960493"
---
# <a name="monitoring-active-queries---parallel-data-warehouse"></a>Überwachen aktiver Abfragen – Parallel Data Warehouse
In diesem Artikel zeigt, wie Sie mit der Verwaltungskonsole und die SQL Server-PDW-Systemsichten zum Überwachen von aktiven Abfragen. Finden Sie unter [Überwachen der Appliance mithilfe der Verwaltungskonsole](monitor-the-appliance-by-using-the-admin-console.md) und [Systemsichten](tsql-system-views.md) für Informationen zu diesen Tools.  
  
## <a name="prerequisites"></a>Vorraussetzungen  
Unabhängig von der Methode, die zum Überwachen von aktiven Abfragen verwendet wird, muss die Anmeldung in in "Verwenden alle von der Verwaltungskonsole" beschriebenen Berechtigungen besitzen [Erteilen von Berechtigungen zum Verwenden der Verwaltungskonsole](grant-permissions.md#grant-permissions-to-use-the-admin-console).  
  
## <a name="PermsAdminConsole"></a>Überwachen aktiver Abfragen  
Sowohl der Verwaltungskonsole und die SQL Server-PDW-Systemsichten können verwendet werden, um aktive Abfragen zu überwachen. Führen Sie die folgenden Anweisungen aus.  
  
### <a name="to-monitor-active-queries-by-using-the-admin-console"></a>Zum Überwachen von aktiven Abfragen mithilfe der Verwaltungskonsole  
  
1.  Melden Sie sich bei der Verwaltungskonsole. Finden Sie unter [Überwachen der Appliance mithilfe der Verwaltungskonsole](monitor-the-appliance-by-using-the-admin-console.md) Anweisungen.  
  
2.  Klicken Sie auf die im oberen Menü auf **Abfragen**. Es wird eine Tabelle mit grundlegenden Informationen zu den neuesten Abfragen angezeigt, auf dem Gerät, einschließlich der Anmeldename, übermittelt die Abfrage, die Start- und Endzeiten für die Abfrage und den aktuellen Status der Abfrage hat.  
  
3.  Um den Abfragebefehl anzuzeigen, zeigen Sie mit der Maus die Abfrage-ID in der linken Spalte für diese Zeile.  
  
    Ausführlichere Informationen für eine bestimmte Abfrage erhalten, klicken Sie auf der Abfrage-ID Informationen, die als auch die vollständige Abfrage der Abfrageplan mit Statusinformationen für jeden Schritt in die Ausführung der Abfrage wird angezeigt. Wenn keine Fehler zurückgegeben wurden, sehen Sie auch detaillierte Informationen zu den Fehlern. <!-- MISSING LINKS See [Understanding Query Plans &#40;SQL Server PDW&#41;](../sqlpdw/understanding-query-plans-sql-server-pdw.md) for information on how to interpret the query plan information available in the Admin Console.  -->
  
### <a name="to-monitor-active-queries-by-using-the-system-views"></a>Zum Überwachen von aktiven Abfragen mithilfe von Systemsichten  
Die primäre Systemsicht, die zum Überwachen von Abfragen ist [dm_pdw_exec_requests](../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md). Verwenden Sie diese Systemansicht zum Suchen der `request_id` für eine Abfrage aktiv "oder" letzte, basierend auf den Text der Abfrage.  
  
Z. B. die folgende Abfrage sucht die `request_id` und der aktuelle `status` für jede Abfrage, die wählt alle Spalten aus der `memberAddresses` Tabelle.  
  
```sql  
SELECT request_id, command, status   
FROM sys.dm_pdw_exec_requests   
WHERE command   
LIKE '%SELECT * FROM db1..memberAddresses%';  
```  
  
Nach der `request_id` wurde für eine Abfrage identifiziert wird, verwenden Sie die anderen Informationen in den `dm_pdw_exec_requests` -Tabelle ab, um Informationen über die Verarbeitung der Abfrage finden, oder verwenden Sie [dm_pdw_request_steps](../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md) Anzeigen des Status der einzelnen Abfrage Schritte für die Ausführung der Abfrage.  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
