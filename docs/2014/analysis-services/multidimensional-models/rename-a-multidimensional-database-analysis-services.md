---
title: Umbenennen einer mehrdimensionalen Datenbank (Analysis Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- renaming databases
ms.assetid: 15fdaec7-f3e4-44d9-9b78-1a1d78c484e0
author: minewiskan
ms.author: owend
ms.openlocfilehash: fdcfd54f447a363f4de12f1883455d9f0bf93c54
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84545762"
---
# <a name="rename-a-multidimensional-database-analysis-services"></a>Umbenennen einer mehrdimensionalen Datenbank (Analysis Services)
  Die Art und Weise, in der Sie den Namen einer [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Datenbank ändern, hängt davon ab, wie Sie eine Verbindung mit der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Datenbank herstellen. Zum Ändern des Namens einer vorhandenen Datenbank müssen Sie die Verbindung im Onlinemodus herstellen. Zum Ändern des Namens der Datenbank, in die Objekte in einem [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekt instanziiert werden, müssen Sie die Verbindung im Projektmodus herstellen.  
  
### <a name="to-change-the-database-name-in-online-mode"></a>So ändern Sie den Datenbanknamen im Onlinemodus  
  
1.  Stellen Sie mithilfe von [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]eine direkte Verbindung mit der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank her.  
  
2.  Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf die Datenbank, und klicken Sie anschließend auf **Datenbank bearbeiten**.  
  
3.  Ändern Sie im Textfeld **Datenbankname** den Namen der Datenbank.  
  
4.  Klicken Sie auf der Symbolleiste auf **Speichern** oder **Alle speichern** , klicken Sie im Menü **Datei** auf **Ausgewählte Elemente speichern** oder **Alle speichern** , oder schließen Sie den Datenbank-Designer **** , und klicken Sie bei entsprechender Aufforderung auf **Speichern** .  
  
     Der Datenbankname wird in der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz aktualisiert, und das Datenbankobjekt im Projektmappen-Explorer wird aktualisiert.  
  
### <a name="to-change-the-database-name-in-project-mode"></a>So ändern Sie den Datenbanknamen im Projektmodus  
  
1.  Öffnen Sie das [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekt.  
  
2.  Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekt, und klicken Sie anschließend auf **Eigenschaften**.  
  
3.  Klicken Sie im Dialogfeld **Eigenschaftenseiten** im Abschnitt **Konfigurationseigenschaften** auf **Bereitstellung** .  
  
4.  Ändern Sie die **Database** -Eigenschaft in den neuen Datenbanknamen.  
  
     Bei der nächsten Bereitstellung des [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekts wird es mit diesem neuen Datenbanknamen bereitgestellt. Wenn eine Datenbank mit diesem Namen bereits vorhanden ist, wird sie überschrieben.  
  
### <a name="to-change-the-database-name-using-sql-server-management-studio"></a>So ändern Sie den Datenbanknamen mithilfe von SQL Server Management Studio  
  
-   Klicken Sie mit der rechten Maustaste auf die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank, und bearbeiten Sie die Eigenschaft „Name“.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren von Server Eigenschaften in Analysis Services](../server-properties/server-properties-in-analysis-services.md)   
 [&#40;Analysis Services Eigenschaften für mehrdimensionale Datenbanken festlegen&#41;](set-multidimensional-database-properties-analysis-services.md)   
 [Konfigurieren von Analysis Services Projekteigenschaften &#40;SSDT&#41;](configure-analysis-services-project-properties-ssdt.md)   
 [Bereitstellen von Analysis Services-Projekten &#40;SSDT&#41;](deploy-analysis-services-projects-ssdt.md)  
  
  
