---
title: Ziel-Editor für Partitions Verarbeitung (Seite Verbindungs-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.partprocessingtransformation.connection.f1
helpviewer_keywords:
- Partition Processing Destination Editor
ms.assetid: 7add6f82-eed1-47fc-a5d7-7b91f3f24d34
author: janinezhang
ms.author: janinez
ms.openlocfilehash: bb2efbff93fb7cc831038a7e26fe4ada44d81325
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84964750"
---
# <a name="partition-processing-destination-editor-connection-manager-page"></a>Ziel-Editor für Partitionsverarbeitung (Seite Verbindungs-Manager)
  Geben Sie auf der Seite **Verbindungs-Manager** des Dialogfelds **Ziel-Editor für Partitionsverarbeitung** eine Verbindung mit einem [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Projekt oder einer Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] an.  
  
 Weitere Informationen zum Ziel für Partitionsverarbeitung finden Sie unter [Partition Processing Destination](data-flow/partition-processing-destination.md).  
  
> [!NOTE]  
>  Hier beschriebene Tasks gelten nicht für tabellarische Analysis Services-Modelle.  Sie können Partitionsspalten für tabellarische Modelle keine Eingabespalten zuordnen. Sie können stattdessen den Analysis Services-Task "DDL ausführen" [Analysis Services Execute DDL Task](control-flow/analysis-services-execute-ddl-task.md) verwenden, um die Partition zu verarbeiten.  
  
## <a name="options"></a>Tastatur  
 **Verbindungs-Manager**  
 Wählen Sie in der Liste einen vorhandenen Verbindungs-Manager aus, oder erstellen Sie eine neue Verbindung, indem Sie auf **Neu**klicken.  
  
 **Neu**  
 Erstellen Sie mithilfe des Dialogfelds **Analysis Services-Verbindungs-Manager hinzufügen** eine neue Verbindung.  
  
 **Liste der verfügbaren Partitionen**  
 Wählen Sie die zu verarbeitende Partition aus.  
  
 **Verarbeitungsmethode**  
 Wählen Sie die Verarbeitungsmethode aus. Der Standardwert für diese Option ist **Vollständig**.  
  
|Value|Beschreibung|  
|-----------|-----------------|  
|Hinzufügen (inkrementell)|Führt eine inkrementelle Verarbeitung der Partition aus.|  
|Vollständig|Führt eine vollständige Verarbeitung der Partition aus.|  
|Nur Daten|Führt eine Verarbeitung der Updates für die Partition aus.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler-und Meldungs Referenz für Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Ziel-Editor für Partitions Verarbeitung &#40;Seite Zuordnungen&#41;](../../2014/integration-services/partition-processing-destination-editor-mappings-page.md)   
 [Ziel-Editor für Partitionsverarbeitung &#40;Seite „Erweitert“&#41;](../../2014/integration-services/partition-processing-destination-editor-advanced-page.md)  
  
  
