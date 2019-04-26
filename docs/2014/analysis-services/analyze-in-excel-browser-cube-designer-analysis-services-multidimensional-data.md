---
title: In Excel analysieren (Registerkarte ' Browser ', Cube-Designer) (Analysis Services – mehrdimensionale Daten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.browsecube.datapane.f1
- sql12.asvs.ssms.analyzeinexcel.f1
ms.assetid: 890ed457-137e-44ac-9b2c-83344a1b8fc9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: cdd0c98a00b5643c73b1536b7449c855a444aea8
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62643519"
---
# <a name="analyze-in-excel-browser-tab-cube-designer-analysis-services---multidimensional-data"></a>In Excel analysieren (Registerkarte 'Browser', Cube-Designer) (Analysis Services – Mehrdimensionale Daten)
  Die Funktion**In Excel analysieren** bietet dem Cubeentwickler eine Möglichkeit, schnell zu überprüfen, wie ein Projekt für den Endbenutzer aussehen würde. Über die Funktion **In Excel analysieren** wird Microsoft Excel geöffnet; stellt eine Datenquellenverbindung mit der Arbeitsbereichsdatenbank her und fügt automatisch eine PivotTable in das Arbeitsblatt ein. Diese Funktion ersetzt das Office-Websteuerelement, durch das in vorherigen Versionen eine eingebettete PivotTable auf der Registerkarte Browser bereitgestellt wurde.  
  
 **So zeigen Sie Cubedaten an**  
  
1.  Doppelklicken Sie im Projektmappen-Explorer von [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]auf einen Cube, um ihn im Cube-Designer zu öffnen.  
  
2.  Klicken Sie auf die Registerkarte **Browser** .  
  
3.  Klicken Sie auf **Verbindung wiederherstellen** , um die Verbindung zu überprüfen.  
  
4.  Klicken Sie in der Menüleiste auf das Excel-Symbol.  
  
5.  Klicken Sie auf **Aktivieren**, wenn Sie zur Aktivierung von Datenverbindungen aufgefordert werden. Excel wird unter Verwendung der aktuellen Datenverbindung geöffnet. Dem Arbeitsblatt wird eine PivotTable hinzugefügt, sodass Sie die Daten direkt durchsuchen können.  
  
 Sie können nun interaktiv eine PivotTable erstellen, indem Sie Measures aus der Faktentabelle in den Wertebereich und Dimensionsattribute in die Zeilen- und Spaltenbereiche ziehen. Wenn Sie über Hierarchien verfügen, fügen Sie diese dem Zeilen- oder Spaltenbereich hinzu. Sie können Rollups oder Drilldowns in der Hierarchie ausführen, um Faktendaten auf unterschiedlichen Ebenen zu durchsuchen.  
  
 Objekte und Daten werden innerhalb des Kontexts des effektiven Benutzers oder der Rolle und Perspektive angezeigt. Bei Verwendung von Excel werden die Anmeldeinformationen des aktuellen Benutzers und nicht die auf der Seite **Identitätswechselinformationen** angegebenen Anmeldeinformationen zum Herstellen einer Verbindung mit der Datenquelle verwendet, wenn eine Abfrage ausgeführt wird.  
  
> [!NOTE]  
>  Um die Funktion In Excel analysieren zu verwenden, muss Excel auf demselben Computer wie [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]installiert sein. Wenn Excel nicht auf demselben Computer installiert ist, können Sie Excel auf einem anderen Computer verwenden und eine Verbindung mit dem Cube als Datenquelle herstellen. Sie können dem Arbeitsblatt dann manuell eine PivotTable hinzufügen. Modellobjekte (Tabellen, Spalten, Measures und KPIs) sind als Felder in der PivotTable-Feldliste enthalten.  
  
 Weitere Informationen zur Funktion **In Excel analysieren** finden Sie in den folgenden Ressourcen.  
  
 [Analysieren in Excel &#40;SSAS – tabellarisch&#41;](tabular-models/analyze-in-excel-ssas-tabular.md)  
  
 [Analysieren eines Tabellenmodells in Excel &#40;SSAS – tabellarisch&#41;](tabular-models/analyze-a-tabular-model-in-excel-ssas-tabular.md)  
  
 [Durchsuchen von Daten und Metadaten im Cube](multidimensional-models/browse-data-and-metadata-in-cube.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Browser &#40;Cube-Designer&#41; &#40;Analysis Services – mehrdimensionale Daten&#41;](browser-cube-designer-analysis-services-multidimensional-data.md)   
 [Symbolleiste &#40;Registerkarte ' Browser ', Cube-Designer&#41; &#40;Analysis Services – mehrdimensionale Daten&#41;](toolbar-browser-tab-cube-designer-analysis-services-multidimensional-data.md)   
 [Metadaten &#40;Registerkarte ' Browser ', Cube-Designer&#41; &#40;Analysis Services – mehrdimensionale Daten&#41;](metadata-browser-tab-cube-designer-analysis-services-multidimensional-data.md)   
 [Abfrage- und Filterbereich &#40;Registerkarte ' Browser ', Cube-Designer&#41; &#40;Analysis Services – mehrdimensionale Daten&#41;](query-filter-browser-cube-designer-analysis-services-multidimensional-data.md)  
  
  
