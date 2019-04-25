---
title: PowerShell-Reference für Analysis Services | Microsoft-Dokumentation
ms.date: 06/25/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: powershell
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 13ea15a23bbf6de6c50b494f709f65cae2f7c48b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62509837"
---
# <a name="analysis-services-powershell-reference"></a>PowerShell-Reference für Analysis Services
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] PowerShell-Cmdlets sind in enthalten die [SqlServer-Modul](https://www.powershellgallery.com/packages/SqlServer/21.0.17099). 
  
>[!NOTE] 
> Vorgänge der Azure Analysis Services-Datenbank verwenden Sie die gleiche SqlServer-Modul als SQL Server Analysis Services. Allerdings werden nicht alle Cmdlets für Azure Analysis Services unterstützt. Weitere Informationen finden Sie unter [Verwalten von Azure Analysis Services mit PowerShell](https://docs.microsoft.com/azure/analysis-services/analysis-services-powershell).
  
##  <a name="bkmk_cmdlets"></a> Analysis Services-Cmdlets  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] stellt Cmdlets bereit, die den Methoden im **Microsoft.AnalysisServices** -Namespace entsprechen. In der folgenden Tabelle wird jedes Cmdlet beschrieben und ein Link zur entsprechenden AMO-Methode angegeben.  
  
 Wenn Sie PowerShell verwenden möchten, um einen Task auszuführen, der nicht in der folgenden Liste enthalten ist (z.B. das Erstellen oder Synchronisieren einer Datenbank), können Sie ein TMSL- oder ein XMLA-Skript für diese Aktion schreiben und dann mithilfe des **Invoke-ASCmd** -Cmdlets ausführen.  
  
|Cmdlet|Description|Entsprechende AMO-Methoden|  
|------------|-----------------|----------------------------|  
|[Add-RoleMember-Cmdlet](https://docs.microsoft.com/powershell/module/sqlserver/Add-RoleMember)|Hinzufügen eines Mitglieds zu einer Datenbankrolle.|<xref:Microsoft.AnalysisServices.RoleMemberCollection.Add%2A>|  
|[Backup-ASDatabase-Cmdlet](https://docs.microsoft.com/powershell/module/sqlserver/backup-asdatabase)|Sichern einer Analysis Services-Datenbank.|[Database.Backup](https://msdn.microsoft.com/library/microsoft.analysisservices.database.backup.aspx)|  
|[Invoke-ASCmd cmdlet (Invoke-ASCmd-Cmdlet)](https://docs.microsoft.com/powershell/module/sqlserver/invoke-ascmd)|Ausführen einer Abfrage oder eines Skripts im XMLA- oder TSML-Format (JSON).|<xref:Microsoft.AnalysisServices.Core.Server.Execute%2A>|  
|[Invoke-ProcessASDatabase (Invoke-ProcessASDatabase)](https://docs.microsoft.com/powershell/module/sqlserver/invoke-processasdatabase)|Verarbeiten einer Datenbank.|<xref:Microsoft.AnalysisServices.IProcessable.Process%2A>|  
|[Invoke-ProcessCube cmdlet (Invoke-ProcessCube-Cmdlet)](https://docs.microsoft.com/powershell/module/sqlserver/invoke-processcube)|Verarbeiten eines Cubes.|<xref:Microsoft.AnalysisServices.IProcessable.Process%2A>|  
|[Invoke-ProcessDimension cmdlet (Invoke-ProcessDimension-Cmdlet)](https://docs.microsoft.com/powershell/module/sqlserver/invoke-processdimension)|Verarbeiten einer Dimension.|<xref:Microsoft.AnalysisServices.IProcessable.Process%2A>|  
|[Invoke-ProcessPartition-Cmdlet](https://docs.microsoft.com/powershell/module/sqlserver/invoke-processpartition)|Verarbeiten einer Partition.|<xref:Microsoft.AnalysisServices.IProcessable.Process%2A>|  
|[Invoke-ProcessTable cmdlet (Invoke-ProcessTable-Cmdlet)](https://docs.microsoft.com/powershell/module/sqlserver/invoke-processtable)|Verarbeiten einer Tabelle in einem Tabellenmodell, kompatibilitätsmodell 1200 oder höher.|<xref:Microsoft.AnalysisServices.IProcessable.Process%2A>|  
|[Merge-Partition cmdlet (Merge-Partition-Cmdlet)](https://docs.microsoft.com/powershell/module/sqlserver/merge-partition)|Zusammenführen einer Partition.|<xref:Microsoft.AnalysisServices.Partition.Merge%2A>|  
|[New-RestoreFolder cmdlet (New-RestoreFolder-Cmdlet)](https://docs.microsoft.com/powershell/module/sqlserver/new-restorefolder)|Erstellen eines Ordners zum Ablegen einer Datenbanksicherung|<xref:Microsoft.AnalysisServices.RestoreFolder>|  
|[New-RestoreLocations-Cmdlet](https://docs.microsoft.com/powershell/module/sqlserver/new-restorelocation)|Angeben eines oder mehrerer Remoteserver für die Wiederherstellung der Datenbank|<xref:Microsoft.AnalysisServices.RestoreLocation>|  
|[Remove-RoleMember-Cmdlet](https://docs.microsoft.com/powershell/module/sqlserver/remove-rolemember)|Entfernen eines Mitglieds aus einer Datenbankrolle|<xref:Microsoft.AnalysisServices.RoleMemberCollection.Remove%2A>|  
|[Restore-ASDatabase cmdlet (Restore-ASDatabase-Cmdlet)](https://docs.microsoft.com/powershell/module/sqlserver/restore-asdatabase)|Wiederherstellen einer Datenbank auf einer Serverinstanz|<xref:Microsoft.AnalysisServices.Core.Server.Restore%2A>|  
  

  
  
