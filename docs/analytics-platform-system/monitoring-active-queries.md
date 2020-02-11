---
title: Aktive Abfragen überwachen
description: Verwenden Sie die Verwaltungskonsole und die parallelen Data Warehouse System Sichten, um aktive Abfragen auf dem Analytics Platform System zu überwachen.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 9157db745b999711966f0019747ba1d61823569e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "74400914"
---
# <a name="monitoring-active-queries---parallel-data-warehouse"></a>Überwachen aktiver Abfragen-parallele Data Warehouse
In diesem Artikel wird beschrieben, wie Sie mithilfe der-Verwaltungskonsole und der SQL Server PDW-System Sichten aktive Abfragen überwachen. Weitere Informationen zu diesen Tools finden [Sie unter Überwachen der Appliance mithilfe der Verwaltungskonsole](monitor-the-appliance-by-using-the-admin-console.md) und [System Sichten](tsql-system-views.md) .  
  
## <a name="prerequisites"></a>Voraussetzungen  
Unabhängig von der Methode, die zum Überwachen aktiver Abfragen verwendet wird, muss die Anmeldung über die Berechtigungen verfügen, die unter [Erteilen von Berechtigungen zur Verwendung der Verwaltungskonsole](grant-permissions.md#grant-permissions-to-use-the-admin-console)in "alle Verwaltungskonsole verwenden" beschrieben werden.  
  
## <a name="PermsAdminConsole"></a>Aktive Abfragen überwachen  
Die Verwaltungskonsole und die SQL Server PDW System Sichten können verwendet werden, um aktive Abfragen zu überwachen. Befolgen Sie die nachstehenden Anweisungen.  
  
### <a name="to-monitor-active-queries-by-using-the-admin-console"></a>So überwachen Sie aktive Abfragen mithilfe der Verwaltungskonsole  
  
1.  Melden Sie sich bei der Verwaltungskonsole an. Anweisungen hierzu finden [Sie unter Überwachen der Appliance mithilfe der Verwaltungskonsole](monitor-the-appliance-by-using-the-admin-console.md) .  
  
2.  Klicken Sie im oberen Menü auf **Abfragen**. Es wird eine Tabelle mit grundlegenden Informationen zu den letzten Abfragen auf dem Gerät angezeigt, einschließlich der Anmeldung, die die Abfrage übermittelt hat, der Start-und Endzeiten für die Abfrage und dem aktuellen Status der Abfrage.  
  
3.  Um den Abfragebefehl anzuzeigen, zeigen Sie mit dem Mauszeiger auf die Abfrage-ID in der linken Spalte für diese Zeile.  
  
    Wenn Sie ausführlichere Informationen zu einer bestimmten Abfrage anzeigen möchten, klicken Sie auf die Abfrage-ID. Informationen einschließlich der vollständigen Abfrage und des Abfrage Plans mit Statusinformationen zu den einzelnen Schritten in der Abfrage Ausführung werden angezeigt. Wenn Fehler zurückgegeben wurden, können Sie auch ausführliche Informationen zu den Fehlern sehen. <!-- MISSING LINKS See [Understanding Query Plans &#40;SQL Server PDW&#41;](../sqlpdw/understanding-query-plans-sql-server-pdw.md) for information on how to interpret the query plan information available in the Admin Console.  -->
  
### <a name="to-monitor-active-queries-by-using-the-system-views"></a>So überwachen Sie aktive Abfragen mithilfe der System Sichten  
Die primäre Systemsicht, die zum Überwachen von Abfragen verwendet wird, ist [sys. dm_pdw_exec_requests](../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md). Verwenden Sie diese Systemsicht, um `request_id` den für eine aktive oder aktuelle Abfrage basierend auf dem Abfragetext zu suchen.  
  
Die folgende Abfrage sucht z. b. `request_id` die und die `status` aktuelle für jede Abfrage, die alle Spalten aus `memberAddresses` der Tabelle auswählt.  
  
```sql  
SELECT request_id, command, status   
FROM sys.dm_pdw_exec_requests   
WHERE command   
LIKE '%SELECT * FROM db1..memberAddresses%';  
```  
  
Nachdem der `request_id` für eine Abfrage identifiziert wurde, verwenden Sie die anderen Informationen in der `dm_pdw_exec_requests` Tabelle, um die Verarbeitung der Abfrage zu ermitteln, oder verwenden Sie [sys. dm_pdw_request_steps](../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md) , um den Status der einzelnen Abfrage Schritte für die Abfrage Ausführung anzuzeigen.  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
