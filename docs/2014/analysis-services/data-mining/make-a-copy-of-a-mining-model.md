---
title: Erstellen Sie eine Kopie eines Miningmodells | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models [Analysis Services], copying
- mining models [Analysis Services], creating
- mining models [Analysis Services], how-to topics
- copying mining models
ms.assetid: 7975bb02-f188-49a0-b7de-5b9b216254ad
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1ce5f68df0b543fb4c461fb34921ce2ee32a3357
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48116240"
---
# <a name="make-a-copy-of-a-mining-model"></a>Erstellen einer Kopie eines Miningmodells
  Die Erstellung einer Kopie eines Miningmodells ist hilfreich, wenn Sie schnell mehrere Miningmodelle erstellen möchten, die auf den gleichen Daten basieren. Nach dem Kopieren des Modells können Sie die neue Kopie bearbeiten, indem Sie Parameter ändern oder einen Filter hinzufügen.  
  
 Wenn Sie zum Beispiel eine Customers-Tabelle besitzen, die mit einer Tabelle verknüpft ist, in der Einkäufe aufgeführt sind, können Sie Kopien erstellen, um separate Miningmodelle für jede Kundendemografie zu generieren und nach Attributen wie Alter oder Region zu filtern.  
  
 Informationen zum Kopieren des Inhalts des Modells (z.B. die grafische Darstellung oder die Modellmuster) in die Zwischenablage zur Verwendung in anderen Programmen finden Sie unter [Kopieren einer Sicht eines Miningmodells](copy-a-view-of-a-mining-model.md).  
  
### <a name="to-create-a-related-mining-model"></a>So erstellen Sie ein verknüpftes Miningmodell  
  
1.  Klicken Sie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]in Projektmappen-Explorer auf die Miningstruktur, die das Miningmodell enthält.  
  
2.  Klicken Sie auf die Registerkarte **Miningmodelle** .  
  
3.  Wählen Sie das Modell aus, und klicken Sie mit der rechten Maustaste, um das Kontextmenü zu öffnen.  
  
     – Oder –  
  
     Wählen Sie das Modell aus. Klicken Sie im Menü **Miningmodell** auf **Neues Miningmodell**.  
  
4.  Geben Sie einen Namen für das neue Miningmodell ein, und wählen Sie einen Algorithmus aus. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-edit-the-filter-on-the-copied-mining-model"></a>So bearbeiten Sie den Filter im kopierten Miningmodell  
  
1.  Wählen Sie das Miningmodell aus.  
  
2.  Klicken Sie im Fenster **Eigenschaften** auf das Textfeld für die **Filter** -Eigenschaft, und klicken Sie dann auf die Schaltfläche ( **…** ).  
  
3.  Ändern Sie die Filterbedingungen.  
  
     Weitere Informationen zur Verwendung der Dialogfelder des Filter-Editors finden Sie unter [Anwenden eines Filters auf ein Miningmodell](apply-a-filter-to-a-mining-model.md).  
  
4.  In der **Eigenschaften** Fenster in der `AlgorithmParameters` Textfeld klicken Sie auf **Algorithmusparameter**, und ändern Sie bei Bedarf Algorithmusparameter.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Filter für Miningmodelle &#40;Analysis Services – Datamining&#41;](mining-models-analysis-services-data-mining.md)   
 [Miningmodelltasks und Anweisungen Mining](mining-model-tasks-and-how-tos.md)   
 [Löschen eines Filters aus einem Miningmodell](delete-a-filter-from-a-mining-model.md)  
  
  
