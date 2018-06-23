---
title: Befehle (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
- apinav
helpviewer_keywords:
- commands [XML for Analysis]
- XML for Analysis, commands
- XMLA, commands
ms.assetid: c8a93ea6-8eb5-4204-b037-69cb442a0082
caps.latest.revision: 14
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: bbfb56cc1ee12acd511c344ba3e1940fd5d56b32
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36050655"
---
# <a name="commands-xmla"></a>Befehle (XMLA)
  Dieser Referenzabschnitt enthält XMLA-Elemente (XML for Analysis), die im `Command`-Element während eines `Execute`-Methodenaufrufs verwendet werden können.  
  
|Element|Description|  
|-------------|-----------------|  
|[Alter-Element (XMLA)](alter-element-xmla.md)|Enthält Analysis Services Scripting Language (ASSL)-Elementen, die verwendet werden, indem die [Execute](../xml-elements-methods-execute.md) Methode, um Objekte auf einer Instanz von alter [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Backup-Element](backup-element-xmla.md)|Sichert eine [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Datenbank in einer Sicherungsdatei.|  
|[Batch-Element](batch-element-xmla.md)|Führt eine oder mehrere XML für Analysis (XMLA) Befehle als Batchvorgang ein, sequenziell oder parallel auf einer Instanz von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[BeginTransaction-Element](begintransaction-element-xmla.md)|Startet in der aktuellen Sitzung eine Transaktion mit einer Analysis Services-Instanz.|  
|[Cancel-Element](cancel-element-xmla.md)|Bricht in einer Analysis Services-Instanz einen gerade ausgeführten Befehl ab.|  
|[ClearCache-Element](clearcache-element-xmla.md)|Löscht den Arbeitsspeichercache des angegebenen Objekts in einer Analysis Services-Instanz.|  
|[CommitTransaction-Element](committransaction-element-xmla.md)|Übermittelt in der aktuellen Sitzung eine Transaktion mit einer Analysis Services-Instanz.|  
|[Create-Element](create-element-xmla.md)|Enthält Analysis Services Scripting Language (ASSL)-Elementen, die verwendet werden, indem die [Execute](../xml-elements-methods-execute.md) Methode zum Erstellen von Objekten auf einer Analysis Services-Instanz.|  
|[Delete-Element](delete-element-xmla.md)|Löscht auf einer Analysis Services-Instanz ein Objekt.|  
|[DesignAggregations-Element](designaggregations-element-xmla.md)|Erstellt Aggregationen für einen Aggregationsentwurf auf einer Analysis Services-Instanz.|  
|[Drop-Element](drop-element-xmla.md)|Löscht Attributelemente aus einer Dimension.|  
|[Insert-Element](insert-element-xmla.md)|Fügt Attributelemente in eine Dimension ein.|  
|[Lock-Element](lock-element-xmla.md)|Sperrt ein bestimmtes Objekt auf einer Analysis Services-Instanz.|  
|[MergePartitions-Element](mergepartitions-element-xmla.md)|Führt die Daten von einer oder mehreren Quellpartitionen zu einer Zielpartition zusammen und löscht dann die Quellpartitionen.|  
|[NotifyTableChange-Element](notifytablechange-element-xmla.md)|Benachrichtigt eine Analysis Services-Instanz, dass Tabellen in einer bestimmten Datenquelle geändert wurden.|  
|[Process-Element](process-element-xmla.md)|Verarbeitet Objekte auf einer Analysis Services-Instanz.|  
|[Restore-Element](restore-element-xmla.md)|Stellt eine Analysis Services-Datenbank aus einer Sicherungsdatei wieder her.|  
|[RollbackTransaction-Element](rollbacktransaction-element-xmla.md)|Führt in der aktuellen Sitzung ein Rollback einer Transaktion mit einer Analysis Services-Instanz durch.|  
|[Statement-Element](statement-element-xmla.md)|Enthält eine Abfrage oder Anweisung gesendet werden mithilfe der [Execute](../xml-elements-methods-execute.md) Methode mit einer Instanz von Analysis Services.|  
|[Subscribe-Element](subscribe-element-xmla.md)|Abonniert eine Ablaufverfolgung und gibt ein Rowset zurück, das die Ablaufverfolgungsereignisse einer Analysis Services-Instanz enthält.|  
|[Synchronize-Element](synchronize-element-xmla.md)|Synchronisiert eine Analysis Services-Datenbank mit einer anderen vorhandenen Datenbank.|  
|[Unlock-Element](unlock-element-xmla.md)|Entsperrt eine bestimmte Sperre auf einer Analysis Services-Instanz.|  
|[Update-Element](../xml-elements-commands/update-element-xmla.md)|Aktualisiert Attributelemente in einer Dimension.|  
|[UpdateCells-Element](updatecells-element-xmla.md)|Aktualisiert Zellen in einem Cube mit aktiviertem Schreibzugriff.|  
  
  