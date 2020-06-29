---
title: SQL Server Integration Services-Container | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SSIS containers
- containers [Integration Services]
- containers [Integration Services], about containers
- control flow [Integration Services], containers
- SQL Server Integration Services containers
ms.assetid: 1b725922-ec59-4a47-9d55-e079463058f3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 316383c29b96a214dd36b958accc84a40eb5d3d6
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85432867"
---
# <a name="integration-services-containers"></a>SQL Server Integration Services-Container
  Bei Containern handelt es sich um Objekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], die eine Struktur für Pakete, Dienste sowie Tasks bereitstellen. Sie unterstützen das Wiederholen von Ablaufsteuerungen in Paketen und sie gruppieren Tasks und Container zu sinnvollen Arbeitseinheiten. Container können neben Tasks andere Container einschließen.  
  
 Container werden von Paketen für folgende Zwecke verwendet:  
  
-   Wiederholen von Tasks für jedes Element in einer Auflistung, z. B. Dateien in einem Ordner, Schemas oder SMO-Objekte ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects). Beispielsweise kann ein Paket Transact-SQL-Anweisungen ausführen, die in mehreren Dateien vorhanden sind.  
  
-   Wiederholen von Tasks, bis ein angegebener Ausdruck zu `false` ausgewertet wird. Beispielsweise kann von einem Paket siebenmal eine unterschiedliche E-Mail-Nachricht gesendet werden, einmal für jeden Wochentag.  
  
-   Gruppieren von Tasks und Containern, die als Einheit erfolgreich ausgeführt werden oder einen Fehler erzeugen müssen. Beispielsweise kann ein Paket Tasks gruppieren, mit denen Zeilen in einer Datenbanktabelle gelöscht und hinzugefügt werden, und anschließend einen Commit oder ein Rollback für alle Tasks ausführen, wenn bei einem Task ein Fehler auftritt.  
  
## <a name="container-types"></a>Containertypen  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] stellt vier verschiedene Containertypen zum Erstellen von Paketen bereit. In der folgenden Tabelle sind die Containertypen aufgeführt.  
  
