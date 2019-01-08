---
title: Feste Datenbankrollen des SQL Server-Agents|Microsoft-Dokumente
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- roles [SQL Server], SQL Server Agent
- SQL Server Agent, roles
- SQLAgentUserRole database role
- SQLAgentReaderRole database role
- multiple roles
- security [SQL Server Agent], fixed database roles
- fixed database roles [SQL Server]
- SQLAgentOperatorRole database role
ms.assetid: 719ce56b-d6b2-414a-88a8-f43b725ebc79
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: dcb939b8eb04fafce163a395b05eb0e272977283
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52773772"
---
# <a name="sql-server-agent-fixed-database-roles"></a>Feste Datenbankrollen des SQL Server-Agents
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verfügt über die folgenden festen **msdb** -Datenbankrollen, mit denen Administratoren den Zugriff auf den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent besser steuern können. In der folgenden Auflistung sind die Rollen von den niedrigsten bis hin zu den höchsten Zugriffsberechtigungen enthalten:  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Wenn Benutzer, die nicht Mitglied einer dieser Rollen sind, mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]verbunden sind, ist der **SQL Server-Agent** -Knoten in Objekt-Explorer nicht sichtbar. Ein Benutzer muss Mitglied einer dieser festen Datenbankrollen oder der festen **sysadmin** -Serverrolle sein, um den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent verwenden zu können.  
  
## <a name="permissions-of-sql-server-agent-fixed-database-roles"></a>Berechtigungen der festen Datenbankrollen des SQL Server-Agents  
 Die Datenbankrollen-Berechtigungen des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents stehen konzentrisch zueinander in Beziehung: Rollen mit höheren Berechtigungen erben die Berechtigungen der Rollen mit niedrigeren Berechtigungen für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Objekte (einschließlich Warnungen, Operatoren, Aufträge, Zeitpläne und Proxys). Wenn z. B. Mitglieder der Rolle **SQLAgentUserRole** mit den niedrigsten Berechtigungen Zugriff auf „proxy_A“ haben, haben die Mitglieder von **SQLAgentReaderRole** und **SQLAgentOperatorRole** automatisch Zugriff auf diesen Proxy, selbst wenn ihnen der Zugriff auf „proxy_A“ nicht ausdrücklich erteilt wurde. Dies kann zu Sicherheitsrisiken führen, die in den folgenden Abschnitten zu den einzelnen Rollen erläutert werden.  
  
### <a name="sqlagentuserrole-permissions"></a>SQLAgentUserRole-Berechtigungen  
 **SQLAgentUserRole** ist die feste Datenbankrolle des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents mit den niedrigsten Berechtigungen. Sie hat lediglich Berechtigungen für Operatoren, lokale Aufträge und Auftragszeitpläne. Die Mitglieder von **SQLAgentUserRole** haben lediglich Berechtigungen für lokale Aufträge und Auftragszeitpläne, deren Besitzer sie sind. Sie können keine Multiserveraufträge (Master- und Zielserveraufträge) verwenden, und sie können den Auftragsbesitz nicht ändern, um Zugriff auf Aufträge zu erhalten, deren Besitzer sie nicht bereits sind. Die Mitglieder von**SQLAgentUserRole** können lediglich im Dialogfeld **Auftragsschritt-Eigenschaften** von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]eine Liste mit vorhandenen Proxys anzeigen. Nur der Knoten **Aufträge** in Objekt-Explorer von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ist für die Mitglieder von **SQLAgentUserRole** sichtbar.  
  
> [!IMPORTANT]  
>  Beachten Sie die Sicherheitsrisiken, bevor Sie den Mitgliedern **der**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-**Agent-Datenbankrollen** Proxyzugriff erteilen. **SQLAgentReaderRole** und **SQLAgentOperatorRole** sind automatisch Mitglieder von **SQLAgentUserRole**. Dies bedeutet, dass die Mitglieder von **SQLAgentReaderRole** und **SQLAgentOperatorRole** Zugriff auf alle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Proxys haben, die **SQLAgentUserRole** erteilt wurden und diese Proxys verwenden können.  
  
 Die folgende Tabelle enthält einen Überblick über die **SQLAgentUserRole** -Berechtigungen für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Objekte.  
  
