---
title: Dialog Feld ' Verweis hinzufügen ' (Analysis Services Mehrdimensionale Daten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.addreference.f1
- sql12.asvs.bidevstudio.assembly.addassembly.f1
helpviewer_keywords:
- Add Reference dialog box
ms.assetid: 457958c4-6baa-474d-99a0-34c195ceba09
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 541b7371cdc05ee316e9fb9de9f50affc4f14fc7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66062862"
---
# <a name="add-reference-dialog-box-analysis-services---multidimensional-data"></a>Dialogfeld 'Verweis hinzufügen' (Analysis Services – Mehrdimensionale Daten)
  Mithilfe des Dialogfelds **Verweis hinzufügen** in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] können Sie einer [!INCLUDE[msCoName](../includes/msconame-md.md)] -.NET Framework-Assembly oder einem anderen Projekt des Entwicklungsprojekts einen Verweis hinzufügen. Sie können das Dialogfeld **Verweis hinzufügen** anzeigen, indem Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Ordner [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]Assemblys** eines **-Projekts klicken und aus dem Kontextmenü **Neuer Assemblyverweis** auswählen.  
  
## <a name="options"></a>Tastatur  
  
|Begriff|Definition|  
|----------|----------------|  
|**.NET**|Mithilfe dieser Registerkarte können Sie einer registrierten Komponente einen Verweis hinzufügen. Mit dieser Registerkarte können Sie ein Raster anzeigen, das eine Liste der registrierten .NET Framework-Komponenten enthält. Wählen Sie ein oder mehrere Elemente aus dem Raster aus, und klicken Sie anschließend auf **Hinzufügen** , um die ausgewählten .NET-Komponenten zu **Ausgewählte Projekte und Komponenten**hinzuzufügen. Das Raster enthält die folgenden Spalten:<br /><br /> **Komponenten Name**: der vollständige oder "freundliche" Name der Komponente. Wählen Sie den Titel aus, um nach dem Komponentennamen zu sortieren.<br /><br /> **Version**: die aufgeführte Versionsnummer der Komponente. Wählen Sie den Titel aus, um nach der Version zu sortieren.<br /><br /> **Runtime**: die Version der .NET Framework, auf der die Komponente basiert. Wählen Sie den Titel aus, um nach der Laufzeitversion zu sortieren.<br /><br /> **Path**: der Dateiname der Komponente und der Pfad, in dem Sie sich befindet. Wählen Sie den Titel aus, um nach dem Pfad zu sortieren.|  
|**Durchsuchen**|Klicken Sie auf diese Option, um das Dateisystem nach einem Assembly zu durchsuchen, das nicht auf den Registerkarten **.NET** oder **Aktuell** aufgeführt ist. Auf dieser Registerkarte werden die folgenden Optionen angezeigt:<br /><br /> **Suchen in**: Wählen Sie einen Ordner aus dieser Dropdown Liste aus. Nach der Auswahl eines Ordners aus dieser Liste wird der Inhalt im primären Bereich angezeigt.<br /><br /> **Zum letzten besuchten Ordner**wechseln: gibt die **Suche in** den vorherigen Speicherort zurück.<br /><br /> **Eine Ebene nach oben**: Es wird der nächste höhere Ordner in der Hierarchie lokalisiert.<br /><br /> **Neuen Ordner erstellen**: Wählen Sie diese Option aus, um unter dem in **Suchen in**ausgewählten Ordner einen neuen untergeordneten Ordner zu erstellen.<br /><br /> **Menü Ansicht**: Wählen Sie diese Option aus, um die Ansicht der Inhalte im primären Bereich zu ändern.  Weitere Informationen zu den Optionen im Menü **Ansicht**finden Sie im Thema über das Anzeigen von Dateien und Ordnern in der [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows-Dokumentation. Die folgenden Optionen sind verfügbar:<br />Miniaturbilder<br />Kacheln<br />Symbole<br />List<br />Details<br /><br /> **Primärer**Bereich: zeigt den Inhalt des in **Suchen in**ausgewählten Ordners an. Wählen Sie ein oder mehrere Elemente aus, und klicken Sie dann auf **Hinzufügen** , um die ausgewählten Dateien den **ausgewählten Produkten und Komponenten**hinzuzufügen. Weitere Informationen zu Optionen und zum Kontextmenü im primären Bereich finden Sie im Thema über das Anzeigen von Dateien und Ordnern in der Windows-Dokumentation.<br /><br /> **Dateiname**: Verwenden Sie diese Option, um die angezeigten Dateien und Ordner zu filtern. Geben Sie einen vollständigen oder teilweisen Namen ein, für den der Filtervorgang durchgeführt werden soll. Sie können das Sternchen (\*) als Platzhalter verwenden. Geben Sie mehrere Dateinamen ein (die Dateinamen müssen in doppelte Anführungszeichen gesetzt und durch ein Leerzeichen voneinander getrennt sein), um mehrere Dateien auszuwählen. Sie können auch bereits überprüfte Dateien auswählen, indem Sie den entsprechenden Dateinamen aus der Dropdown-Liste auswählen. Tipp: Sie können nach Webservern und Netzwerkcomputern suchen, indem Sie eine URL oder einen Netzwerkpfad in den **Dateinamen**eingeben. Beispielsweise werden mit http://mywebsite alle Dateien angezeigt, die unter der Webadresse „mywebsite“ verfügbar sind, während mit „\\\myserver\myshare“ alle Dateien angezeigt werden, die im Ordner „myshare“ des Servers „myserver“ gespeichert sind.<br /><br /> **Dateityp**: Verwenden Sie diese Option, um den Inhalt des in **Suchen in** ausgewählten Ordners oder Verzeichnisses nach einem bestimmten Dateityp zu filtern.|  
|**Jüngste**|Zeigt eine Liste der kürzlich zu Projekten in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]hinzugefügten Komponentenverweise an. Wählen Sie ein oder mehrere Elemente aus dem Raster aus, und klicken Sie anschließend auf **Hinzufügen** , um die ausgewählten .NET Framework-Assemblys zu **Ausgewählte Projekte und Komponenten**hinzuzufügen. Das Raster enthält die folgenden Spalten:<br /><br /> **Komponenten Name**: der vollständige oder "freundliche" Name der Komponente. Wählen Sie den Titel aus, um nach dem Komponentennamen zu sortieren.<br /><br /> **Version**: die aufgeführte Versionsnummer der Komponente. Wählen Sie den Titel aus, um nach der Version zu sortieren.<br /><br /> **Runtime**: die Version der .NET Framework, auf der die Komponente basiert. Wählen Sie den Titel aus, um nach der Laufzeitversion zu sortieren.<br /><br /> **Path**: der Dateiname der Komponente und der Pfad, in dem Sie sich befindet. Wählen Sie den Titel aus, um nach dem Pfad zu sortieren.|  
|**Add (Hinzufügen)**|Klicken Sie auf diese Option, um eine auf den Registerkarten **.NET**, **Durchsuchen**oder **Aktuell** ausgewählte Komponente zu **Ausgewählte Projekte und Komponenten**hinzuzufügen.|  
|**Remove**|Klicken Sie auf diese Option, um eine in **Ausgewählte Projekte und Komponenten**ausgewählte Komponente zu entfernen.|  
|**Ausgewählte Projekte und Komponenten**|Zeigt eine Liste von Komponentenverweisen an, die zum [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Projekt in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]hinzugefügt werden soll. Wählen Sie ein oder mehrere Elemente aus dem Raster aus, und klicken Sie dann auf **Entfernen** , um die ausgewählten Komponenten aus dem Raster zu entfernen. Das Raster enthält die folgenden Spalten:<br /><br /> **Komponenten Name**: der vollständige oder "freundliche" Name der Komponente. Wählen Sie den Titel aus, um nach dem Komponentennamen zu sortieren.<br /><br /> **Version**: die aufgeführte Versionsnummer der Komponente. Wählen Sie den Titel aus, um nach der Version zu sortieren.<br /><br /> **Runtime**: die Version der .NET Framework, auf der die Komponente basiert. Wählen Sie den Titel aus, um nach der Laufzeitversion zu sortieren.<br /><br /> **Path**: der Dateiname der Komponente und der Pfad, in dem Sie sich befindet. Wählen Sie den Titel aus, um nach dem Pfad zu sortieren.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Analysis Services Designer und Dialog Felder &#40;Mehrdimensionale Daten&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Verwaltung von mehrdimensionalen Modellen](multidimensional-models/multidimensional-model-assemblies-management.md)  
  
  
