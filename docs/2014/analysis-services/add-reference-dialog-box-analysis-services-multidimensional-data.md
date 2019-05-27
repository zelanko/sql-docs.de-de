---
title: Add Reference Dialog Box (Analysis Services – mehrdimensionale Daten) | Microsoft-Dokumentation
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
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66062862"
---
# <a name="add-reference-dialog-box-analysis-services---multidimensional-data"></a>Dialogfeld 'Verweis hinzufügen' (Analysis Services – Mehrdimensionale Daten)
  Mithilfe des Dialogfelds **Verweis hinzufügen** in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] können Sie einer [!INCLUDE[msCoName](../includes/msconame-md.md)] -.NET Framework-Assembly oder einem anderen Projekt des Entwicklungsprojekts einen Verweis hinzufügen. Sie können das Dialogfeld **Verweis hinzufügen** anzeigen, indem Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Ordner **Assemblys** eines [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Projekts klicken und aus dem Kontextmenü **Neuer Assemblyverweis** auswählen.  
  
## <a name="options"></a>Optionen  
  
|Begriff|Definition|  
|----------|----------------|  
|**.NET**|Mithilfe dieser Registerkarte können Sie einer registrierten Komponente einen Verweis hinzufügen. Mit dieser Registerkarte können Sie ein Raster anzeigen, das eine Liste der registrierten .NET Framework-Komponenten enthält. Wählen Sie ein oder mehrere Elemente aus dem Raster aus, und klicken Sie anschließend auf **Hinzufügen** , um die ausgewählten .NET-Komponenten zu **Ausgewählte Projekte und Komponenten**hinzuzufügen. Das Raster enthält die folgenden Spalten:<br /><br /> **Komponentenname**: Der vollständige oder Anzeigename der Komponente. Wählen Sie den Titel aus, um nach dem Komponentennamen zu sortieren.<br /><br /> **Version**: Die aufgeführte Versionsnummer der Komponente. Wählen Sie den Titel aus, um nach der Version zu sortieren.<br /><br /> **Laufzeit**: Die Version von .NET Framework, auf der die Version basiert. Wählen Sie den Titel aus, um nach der Laufzeitversion zu sortieren.<br /><br /> **Pfad**: Der Dateiname der Komponente und der Pfad zum Speicherort. Wählen Sie den Titel aus, um nach dem Pfad zu sortieren.|  
|**Durchsuchen**|Klicken Sie auf diese Option, um das Dateisystem nach einem Assembly zu durchsuchen, das nicht auf den Registerkarten **.NET** oder **Aktuell** aufgeführt ist. Auf dieser Registerkarte werden die folgenden Optionen angezeigt:<br /><br /> **Suchen in**: Wählen Sie einen Ordner aus dieser Dropdownliste aus. Nach der Auswahl eines Ordners aus dieser Liste wird der Inhalt im primären Bereich angezeigt.<br /><br /> **Zum zuletzt besuchten Ordner wechseln**: Mit dieser Option wechselt **Suchen in** zum vorigen Speicherort.<br /><br /> **Eine Ebene nach oben**: Sucht nach dem nächsthöheren Ordner in der Hierarchie.<br /><br /> **Neuen Ordner erstellen**: Wählen Sie diese Option aus, um unterhalb des in **Suchen in**ausgewählten Ordners einen untergeordneten Ordner zu erstellen.<br /><br /> **Menü „Ansicht“**: Wählen Sie diese Option aus, um die Inhalte des primären Bereichs anzuzeigen.  Weitere Informationen zu den Optionen im Menü **Ansicht**finden Sie im Thema über das Anzeigen von Dateien und Ordnern in der [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows-Dokumentation. Die folgenden Optionen stehen zur Verfügung:<br />Miniaturansicht<br />Kacheln<br />Symbole<br />Liste<br />Details<br /><br /> **Bereich für primäre**: Zeigt den Inhalt des Ordners im ausgewählten **Suchen in**. Wählen Sie ein oder mehrere Elemente aus, und klicken Sie dann auf **hinzufügen** zum Hinzufügen der ausgewählten Dateien zu **ausgewählte Projekte und Komponenten**. Weitere Informationen zu Optionen und zum Kontextmenü im primären Bereich finden Sie im Thema über das Anzeigen von Dateien und Ordnern in der Windows-Dokumentation.<br /><br /> **Dateiname**: Mithilfe dieser Option können Sie die anzuzeigenden Dateien oder Ordner filtern. Geben Sie einen vollständigen oder teilweisen Namen ein, für den der Filtervorgang durchgeführt werden soll. Sie können das Sternchen (\*) als Platzhalter verwenden. Geben Sie mehrere Dateinamen ein (die Dateinamen müssen in doppelte Anführungszeichen gesetzt und durch ein Leerzeichen voneinander getrennt sein), um mehrere Dateien auszuwählen. Sie können auch bereits überprüfte Dateien auswählen, indem Sie den entsprechenden Dateinamen aus der Dropdown-Liste auswählen. Tipp: Sie können die Webservern und Netzwerkcomputern suchen, indem Sie eingeben einer URL oder Netzwerkpfad in **Dateiname**. Beispielsweise werden mit http://mywebsite alle Dateien angezeigt, die unter der Webadresse „mywebsite“ verfügbar sind, während mit „\\\myserver\myshare“ alle Dateien angezeigt werden, die im Ordner „myshare“ des Servers „myserver“ gespeichert sind.<br /><br /> **Dateityp**: Mit dieser Option können Sie den Inhalt des Ordners oder Verzeichnisses im ausgewählten filtern **Suchen in** für einen bestimmten Dateityp.|  
|**Aktuelle**|Zeigt eine Liste der kürzlich zu Projekten in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]hinzugefügten Komponentenverweise an. Wählen Sie ein oder mehrere Elemente aus dem Raster aus, und klicken Sie anschließend auf **Hinzufügen** , um die ausgewählten .NET Framework-Assemblys zu **Ausgewählte Projekte und Komponenten**hinzuzufügen. Das Raster enthält die folgenden Spalten:<br /><br /> **Komponentenname**: Der vollständige oder Anzeigename der Komponente. Wählen Sie den Titel aus, um nach dem Komponentennamen zu sortieren.<br /><br /> **Version**: Die aufgeführte Versionsnummer der Komponente. Wählen Sie den Titel aus, um nach der Version zu sortieren.<br /><br /> **Laufzeit**: Die Version von .NET Framework, auf der die Version basiert. Wählen Sie den Titel aus, um nach der Laufzeitversion zu sortieren.<br /><br /> **Pfad**: Der Dateiname der Komponente und der Pfad zum Speicherort. Wählen Sie den Titel aus, um nach dem Pfad zu sortieren.|  
|**Hinzufügen**|Klicken Sie auf diese Option, um eine auf den Registerkarten **.NET**, **Durchsuchen**oder **Aktuell** ausgewählte Komponente zu **Ausgewählte Projekte und Komponenten**hinzuzufügen.|  
|**Entfernen**|Klicken Sie auf diese Option, um eine in **Ausgewählte Projekte und Komponenten**ausgewählte Komponente zu entfernen.|  
|**Ausgewählte Projekte und Komponenten**|Zeigt eine Liste von Komponentenverweisen an, die zum [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Projekt in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]hinzugefügt werden soll. Wählen Sie ein oder mehrere Elemente aus dem Raster aus, und klicken Sie dann auf **Entfernen** , um die ausgewählten Komponenten aus dem Raster zu entfernen. Das Raster enthält die folgenden Spalten:<br /><br /> **Komponentenname**: Der vollständige oder Anzeigename der Komponente. Wählen Sie den Titel aus, um nach dem Komponentennamen zu sortieren.<br /><br /> **Version**: Die aufgeführte Versionsnummer der Komponente. Wählen Sie den Titel aus, um nach der Version zu sortieren.<br /><br /> **Laufzeit**: Die Version von .NET Framework, auf der die Version basiert. Wählen Sie den Titel aus, um nach der Laufzeitversion zu sortieren.<br /><br /> **Pfad**: Der Dateiname der Komponente und der Pfad zum Speicherort. Wählen Sie den Titel aus, um nach dem Pfad zu sortieren.|  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services-Designer und-Dialogfelder &#40;mehrdimensionale Daten&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Verwaltung von mehrdimensionalen Modellassemblys](multidimensional-models/multidimensional-model-assemblies-management.md)  
  
  