|Aktion|Operatoren|Lokale Aufträge<br /><br /> (nur Aufträge mit Besitzern)|Auftragszeitpläne<br /><br /> (nur Zeitpläne mit Besitzern)|Proxys|  
|------------|---------------|----------------------------------------|------------------------------------------------|-------------|  
|Erstellen/Ändern/Löschen|Nein|Ja <sup>1</sup>|Ja|Nein|  
|Liste anzeigen (aufzählen)|Ja <sup>2</sup>|Ja|Ja|Ja <sup>3</sup>|  
|Aktivieren/Deaktivieren|Nein|Ja|Ja|Nicht verfügbar|  
|Eigenschaften anzeigen|Nein|Ja|Ja|Nein|  
|Ausführen/Beenden/Starten|Nicht verfügbar|Ja|Nicht verfügbar|Nicht verfügbar|  
|Auftragsverlauf anzeigen|Nicht verfügbar|Ja|Nicht verfügbar|Nicht verfügbar|  
|Auftragsverlauf löschen|Nicht verfügbar|Keine <sup>4</sup>|Nicht verfügbar|Nicht verfügbar|  
|Anfügen/Trennen|Nicht verfügbar|Nicht verfügbar|Ja|Nicht verfügbar|  
  
 <sup>1</sup> Auftragsbesitz nicht ändern.  
  
 <sup>2</sup> können Sie die Liste der verfügbaren Operatoren für die Verwendung in abrufen **Sp_notify_operator** und **Auftragseigenschaften** Dialogfeld von Management Studio.  
  
 <sup>3</sup> Liste der Proxys ist nur verfügbar, in der **Auftragsschritt-Eigenschaften** Dialogfeld von Management Studio.  
  
 <sup>4</sup> Mitglied **SQLAgentUserRole** muss explizit erteilt werden die EXECUTE-Berechtigung auf **Sp_purge_jobhistory** zum Löschen des Auftragsverlaufs für Aufträge, die sie besitzen. Sie können den Auftragsverlauf für keine anderen Aufträge löschen.  
  
### <a name="sqlagentreaderrole-permissions"></a>SQLAgentReaderRole-Berechtigungen  
 **SQLAgentReaderRole** enthält alle **SQLAgentUserRole** -Berechtigungen sowie die Berechtigungen zum Anzeigen der Liste verfügbarer Multiserveraufträge, ihrer Eigenschaften und ihres Verlaufs. Die Mitglieder dieser Rolle können auch die Liste aller verfügbaren Aufträge und Auftragszeitpläne sowie ihre Eigenschaften anzeigen, nicht nur die Aufträge und Auftragszeitpläne, deren Besitzer sie sind. Die Mitglieder von**SQLAgentReaderRole** können den Auftragsbesitz nicht ändern, um Zugriff auf Aufträge zu erhalten, deren Besitzer sie nicht bereits sind. Nur der Knoten **Aufträge** in Objekt-Explorer von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ist für die Mitglieder von **SQLAgentReaderRole** sichtbar.  
  
> [!IMPORTANT]  
>  Beachten Sie die Sicherheitsrisiken, bevor Sie den Mitgliedern **der**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-**Agent-Datenbankrollen** Proxyzugriff erteilen. Die Mitglieder von **SQLAgentReaderRole** sind automatisch auch Mitglieder von **SQLAgentUserRole**. Dies bedeutet, dass die Mitglieder von **SQLAgentReaderRole** Zugriff auf alle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Proxys haben, die **SQLAgentUserRole** erteilt wurden und diese Proxys verwenden können.  
  
 Die folgende Tabelle enthält einen Überblick über die **SQLAgentReaderRole** -Berechtigungen für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Objekte.  
  
