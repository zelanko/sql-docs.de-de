---
title: Automatisieren von Analysis Services administrative Aufgaben mit SSIS | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Execute DDL Task [Analysis Services]
- Analysis Services Processing task
ms.assetid: e960a9a2-80b4-45da-9369-bc560ecdccac
author: minewiskan
ms.author: owend
ms.openlocfilehash: a8b44e09f929ad6a331bb335e801838ed3de64de
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84544108"
---
# <a name="automate-analysis-services-administrative-tasks-with-ssis"></a>Automatisieren von Analysis Services-Verwaltungsaufgaben mit SSIS
  [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ermöglicht die Automatisierung der Ausführung von DDL-Skripts, Cube-und Mining Modell-Verarbeitungs Tasks und Data Mining Abfrage Tasks. [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] kann als eine Sammlung von Ablaufsteuerung und Wartungstasks angesehen werden, die verknüpft werden können, um sequenzielle und parallele Datenverarbeitungsaufträge zu bilden.  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] wurde zum Ausführen von Datencleanupvorgängen während der Datenverarbeitungstasks und zum Zusammenführen von Daten aus unterschiedlichen Datenquellen entwickelt. Beim Arbeiten mit Cubes und Miningmodellen kann [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] nicht-numerische Daten in numerische Daten transformieren und sicherstellen, dass die Datenwerte sich innerhalb erwarteter Grenzen befinden. Auf diese Weise können Daten erstellt werden, aus denen Faktentabellen und Dimensionen aufgefüllt werden.  
  
## <a name="integration-services-tasks"></a>Integration Services-Tasks  
 In jedem [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Task oder -Auftrag gibt es zwei Hauptelemente: Ablaufsteuerungselemente und Datenflusselemente. Mit den Ablaufsteuerungselementen wird die logische Reihenfolge des Auftragsverlaufs durch die Anwendung von Rangfolgeneinschränkungen definiert. Die Datenflusselemente betreffen die Konnektivität zwischen der Ausgabe einer Komponente und der Eingabe der folgenden Komponente sowie alle Datentransformationen auf dazwischen liegende Daten. Im Hinblick auf die Entscheidung, wohin die Daten gehen sollen, enthalten die Rangfolgeneinschränkungen die entsprechende Logik, um die Komponente anzugeben, die die Ausgabe empfangen soll. [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]Zu den Aufgaben, die am relevantesten sind, [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] gehören der Task DDL ausführen, der Analysis Services Verarbeitungs Task und der Data Mining-Abfrage Task. Bei jedem dieser Tasks kann mithilfe des Tasks Mail senden dem Administrator eine E-Mail-Nachricht mit den Taskergebnissen gesendet werden.  
  
## <a name="the-execute-ddl-task"></a>Der Task DDL ausführen  
 Mit dem Task DDL ausführen können Sie in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] DDL-Skripts direkt an den [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Server senden und diese dort automatisch ausführen. Dadurch ist der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Administrator in der Lage, Sicherungs-, Wiederherstellungs- und Synchronisierungsvorgänge von innerhalb eines [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Pakets auszuführen. Ein Paket besteht aus den zuvor beschriebenen Ablaufsteuerungs- und Datenflusselementen, die, wie alle anderen DDL-Anweisungen, die Tasks hinzugefügt werden können, **run regularly**werden müssen. Weil die hier besprochenen Tasks häufig während der Nacht ausgeführt werden, sind insbesondere Pakete besonders nützlich, die ohne großen Aufwand von einer Planungsanwendung ausgeführt werden können. Mit dem [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Agenten können Sie die Ausführung eines Pakets zu einem beliebigen Zeitpunkt planen. Weitere Informationen zum Implementieren dieses Tasks finden Sie unter [DDL ausführen (Analysis Services-Task)](../../integration-services/control-flow/analysis-services-execute-ddl-task.md).  
  
## <a name="analysis-services-processing-task"></a>Analysis Services-Verarbeitungstask  
 Mit dem Analysis Services-Verarbeitungstask in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] können Sie automatisch Cube mit neuen Informationen auffüllen, wenn Sie regelmäßige Updates an der relationalen Quelldatenbank vornehmen. Mit dem Analysis Services-Verarbeitungstask können Sie Daten auf Ebene einer Dimension, eines Cubes oder einer Partition verarbeiten. Bei der eigentlichen Verarbeitung kann es sich um die Typen `incremental` oder `full` handeln, die Sie auf Grundlage der Auftragsanforderungen auswählen. Beim inkrementellen Verarbeiten werden neue Daten hinzugefügt und ausreichend Neuberechnungen ausgeführt, damit das Ziel aktuell ist, wohingegen beim vollständigen Verarbeiten die vorhandenen Daten gelöscht und die Daten vollständig neu geladen und neu berechnet werden. Die vollständige Verarbeitung dauert länger, ist aber vollständiger. Weitere Informationen zum Implementieren dieses Tasks finden Sie unter [Analysis Services Processing Task](../../integration-services/control-flow/analysis-services-processing-task.md).  
  
## <a name="data-mining-query-task"></a>Data Mining-Abfragetask  
 Mit dem Data Mining-Abfragetask können Sie in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Informationen aus Miningmodellen extrahieren und speichern. Die Informationen werden häufig in einer relationalen Datenbank gespeichert und können z. B. zum Isolieren einer Liste potenzieller Kunden für eine gezielte Marketingkampagne verwendet werden. Mithilfe von Data Mining können der Wert eines Kunden und die Wahrscheinlichkeit identifiziert werden, mit der der Kunde auf eine bestimmte Marketingmaßnahme reagiert. Sie können mit dem Data Mining-Abfragetask Daten in das bevorzugte Format extrahieren und diese Daten ändern. Weitere Informationen zum Implementieren dieses Tasks finden Sie unter [Data Mining Query Task](../../integration-services/control-flow/data-mining-query-task.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ziel für Partitions Verarbeitung](../../integration-services/data-flow/partition-processing-destination.md)   
 [Ziel für Dimensions Verarbeitung](../../integration-services/data-flow/dimension-processing-destination.md)   
 [Transformation für Data Mining-Abfragen](../../integration-services/data-flow/transformations/data-mining-query-transformation.md)   
 [Objekt Verarbeitung für mehrdimensionale Modelle](../multidimensional-models/processing-a-multidimensional-model-analysis-services.md)   
 [Skriptverwaltungsaufgaben in Analysis Services](../script-administrative-tasks-in-analysis-services.md)  
  
  
