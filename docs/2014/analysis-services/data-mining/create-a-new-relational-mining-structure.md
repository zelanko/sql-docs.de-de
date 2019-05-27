---
title: Erstellen einer neuen relationalen Miningstruktur | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], relational
- mining structures [Analysis Services], creating
- relational mining models [Analysis Services]
ms.assetid: 55bac3bd-700e-4f91-bcc6-f3cd8c026da1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b4ec4bc871723b829d9ce9ec805d4b52b1c649e8
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66085388"
---
# <a name="create-a-new-relational-mining-structure"></a>Erstellen einer neuen relationalen Miningstruktur
  Erstellen Sie mithilfe des Data Mining-Assistenten eine neue Miningstruktur. Verwenden Sie hierzu Daten aus einer relationalen Datenbank oder einer anderen Quelle. Speichern Sie dann die Struktur und beliebige verwandte Modelle in einer [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank.  
  
### <a name="to-create-a-relational-mining-structure"></a>So erstellen Sie eine relationale Miningstruktur  
  
1.  Klicken Sie im Projektmappen-Explorer in einem **-Projekt mit der rechten Maustaste auf den Ordner** Miningstrukturen [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , und klicken Sie dann auf **Neue Miningstruktur**.  
  
     Der Data Mining-Assistent wird geöffnet.  
  
2.  Klicken Sie auf der Seite **Willkommen** auf **Weiter**.  
  
3.  Wählen Sie auf der Seite **Definitionsmethode auswählen** die Option **Aus vorhandener relationaler Datenbank oder vorhandenem Data Warehouse**aus, und klicken Sie dann auf **Weiter**.  
  
4.  Wählen Sie auf der Seite **Data Mining-Technik auswählen** den Data Mining-Algorithmus aus, den Sie verwenden wollen, und klicken Sie dann auf **Weiter**.  
  
     Weitere Informationen zu Data Mining-Algorithmen finden Sie unter [Data Mining-Algorithmen &#40;Analysis Services – Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md).  
  
5.  Klicken Sie auf der Seite **Datenquelle auswählen** unter **Verfügbare Datenquellensichten**auf die Datenquellensicht, die Sie verwenden wollen, und klicken Sie auf **Weiter**.  
  
     Weitere Informationen zum Erstellen einer Datenquellensicht finden Sie unter [Datenquellensichten in mehrdimensionalen Modellen](../multidimensional-models/data-source-views-in-multidimensional-models.md).  
  
6.  Wählen Sie auf der Seite **Tabellentypen angeben** unter **Eingabetabellen**eine Falltabelle und eine geschachtelte Tabelle aus.  
  
7.  Wählen Sie auf der Seite **Trainingsdaten angeben** unter **Miningmodellstruktur**den Schlüssel, die Eingabe und die vorhersagbaren Spalten aus.  
  
     Nachdem Sie die vorhersagbare Spalte ausgewählt haben, können Sie auf die Schaltfläche **Vorschlagen** klicken, um das Dialogfeld **Verbundene Spalten vorschlagen** zu öffnen. Sie können die vorgeschlagenen Spalten übernehmen, indem Sie in diesem Dialogfeld auf **OK** klicken. Die ausgewählten Spalten werden dann in die Miningstruktur übernommen. Oder Sie ändern zuerst die Auswahl in der **Eingabe** -Spalte und klicken anschließend auf **OK**. Um die Vorschläge zu ignorieren, klicken Sie auf **Abbrechen**.  
  
8.  Klicken Sie auf **Weiter**.  
  
9. Auf der Seite **Inhalt und Datentyp der Spalten angeben** können Sie unter **Miningmodellstruktur**den Inhaltstyp und den Datentyp jeder Spalte anpassen.  
  
    > [!NOTE]  
    >  Sie können auf **Erkennen** klicken, damit automatisch erkannt wird, ob eine Spalte kontinuierliche oder diskrete Daten enthält. Nachdem Sie auf diese Schaltfläche geklickt haben, werden in den Spalten **Inhaltstyp** und **Datentyp** der Spalteninhalt und die Datentypen aktualisiert. Weitere Informationen zu den Inhalts- und Datentypen finden Sie unter [Inhaltstypen &#40;Data Mining&#41;](content-types-data-mining.md) und [Datentypen &#40;Data Mining&#41;](data-types-data-mining.md).  
  
10. Klicken Sie auf **Weiter**.  
  
11. Geben Sie auf der Seite **Assistenten abschließen** einen Namen für die zu erstellende Miningstruktur und das zugehörige ursprüngliche Miningmodell an. Klicken Sie anschließend auf **Fertig stellen**.  
  
## <a name="see-also"></a>Siehe auch  
 [Tasks und Anweisungen für Miningstrukturen](mining-structure-tasks-and-how-tos.md)  
  
  
