---
title: Workloadverwaltungsaufgaben
description: Verwaltungsaufgaben für die Arbeitsauslastung in Analytics Platform System.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 88d95eb0a2e0805930cb5f01f5af05b8fc6b3f2e
ms.sourcegitcommit: 33e774fbf48a432485c601541840905c21f613a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "74399416"
---
# <a name="workload-management-tasks-in-analytics-platform-system"></a>Verwaltungsaufgaben für die Arbeitsauslastung in Analytics Platform System
Verwaltungsaufgaben für die Arbeitsauslastung in Analytics Platform System.

## <a name="view-login-members-of-each-resource-class"></a>Anmelde Mitglieder jeder Ressourcen Klasse anzeigen
Beschreibt, wie die Anmeldungs Mitglieder jeder Ressourcen Klassen-Server Rolle in SQL Server PDW angezeigt werden. Verwenden Sie diese Abfrage, um die Klasse von Ressourcen zu ermitteln, die von den einzelnen Anmelde Informationen übermittelt werden.  
  
Ressourcen Klassen Beschreibungen finden Sie unter [workloadverwaltung](workload-management.md).  
  
Diese Abfrage zeigt die Mitgliedschafts Liste für jede Ressourcen Klasse an. Es gibt drei Ressourcen Klassen, Medium RC, largerc und xlargerc.  
  
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
  
Wenn eine Anmeldung nicht in dieser Liste enthalten ist, werden die Standard Ressourcen von Ihren Anforderungen empfangen. Wenn eine Anmeldung Mitglied von mehr als einer Ressourcen Klasse ist, hat die größte Klasse Vorrang.  
  
Die Ressourcenzuweisungen werden in der [workloadverwaltung](workload-management.md)aufgeführt.  
  
## <a name="change-the-system-resources-allocated-to-a-request"></a>Ändern der einer Anforderung zugeordneten System Ressourcen
Beschreibt, wie ermittelt wird, unter welcher Ressourcen Klasse eine SQL Server PDW Anforderung ausgeführt wird, und wie die Systemressourcen für diese Anforderung geändert werden. Wenn Sie die Ressourcen für eine Anforderung ändern, müssen Sie die Ressourcen Klassenmitgliedschaft der Anmeldung, die die Anforderung sendet, mithilfe der [Alter Server Role](../t-sql/statements/alter-server-role-transact-sql.md) -Anweisung ändern.  
  
### <a name="step-1-determine-the-resource-class-for-the-login-running-the-request"></a>Schritt 1: Ermitteln der Ressourcen Klasse für den Anmelde Namen, der die Anforderung durchführt.  
Diese Abfrage zeigt Anmeldungen an, die Mitglieder der Server Rollen Mitgliedschaften der Ressourcen Klasse sind. Es gibt drei Ressourcen Klassen, **Medium RC**, **largerc**und **xlargerc**.  
  
> [!IMPORTANT]  
> Diese Abfrage muss von einem Anmelde Namen ausgeführt werden, der über die **Control Server** -Berechtigung verfügt. Bei Ausführung durch eine Anmeldung ohne **Control Server** -Berechtigung gibt diese Abfrage nur die Rollen Mitgliedschaften für den aktuellen Anmelde Namen zurück.  
  
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
  
Wenn keine Anmeldungen vorhanden sind, die Mitglieder einer Ressourcen Klassen-Server Rolle sind, ist die resultierende Tabelle leer. Wenn in diesem Fall die Abfrage einen Anmelde Namen mit dem Namen "Ching" zurückgibt, empfängt die Anforderung beim Senden einer Anforderung die Standardsystem Ressourcen, die kleiner sind als die Ressourcen Klassensystem Ressourcen. Wenn eine Anmeldung Mitglied von mehr als einer Ressourcen Klasse ist, hat die größte Klasse Vorrang.  
  
Eine Liste der Ressourcen Zuordnungen für jede Ressourcen Klasse finden Sie [Workload Management](workload-management.md)unter workloadverwaltung.  
  
### <a name="step-2-run-the-request-under-a-login-with-different-resource-class-membership"></a>Schritt 2: Ausführen der Anforderung unter einem Anmelde Namen mit einer anderen Ressourcen Klassenmitgliedschaft  
Es gibt zwei Möglichkeiten, eine Anforderung mit größeren oder kleineren Systemressourcen auszuführen:  
  
-   Führen Sie die Anforderung unter einem anderen Anmelde Namen aus, der Mitglied einer größeren oder geringeren Ressourcen Klasse ist.  
  
