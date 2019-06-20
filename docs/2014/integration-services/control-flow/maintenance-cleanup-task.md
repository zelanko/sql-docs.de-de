---
title: Wartungscleanup (Task) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.maintenancecleanuptask.f1
helpviewer_keywords:
- deleting files
- removing files
- Maintenance Cleanup task
ms.assetid: 73ad3cd6-9a6d-44cf-905f-c56aa658bf42
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: d8b3c3aa4f63018e91370c4e01dada40c35a5f2f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62830799"
---
# <a name="maintenance-cleanup-task"></a>Wartungscleanup (Task)
  Mit dem Task Wartungscleanup werden Dateien entfernt, die mit Wartungsplänen verbunden sind, einschließlich Datenbanksicherungsdateien und Berichte, die von Wartungsplänen erstellt wurden. Weitere Informationen finden Sie unter [Wartungspläne](../../relational-databases/maintenance-plans/maintenance-plans.md) und [Sichern und Wiederherstellen von SQL Server-Datenbanken](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md).  
  
 Ein Paket kann mithilfe des Tasks Wartungscleanup die Sicherungsdateien oder Wartungsplanberichte auf dem angegebenen Server entfernen. Der Task Wartungscleanup schließt eine Option zum Entfernen einer bestimmten Datei bzw. einer Gruppe von Dateien eines Ordners ein. Optional können Sie die Erweiterung der zu löschenden Dateien angeben.  
  
 Wenn Sie den Task Wartungscleanup zum Entfernen von Sicherungsdateien konfigurieren, lautet die Standard-Dateinamenerweiterung BAK. Für Berichtsdateien lautet die Standard-Dateinamenerweiterung TXT. Sie können die Erweiterungen nach Ihren Bedürfnissen aktualisieren. Als einzige Beschränkung gilt, dass Erweiterungen eine Länge von maximal 256 Zeichen aufweisen dürfen.  
  
 In der Regel werden alte Dateien, die nicht mehr benötigt werden, entfernt. Der Task Wartungscleanup kann so konfiguriert werden, dass sämtliche Dateien, die ein bestimmtes Alter erreicht haben, gelöscht werden. Der Task kann beispielsweise zum Löschen von Dateien konfiguriert werden, die älter als vier Wochen sind. Sie können das Alter der zu löschenden Dateien angeben, indem Sie Tage, Wochen, Monate oder Jahre verwenden. Wenn Sie das Mindestalter der zu löschenden Dateien nicht angeben, werden alle Dateien des angegebenen Typs gelöscht.  
  
 Im Gegensatz zu früheren Versionen des Tasks Wartungscleanup löscht die Version des Tasks in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nicht automatisch Dateien in den Unterverzeichnissen des angegebenen Verzeichnisses. Diese Einschränkung verringert die Oberfläche eines Angriffs, der die Funktionalität des Tasks Wartungscleanup ausnutzen könnte, um Dateien in böswilliger Absicht zu löschen. Wenn Sie die Unterordner auf oberster Ebene löschen möchten, müssen Sie dies ausdrücklich durch Aktivieren der Option **Unterordner auf oberster Ebene einschließen** im Dialogfeld **Task "Wartungscleanup"** auswählen.  
  
## <a name="configuration-of-the-maintenance-cleanup-task"></a>Konfiguration des Task "Wartungscleanup"  
 Eigenschaften können Sie mit dem [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer festlegen. Dieser Task ist im **-Designer in der** Toolbox **im Abschnitt** Wartungsplantasks [!INCLUDE[ssIS](../../includes/ssis-md.md)] enthalten.  
  
 Klicken Sie auf das folgende Thema, um weitere Informationen zu den Eigenschaften zu erhalten, die Sie im [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer festlegen können:  
  
-   [Task „Wartungscleanup“ &#40;Wartungsplan&#41;](../../relational-databases/maintenance-plans/maintenance-cleanup-task-maintenance-plan.md)  
  
## <a name="related-tasks"></a>Related Tasks  
 Informationen zum Festlegen dieser Eigenschaften im [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer finden Sie unter [Festlegen der Eigenschaften eines Tasks oder Containers](../set-the-properties-of-a-task-or-container.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Integration Services-Tasks](integration-services-tasks.md)   
 [Ablaufsteuerung](control-flow.md)  
  
  
