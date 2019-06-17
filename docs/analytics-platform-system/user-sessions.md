---
title: Benutzersitzungen in Analytics Platform System | Microsoft-Dokumentation"
description: Benutzersitzungen in Analytics Platform System Parallel Data Warehouse.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 33bf052e27640ee08784927351579378bffbec2b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63316358"
---
# <a name="user-sessions-in-analytics-platform-system"></a>Benutzersitzungen in Analytics Platform System
Eine Anmeldung mit den entsprechenden Berechtigungen kann die Sitzungen, die von der alle Anmeldenamen auf eine SQL Server-PDW-Appliance, einschließlich der Durchführung dieser Aktionen verwalten:  
  
-   Zeigen Sie die aktuellen Sitzungen auf dem Gerät, u. a. aktive und im Leerlauf befindet.  
  
-   Zeigen Sie die aktiven und kürzlich vorgenommene Abfragen für eine Sitzung an.  
  
-   Aktive Sitzungen zu beenden.  
  
Diese Aktionen können ausgeführt werden, indem Sie entweder die [Überwachen der Appliance mithilfe der Verwaltungskonsole](monitor-the-appliance-by-using-the-admin-console.md) oder [Systemsichten](tsql-system-views.md) über SQL-Befehlen, wie unten dargestellt.  
  
Die erforderlichen Berechtigungen zum Verwalten von Sitzungen mit beiden Methoden sind identisch und werden in beschrieben [Erteilen von Berechtigungen zum Verwalten von Anmeldungen, Benutzer und Datenbankrollen](grant-permissions.md#grant-permissions-to-manage-logins-users-and-database-roles).  
  
## <a name="manage-sessions-by-using-the-admin-console"></a>Verwalten von Sitzungen mit der Verwaltungskonsole  
  
### <a name="to-view-current-sessions-by-using-the-admin-console"></a>So zeigen Sie aktuelle Sitzungen mit der Verwaltungskonsole  
  
1.  Klicken Sie auf die im oberen Menü auf **Sitzungen**.  
  
2.  Die resultierende Liste zeigt alle aktuellen Sitzungen. Um nur die Sitzungen "Aktiv" oder "Idle" anzuzeigen, klicken Sie auf die **Status** Spaltenheader, um die Ergebnisse nach Status sortieren.  
  
### <a name="to-view-active-and-recent-queries-for-a-session-by-using-the-admin-console"></a>So zeigen aktive und kürzlich vorgenommene Abfragen für eine Sitzung mit der Verwaltungskonsole  
  
1.  Klicken Sie auf die im oberen Menü auf **Sitzungen**.  
  
2.  Klicken Sie in der Ergebnisliste auf die gewünschte Sitzung-ID der Sitzung.  
  
3.  Die resultierende Liste der Abfragen zeigt die aktuellen Abfragen für die Sitzung. Informationen zum Anzeigen von Abfragedetails können, finden Sie unter [überwachen aktiver Abfragen](monitoring-active-queries.md).  
  
### <a name="to-end-sessions-by-using-the-admin-console"></a>Um Sitzungen zu beenden, mithilfe der Verwaltungskonsole  
  
1.  Klicken Sie auf die im oberen Menü auf **Sitzungen**.  
  
2.  Suchen Sie die Sitzungs-ID für die Sitzung abgebrochen.  
  
3.  Klicken Sie auf das rote **X** links neben die Sitzungs-ID zum Beenden der Sitzung. Nur Sitzungen mit dem Status 'Aktiv' oder 'Im Leerlauf' ein rotes **X**, sondern nur diese Sitzungen beendet werden können.  
  
## <a name="manage-sessions-by-using-system-views-and-sql-commands"></a>Verwalten von Sitzungen mit Systemsichten und SQL-Befehle  
  
### <a name="to-view-current-sessions-by-using-system-views"></a>So zeigen Sie aktuelle Sitzungen Verwenden von Systemansichten  
Verwendung [dm_pdw_exec_sessions](../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md) zum Generieren einer Liste aktueller Sitzungen.  
  
In diesem Beispiel gibt die Sitzungs-ID, Login_name und Status für alle Sitzungen, die mit dem Status 'Active' oder "Im Leerlauf" zurück.  
  
```sql  
SELECT session_id, login_name, status FROM sys.dm_pdw_exec_sessions WHERE status='Active' OR status='Idle';  
```  
  
### <a name="to-view-active-and-recent-queries-for-a-session-by-using-system-views"></a>So zeigen Sie aktive und kürzlich vorgenommene Abfragen für eine Sitzung mithilfe von Systemsichten  
Um die aktiven und kürzlich abgeschlossenen Abfragen, die einer Sitzung zugeordneten anzuzeigen, verwenden Sie die [dm_pdw_exec_sessions](../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md) und [dm_pdw_exec_requests](../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md) Ansichten. Diese Abfrage gibt eine Liste aller aktiven oder im Leerlauf Sitzungen sowie alle aktiven "oder" letzten Abfragen, die jede Sitzungs-ID zugeordnet  
  
```sql  
SELECT es.session_id, es.login_name, es.status AS sessionStatus,   
er.request_id, er.status AS requestStatus, er.command   
FROM sys.dm_pdw_exec_sessions es   
LEFT OUTER JOIN sys.dm_pdw_exec_requests er   
ON (es.session_id=er.session_id)   
WHERE (es.status='Active' OR es.status='Idle') AND   
(er.status!= 'Completed' AND er.status!= 'Failed' AND er.status!= 'Cancelled');  
```  
  
### <a name="to-end-sessions-by-using-sql-commands"></a>Um Sitzungen zu beenden, mithilfe von SQL-Befehlen  
Verwenden der [KILL](../t-sql/language-elements/kill-transact-sql.md) Befehl aus, um eine aktuelle Sitzung zu beenden. Sie benötigen die Sitzungs-ID für den Prozess beendet wurde, die mit der [dm_pdw_exec_sessions](../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md) anzeigen.  
  
Wählen Sie in diesem Beispiel die Login_name, Sitzungs-ID und Statuswerte, um eine Sitzung basierend auf den Anmeldenamen zu finden.  
  
```sql  
SELECT session_id, login_name, status FROM sys.dm_pdw_exec_sessions;  
```  
  
Sitzungen mit dem Status "Aktiv" oder "Idle" können beendet werden, mithilfe des KILL-Befehls.  
  
```sql  
KILL 'SID137';  
```  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
