---
title: Erstellen von Datamining-Dimension | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], dimensions
ms.assetid: 9f0c39e5-3516-43ab-b203-f3f6dbcff89a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b642d7a0bdf552d8944602761aa76eec1cf35306
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66085500"
---
# <a name="create-a-data-mining-dimension"></a>Erstellen einer Data Mining-Dimension
  Wenn Ihre Miningstruktur auf einem OLAP-Cube basiert, können Sie eine Dimension erstellen, die den Inhalt des Miningmodells enthält. Sie können dann die Dimension wieder in den Quellcube einbinden.  
  
 Sie können auch die Dimension durchsuchen, sie zum Untersuchen der Modellergebnisse verwenden oder die Dimension mit MDX abfragen.  
  
### <a name="to-create-a-data-mining-dimension"></a>So erstellen Sie eine Data Mining-Dimension  
  
1.  Wählen Sie im Data Mining-Designer in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]entweder die **Miningstruktur** -Registerkarte oder die **Miningmodelle** -Registerkarte aus.  
  
2.  Wählen Sie aus dem Menü **Miningmodell** die Option **Data Mining-Dimension erstellen**aus.  
  
     Das Dialogfeld **Data Mining-Dimension erstellen** wird geöffnet.  
  
3.  Wählen Sie in der **Modellname** -Liste des Dialogfelds **Data Mining-Dimension auswählen** ein OLAP-Miningmodell aus.  
  
4.  Geben Sie im Feld **Dimensionsname** einen Namen für die neue Data Mining-Dimension ein.  
  
5.  Wenn Sie einen Cube erstellen wollen, der die neue Data Mining-Dimension einbindet, wählen Sie **Cube erstellen**aus. Nachdem Sie **Cube erstellen**ausgewählt haben, können Sie einen neuen Namen für den Cube eingeben.  
  
6.  Klicken Sie auf **OK**.  
  
     Die Data Mining-Dimension wird erstellt und dem **Dimensionen** -Ordner im Projektmappen-Explorer hinzugefügt. Wenn Sie **Cube erstellen**ausgewählt haben, wird auch ein neuer Cube erstellt und dem **Cubes** -Ordner hinzugefügt.  
  
## <a name="see-also"></a>Siehe auch  
 [Tasks und Anweisungen für Miningstrukturen](mining-structure-tasks-and-how-tos.md)  
  
  
