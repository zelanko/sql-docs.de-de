---
title: Workload-Verwaltungsaufgaben – Analytics Platform System | Microsoft-Dokumentation
description: Workload-Verwaltungsaufgaben in Analytics Platform System.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 8e538b96c482a6a16fffcfdac197e62885426b52
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63243801"
---
# <a name="workload-management-tasks-in-analytics-platform-system"></a>Workload von Verwaltungsaufgaben in Analytics Platform System
Workload-Verwaltungsaufgaben in Analytics Platform System.

## <a name="view-login-members-of-each-resource-class"></a>Anzeigen der Anmeldung Mitglieder jeder Ressourcenklasse
Beschreibt, wie die Anmeldung Mitglied jeder Resource-Klasse-Serverrolle in SQL Server PDW angezeigt. Verwenden Sie diese Abfrage, um zu ermitteln, die Klasse der Ressourcen für Anforderungen, die von jeder Anmeldung übermittelt wurden.  
  
Beschreibungen der Resource-Klasse, finden Sie unter [Workloadverwaltung](workload-management.md).  
  
Diese Abfrage zeigt die Liste der Mitglieder für jede Ressourcenklasse. Es gibt drei Ressourcenklassen, "mediumrc", "largerc" und "xlargerc".  
  
```sql  
SELECT l.name AS [member], r.name AS [server role]  
FROM sys.server_role_members AS rm  
JOIN sys.server_principals AS l  
  ON l.principal_id = rm.member_principal_id  
JOIN  
  sys.server_principals AS r  
  ON r.principal_id = rm.role_principal_id  
WHERE  
  ( l.[type] = 'S' OR l.[type] = 'U' OR l.[type] = 'G' )  
  AND r.[type] = 'R'  
  AND r.[name] in ('mediumrc', 'largerc', 'xlargerc');  
```  
  
Wenn eine Anmeldung nicht in dieser Liste enthalten ist, erhalten ihre Anforderungen die Standardressourcen. Wenn eine Anmeldung ein Mitglied von mehr als einer Ressourcenklasse ist, hat die größte Klasse Vorrang.  
  
In der Ressourcenzuordnung aufgelisteten [Workloadverwaltung](workload-management.md).  
  
## <a name="change-the-system-resources-allocated-to-a-request"></a>Ändern Sie die Systemressourcen auf eine Anforderung
Beschreibt, wie Sie herausfinden, welche Ressource Klasse, die eine SQL Server-PDW-Anforderung unter ausgeführt wird, und dann auf die Systemressourcen für diese Anforderung zu ändern. Ändern die Ressourcen aus, für eine Anforderung erfordert eine Änderung der Ressource Mitgliedschaft des Anmeldenamens übermitteln der Anforderung, mit der [ALTER SERVER ROLE](../t-sql/statements/alter-server-role-transact-sql.md) Anweisung.  
  
### <a name="step-1-determine-the-resource-class-for-the-login-running-the-request"></a>Schritt 1: Bestimmen Sie die Ressourcenklasse für die Anmeldung, die Anforderung wird ausgeführt.  
Diese Abfrage zeigt die Anmeldungen, die Elemente der serverrollenmitgliedschaften Resource-Klasse. Es gibt drei Ressourcenklassen, **"mediumrc"**, **"largerc"**, und **"xlargerc"**.  
  
> [!IMPORTANT]  
> Diese Abfrage muss ausgeführt werden, indem Sie eine Anmeldung **CONTROL SERVER** Berechtigung. Wenn durch eine Anmeldung ohne ausgeführt **CONTROL SERVER** -Berechtigung, diese Abfrage nur die Rollenmitgliedschaften für den aktuellen Anmeldenamen zurückgegeben.  
  
```sql  
SELECT l.name AS [member], r.name AS [server role]  
FROM sys.server_role_members AS rm  
JOIN sys.server_principals AS l  
  ON l.principal_id = rm.member_principal_id  
JOIN  
  sys.server_principals AS r  
  ON r.principal_id = rm.role_principal_id  
WHERE  
  l.[type] = 'S'   
  AND r.[type] = 'R'  
  AND r.[name] in ('mediumrc', 'largerc', 'xlargerc');  
GO  
```  
  
Wenn es keine Anmeldungen, die Mitglieder einer Datenbankrolle Resource-Klasse sind sind, wird die daraus resultierende Tabelle leer sein. In diesem Fall, wenn die Abfrage eine Anmeldung mit dem Namen Ching zurückgibt, erhalten klicken Sie dann Wenn Ching eine Anforderung übermittelt die Anforderung standardmäßig Systemressourcen, die kleiner als die Systemressourcen des Ressource-Klasse sind. Wenn eine Anmeldung ein Mitglied von mehr als einer Ressourcenklasse ist, hat die größte Klasse Vorrang.  
  
Eine Liste der Ressourcenzuordnung für jede Ressourcenklasse, finden Sie unter [Workloadverwaltung](workload-management.md).  
  
