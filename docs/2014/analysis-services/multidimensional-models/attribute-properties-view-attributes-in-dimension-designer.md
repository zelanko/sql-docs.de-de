---
title: Anzeigen von Attributen im Dimensions-Designer | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- displaying attributes
- attributes [Analysis Services], viewing
- viewing attributes
ms.assetid: 855bef07-b72d-4ce3-bf02-de77abeee71a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ec86d5e7a910b7fb17397b1601fcc912b46c4d7f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66077130"
---
# <a name="view-attributes-in-dimension-designer"></a>Anzeigen von Attributen im Dimensions-Designer
  Attribute werden für Dimensionsobjekte erstellt. Sie können Attribute mithilfe des Dimensions-Designers in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]anzeigen und konfigurieren. Die in einer Dimension enthaltenen Attribute werden im Dimensions-Designer auf der Registerkarte **Dimensionsstruktur** im Bereich **Attribute** angezeigt. Verwenden Sie diesen Bereich, um Attribute hinzuzufügen, zu entfernen oder zu konfigurieren. Sie können außerdem Attribute auswählen, um sie als Ebene in einer neuen Hierarchie zu verwenden oder einer vorhandenen Hierarchie als Ebene hinzuzufügen.  
  
 Um die Attribute in einer Dimension anzuzeigen, öffnen Sie den Dimensions-Designer für die Dimension. Die in der Dimension enthaltenen Attribute werden im Dimensions-Designer auf der Registerkarte **Dimensionsstruktur** im Bereich **Attribute**  angezeigt. Sie können zwischen einer Listen-, Struktur- oder Raster durch Zeigen auf wechseln **Attribute anzeigen in** auf die **Dimension** im Menü [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] , und klicken Sie dann auf einen der Befehle in der folgenden Tabelle gezeigt.  
  
|Attribute anzeigen in|Beschreibung|  
|------------------------|-----------------|  
|**Liste**|Zeigt die Attribute im Listenformat an.<br /><br /> Klicken Sie mit der rechten Maustaste auf ein Attribut, um es aus der Liste zu löschen, umzubenennen oder die Verwendung des Attributs zu ändern.<br /><br /> Verwenden Sie diese Ansicht zum Erstellen von Hierarchien. Attributinformationen und Elementeigenschaften werden nicht angezeigt.|  
|**Struktur**|Zeigen Sie die Attribute im Strukturformat an, wobei die Dimension als Knoten der obersten Ebene in der Struktur dargestellt wird. Verwenden Sie diese Ansicht zum Anzeigen und Erstellen von Elementeigenschaften. Mithilfe dieser Ansicht können Sie auch Hierarchien erstellen. Erweitern Sie ein Attribut, um seine Attributbeziehungen anzuzeigen oder um eine neue Attributbeziehung zu erstellen. Führen Sie hierzu folgende Aktionen aus:<br /><br /> Klicken Sie auf die Dimension, ein Attribut oder eine Elementeigenschaft, um die zugehörigen Eigenschaften im Fenster **Eigenschaften** anzuzeigen.<br /><br /> Klicken Sie mit der rechten Maustaste auf ein Attribut oder eine Elementeigenschaft, um das Attribut oder die Elementeigenschaft aus der Liste zu löschen, umzubenennen oder die Verwendung zu ändern.|  
|**Raster**|Zeigt die Attribute im Rasterformat an. Klicken Sie auf eine Zeile im Raster, um Eigenschaften für dieses Attribut anzuzeigen.  Verwenden Sie diese Ansicht zum Erstellen und Konfigurieren von Attributen. Das Raster zeigt die folgenden Spalten an:<br /><br /> **Namen**: Zeigt den Wert des der **Namen** Eigenschaft. Geben Sie einen anderen Namen ein, um die Einstellung zu ändern.<br /><br /> **Nutzung**: Gibt an, ob dies ein regulärer, Schlüssel, Elternteil oder AccountType-Attribut ist. Klicken Sie auf einen Wert in dieser Spalte, um eine andere Einstellung auszuwählen.<br /><br /> **Typ**: Gibt an, die Business Intelligence-Kategorie für das Attribut. Klicken Sie auf diese Zelle, um eine andere Einstellung auszuwählen.<br /><br /> **Schlüsselspalte**: Zeigt die OLE DB-Datentyp für die **KeyColumn** -Eigenschaft des Attributs. Diese Spalte kann nicht geändert werden.<br /><br /> **Benennen Sie Spalte**: Gibt an, ob der **NameColumn** -eigenschaftseinstellung für das Attribut ist die gleiche Spalte wie die Einstellung für die **KeyColumn** Eigenschaft. Diese Spalte kann nicht geändert werden.|  
  
 In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]kennzeichnen die in der folgenden Tabelle dargestellten Symbole Attribute gemäß ihrer Verwendung.  
  
|Symbol|Attributverwendung|  
|----------|---------------------|  
|![Symbol "Kontoattribut"](../media/as-icon-attribute.gif "Attribut (Symbol)")|Regular oder AccountType|  
|![Schlüsselattribut (Symbol)](../media/as-icon-key-attribute.gif "schlüsselattributsymbol")|Key|  
|![Übergeordnetes Attribut (Symbol)](../media/as-icon-parent-attribute.gif "übergeordnetes Attribut (Symbol)")|Parent|  
  
## <a name="see-also"></a>Siehe auch  
 [Dimensionsattributeigenschaftenverweis](dimension-attribute-properties-reference.md)  
  
  
