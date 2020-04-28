---
title: Benutzersitzungen
description: Benutzersitzungen in der parallelen Data Warehouse des Analytics-plattformsystems.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: a0e5b338cc616be214ef39527551ee4a6ffd8f56
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "74399399"
---
# <a name="user-sessions-in-analytics-platform-system"></a>Benutzersitzungen in Analytics Platform System
Ein Anmelde Name mit den entsprechenden Berechtigungen kann die Sitzungen aller Anmeldungen auf einer SQL Server PDW Appliance verwalten, einschließlich der folgenden Aktionen:  
  
-   Anzeigen der aktuellen Sitzungen auf dem Gerät, einschließlich aktiver und Leerlauf Sitzungen.  
  
-   Anzeigen der aktiven und letzten Abfragen für eine Sitzung.  
  
-   Beenden Sie aktive Sitzungen.  
  
Diese Aktionen können mithilfe der Befehle [Überwachen der Appliance mithilfe der Verwaltungskonsole](monitor-the-appliance-by-using-the-admin-console.md) oder mithilfe von SQL-Befehlen von [System Sichten](tsql-system-views.md) ausgeführt werden, wie unten dargestellt.  
  
Die erforderlichen Berechtigungen zum Verwalten von Sitzungen mit einer der beiden Methoden sind identisch. Sie werden unter [Erteilen von Berechtigungen zum Verwalten von Anmeldungen, Benutzern und Daten bankrollen](grant-permissions.md#grant-permissions-to-manage-logins-users-and-database-roles)beschrieben.  
  
## <a name="manage-sessions-by-using-the-admin-console"></a>Verwalten von Sitzungen mithilfe der Verwaltungskonsole  
  
### <a name="to-view-current-sessions-by-using-the-admin-console"></a>So zeigen Sie aktuelle Sitzungen mithilfe der Verwaltungskonsole an  
  
1.  Klicken Sie im oberen Menü auf **Sitzungen**.  
  
2.  In der resultierenden Liste werden alle aktuellen Sitzungen angezeigt. Um nur die Sitzungen "aktiv" oder "Leerlauf" anzuzeigen, klicken Sie auf die Spaltenüberschrift **Status** , um die Ergebnisse nach Status zu sortieren.  
  
### <a name="to-view-active-and-recent-queries-for-a-session-by-using-the-admin-console"></a>So zeigen Sie mithilfe der Verwaltungskonsole aktive und aktuelle Abfragen für eine Sitzung an  
  
1.  Klicken Sie im oberen Menü auf **Sitzungen**.  
  
2.  Klicken Sie in der Ergebnisliste auf die Sitzungs-ID der gewünschten Sitzung.  
  
3.  In der Liste der resultierenden Abfragen werden die aktuellen Abfragen für die Sitzung angezeigt. Weitere Informationen zum Anzeigen von Abfrage Details finden Sie unter über [Wachen aktiver Abfragen](monitoring-active-queries.md).  
  
### <a name="to-end-sessions-by-using-the-admin-console"></a>So beenden Sie Sitzungen mithilfe der Verwaltungskonsole  
  
1.  Klicken Sie im oberen Menü auf **Sitzungen**.  
  
2.  Die Sitzungs-ID für die Sitzung ermitteln, die abgebrochen werden soll.  
  
3.  Klicken Sie auf das rote **X** links neben der Sitzungs-ID, um die Sitzung zu beenden. Nur Sitzungen mit dem Status ' Active ' oder ' Idle ' haben ein rotes **X**; nur diese Sitzungen können beendet werden.  
  
## <a name="manage-sessions-by-using-system-views-and-sql-commands"></a>Verwalten von Sitzungen mithilfe von System Sichten und SQL-Befehlen  
  
### <a name="to-view-current-sessions-by-using-system-views"></a>So zeigen Sie aktuelle Sitzungen mithilfe von System Sichten an  
Verwenden Sie [sys. dm_pdw_exec_sessions](../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md) , um eine Liste der aktuellen Sitzungen zu generieren.  
  
In diesem Beispiel werden die session_id, login_name und der Status für alle Sitzungen mit dem Status "aktiv" oder "idle" zurückgegeben.  
  
```sql  
SELECT session_id, login_name, status FROM sys.dm_pdw_exec_sessions WHERE status='Active' OR status='Idle';  
```  
  
### <a name="to-view-active-and-recent-queries-for-a-session-by-using-system-views"></a>So zeigen Sie aktive und aktuelle Abfragen für eine Sitzung mithilfe von System Sichten an  
Wenn Sie die einer Sitzung zugeordneten aktiven und kürzlich abgeschlossenen Abfragen anzeigen möchten, verwenden Sie die Sichten [sys. dm_pdw_exec_sessions](../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md) und [sys. dm_pdw_exec_requests](../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md) . Diese Abfrage gibt eine Liste aller aktiven oder Leerlauf Sitzungen sowie alle aktiven oder aktuellen Abfragen zurück, die den einzelnen Sitzungs-IDs zugeordnet sind.  
  
```sql  
SELECT es.session_id, es.login_name, es.status AS sessionStatus,   
er.request_id, er.status AS requestStatus, er.command   
FROM sys.dm_pdw_exec_sessions es   
LEFT OUTER JOIN sys.dm_pdw_exec_requests er   
ON (es.session_id=er.session_id)   
WHERE (es.status='Active' OR es.status='Idle') AND   
(er.status!= 'Completed' AND er.status!= 'Failed' AND er.status!= 'Cancelled');  
```  
  
### <a name="to-end-sessions-by-using-sql-commands"></a>So beenden Sie Sitzungen mithilfe von SQL-Befehlen  
Verwenden Sie den [Kill](../t-sql/language-elements/kill-transact-sql.md) -Befehl, um eine aktuelle Sitzung zu beenden. Sie benötigen die Sitzungs-ID, um den Prozess zu beenden, der mithilfe der [sys. dm_pdw_exec_sessions](../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md) -Sicht abgerufen werden kann.  
  
Wählen Sie in diesem Beispiel die Werte login_name, session_id und Status aus, um eine Sitzung basierend auf dem Anmelde Namen zu suchen.  
  
```sql  
SELECT session_id, login_name, status FROM sys.dm_pdw_exec_sessions;  
```  
  
Sitzungen mit dem Status "aktiv" oder "im Leerlauf" können mit dem Kill-Befehl beendet werden.  
  
```sql  
KILL 'SID137';  
```  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
