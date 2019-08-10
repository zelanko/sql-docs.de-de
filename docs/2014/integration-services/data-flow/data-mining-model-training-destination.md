---
title: Ziel des Data Mining-Modelltrainings | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dataminingmodeltrainingdest.f1
helpviewer_keywords:
- destinations [Integration Services], Data Mining Model Training
- Data Mining Model Training destination
- mining models [Analysis Services], training
- training mining models
ms.assetid: 6bc8cbe2-46af-4f7b-93d6-86779313c9d7
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 5dac84fe42185806ae468593876a6bd439c1c689
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68890645"
---
# <a name="data-mining-model-training-destination"></a>Ziel des Data Mining-Modelltrainings
  Das Ziel des Data Mining-Modelltrainings trainiert Data Mining-Modelle, indem die Daten, die vom Ziel empfangen werden, über Data Mining-Modellalgorithmen übergeben werden. Mehrere Data Mining-Modelle können von einem Ziel trainiert werden, falls die Modelle mit der gleichen Data Mining-Struktur erstellt wurden. Weitere Informationen finden Sie unter [Mining Structure Columns](https://docs.microsoft.com/analysis-services/data-mining/mining-structure-columns) und [Mining Model Columns](https://docs.microsoft.com/analysis-services/data-mining/mining-model-columns).  
  
## <a name="configuration-of-the-data-mining-model-training-destination"></a>Konfiguration des Ziels des Data Mining-Modelltrainings  
 Wenn eine Spalte auf Fallebene der Zielstruktur und die Modelle, die mit der Struktur erstellt wurden, den Inhaltstyp KEY TIME oder KEY SEQUENCE aufweisen, müssen die Eingabedaten nach dieser Spalte sortiert werden. Beispielsweise verwenden Modelle, die mit dem Microsoft Time Series-Algorithmus erstellt wurden, den KEY TIME-Inhaltstyp. Falls Eingabedaten nicht sortiert sind, wird beim Verarbeiten des Modells möglicherweise ein Fehler gemeldet. Falls die Daten sortiert werden müssen, können sie mithilfe einer Transformation zum Sortieren in einer früheren Phase des Datenflusses sortiert werden. Diese Anforderung gilt nicht für Spalten mit dem KEY-Inhaltstyp. Weitere Informationen finden Sie unter [Inhaltstypen &#40;Data Mining&#41;](https://docs.microsoft.com/analysis-services/data-mining/content-types-data-mining) und [Transformation zum Sortieren](transformations/sort-transformation.md).  
  
> [!NOTE]  
>  Die Eingabe des Zieles für das Data Mining-Modelltraining muss sortiert werden. Zum Sortieren der Daten können Sie ein Upstreamsortierungsziel aus dem Ziel des Data Mining-Modelltrainings in den Datenfluss einschließen. Weitere Informationen finden Sie unter [Sort Transformation](transformations/sort-transformation.md).  
  
 Dieses Ziel weist eine Eingabe und keine Ausgabe auf.  
  
 Das Ziel des Data Mining-Modelltrainings stellt mithilfe eines Verbindungs-Managers für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] eine Verbindung mit dem [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekt oder der Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] her, die die Miningstruktur und die Miningmodelle enthält, die vom Ziel trainiert werden. Weitere Informationen finden Sie unter [Analysis Services Connection Manager](../connection-manager/analysis-services-connection-manager.md).  
  
 Sie können Eigenschaften mit dem [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer oder programmgesteuert festlegen.  
  
 Klicken Sie auf eines der folgenden Themen, um weitere Informationen zu den Eigenschaften zu erhalten, die Sie im Dialogfeld **Trainings-Editor für Data Mining-Modelle** festlegen können:  
  
-   [Trainings-Editor für Data Mining-Modelle &#40;Registerkarte Verbindung&#41;](../data-mining-model-training-editor-connection-tab.md)  
  
-   [Trainings-Editor für Data Mining-Modelle &#40;Registerkarte Spalten&#41;](../data-mining-model-training-editor-columns-tab.md)  
  
 Das Dialogfeld **Erweiterter Editor** enthält die Eigenschaften, die programmgesteuert festgelegt werden können. Klicken Sie auf eines der folgenden Themen, um weitere Informationen zu den Eigenschaften zu erhalten, die Sie im Dialogfeld **Erweiterter Editor** oder programmgesteuert festlegen können:  
  
-   [Common Properties](../common-properties.md)  
  
-   [Benutzerdefinierte Eigenschaften des Ziels des Data Mining-Modelltrainings](data-mining-model-training-destination-custom-properties.md)  
  
 Weitere Informationen zum Festlegen der Eigenschaften finden Sie unter [Festlegen der Eigenschaften einer Datenflusskomponente](set-the-properties-of-a-data-flow-component.md).  
  
  
