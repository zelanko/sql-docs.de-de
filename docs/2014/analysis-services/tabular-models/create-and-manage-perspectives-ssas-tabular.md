---
title: Erstellen und Verwalten von Perspektiven (SSAS – tabellarisch) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.perspectivedb.f1
ms.assetid: 2a411c2b-2820-4086-ad7f-ce6a941fefc7
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 25f8de0649f82abbcc6ceb4ac6a92844de04b4b7
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62795397"
---
# <a name="create-and-manage-perspectives-ssas-tabular"></a>Erstellen und Verwalten von Perspektiven (SSAS – tabellarisch)
  Eine Perspektive definiert sichtbare Teilmengen eines Modells, die fokussierte, unternehmensspezifische oder anwendungsspezifische Blickpunkte des Modells bereitstellen. In den Tasks in diesem Thema wird beschrieben, wie Perspektiven mithilfe des Dialogfelds **Perspektiven** im Modell-Designer erstellt und verwaltet werden.  
  
 Dieses Thema umfasst folgende Aufgaben:  
  
-   [So fügen Sie eine Perspektive hinzu](#bkmk_add)  
  
-   [So bearbeiten Sie eine Perspektive](#bkmk_edit)  
  
-   [So benennen Sie eine Perspektive um](#bkmk_rename)  
  
-   [So löschen Sie eine Perspektive](#bkmk_delete)  
  
-   [So kopieren Sie eine Perspektive](#bkmk_copy)  
  
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
 [Perspektiven &#40;SSAS – tabellarisch&#41;](perspectives-ssas-tabular.md)   
 [Hierarchien &#40;SSAS – tabellarisch&#41;](hierarchies-ssas-tabular.md)  
  
  