|Aktion|Operatoren|Lokale Aufträge|Multiserveraufträge|Auftragszeitpläne|Proxys|  
|------------|---------------|----------------|----------------------|-------------------|-------------|  
|Erstellen/Ändern/Löschen|Nein|Ja <sup>1</sup> (nur Aufträge mit Besitzer)|Nein|Ja (nur Zeitpläne mit Besitzer)|Nein|  
|Liste anzeigen (aufzählen)|Ja <sup>2</sup>|Ja|Ja|Ja|Ja <sup>3</sup>|  
|Aktivieren/Deaktivieren|Nein|Ja (nur Aufträge mit Besitzer)|Nein|Ja (nur Zeitpläne mit Besitzer)|Nicht verfügbar|  
|Eigenschaften anzeigen|Nein|Ja|Ja|Ja|Nein|  
|Eigenschaften bearbeiten|Nein|Ja (nur Aufträge mit Besitzer)|Nein|Ja (nur Zeitpläne mit Besitzer)|Nein|  
|Ausführen/Beenden/Starten|Nicht verfügbar|Ja (nur Aufträge mit Besitzer)|Nein|Nicht verfügbar|Nicht verfügbar|  
|Auftragsverlauf anzeigen|Nicht verfügbar|Ja|Ja|Nicht verfügbar|Nicht verfügbar|  
|Auftragsverlauf löschen|Nicht verfügbar|Keine <sup>4</sup>|Nein|Nicht verfügbar|Nicht verfügbar|  
|Anfügen/Trennen|Nicht verfügbar|Nicht verfügbar|Nicht verfügbar|Ja (nur Zeitpläne mit Besitzer)|Nicht verfügbar|  
  
 <sup>1</sup> Auftragsbesitz nicht ändern.  
  
 <sup>2</sup> können Sie die Liste der verfügbaren Operatoren für die Verwendung in abrufen **Sp_notify_operator** und **Auftragseigenschaften** Dialogfeld von Management Studio.  
  
 <sup>3</sup> Liste der Proxys ist nur verfügbar, in der **Auftragsschritt-Eigenschaften** Dialogfeld von Management Studio.  
  
 <sup>4</sup> Mitglied **SQLAgentReaderRole** muss explizit erteilt werden die EXECUTE-Berechtigung auf **Sp_purge_jobhistory** zum Löschen des Auftragsverlaufs für Aufträge, die sie besitzen. Sie können den Auftragsverlauf für keine anderen Aufträge löschen.  
  
### <a name="sqlagentoperatorrole-permissions"></a>SQLAgentOperatorRole-Berechtigungen  
 **SQLAgentOperatorRole** ist die feste Datenbankrolle des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents mit den höchsten Berechtigungen. Sie enthält alle Berechtigungen von **SQLAgentUserRole** und **SQLAgentReaderRole**. Die Mitglieder dieser Rolle können auch die Eigenschaften für Operatoren und Proxys anzeigen und die verfügbaren Proxys und Warnungen auf dem Server aufzählen.  
  
 Die Mitglieder von**SQLAgentOperatorRole** haben zusätzliche Berechtigungen für lokale Aufträge und Zeitpläne. Sie können alle lokalen Aufträge ausführen, beenden oder starten, und sie können den Auftragsverlauf eines lokalen Auftrags auf dem Server löschen. Sie können auch alle lokalen Aufträge und Zeitpläne auf dem Server aktivieren und deaktivieren. Um lokale Aufträge oder Zeitpläne zu aktivieren oder zu deaktivieren, müssen die Mitglieder dieser Rolle die gespeicherten Prozeduren **sp_update_job** und **sp_update_schedule**verwenden. Nur die Parameter, die den Namen oder den Bezeichner des Auftrags oder Zeitplans sowie den **@enabled** -Parameter angeben, können von den Mitgliedern von **SQLAgentOperatorRole**eine Liste mit vorhandenen Proxys anzeigen. Wenn sie andere Parameter angeben, erzeugt die Ausführung dieser gespeicherten Prozeduren einen Fehler. Die Mitglieder von**SQLAgentOperatorRole** können den Auftragsbesitz nicht ändern, um Zugriff auf Aufträge zu erhalten, deren Besitzer sie nicht bereits sind.  
  
 Die Knoten **Aufträge**, **Warnungen**, **Operatoren**und **Proxys** in Objekt-Explorer von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] sind für die Mitglieder von **SQLAgentOperatorRole**sichtbar. Nur der Knoten **Fehlerprotokolle** ist für die Mitglieder dieser Rolle nicht sichtbar.  
  
> [!IMPORTANT]  
>  Beachten Sie die Sicherheitsrisiken, bevor Sie den Mitgliedern **der**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-**Agent-Datenbankrollen** Proxyzugriff erteilen. Die Mitglieder von **SQLAgentOperatorRole** sind automatisch auch Mitglieder von **SQLAgentUserRole** und **SQLAgentReaderRole**. Dies bedeutet, dass die Mitglieder von **SQLAgentOperatorRole** Zugriff auf alle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Proxys haben, die **SQLAgentUserRole** oder **SQLAgentReaderRole** erteilt wurden und diese Proxys verwenden können.  
  
 Die folgende Tabelle enthält einen Überblick über die **SQLAgentOperatorRole** -Berechtigungen für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Objekte.  
  