### <a name="step-2-run-the-request-under-a-login-with-different-resource-class-membership"></a>Schritt 2: Führen Sie die Anforderung unter eine Anmeldung mit anderen Ressource Mitgliedschaft  
Es gibt zwei Möglichkeiten, eine Anforderung mit entweder größer oder kleiner Systemressourcen auszuführen:  
  
-   Führen Sie die Anforderung unter einem anderen Anmeldenamen, der einen größeren oder kleineren Ressourcenklasse angehört.  
  
-   Fügen Sie die erforderlichen Anmelde, eines der Klasse-Ressourcenrollen. Wählen Sie diese Option mit Vorsicht, durch das Ändern der Ressourcenklasse für die Anmeldung wird der Systemebene für die Ressource für alle Anforderungen, die von der Anmeldung gesendet.  
  
Nehmen wir an, dass Ching ein Mitglied der Serverrolle "largerc" ist. Das folgende Beispiel zeigt, wie die Serverrolle "xlargerc" Anmeldung Ching hinzugefügt wird.  
  
```sql  
ALTER SERVER ROLE xlargerc ADD MEMBER Ching;  
```  
  
Ching ist jetzt ein Mitglied der "largerc" und die Serverrollen "xlargerc". Ching Anforderungen sendet, werden die Anforderungen die Systemressourcen "xlargerc" empfangen.  
  
Im folgenden Beispiel wird Ching zurück, der Server-Rolle "mediumrc".  Um der neuen Rolle zu ändern, muss die Anmeldung entfernt von "xlargerc" und "largerc" Server-Rollen, und der Server-Rolle "mediumrc" hinzugefügt.  
  
```sql  
-- Move login Ching back to using medium system resources for requests.  
ALTER SERVER ROLE xlargerc DROP MEMBER Ching;  
ALTER SERVER ROLE largerc DROP MEMBER Ching;  
ALTER SERVER ROLE mediumrc ADD MEMBER Ching;  
```  
  
Ching ist jetzt ein Mitglied der Serverrolle "mediumrc".  Im folgende Beispiel ändert die Ching, um die System-Standardressourcen für Anforderungen zu erhalten.  
  
```sql  
-- Move login Ching to use the default system resources for requests.  
ALTER SERVER ROLE mediumrc DROP MEMBER Ching;  
```  
  
Weitere Informationen zu Resource-Klasse-Rollenmitgliedschaft zu ändern, finden Sie unter [ALTER SERVER ROLE](../t-sql/statements/alter-server-role-transact-sql.md).  

## <a name="change-a-login-to-the-default-system-resources-for-its-requests"></a>Ändern Sie eine Anmeldung auf die Standard-System-Ressourcen für ihre Anforderungen
Beschreibt, wie so ändern Sie die System-ressourcenzuweisungen, die eine SQL Server-PDW-Anmeldung bei der standardmäßigen Dienstkontingente zugewiesen. 
  
Beschreibungen der Resource-Klasse, finden Sie unter [Workloadverwaltung](workload-management.md)  
  
Wenn eine Anmeldung nicht Mitglied einer Serverrolle des Ressource-Klasse ist, erhalten Anforderungen bei der Anmeldung übermittelt die Standarddauer von Systemressourcen.  
  
Nehmen wir an der Anmeldung, die Matt derzeit Mitglied aller Serverfunktionen von Resource-Klasse und zurück an die Anforderungen, die nur die Standardressourcen erhalten, dass wiederherstellen möchte.  Das folgende Beispiel weist die Standardressourcen, Matt Anforderungen durch seine Mitgliedschaft aus allen drei Ressourcen-Klasse-Server-Rollen löschen.  
  
```sql  
--Give the requests submitted by Matt the default system resources   
--by dropping Matt from all resource class server roles.  
ALTER SERVER ROLE XLargeRC DROP MEMBER Matt;  
ALTER SERVER ROLE LargeRC DROP MEMBER Matt;  
ALTER SERVER ROLE MediumRC DROP MEMBER Matt;  
```  
  
## <a name="display-the-number-of-concurrency-slots-needed-for-a-waiting-request"></a>Anzeigen, die die Anzahl von Parallelitätsslots für eine wartende anfordern erforderlich
Beschreibt, wie die Anzahl der Parallelität herausfinden, die Slots von einer Anforderung, die darauf warten benötigt werden, auf SQL Server PDW ausgeführt werden.  
  
Weitere Informationen finden Sie unter [Workloadverwaltung](workload-management.md).  
  
Eine Anforderung konnte zu lange ohne die erste Ausführung wartet. Eine der Möglichkeiten, um anforderungsprobleme zu behandeln ist, Suchen nach der Anzahl von parallelitätsslots, die die Anforderung benötigt.  Das folgende Beispiel zeigt die Anzahl von parallelitätsslots, die von jeder wartender Anforderungen benötigt werden.  
  
```sql  
--Display the number of concurrency slots required   
--for each request that is waiting to run.  
SELECT request_id, concurrency_slots_used AS [Slots Needed], resource_class AS [Resource Class]  
FROM sys.dm_pdw_resource_waits;  
```  
  
  
## <a name="see-also"></a>Siehe auch  
[Workloadverwaltung](workload-management.md)  
  
