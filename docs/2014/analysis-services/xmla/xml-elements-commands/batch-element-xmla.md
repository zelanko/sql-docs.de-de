---
title: Batch-Element (XMLA) | Microsoft-Dokumentation
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
api_name:
- Batch Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Batch
- microsoft.xml.analysis.batch
- http://schemas.microsoft.com/analysisservices/2003/engine#Batch
helpviewer_keywords:
- Batch command
ms.assetid: 818f3212-9605-4e34-8623-1154d9fae1f0
caps.latest.revision: 14
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 269eedd9a48d1bf7bde43d0294bac7a81b9f90ad
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37291236"
---
# <a name="batch-element-xmla"></a>Batch-Element (XMLA)
  Führt eine oder mehrere XML-Code für Befehle Analysis (XMLA) als Batchvorgang ein, entweder sequentiell oder parallel auf einer Instanz von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Command>  
   <Batch Transaction="Boolean" ProcessAffectedObjects="Boolean">  
      <Bindings>...</Bindings>  
      <DataSource>...</DataSource>  
      <DataSourceView>...</DataSourceView>  
      <ErrorConfiguration>...</ErrorConfiguration>  
      <Parallel>...</Parallel>  
      <!-- One or more XMLA commands -->  
   </Batch>  
</Command>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|InclusionThresholdSetting|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Befehl](../xml-elements-properties/command-element-xmla.md)|  
|Untergeordnete Elemente|[Bindungen](../xml-elements-properties/bindings-element-xmla.md), [DataSource](../xml-elements-properties/source-element-xmla.md), [DataSourceView](../xml-elements-properties/datasourceview-element-xmla.md), [ErrorConfiguration](../../scripting/objects/errorconfiguration-element-assl.md), [Parallel](../xml-elements-properties/parallel-element-xmla.md)<br /><br /> Eine oder mehrere der folgenden XMLA-Befehle: [Alter](alter-element-xmla.md), [Sicherung](backup-element-xmla.md), [BeginTransaction](begintransaction-element-xmla.md), [ClearCache](clearcache-element-xmla.md), [ CommitTransaction](committransaction-element-xmla.md), [erstellen](create-element-xmla.md), [löschen](delete-element-xmla.md), [DesignAggregations](designaggregations-element-xmla.md), [löschen](drop-element-xmla.md), [Einfügen](insert-element-xmla.md), [Sperre](lock-element-xmla.md), [MergePartitions](mergepartitions-element-xmla.md), [NotifyTableChange](notifytablechange-element-xmla.md), [Prozess](process-element-xmla.md), [Wiederherstellen](restore-element-xmla.md), [RollbackTransaction](rollbacktransaction-element-xmla.md), [SetPasswordEncryptionKey](http://msdn.microsoft.com/en-us/fb262737-f0f4-4441-985e-3b2a94d00a9e), [Anweisung](statement-element-xmla.md), [abonnieren](subscribe-element-xmla.md), [Synchronisieren](synchronize-element-xmla.md), [nicht entsperren](unlock-element-xmla.md), [Update](update-element-xmla.md), [UpdateCells](drop-element-xmla.md)|  
  
## <a name="attributes"></a>Attribute  
  
|attribute|Description|  
|---------------|-----------------|  
|ProcessAffectedObjects|(Optionales `Boolean`-Attribut) Gibt an, ob alle Objekte, die eine Wiederverarbeitung erfordern, verarbeitet werden.<br /><br /> Wenn auf True festgelegt, die [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Instanz verarbeitet alle Objekte, die erfordern eine erneute Verarbeitung als Ergebnis der Verarbeitung eines Objekts in der `Batch` Befehl.<br /><br /> Wenn es auf `false` festgelegt ist, verarbeitet die [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]-Instanz nur diejenigen Objekte, die im `Batch`-Befehl enthalten sind.|  
|Transaction|(Optional `Boolean` Attribut) angibt, ob der Befehl umfasst die `Batch` Befehl als eine einzelne Transaktion oder als individuelle Transaktionen behandelt werden.<br /><br /> Wenn er auf "True" gesetzt ist, gelten alle im `Batch`-Befehl enthaltenen Befehle als eine einzelne Transaktion. Wenn einer der Befehle fehlschlägt, findet für alle Befehle, die vor dem fehlgeschlagenen Befehl ausgeführt wurden, ein Rollback statt und der `Batch`-Befehl wird angehalten, ohne die folgenden Befehle auszuführen.<br /><br /> Wenn der `false`-Befehl auf `Batch` festgelegt ist, wird versucht, jeden Befehl auszuführen. Anschließend wird für die Ergebnisse jedes Befehls, der erfolgreich abgeschlossen wurde, ein Commit ausgeführt.|  
  
## <a name="remarks"></a>Hinweise  
  
> [!WARNING]  
>  Command/Execute/Statement wird in einem Batchvorgang derzeit nicht unterstützt.  
  
 Weitere Informationen zum Durchführen von Batchvorgängen in XMLA finden Sie unter [Ausführen von Batchvorgängen &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/performing-batch-operations-xmla.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Befehle &#40;XMLA&#41;](xml-elements-commands.md)  
  
  