|Container|BESCHREIBUNG|  
|---------------|-----------------|  
|[Foreach-Schleifencontainer](foreach-loop-container.md)|Führt eine Ablaufsteuerung wiederholt mithilfe eines Enumerators aus.|  
|[For-Schleifencontainer](for-loop-container.md)|Führt eine Ablaufsteuerung wiederholt durch Testen einer Bedingung aus.|  
|[Sequenzcontainer](sequence-container.md)|Gruppiert Tasks und Container zu Ablaufsteuerungen, die Teilmengen der Paketablaufsteuerung sind.|  
|[Taskhostcontainer](task-host-container.md)|Stellt Dienste für einen einzelnen Task bereit.|  
  
 Pakete und Ereignishandler sind ebenfalls Containertypen. Weitere Informationen finden Sie unter [Integration Services-Pakete &#40;SSIS&#41;](../integration-services-ssis-packages.md). und [Integration Services-Ereignishandler &#40;SSIS&#41;](../integration-services-ssis-event-handlers.md).  
  
### <a name="summary-of-container-properties"></a>Zusammenfassung der Containereigenschaften  
 Alle Containertypen haben einen Teil der Eigenschaften gemeinsam. Wenn Sie Pakete mithilfe des grafischen Tools erstellen, das von [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] bereitgestellt wird, werden im Eigenschaftenfenster die folgenden Eigenschaften für die Foreach-Schleife, die For-Schleife und die Sequenzcontainer aufgelistet. Die Eigenschaften für den Host-Container des Tasks werden als Teil des Tasks konfiguriert, den der Host für den Task kapselt. Sie legen die Eigenschaften des Tasks für den Host fest, wenn Sie den Task konfigurieren.  
  
|Eigenschaft|BESCHREIBUNG|  
|--------------|-----------------|  
|`DelayValidation`|Ein boolescher Wert, der angibt, ob die Überprüfung des Containers bis zur Ausführungszeit ausgesetzt wird. Der Standardwert dieser Eigenschaft ist `False`.<br /><br /> Weitere Informationen finden Sie unter <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.DelayValidation%2A>.|  
|`Description`|Die Containerbeschreibung. Die Eigenschaft enthält eine Zeichenfolge, die aber möglicherweise leer ist.<br /><br /> Weitere Informationen finden Sie unter <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.Description%2A>.|  
|`Disable`|Ein boolescher Wert, der angibt, ob der Container ausgeführt wird. Der Standardwert dieser Eigenschaft ist `False`.<br /><br /> Weitere Informationen finden Sie unter <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.Disable%2A>.|  
|`DisableEventHandlers`|Ein boolescher Wert, der angibt, ob der Ereignishandler mit dem ausgeführten Container verbunden ist. Der Standardwert dieser Eigenschaft ist `False`.|  
|`FailPackageOnFailure`|Ein boolescher Wert, der angibt, ob ein Paketfehler auftritt, wenn der Container fehlerhaft ist. Der Standardwert dieser Eigenschaft ist `False`.<br /><br /> Weitere Informationen finden Sie unter <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.FailPackageOnFailure%2A>.|  
|`FailParentOnFailure`|Ein boolescher Wert, der angibt, ob ein Fehler beim übergeordneten Container auftritt, wenn der Container fehlerhaft ist. Der Standardwert dieser Eigenschaft ist `False`.<br /><br /> Weitere Informationen finden Sie unter <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.FailParentOnFailure%2A>.|  
|`ForcedExecutionValue`|Ein Objekt, das den optionalen Ausführungswert für den Container enthält, falls `ForceExecutionValue` auf `True` festgelegt ist. Der Standardwert dieser Eigenschaft ist **0**.<br /><br /> Weitere Informationen finden Sie unter <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.ForcedExecutionValue%2A>.|  
|`ForcedExecutionValueType`|Der Datentyp von `ForcedExecutionValue`. Der Standardwert dieser Eigenschaft ist `Int32`.|  
|`ForceExecutionResult`|Ein Wert, der das Ergebnis der erzwungenen Ausführung des Pakets oder Containers angibt. Mögliche Werte sind `None`, `Success`, `Failure` und `Completion`. Der Standardwert dieser Eigenschaft ist `None`.<br /><br /> Weitere Informationen finden Sie unter <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.ForceExecutionResult%2A>.|  
|`ForceExecutionValue`|Ein boolescher Wert, der angibt, ob ein bestimmter optionaler Ausführungswert des Containers erzwungen werden soll. Der Standardwert dieser Eigenschaft ist `False`.<br /><br /> Weitere Informationen finden Sie unter <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.ForceExecutionValue%2A>.|  
|`ID`|Der Container-GUID, der dem Paket beim Erstellen zugewiesen wird. Diese Eigenschaft ist schreibgeschützt.<br /><br /> <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.ID%2A>.|  
|`IsolationLevel`|Die Isolationsstufe der Containertransaktion. Mögliche Werte sind `Unspecified`, `Chaos`, `ReadUncommitted`, `ReadCommitted`, `RepeatableRead``Serializable` und `Snapshot`. Der Standardwert dieser Eigenschaft ist `Serializable`. Weitere Informationen finden Sie unter <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.IsolationLevel%2A>.|  
|`LocaleID`|Ein Microsoft Win32-Gebietsschema. Der Standardwert dieser Eigenschaft ist das Gebietsschema des Betriebssystems auf dem lokalen Computer.<br /><br /> Weitere Informationen finden Sie unter <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.LocaleID%2A>.|  
|`LoggingMode`|Ein Wert, der das Protokollierungsverhalten des Containers angibt. Mögliche Werte sind `Disabled`, `Enabled` und `UseParentSetting`. Der Standardwert dieser Eigenschaft ist `UseParentSetting`. Weitere Informationen finden Sie unter <xref:Microsoft.SqlServer.Dts.Runtime.DTSLoggingMode>.|  
|`MaximumErrorCount`|Die maximal zulässige Anzahl von Fehlern, nach der die Ausführung eines Containers beendet wird. Der Standardwert dieser Eigenschaft ist **1**.<br /><br /> Weitere Informationen finden Sie unter <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.MaximumErrorCount%2A>.|  
|`Name`|Der Name des Containers,<br /><br /> Weitere Informationen finden Sie unter <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.Name%2A>.|  
|`TransactionOption`|Die Transaktionsteilnahme des Containers. Die Werte lauten `NotSupported` , `Supported` , `Required` . Der Standardwert dieser Eigenschaft ist `Supported`. Weitere Informationen finden Sie unter <xref:Microsoft.SqlServer.Dts.Runtime.DTSTransactionOption>.|  
  
 Weitere Informationen zu Eigenschaften, die in Foreach-Schleifencontainer, For-Schleifencontainer, Sequenzcontainer und Taskhostcontainer verfügbar sind, wenn Sie sie programmgesteuert konfigurieren, finden Sie unter dem API-Thema von [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] :  
  
-   T:Microsoft.SqlServer.Dts.Runtime.ForEachLoop  
  
-   T:Microsoft.SqlServer.Dts.Runtime.ForLoop  
  
-   T:Microsoft.SqlServer.Dts.Runtime.Sequence  
  
-   T:Microsoft.SqlServer.Dts.Runtime.TaskHost  
  
## <a name="objects-that-extend-container-functionality"></a>Objekte, die die Containerfunktionalität erweitern  
 Container enthalten Ablaufsteuerungen, die aus ausführbaren Dateien und Rangfolgeneinschränkungen bestehen und Ereignishandler und Variablen verwenden können. Der Taskhostcontainer ist eine Ausnahme, da er einen einzelnen Task kapselt und deshalb keine Rangfolgeneinschränkungen verwendet.  
  
### <a name="executables"></a>Ausführbare Dateien  
 Ausführbare Dateien beziehen sich auf die Tasks auf Containerebene und Container innerhalb des Containers. Eine ausführbare Datei kann einer der Tasks und Container sein, die [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] bereitstellt, oder ein benutzerdefinierter Task. Weitere Informationen finden Sie unter [Integration Services Tasks](integration-services-tasks.md) und [Integration Services Containern](integration-services-containers.md).  
  
### <a name="precedence-constraints"></a>Rangfolgeneinschränkungen  
 Rangfolgeneinschränkungen verlinken Container und Tasks innerhalb desselben übergeordneten Containers zu einer geordneten Ablaufsteuerung. Weitere Informationen finden Sie unter [Rangfolgeneinschränkungen](precedence-constraints.md).  
  
### <a name="event-handlers"></a>Ereignishandler  
 Ereignishandler auf Containerebene entsprechen Ereignissen, die vom Container oder den darin enthaltenen Objekten ausgelöst werden. Weitere Informationen finden Sie unter [Integration Services-Ereignishandler &#40;SSIS&#41;](../integration-services-ssis-event-handlers.md).  
  
### <a name="variables"></a>Variablen  
 Zu Variablen, die in Containern verwendet werden, zählen die Systemvariablen auf Containerebene, die von [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] bereitgestellt werden, und die benutzerdefinierten Variablen, die der Container verwendet. Weitere Informationen finden Sie unter [Integration Services-Variablen &#40;SSIS&#41;](../integration-services-ssis-variables.md).  
  
## <a name="break-points"></a>Breakpoints  
 Wenn Sie einen Breakpoint für einen Container festlegen und die Unterbrechungsbedingung **Unterbrechen, wenn der Container das OnVariableValueChanged-Ereignis empfängt**lautet, definieren Sie die Variable im Containerbereich.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ablaufsteuerung](control-flow.md)  
  
  
