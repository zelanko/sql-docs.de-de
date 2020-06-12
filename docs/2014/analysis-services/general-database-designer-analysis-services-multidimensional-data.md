---
title: Allgemein (Datenbank-Designer) (Analysis Services-Mehrdimensionale Daten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.databasedesigner.dbconfigurationpane.f1
helpviewer_keywords:
- Database Designer
ms.assetid: 00c9c42b-db2b-4620-8fb6-1e165ff0cbdd
author: minewiskan
ms.author: owend
ms.openlocfilehash: e1e7b2e1e72263d8edf362941985bb775457fc6d
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84544475"
---
# <a name="general-database-designer-analysis-services---multidimensional-data"></a>Allgemein (Datenbank-Designer) (Analysis Services – Mehrdimensionale Daten)
  Mithilfe der Registerkarte **Allgemein** können Sie die Eigenschaften einer [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank ändern.  
  
 **So zeigen Sie die Registerkarte Allgemein an**  
  
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
  
 Um dem Raster eine neue Übersetzung hinzuzufügen, klicken Sie auf **\<Add new translation>** .  
  
 **Übersetzte Beschriftung**  
 Geben Sie die Beschriftung der Datenbank in der entsprechenden Sprache für die Übersetzung ein. Wenn der Eintrag leer bleibt, wird die Standardbeschriftung für die Datenbank verwendet.  
  
 **Übersetzte Beschreibung**  
 Geben Sie die Beschreibung der Datenbank in der entsprechenden Sprache für die Übersetzung ein. Wenn der Eintrag leer bleibt, wird die Standardbeschriftung für die Datenbank verwendet.  
  
## <a name="account-type-mapping-options"></a>Kontotyp-Zuordnungsoptionen  
 Erweitern Sie den Bereich **Kontotypzuordnung** , um die standardmäßige Aggregatfunktion zu ändern, die jedem **Kontotyp** in der ausgewählten Datenbank zugeordnet ist.  
  
> [!NOTE]  
>   Diese Option ist nur auf Cubes anwendbar, in denen mindestens ein Measure die *ByAccount* -Aggregatfunktion verwendet.  
  
 Dieser Bereich enthält ein Raster mit den folgenden Spalten:  
  
 **Name**  
 Geben Sie den Namen des Kontotyps ein.  
  
 Um einen neuen Kontotyp hinzuzufügen, klicken Sie auf **\<Add new account type>** .  
  
 **Alias**  
 Legt den Standardnamen des Kontotyps fest, der vom Business Intelligence-Assistenten verwendet wird. Wenn diese Spalte leer bleibt, wird der Standardwert aus der **Name** -Spalte verwendet.  
  
 **Aggregations Funktion**  
 Wählen Sie die Aggregationsfunktion aus, die für den ausgewählten Kontotyp verwendet werden soll.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Analysis Services Designer und Dialog Felder &#40;Mehrdimensionale Daten&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Mehrdimensionale Modell Datenbanken &#40;SSAS&#41;](multidimensional-models/multidimensional-model-databases-ssas.md)   
 [Warnungen &#40;Daten Bank Designer&#41; &#40;Analysis Services Mehrdimensionale Daten&#41;](warnings-database-designer-analysis-services-multidimensional-data.md)  
  
  
