---
title: Editor für den Task Aufträge übertragen (Seite Aufträge) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferjobstask.jobs.f1
helpviewer_keywords:
- Transfer Jobs Task Editor
ms.assetid: e72b1dc7-8cda-4ee6-abb5-d438370f04df
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 0c430f08b4a86c981df5138c7f78e76b54e7de28
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84972833"
---
# <a name="transfer-jobs-task-editor-jobs-page"></a>Editor für den Task Aufträge übertragen (Seite Aufträge)
  Auf der Seite **Aufträge** des Dialogfelds **Editor für den Task "Aufträge übertragen"** können Sie die Eigenschaften für das Kopieren von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Agentaufträgen von einer Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] in eine andere angeben. Weitere Informationen zum Task Aufträge übertragen finden Sie unter [Transfer Jobs Task](control-flow/transfer-jobs-task.md).  
  
> [!NOTE]  
>  Um auf dem Quellserver auf Aufträge zuzugreifen, müssen Benutzer auf dem Server Mitglied mindestens einer festen Serverrolle **SQLAgentUserRole** sein. Um auf dem Zielserver Aufträge erfolgreich zu erstellen, muss der Benutzer Mitglied der festen Datenbankrolle **sysadmin** oder einer der festen Datenbankrollen des [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Agents sein. Weitere Informationen zu den festen Datenbankrollen des [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Agents und zu deren Berechtigungen finden Sie unter [Feste Datenbankrollen des SQL Server-Agents](../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
## <a name="options"></a>Tastatur  
 **SourceConnection**  
 Wählen Sie in der Liste einen SMO-Verbindungs-Manager aus, oder klicken Sie **\<New connection...>** auf, um eine neue Verbindung mit dem Quell Server zu erstellen.  
  
 **DestinationConnection**  
 Wählen Sie in der Liste einen SMO-Verbindungs-Manager aus, oder klicken Sie **\<New connection...>** auf, um eine neue Verbindung mit dem Zielserver zu erstellen.  
  
 **TransferAllJobs**  
 Wählen Sie aus, ob der Task alle oder nur angegebene [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Agentaufträge vom Quell- auf den Zielserver kopieren soll.  
  
 Für diese Eigenschaft sind die in der folgenden Tabelle aufgeführten Optionen verfügbar:  
  
|Value|Beschreibung|  
|-----------|-----------------|  
|**True**|Kopiert alle Aufträge.|  
|**Alarm**|Kopiert nur angegebene Aufträge.|  
  
 **JobsList**  
 Klicken Sie auf die Schaltfläche zum Durchsuchen **(...)**, um die zu kopierenden Aufträge auszuwählen. Es muss mindestens ein Auftrag ausgewählt werden.  
  
> [!NOTE]  
>  Geben Sie vor der Auswahl der zu kopierenden Aufträge **SourceConnection** an.  
  
 Die Option **JobsList** ist nicht verfügbar, wenn **TransferAllJobs** auf **True**festgelegt ist.  
  
 **IfObjectExists**  
 Wählen Sie aus, wie der Task Aufträge behandeln soll, die auf dem Zielserver bereits mit demselben Namen vorhanden sind.  
  
 Für diese Eigenschaft sind die in der folgenden Tabelle aufgeführten Optionen verfügbar:  
  
|Value|Beschreibung|  
|-----------|-----------------|  
|**FailTask**|Der Task schlägt fehl, wenn auf dem Zielserver bereits Aufträge mit demselben Namen vorhanden sind.|  
|**Overwrite**|Der Task überschreibt auf dem Zielserver Aufträge mit demselben Namen.|  
|**Skip**|Der Task lässt Aufträge aus, die auf dem Zielserver mit demselben Namen vorhanden sind.|  
  
 **EnableJobsAtDestination**  
 Wählen Sie aus, ob die auf den Zielserver kopierten Aufträge aktiviert werden sollen.  
  
 Für diese Eigenschaft sind die in der folgenden Tabelle aufgeführten Optionen verfügbar:  
  
|Value|Beschreibung|  
|-----------|-----------------|  
|**True**|Aktiviert Jobs auf dem Zielserver.|  
|**Alarm**|Deaktiviert Jobs auf dem Zielserver.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler-und Meldungs Referenz für Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Aufgaben Integration Services](control-flow/integration-services-tasks.md)   
 [Editor für den Task Aufträge übertragen &#40;Seite Allgemein&#41;](general-page-of-integration-services-designers-options.md)   
 [Ausdrucks Seite](expressions/expressions-page.md)   
 [SMO-Verbindungs-Manager](connection-manager/smo-connection-manager.md)  
  
  
