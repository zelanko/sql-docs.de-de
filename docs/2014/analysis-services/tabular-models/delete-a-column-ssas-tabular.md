---
title: Löschen einer Spalte (SSAS – tabellarisch) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 703db83b-e554-450e-813e-23ad08c1cdad
caps.latest.revision: 4
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: bef4966295acafa3b122fe1786cf06495962890d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36161884"
---
# <a name="delete-a-column-ssas-tabular"></a>Löschen einer Spalte (SSAS – tabellarisch)
  In diesem Thema wird beschrieben, wie eine Spalte aus einer Tabelle eines tabellarische Modells gelöscht wird.  
  
## <a name="delete-a-model-table-column"></a>Löschen von Modelltabellenspalten  
  
> [!NOTE]  
>  Wenn Sie eine Spalte aus einer Modelltabelle löschen, wird die Spalte nicht aus einer Partitionsabfragedefinition gelöscht. Falls die Spalte, die Sie löschen, Teil einer Partition ist, müssen Sie die Spalte manuell aus der Partitionsabfragedefinition löschen. Wenn Sie die Spalte nicht aus der Partitionsabfragedefinition löschen, wird die Spalte bei Verarbeitungsvorgängen abgefragt und Daten zurückgegeben, aber nicht in der Modelltabelle ausgefüllt. Weitere Informationen finden Sie unter [Partitions &#40;SSAS Tabular&#41;](partitions-ssas-tabular.md).  
  
#### <a name="to-delete-a-model-table-column"></a>So löschen Sie eine Modelltabellenspalte  
  
-   Klicken Sie im Modell-Designer in der Tabelle, die die Spalte enthält, mit der rechten Maustaste auf die Spalte und anschließend auf **Löschen**.  
  
#### <a name="to-delete-a-model-table-column-by-using-the-table-properties-dialog-box"></a>So löschen Sie mithilfe des Dialogfelds 'Tabelleneigenschaften' eine Modelltabellenspalte  
  
1.  Klicken Sie im Modell-Designer auf die Tabelle, die die zu löschende Spalte enthält, klicken Sie auf das Menü **Tabelle** und dann auf  **Tabelleneigenschaften**.  
  
2.  Wählen Sie unter **Spaltennamen aus**die Option **Modell** aus,*um Modelltabellen-Spaltennamen zu verwenden, falls diese von der Quelle abweichen*.  
  
3.  Deaktivieren Sie im Dialogfeld **Tabelleneigenschaften bearbeiten** im Tabellenvorschaufenster die Spalte, die Sie löschen möchten, und klicken Sie dann auf **OK**.  
  
## <a name="see-also"></a>Siehe auch  
 [Hinzufügen von Spalten zu einer Tabelle &#40;SSAS – tabellarisch&#41;](add-columns-to-a-table-ssas-tabular.md)   
 [Partitionen &#40;SSAS – tabellarisch&#41;](partitions-ssas-tabular.md)  
  
  