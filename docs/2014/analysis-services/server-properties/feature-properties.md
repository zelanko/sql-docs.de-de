---
title: Funktionseigenschaften | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- SQMSupportEnabled property
- ComUdfEnabled property
- LinkToOtherInstanceEnabled property
- ManagedCodeEnabled property
- ConnStringEncryptionEnabled property
- LinkFromOtherInstanceEnabled property
- LinkInsideInstanceEnabled property
- UseCachedPageAllocators property
ms.assetid: a34d046a-6562-4d98-b827-37cebc6d77b4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 08001a172c1b39fb912ef042ed85effd4f8ededa
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84940711"
---
# <a name="feature-properties"></a>Funktionseigenschaften
  Funktionseigenschaften beziehen sich auf Produktfunktionen. Die meisten sind erweiterte Eigenschaften sowie Eigenschaften zum Steuern der Verbindungen zwischen Serverinstanzen.  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] unterstützt die in der folgenden Tabelle aufgeführten Servereigenschaften. Weitere Informationen zu zusätzlichen Servereigenschaften und zum Festlegen dieser Eigenschaften finden Sie unter [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md).  
  
 **Gilt für:** Nur mehrdimensionaler Server Modus  
  
## <a name="properties"></a>Eigenschaften  
  
|Eigenschaft|Standard|BESCHREIBUNG|  
|--------------|-------------|-----------------|  
|`ManagedCodeEnabled`|1|Eine boolesche Eigenschaft, die anzeigt, ob CLR-gespeicherte Prozeduren aktiviert sind.|  
|`LinkInsideInstanceEnabled`|1|Eine boolesche Eigenschaft, die anzeigt, ob innerhalb derselben Serverinstanz ein verknüpftes Objekt erstellt werden kann.|  
|`LinkToOtherInstanceEnabled`|0|Eine boolesche Eigenschaft, die anzeigt, ob ein Link mit Objekten auf Remoteservern möglich ist.|  
|`LinkFromOtherInstanceEnabled`|0|Eine boolesche Eigenschaft, die anzeigt, ob von anderen Serverinstanzen aus ein Link mit Objekten möglich ist.|  
|`ConnStringEncryptionEnabled`|1|Eine boolesche Eigenschaft, die anzeigt, ob die Verbindungszeichenfolge in der Serverkonfigurationsdatei verschlüsselt wird.|  
|`UseCachedPageAllocators`|0|Eine boolesche Eigenschaft, die anzeigt, ob zwischengespeicherte Seitenzuordnungen aktiviert sind.|  
|`ComUdfEnabled`|0|Eine boolesche Eigenschaft, die angibt, ob benutzerdefinierte Funktionen, die als COM-Objekte definiert sind, aktiviert sind.|  
|`SQMSupportEnabled`|1|Eine boolesche Eigenschaft, die anzeigt, ob Fehler- und Funktionsverwendungsberichte automatisch an [!INCLUDE[msCoName](../../includes/msconame-md.md)] gesendet werden.|  
|`ResourceMonitoringEnabled`|1|Eine boolesche Eigenschaft, die angibt, ob Leistungsindikatoren für interne Ressourcen aktiviert sind. Diese Eigenschaft ist standardmäßig aktiviert. Wenn sie aktiviert ist, können Leistungsindikatoren Verwendungsdaten zu CPU, Arbeitsspeicher und E/A-Aktivität erfassen.<br /><br /> Leistungsindikatoren für interne Ressourcen werden von dynamischen Verwaltungssichten (DMV) verwendet, die die Ressourcennutzung protokollieren. Wenn Sie diese Eigenschaft deaktivieren, werden die DMV-Abfragen zwar immer noch ausgeführt, aber das Resultset ist ungültig. DMVs, die von dieser Eigenschaft abhängig sind, schließen Folgendes ein:<br />**DISCOVER_OBJECT_ACTIVITY**<br />**DISCOVER_COMMAND_OBJECTS**<br />**DISCOVER_SESSIONS** (für SESSION_READS, SESSION_WRITES, SESSION_CPU_TIME_MS)<br /><br /> <br /><br /> Auf einem Multikern-System mit NUMA-Architektur kann durch Deaktivieren dieser Eigenschaft die Abfrageleistung verbessert werden, insbesondere für hohe Mehrbenutzerarbeitsauslastungen. Sie müssen Vergleichstests ausführen, um zu bestimmen, ob die Abfrageleistung durch Ändern dieser Eigenschaft verbessert wird. Best Practices zum Ausführen von Vergleichstests, einschließlich des Löschens des Caches und des Vermeidens von häufigen Fehlern, finden Sie im [SQL Server 2008 R2 Analysis Services-Vorgangshandbuch](https://go.microsoft.com/fwlink/?LinkID=225539).|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren von Server Eigenschaften in Analysis Services](server-properties-in-analysis-services.md)   
 [Bestimmen des Server Modus einer Analysis Services Instanz](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)   
 [Verwenden von dynamischen Verwaltungssichten &#40;DMVs&#41; zum Überwachen von Analysis Services](../instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md)  
  
  
