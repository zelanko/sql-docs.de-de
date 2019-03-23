---
title: Partition Ziel-Editor (Seite Verbindungs-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.partprocessingtransformation.connection.f1
helpviewer_keywords:
- Partition Processing Destination Editor
ms.assetid: 7add6f82-eed1-47fc-a5d7-7b91f3f24d34
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 4b86348e6e7fa8331697c4a0aa3b23a494ae54a5
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2019
ms.locfileid: "58374758"
---
# <a name="partition-processing-destination-editor-connection-manager-page"></a>Ziel-Editor für Partitionsverarbeitung (Seite Verbindungs-Manager)
  Geben Sie auf der Seite **Verbindungs-Manager** des Dialogfelds **Ziel-Editor für Partitionsverarbeitung** eine Verbindung mit einem [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Projekt oder einer Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]an.  
  
 Weitere Informationen zum Ziel für Partitionsverarbeitung finden Sie unter [Partition Processing Destination](data-flow/partition-processing-destination.md).  
  
> [!NOTE]  
>  Hier beschriebene Tasks gelten nicht für tabellarische Analysis Services-Modelle.  Sie können Partitionsspalten für tabellarische Modelle keine Eingabespalten zuordnen. Sie können stattdessen den Analysis Services-Task "DDL ausführen" [Analysis Services Execute DDL Task](control-flow/analysis-services-execute-ddl-task.md) verwenden, um die Partition zu verarbeiten.  
  
## <a name="options"></a>Optionen  
 **Connection manager**  
 Wählen Sie in der Liste einen vorhandenen Verbindungs-Manager aus, oder erstellen Sie eine neue Verbindung, indem Sie auf **Neu**klicken.  
  
 **Neu**  
 Erstellen Sie mithilfe des Dialogfelds **Analysis Services-Verbindungs-Manager hinzufügen** eine neue Verbindung.  
  
 **Liste der verfügbaren Partitionen**  
 Wählen Sie die zu verarbeitende Partition aus.  
  
 **Verarbeitungsmethode**  
 Wählen Sie die Verarbeitungsmethode aus. Der Standardwert für diese Option ist **Vollständig**.  
  
|Wert|Description|  
|-----------|-----------------|  
|Hinzufügen (inkrementell)|Führt eine inkrementelle Verarbeitung der Partition aus.|  
|Vollständig|Führt eine vollständige Verarbeitung der Partition aus.|  
|Nur Daten|Führt eine Verarbeitung der Updates für die Partition aus.|  
  
## <a name="see-also"></a>Siehe auch  
 [Fehler- und Meldungsreferenz von Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Ziel-Editor für Partitionsverarbeitung &#40;Seite „Zuordnungen“&#41;](../../2014/integration-services/partition-processing-destination-editor-mappings-page.md)   
 [Ziel-Editor für Partitionsverarbeitung &#40;Seite „Erweitert“&#41;](../../2014/integration-services/partition-processing-destination-editor-advanced-page.md)  
  
  
