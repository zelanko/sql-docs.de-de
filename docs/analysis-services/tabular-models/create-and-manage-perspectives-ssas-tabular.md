---
title: Erstellen und Verwalten von Perspektiven in tabellenmodellen von Analysis Services | Microsoft-Dokumentation
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 962b6b90de6d95107d1a4cdd3484a44205afb630
ms.sourcegitcommit: 8a64c59c5d84150659a015e54f8937673cab87a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2018
ms.locfileid: "53071847"
---
# <a name="create-and-manage-perspectives"></a>Erstellen und Verwalten von Perspektiven 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Eine Perspektive definiert sichtbare Teilmengen eines Modells, die fokussierte, unternehmensspezifische oder anwendungsspezifische Blickpunkte des Modells bereitstellen. In den Tasks in diesem Thema wird beschrieben, wie Perspektiven mithilfe des Dialogfelds **Perspektiven** im Modell-Designer erstellt und verwaltet werden.  
  
## <a name="tasks"></a>Richtlinienübersicht  
 Zum Erstellen von Perspektiven verwenden Sie das Dialogfeld **Perspektiven** , in dem Sie Perspektiven hinzufügen, bearbeiten, löschen, kopieren und anzeigen können. Um das Dialogfeld **Perspektiven** anzuzeigen, klicken Sie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]auf das Menü **Modell** und dann auf **Perspektiven**.  
  
###  <a name="bkmk_add"></a> So fügen Sie eine Perspektive hinzu  
  
-   Zum Hinzufügen einer neuen Perspektive klicken Sie auf **Neue Perspektive**. Anschließend können Sie die einzufügenden Feldobjekte aktivieren und deaktivieren und einen Namen für die neue Perspektive angeben.  
  
     Wenn Sie eine leere Perspektive erstellen, die alle Felder mit Feldobjekten enthält, wird dem Benutzer, der diese Perspektive verwendet, eine leere Feldliste angezeigt. Perspektiven sollten mindestens eine Tabelle und eine Spalte enthalten.  
  
###  <a name="bkmk_edit"></a> So bearbeiten Sie eine Perspektive  
  
-   Um eine Perspektive ändern, überprüfen Sie, und deaktivieren Sie Felder in der Spalte der Perspektive, die hinzugefügt und entfernt aus der Perspektive Feldobjekte.  
  
###  <a name="bkmk_rename"></a> So benennen Sie eine Perspektive um  
  
-   Wenn Sie eine Perspektive Spaltenüberschrift (den Namen der Perspektive) zeigen die **umbenennen** Schaltfläche angezeigt wird. Klicken Sie auf **Umbenennen**, um die Perspektive umzubenennen. Geben Sie dann einen neuen Namen ein, oder bearbeiten Sie den vorhandenen Namen.  
  
###  <a name="bkmk_delete"></a> So löschen Sie eine Perspektive  
  
-   Wenn Sie eine Perspektive Spaltenüberschrift (den Namen der Perspektive) zeigen die **löschen** Schaltfläche angezeigt wird. Klicken Sie zum Löschen der Perspektive auf die Schaltfläche **Löschen** , und klicken Sie im Bestätigungsfenster auf **Ja** .  
  
###  <a name="bkmk_copy"></a> So kopieren Sie eine Perspektive  
  
-   Wenn Sie auf die Spaltenüberschrift einer Perspektive zeigen die **Kopie** Schaltfläche angezeigt wird. Klicken Sie auf die Schaltfläche **Kopieren** , um eine Kopie dieser Perspektive zu erstellen. Rechts neben den vorhandenen Perspektiven wird eine Kopie der ausgewählten Perspektive als neue Perspektive hinzugefügt. Die neue Perspektive erbt den Namen der kopierten Perspektive, und an das Ende des Namens wird die Anmerkung *-Kopieren* angefügt. Angenommen, eine Kopie der *Sales* Perspektive erstellt wurde, die neue Perspektive den Namen *Sales – Kopie*.  
  
## <a name="see-also"></a>Siehe auch  
 [Perspektiven](../../analysis-services/tabular-models/perspectives-ssas-tabular.md)   
 [Hierarchien](../../analysis-services/tabular-models/hierarchies-ssas-tabular.md)  
  
  
