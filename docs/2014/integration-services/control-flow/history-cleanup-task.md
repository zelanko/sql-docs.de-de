---
title: Verlaufscleanup (Task) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.historycleanuptask.f1
helpviewer_keywords:
- history tables [SQL Server]
- History Cleanup task [Integration Services]
ms.assetid: 5defc5b9-dfd3-4859-a7fe-ac8c2b5480f8
author: janinezhang
ms.author: janinez
ms.openlocfilehash: a5b71480ef7396e935e80f9d94633a5278446700
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84918794"
---
# <a name="history-cleanup-task"></a>Verlaufscleanup (Task)
  Der Task Verlaufscleanup löscht Einträge in den folgenden Verlaufstabellen in der msdb-Datenbank von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   backupfile  
  
-   backupfilegroup  
  
-   backupmediafamily  
  
-   backupmediaset  
  
-   backupset  
  
-   restorefile  
  
-   restorefilegroup  
  
-   restorehistory  
  
 Mithilfe des Tasks "Verlaufscleanup" können für ein Paket Vergangenheitsdaten für Sicherungs- und Wiederherstellungsaktivitäten, Aufträge des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents und Datenbankwartungspläne gelöscht werden.  
  
 Dieser Task kapselt die gespeicherte Systemprozedur sp_delete_backuphistory und übergibt das angegebene Datum als Argument an die Prozedur. Weitere Informationen finden Sie unter [sp_delete_backuphistory &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql).  
  
## <a name="configuration-of-the-history-cleanup-task"></a>Konfiguration der Task "Verlaufscleanup"  
 Dieser Task umfasst eine Eigenschaft zur Angabe des am weitesten zurückliegenden Datums von Daten, die in Verlaufstabellen beibehalten werden. Sie können das Datum anhand der Anzahl von Tagen, Wochen, Monaten oder Jahren ab dem aktuellen Datum angeben. Der Task übersetzt das Intervall dann automatisch in ein Datum.  
  
 Eigenschaften können Sie mit dem [!INCLUDE[ssIS](../../../includes/ssis-md.md)] -Designer festlegen. Dieser Task ist im **-Designer in der** Toolbox **im Abschnitt** Wartungsplantasks [!INCLUDE[ssIS](../../../includes/ssis-md.md)] enthalten.  
  
 Klicken Sie auf das folgende Thema, um weitere Informationen zu den Eigenschaften zu erhalten, die Sie im [!INCLUDE[ssIS](../../../includes/ssis-md.md)] -Designer festlegen können:  
  
-   [Task „Verlaufscleanup“ &#40;Wartungsplan&#41;](../../relational-databases/maintenance-plans/history-cleanup-task-maintenance-plan.md)  
  
 Klicken Sie auf das folgende Thema, um weitere Informationen zum Festlegen dieser Eigenschaften im [!INCLUDE[ssIS](../../../includes/ssis-md.md)] -Designer zu erhalten:  
  
-   [Festlegen der Eigenschaften eines Tasks oder Containers](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Integration Services-Tasks](integration-services-tasks.md)   
 [Ablaufsteuerung](control-flow.md)  
  
  