|Aktion|Benachrichtigungen|Operatoren|Lokale Aufträge|Multiserveraufträge|Auftragszeitpläne|Proxys|  
|------------|------------|---------------|----------------|----------------------|-------------------|-------------|  
|Erstellen/Ändern/Löschen|Nein|Nein|Ja <sup>2</sup> (nur Aufträge mit Besitzer)|Nein|Ja (nur Zeitpläne mit Besitzer)|Nein|  
|Liste anzeigen (aufzählen)|Ja|Ja <sup>1</sup>|Ja|Ja|Ja|Ja|  
|Aktivieren/Deaktivieren|Nein|Nein|Ja <sup>3</sup>|Nein|Ja <sup>4</sup>|Nicht verfügbar|  
|Eigenschaften anzeigen|Ja|Ja|Ja|Ja|Ja|Ja|  
|Eigenschaften bearbeiten|Nein|Nein|Ja (nur Aufträge mit Besitzer)|Nein|Ja (nur Zeitpläne mit Besitzer)|Nein|  
|Ausführen/Beenden/Starten|Nicht verfügbar|Nicht verfügbar|Ja|Nein|Nicht verfügbar|Nicht verfügbar|  
|Auftragsverlauf anzeigen|Nicht verfügbar|Nicht verfügbar|Ja|Ja|Nicht verfügbar|Nicht verfügbar|  
|Auftragsverlauf löschen|Nicht verfügbar|Nicht verfügbar|Ja|Nein|Nicht verfügbar|Nicht verfügbar|  
|Anfügen/Trennen|Nicht verfügbar|Nicht verfügbar|Nicht verfügbar|Nicht verfügbar|Ja (nur Zeitpläne mit Besitzer)|Nicht verfügbar|  
  
 <sup>1</sup> können Sie die Liste der verfügbaren Operatoren für die Verwendung in abrufen **Sp_notify_operator** und **Auftragseigenschaften** Dialogfeld von Management Studio.  
  
 <sup>2</sup> Auftragsbesitz nicht ändern.  
  
 <sup>3</sup> **SQLAgentOperatorRole** können aktivieren oder deaktivieren Sie die lokale Aufträge, die sie kein besitzen mithilfe der gespeicherten Prozedur **Sp_update_job** und Angeben von Werten für die **@enabled** und **@job_id** (oder **@job_name**) Parameter. Wenn ein Mitglied dieser Rolle einen anderen Parameter für diese gespeicherte Prozedur angibt, erzeugt die Ausführung der Prozedur einen Fehler.  
  
 <sup>4</sup> **SQLAgentOperatorRole** können aktivieren oder Deaktivieren von Zeitplänen, die sie kein besitzen mithilfe der gespeicherten Prozedur **Sp_update_schedule** und Angeben von Werten für die **@enabled** und **@schedule_id** (oder **@name**) Parameter. Wenn ein Mitglied dieser Rolle einen anderen Parameter für diese gespeicherte Prozedur angibt, erzeugt die Ausführung der Prozedur einen Fehler.  
  
## <a name="assigning-users-multiple-roles"></a>Zuweisen von mehreren Rollen an Benutzer  
 Die Mitglieder der festen Serverrolle **sysadmin** haben Zugriff auf alle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Funktionen. Wenn ein Benutzer nicht Mitglied der **sysadmin** -Rolle ist, sondern von mehr als einer festen Datenbankrolle des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents, sollten Sie das konzentrische Berechtigungsmodell dieser Rollen berücksichtigen. Da die Rollen mit höheren Berechtigungen immer alle Berechtigungen der Rollen mit niedrigeren Berechtigungen enthalten, hat ein Benutzer, der Mitglied von mehreren Rollen ist, automatisch die Berechtigungen der Rolle mit den höchsten Berechtigungen, deren Mitglied der Benutzer ist.  
  
## <a name="see-also"></a>Siehe auch  
 [Implementieren von SQL Server-Agent-Sicherheit](implement-sql-server-agent-security.md)   
 [sp_update_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-job-transact-sql)   
 [sp_update_schedule &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-schedule-transact-sql)   
 [Sp_notify_operator &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-notify-operator-transact-sql)   
 [Sp_purge_jobhistory &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-purge-jobhistory-transact-sql)  
  
  
