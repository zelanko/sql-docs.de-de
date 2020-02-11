---
title: Ziel für Partitionsverarbeitung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.partitionprocessingdest.f1
helpviewer_keywords:
- partitions [Analysis Services], processing
- Partition Processing destination [Integration Services]
- destinations [Integration Services], Partition Processing
ms.assetid: 36c592ff-3f78-4a58-b496-31c1c8eee131
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 53ef09d19b62c0e6ce7742c41581d3cdefdfc374
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68890553"
---
# <a name="partition-processing-destination"></a>Ziel für Partitionsverarbeitung
  Das Ziel für die Partitions Verarbeitung lädt und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] verarbeitet eine Partition. Weitere Informationen zu Partitionen finden Sie unter [Partitionen &#40;Analysis Services – Mehrdimensionale Daten&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data).  
  
 Das Ziel für Partitionsverarbeitung schließt die folgenden Funktionen ein:  
  
-   Optionen für die inkrementelle Verarbeitung, vollständige Verarbeitung oder Updateverarbeitung.  
  
-   Fehlerkonfiguration, um anzugeben, ob die Verarbeitung Fehler ignoriert oder nach einer bestimmten Anzahl von Fehlern beendet wird.  
  
-   Zuordnung von Eingabespalten zu Partitionsspalten.  
  
 Weitere Informationen zum Verarbeiten von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Objekten finden Sie unter [Verarbeitungsoptionen und -einstellungen &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/processing-options-and-settings-analysis-services).  
  
> [!NOTE]  
>  Hier beschriebene Tasks gelten nicht für tabellarische Analysis Services-Modelle.  Sie können Partitionsspalten für tabellarische Modelle keine Eingabespalten zuordnen. Sie können stattdessen den Analysis Services-Task "DDL ausführen" [Analysis Services Execute DDL Task](../control-flow/analysis-services-execute-ddl-task.md) verwenden, um die Partition zu verarbeiten.  
  
## <a name="configuration-of-the-partition-processing-destination"></a>Konfiguration des Ziels für die Partitionsverarbeitung  
 Das Ziel für Partitionsverarbeitung stellt mithilfe eines Verbindungs-Managers für [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] eine Verbindung mit dem [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekt oder der Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] her, die die vom Ziel verarbeiteten Cubes und Partitionen enthält. Weitere Informationen finden Sie unter [Analysis Services Connection Manager](../connection-manager/analysis-services-connection-manager.md).  
  
 Das Ziel weist eine Eingabe auf. Eine Fehlerausgabe wird nicht unterstützt.  
  
 Sie können Eigenschaften mit dem [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer oder programmgesteuert festlegen.  
  
 Klicken Sie auf eines der folgenden Themen, um weitere Informationen zu den Eigenschaften zu erhalten, die Sie im Dialogfeld **Ziel-Editor für Partitionsverarbeitung** festlegen können:  
  
-   [Ziel-Editor für Partitions Verarbeitung &#40;Seite Verbindungs-Manager&#41;](../partition-processing-destination-editor-connection-manager-page.md)  
  
-   [Ziel-Editor für Partitions Verarbeitung &#40;Seite Zuordnungen&#41;](../partition-processing-destination-editor-mappings-page.md)  
  
-   [Ziel-Editor für Partitions Verarbeitung &#40;Seite "Erweitert"&#41;](../partition-processing-destination-editor-advanced-page.md)  
  
 Das Dialogfeld **Erweiterter Editor** enthält die Eigenschaften, die programmgesteuert festgelegt werden können. Klicken Sie auf eines der folgenden Themen, um weitere Informationen zu den Eigenschaften zu erhalten, die Sie im Dialogfeld **Erweiterter Editor** oder programmgesteuert festlegen können:  
  
-   [Common Properties](../common-properties.md)  
  
-   [Benutzerdefinierte Eigenschaften des Ziels für Partitionsverarbeitung](partition-processing-destination-custom-properties.md)  
  
 Informationen zum Festlegen der Eigenschaften finden Sie unter [Festlegen der Eigenschaften einer Datenflusskomponente](set-the-properties-of-a-data-flow-component.md).  
  
  