-   Fügen Sie einer der Ressourcen Klassen Rollen die erforderliche Anmeldung hinzu. Wählen Sie diese Option mit Vorsicht aus. Wenn Sie die Ressourcen Klasse für die Anmeldung ändern, ändert sich die Systemressourcen Ebene für alle Anforderungen, die von der Anmeldung gesendet werden.  
  
Angenommen, das Ching ist ein Mitglied der largerc-Server Rolle. Im folgenden Beispiel wird gezeigt, wie Sie der xlargerc-Server Rolle Anmelde Informationen hinzufügen.  
  
```sql  
ALTER SERVER ROLE xlargerc ADD MEMBER Ching;  
```  
  
Das Ching ist nun ein Mitglied der Server Rolle largerc und xlargerc. Wenn Anforderungen gesendet werden, erhalten die Anforderungen die xlargerc-Systemressourcen.  
  
Im folgenden Beispiel wird der Vorgang zurück zur mediumrc-Server Rolle verschoben.  Um zur neuen Rolle zu wechseln, muss die Anmeldung aus xlargerc-und largerc-Server Rollen entfernt und der mediumrc-Server Rolle hinzugefügt werden.  
  
```sql  
-- Move login Ching back to using medium system resources for requests.  
ALTER SERVER ROLE xlargerc DROP MEMBER Ching;  
ALTER SERVER ROLE largerc DROP MEMBER Ching;  
ALTER SERVER ROLE mediumrc ADD MEMBER Ching;  
```  
  
Das Ching ist nun ein Mitglied der medienrc-Server Rolle.  Im folgenden Beispiel wird die Verarbeitung so geändert, dass Sie die Standardsystem Ressourcen für Anforderungen hat.  
  
```sql  
-- Move login Ching to use the default system resources for requests.  
ALTER SERVER ROLE mediumrc DROP MEMBER Ching;  
```  
  
Weitere Informationen zum Ändern der Rollen Mitgliedschaft in einer Ressourcen Klasse finden Sie unter [Alter Server Role](../t-sql/statements/alter-server-role-transact-sql.md).  

## <a name="change-a-login-to-the-default-system-resources-for-its-requests"></a>Ändern eines Anmelde namens in die Standardsystem Ressourcen für seine Anforderungen
Beschreibt, wie die Systemressourcen Zuordnungen geändert werden, die einer SQL Server PDW-Anmeldung zugewiesen sind, auf die Standard Beträge. 
  
Ressourcen Klassen Beschreibungen finden Sie unter [workloadverwaltung](workload-management.md) .  
  
Wenn ein Anmelde Name kein Mitglied einer Ressourcen Klassen-Server Rolle ist, erhalten die von der Anmeldung übermittelten Anforderungen die Standardmenge an Systemressourcen.  
  
Angenommen, der Anmelde Name Matt ist zurzeit ein Mitglied aller Ressourcen Klassen-Server Rollen und möchte zurückkehren, dass Anforderungen nur die Standard Ressourcen erhalten.  Im folgenden Beispiel werden die Standard Ressourcen zu den Anforderungen von Matt zugewiesen, indem die Mitgliedschaft von allen drei Ressourcen Klassen-Server Rollen gelöscht wird.  
  
```sql  
--Give the requests submitted by Matt the default system resources   
--by dropping Matt from all resource class server roles.  
ALTER SERVER ROLE XLargeRC DROP MEMBER Matt;  
ALTER SERVER ROLE LargeRC DROP MEMBER Matt;  
ALTER SERVER ROLE MediumRC DROP MEMBER Matt;  
```  
  
## <a name="display-the-number-of-concurrency-slots-needed-for-a-waiting-request"></a>Anzeigen der Anzahl von Parallelitäts Slots, die für eine wartende Anforderung benötigt werden
Beschreibt, wie Sie ermitteln können, wie viele Parallelitäts Slots von einer Anforderung benötigt werden, die auf SQL Server PDW ausgeführt wird.  
  
Weitere Informationen finden Sie unter [workloadverwaltung](workload-management.md).  
  
Eine Anforderung kann zu lange warten, ohne ausgeführt zu werden. Eine der Möglichkeiten zur Problembehandlung bei der Anforderung besteht darin, die Anzahl der Parallelitäts Slots zu prüfen, die für die Anforderung erforderlich sind.  Das folgende Beispiel zeigt die Anzahl der Parallelitäts Slots, die für jede wartende Anforderung benötigt werden.  
  
```sql  
--Display the number of concurrency slots required   
--for each request that is waiting to run.  
SELECT request_id, concurrency_slots_used AS [Slots Needed], resource_class AS [Resource Class]  
FROM sys.dm_pdw_resource_waits;  
```  
  
  
## <a name="see-also"></a>Weitere Informationen  
[Workloadverwaltung](workload-management.md)  
  
