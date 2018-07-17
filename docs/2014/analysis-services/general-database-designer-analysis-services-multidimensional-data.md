---
title: Allgemein (Datenbankdesigner) (Analysis Services – mehrdimensionale Daten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.asvs.databasedesigner.dbconfigurationpane.f1
helpviewer_keywords:
- Database Designer
ms.assetid: 00c9c42b-db2b-4620-8fb6-1e165ff0cbdd
caps.latest.revision: 25
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8a2af00d2dcdb6d28ab311067172e808e49539a0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37234270"
---
# <a name="general-database-designer-analysis-services---multidimensional-data"></a>Allgemein (Datenbank-Designer) (Analysis Services – Mehrdimensionale Daten)
  Mithilfe der Registerkarte **Allgemein** können Sie die Eigenschaften einer [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank ändern.  
  
 **Zum Anzeigen der Registerkarte "Allgemein"**  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]ein [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Projekt.  
  
2.  Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf das [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Projekt, klicken Sie auf **Datenbank bearbeiten**und anschließend auf die Registerkarte **Allgemein** .  
  
## <a name="basic-options"></a>Grundlegende Optionen  
 Erweitern Sie den Bereich **Standard** , um grundlegende Informationen zur Datenbank zu ändern. Dieser Bereich enthält die folgenden Optionen:  
  
 **Datenbankname**  
 Zeigt den Namen der Datenbank an.  
  
> [!NOTE]  
>  Klicken Sie zum Umbenennen der Datenbank im **Projektmappen-Explorer**mit der rechten Maustaste auf das Projekt, und klicken Sie anschließend auf **Eigenschaften**. Ändern Sie im Dialogfeld **Eigenschaftenseiten** der Datenbank auf der Seite **Bereitstellung** den Wert der **Datenbank** -Eigenschaft in den neuen Datenbanknamen.  
  
 **Beschreibung**  
 Geben Sie eine Beschreibung der Datenbank ein.  
  
## <a name="translations-options"></a>Optionen für Übersetzungen  
 Expandieren Sie den Bereich **Übersetzungen** , um Übersetzungen für die Beschriftung und Beschreibung der Datenbank zu erstellen und zu ändern. Dieser Bereich enthält ein Raster mit den folgenden Spalten:  
  
 **Sprache**  
 Wählen Sie die Sprache für die angegebene Übersetzung aus.  
  
 Um dem Raster eine neue Übersetzung hinzuzufügen, klicken Sie auf  **\<neue Übersetzung hinzufügen >**.  
  
 **Übersetzte Beschriftung**  
 Geben Sie die Beschriftung der Datenbank in der entsprechenden Sprache für die Übersetzung ein. Wenn der Eintrag leer bleibt, wird die Standardbeschriftung für die Datenbank verwendet.  
  
 **Übersetzte Beschreibung**  
 Geben Sie die Beschreibung der Datenbank in der entsprechenden Sprache für die Übersetzung ein. Wenn der Eintrag leer bleibt, wird die Standardbeschriftung für die Datenbank verwendet.  
  
## <a name="account-type-mapping-options"></a>Kontotyp-Zuordnungsoptionen  
 Erweitern Sie den Bereich **Kontotypzuordnung** , um die standardmäßige Aggregatfunktion zu ändern, die jedem **Kontotyp** in der ausgewählten Datenbank zugeordnet ist.  
  
> [!NOTE]  
>  Diese Option ist nur auf Cubes anwendbar, in denen mindestens ein Measure die *ByAccount* -Aggregatfunktion verwendet.  
  
 Dieser Bereich enthält ein Raster mit den folgenden Spalten:  
  
 **Name**  
 Geben Sie den Namen des Kontotyps ein.  
  
 Um einen neuen Kontotyp hinzuzufügen, klicken Sie auf  **\<neuen Kontotyp hinzufügen >**.  
  
 **Alias**  
 Legt den Standardnamen des Kontotyps fest, der vom Business Intelligence-Assistenten verwendet wird. Wenn diese Spalte leer bleibt, wird der Standardwert aus der **Name** -Spalte verwendet.  
  
 **Aggregationsfunktion**  
 Wählen Sie die Aggregationsfunktion aus, die für den ausgewählten Kontotyp verwendet werden soll.  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services-Designer und-Dialogfelder &#40;mehrdimensionale Daten&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Mehrdimensionale Modelldatenbanken &#40;SSAS&#41;](multidimensional-models/multidimensional-model-databases-ssas.md)   
 [Warnungen &#40;Datenbank-Designer&#41; &#40;Analysis Services – mehrdimensionale Daten&#41;](warnings-database-designer-analysis-services-multidimensional-data.md)  
  
  
