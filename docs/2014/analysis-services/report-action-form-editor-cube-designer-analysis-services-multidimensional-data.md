---
title: Berichts Aktions Formular-Editor (Registerkarte Aktionen, Cube-Designer) (Analysis Services-Mehrdimensionale Daten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.actionexpression.reportaction.f1
ms.assetid: cebfdd07-e376-46d6-86ef-b6f816a2f360
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9b514d2d85a01fdb4b13c922e81a39e694308334
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84539302"
---
# <a name="report-action-form-editor-actions-tab-cube-designer-analysis-services---multidimensional-data"></a>Berichtsaktionsformular-Editor (Registerkarte 'Aktionen', Cube-Designer) (Analysis Services – Mehrdimensionale Daten)
  Mithilfe des **Berichtsaktionsformular-Editors** auf der Registerkarte **Aktionen** im Cube-Designer können Sie die im Bereich **Aktionsplaner** ausgewählte Berichtsaktion ändern.  
  
## <a name="options"></a>Tastatur  
 **Name**  
 Geben Sie den Namen der Aktion ein.  
  
 **Aktionsziel**  
 Erweitern Sie diese Option, um die Optionen **Zieltyp** und **Zielobjekt** anzuzeigen.  
  
 **Zieltyp**  
 Wählen Sie den Typ des Objekts aus, dem die Aktion zugeordnet werden soll. Der Server gibt nur jene Aktionen an den Client zurück, die auf das Objekt vom angegebenen Typ angewendet werden. Die Aktion ist für den Client verfügbar, wenn die **Bedingung** erfüllt ist und die in der folgenden Tabelle angegebenen Objekte ausgewählt sind.  
  
|Wert|Ausgewähltes Objekt|  
|-----------|---------------------|  
|Attributelemente|Ein Element wird aus einer Ebene ausgewählt, die auf dem Attribut unter **Zielobjekt**basiert.<br /><br /> Hinweis: Andere Benutzerhierarchien, die das ausgewählte Attribut verwenden, erben die Berichtsaktion.|  
|Zellen|Die benannte Menge in **Zielobjekt** wird ausgewählt. Wählen Sie **Alle Zellen** aus, um alle Zellen im Cube auszuwählen.|  
|Cube|Der Cube in **Zielobjekt** wird ausgewählt. Wählen Sie CURRENTCUBE aus, um den aktuellen Cube zu verwenden.<br /><br /> Hinweis: Das Verwenden von CURRENTCUBE stellt eine zusätzliche Portabilität für Fälle bereit, in denen der Cube umbenannt oder die Aktion in andere Cubes kopiert wird. Es wird empfohlen, zum Darstellen des aktuellen Cubes CURRENTCUBE zu verwenden.|  
|Dimensionselemente|Ein Element der Dimension in **Zielobjekt** wird ausgewählt.|  
|Hierarchy|Die Hierarchie in **Zielobjekt** wird ausgewählt.|  
|Hierarchieelemente|Ein Element innerhalb der Hierarchie in **Zielobjekt** wird ausgewählt.|  
|Ebene|Die Ebene in **Zielobjekt** wird ausgewählt.|  
|Ebenenelemente|Ein Element innerhalb der Ebene in **Zielobjekt** wird ausgewählt.|  
  
 **Zielobjekt**  
 Wählen Sie das Objekt aus, dem die Aktion zugeordnet werden soll. Die- [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Instanz gibt nur die Aktionen, die für das ausgewählte Objekt gelten, an den Client zurück. Die Liste der verfügbaren Objekte wird durch die Auswahl unter **Zieltyp**eingeschränkt.  
  
 **Bedingung (Optional)**  
 Geben Sie einen MDX-Ausdruck (Multidimensional Expressions) ein, der eine optionale Bedingung für das Verwenden in Verbindung mit **Zielobjekt**beschreibt, wodurch die Verfügbarkeit der Aktion weiter eingeschränkt wird. Der Ausdruck muss einen booleschen Wert zurückgeben, der mit "True" anzeigt, dass die Aktion verfügbar ist.  
  
 Ziehen Sie ausgewählte Elemente aus dem Bereich **Berechnungstools** auf diese Option, um die MDX-Syntax für das ausgewählte Element einzuschließen.  
  
 **Berichts Server**  
 Erweitern Sie dieses Element, um die Optionen **Servername**, **Serverpfad**und **Berichtsformat** anzuzeigen.  
  
 **Servername**  
 Geben Sie den Namen der [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Instanz ein, auf der die Aktion den Bericht ausführt.  
  
 **Serverpfad**  
 Geben Sie den Pfad zum Bericht auf der [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Instanz ein. Geben Sie beispielsweise **Sales/YearlySalesByCategory**ein.  
  
 **Berichtsformat**  
 Wählen Sie das Format aus, in dem der Bericht zurückgegeben wird. In der folgenden Tabelle werden die verfügbaren Formate beschrieben.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|HTML5|Der Bericht wird in einem mit HTML 5.0 konformen Format zurückgegeben.|  
|HTML3|Der Bericht wird in einem mit HTML 3.2 konformen Format zurückgegeben.|  
|Excel|Der Bericht wird als [!INCLUDE[msCoName](../includes/msconame-md.md)] Office Excel-Arbeitsmappendatei (*.xls) zurückgegeben.|  
|PDF|Der Bericht wird als Datei im Adobe Portable Document-Format (*.pdf) zurückgegeben.|  
  
 **Parameter (Optional)**  
 Erweitern Sie dieses Element, um ein Raster anzuzeigen, in dem die Berichtsparameter für den in **Bericht**festgelegten Bericht angegeben werden können. Das Raster enthält die folgenden Spalten:  
  
|Column|Beschreibung|  
|------------|-----------------|  
|**Parameter Name**|Geben Sie den Namen des Berichtsparameters ein, der an den Bericht übergeben werden soll.|  
|**Parameter Wert**|Geben Sie den Wert des Berichtsparameters ein, der an den Bericht übergeben werden soll.<br /><br /> Klicken Sie auf die Schaltfläche mit den drei Punkten (**...**), um das Dialogfeld **MDX-Generator** anzuzeigen und einen MDX-Ausdruck zu erstellen, der den Wert des Berichtsparameters angibt. Weitere Informationen zum Dialogfeld **MDX-Generator** finden Sie unter [MDX-Generator &#40;Analysis Services – Mehrdimensionale Daten&#41;](mdx-builder-analysis-services-multidimensional-data.md).<br /><br /> Wenn der Parameter auf einen MDX-Ausdruck festgelegt ist, wird der Ausdruck beim Ausführen der Aktion ausgewertet. Andernfalls wird der Ausdruck unverändert an den Bericht übergeben.|  
  
 **Zusätzliche Eigenschaften**  
 Erweitern Sie die Option, um die Optionen **Aufruf**, **Anwendung**, **Beschreibung**, **Beschriftung**und **Beschriftung ist MDX** anzuzeigen.  
  
 **Aufruf**  
 Wählen Sie die Einstellung aus, durch die angegeben wird, wann die Aktion ausgeführt werden soll.  
  
> [!NOTE]  
>  Diese Option stellt einer Clientanwendung nur eine Empfehlung für den Ausführungszeitpunkt einer Aktion zur Verfügung. Sie steuert nicht direkt den Aufruf der Aktion.  
  
 Die folgende Tabelle beschreibt die verfügbaren Einstellungen.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|Batch|Die Aktion sollte als Teil eines Batch Vorgangs oder eines-Tasks ausgeführt werden [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .|  
|Interactive|Die Aktion wird ausgeführt, wenn der Benutzer die Aktion aufruft.|  
|Beim Öffnen|Die Aktion wird ausgeführt, wenn der Cube erstmalig geöffnet wird.|  
  
 **Anwendung**  
 Geben Sie den Namen der Anwendung ein, die die Zeichenfolge interpretieren kann, die von **Aktionsausdruck**zurückgegeben wurde.  
  
 Sie können diese Option auch verwenden, um zu ermitteln, welche Clientanwendung diese Aktion am häufigsten verwendet, oder um entsprechende Symbole neben der Aktion in einem Popupmenü anzuzeigen.  
  
> [!NOTE]  
>  Diese Option stellt nur eine Empfehlung für eine Clientanwendung bereit, die angibt, welche Clientanwendung eine Aktion ausführen soll. Sie steuert nicht direkt den Zugriff auf die Aktion. Clientanwendungen sollten alle Aktionen ausblenden, die anderen Clientanwendungen zugeordnet sind.  
  
 **Beschreibung**  
 Geben Sie die optionale Beschreibung der Aktion ein.  
  
 **Caption**  
 Geben Sie die Beschriftung ein, die für die Aktion in der Clientanwendung angezeigt wird, wenn **Beschriftung ist MDX** auf **FALSE**festgelegt ist.  
  
 Geben Sie den MDX-Ausdruck ein, der eine Zeichenfolge für die Beschriftung zurückgibt, wenn **Beschriftung ist MDX** auf **True**festgelegt ist.  
  
 **Beschriftung ist MDX**  
 Wählen Sie **FALSE** aus, um anzuzeigen, dass **Beschriftung** eine Literalzeichenfolge enthält, die eine Beschriftung darstellt, welche für die Aktion in der Clientanwendung angezeigt werden soll.  
  
 Wählen Sie **True** aus, um anzuzeigen, dass **Beschriftung** einen MDX-Ausdruck enthält, der eine Zeichenfolge mit einer Beschriftung zurückgibt, die für die Aktion in der Clientanwendung angezeigt werden soll. Der MDX-Ausdruck muss aufgelöst werden, bevor die Aktion an die Clientanwendung zurückgegeben wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Aktionen &#40;Cube-Designer&#41; &#40;Analysis Services Mehrdimensionale Daten&#41;](actions-cube-designer-analysis-services-multidimensional-data.md)   
 [Symbolleiste &#40;Registerkarte "Aktionen", Cube-Designer&#41; &#40;Analysis Services Mehrdimensionale Daten&#41;](toolbar-actions-tab-cube-designer-analysis-services-multidimensional-data.md)   
 [Aktions Planer &#40;Registerkarte Aktionen, Cube-Designer&#41; &#40;Analysis Services-Mehrdimensionale Daten&#41;](action-organizer-cube-designer-analysis-services-multidimensional-data.md)   
 [Berechnungs Tools &#40;Registerkarte "Aktionen", Cube-Designer&#41; &#40;Analysis Services Mehrdimensionale Daten&#41;](calculation-tools-actions-cube-designer-analysis-services-multidimensional-data.md)   
 [Aktions Formular-Editor &#40;Registerkarte Aktionen, Cube-Designer&#41; &#40;Analysis Services-Mehrdimensionale Daten&#41;](action-form-editor-cube-designer-analysis-services-multidimensional-data.md)   
 [Drillthrough-Aktions Formular-Editor &#40;Registerkarte Aktionen, Cube-Designer&#41; &#40;Analysis Services-Mehrdimensionale Daten&#41;](drillthrough-action-form-editor-cube-designer-analysis-services-multidimensional-data.md)  
  
  
