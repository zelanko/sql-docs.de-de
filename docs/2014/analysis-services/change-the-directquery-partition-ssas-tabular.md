---
title: Ändern der DirectQuery-Partition (SSAS – tabellarisch) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: f9df1e66-dd23-41b4-95eb-af110d10eda4
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1eb0b6349eac28bbd2abc22b9483ef74edf1bf33
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66088191"
---
# <a name="change-the-directquery-partition-ssas-tabular"></a>Ändern der DirectQuery-Partition (SSAS – tabellarisch)
  Da nur eine Partition in einer Tabelle als DirectQuery-Partition festgelegt werden kann, verwendet Analysis Services standardmäßig die erste Partition, die in der Tabelle erstellt wurde. Während der Modellprojekterstellung können Sie die DirectQuery-Partition im Dialogfeld Partitions-Manager in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]ändern. Für bereitgestellte Modelle können Sie die DirectQuery-Partition mit [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]ändern.  
  
### <a name="change-the-directquery-partition-for-a-tabular-model-project"></a>Ändern der DirectQuery-Partition für ein tabellarisches Modellprojekt  
  
1.  Klicken Sie in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]im Modell-Designer auf die Tabelle (Registerkarte), die die partitionierte Tabelle enthält.  
  
2.  Klicken Sie auf das Menü **Tabelle** und dann auf **Partitionen**.  
  
3.  Im **Partitions-Manager**wird die Partition, die die aktuelle Partition für direkte Abfragen ist, durch das Präfix **(DirectQuery)** für den Partitionsnamen angegeben.  
  
     Wählen Sie eine andere Partition in der Liste **Partitionen** aus, und klicken Sie dann auf **Als DirectQuery festlegen**. Die Schaltfläche **Als DirectQuery festlegen** wird bei Auswahl der aktuellen DirectQuery-Partition nicht aktiviert, und sie ist nicht sichtbar, wenn das Modell nicht für den DirectQuery-Modus aktiviert wurde.  
  
4.  Ändern Sie bei Bedarf die Verarbeitungsoptionen, und klicken Sie dann auf **OK**.  
  
### <a name="change-the-directquery-partition-for-a-deployed-tabular-model"></a>Ändern der DirectQuery-Partition für ein bereitgestelltes tabellarisches Modell  
  
1.  Öffnen Sie in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]die Modelldatenbank in Objekt-Explorer.  
  
2.  Erweitern Sie den Knoten **Tabellen** , klicken Sie mit der rechten Maustaste auf die partitionierte Tabelle, und wählen Sie **Partitionen**aus.  
  
     Die Partition, die für die Verwendung mit dem DirectQuery-Modus festgelegt ist, besitzt das Präfix (DirectQuery) für den Partitionsnamen.  
  
3.  Um zu einer anderen Partition zu wechseln, klicken Sie auf der Symbolleiste auf das Symbol für **DirectQuery** , um das Dialogfeld **DirectQuery-Partition festlegen** zu öffnen. Das Symbol für DirectQuery auf der Symbolleiste ist nicht verfügbar für Modelle, für die DirectQuery nicht aktiviert wurde.)  
  
4.  Wählen Sie eine andere Partition in der Dropdownliste **Partitionsname** aus, und ändern Sie ggf. die Verarbeitungsoptionen für die Partition.  
  
## <a name="see-also"></a>Siehe auch  
 [Partitionen &#40;SSAS – tabellarisch&#41;](tabular-models/partitions-ssas-tabular.md)  
  
  
