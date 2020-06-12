---
title: Verwalten von Modellen (SQL Server Data Mining-Add-Ins) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, importing
- mining models, deleting
- mining models, managing
- mining models, training
- mining models, processing
- mining models, exporting
ms.assetid: c11380f0-7c24-4668-9cdf-9c53e4aff665
author: minewiskan
ms.author: owend
ms.openlocfilehash: f37939fea1188c18079fc7e619cee6a336876e24
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84541852"
---
# <a name="manage-models-sql-server-data-mining-add-ins"></a>Modelle verwalten (SQL Server Data Mining-Add-Ins)
  ![Modelle verwalten (Schaltfläche auf Data Mining-Menüband)](media/dmc-manage.gif "Modelle verwalten (Schaltfläche auf Data Mining-Menüband)")  
  
 Im Dialogfeld **Modelle verwalten** können Sie mit vorhandenen Mining Modellen und Mining Strukturen interagieren, die auf dem Server gespeichert sind, mit [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] dem Sie derzeit verbunden sind. Sie können auch temporäre Strukturen und Modelle anzeigen und verwalten, die während der aktuellen Sitzung erstellt wurden. In diesem Dialogfeld werden sowohl Modelle angezeigt, die während der aktuellen Sitzung erstellt wurden, als auch Modelle, die auf dem Server gespeichert sind.  
  
## <a name="using-the-manage-models-wizard"></a>Verwenden des Assistenten zum Verwalten von Modellen  
 Wenn Sie auf **Modelle verwalten**klicken, wird das Dialogfeld **Mining Strukturen und Modelle verwalten** geöffnet, in dem der Zugriff auf die folgenden Funktionen zum Verwalten vorhandener Data Mining Modelle und Strukturen bereitgestellt wird:  
  
-   Umbenennen eines Miningmodells oder einer Miningstruktur  
  
-   Löschen eines Miningmodells oder einer Miningstruktur  
  
-   Entfernen eines Miningmodells oder einer Miningstruktur  
  
-   Verarbeiten einer Miningstruktur mithilfe von neuen oder bereits vorhandenen Daten  
  
-   Exportieren oder Importieren eines Miningmodells oder einer Miningstruktur  
  
> [!NOTE]  
>  In diesem Dialogfeld können Sie keine Abfragen oder Modelle erstellen. Verwenden Sie zum Erstellen einer neuen Mining Struktur einen der im Data Mining-Client für Excel bereitgestellten Assistenten, oder verwenden Sie die **Data Mining-Abfrage Erweiterter Editor**.  
  
### <a name="requirements"></a>Requirements (Anforderungen)  
 Sie müssen zunächst eine Verbindung mit einer Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] herstellen, um Data Mining-Modelle zu verwalten. Diese Verbindung ist auch dann erforderlich, wenn Sie mit Sitzungsmodellen arbeiten, die in einer temporären Datei gespeichert sind. Weitere Informationen zum Erstellen oder Ändern einer Verbindung finden Sie unter Herstellen einer Verbindung [mit Quelldaten &#40;Data Mining-Client für Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md).  
  
 Wenn die Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], mit der Sie eine Verbindung herstellen, nicht bereits Data Mining-Strukturen oder Data Mining-Modelle enthält, können Sie mithilfe der von diesem Add-In bereitgestellten Assistenten und Tools solche Strukturen und Modelle erstellen. Sie können auch neue Modelle erstellen, indem Sie das **Data Mining-Modell Erweiterter Editor**verwenden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Dokumentieren von Mining Modellen &#40;Data Mining-Add-Ins für Excel&#41;](documenting-mining-models-data-mining-add-ins-for-excel.md)   
 [Bereitstellen und Skalieren von Mining Modellen &#40;Data Mining-Add-Ins für Excel&#41;](deploying-and-scaling-mining-models-data-mining-add-ins-for-excel.md)   

  
