---
title: Anzeigen der Attribute im Dimensions-Designer | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- displaying attributes
- attributes [Analysis Services], viewing
- viewing attributes
ms.assetid: 855bef07-b72d-4ce3-bf02-de77abeee71a
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: c78e76030fe216df9e610b0e1ab6e6f37a652b30
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36050672"
---
# <a name="view-attributes-in-dimension-designer"></a>Anzeigen von Attributen im Dimensions-Designer
  Attribute werden für Dimensionsobjekte erstellt. Sie können Attribute mithilfe des Dimensions-Designers in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]anzeigen und konfigurieren. Die in einer Dimension enthaltenen Attribute werden im Dimensions-Designer auf der Registerkarte **Dimensionsstruktur** im Bereich **Attribute** angezeigt. Verwenden Sie diesen Bereich, um Attribute hinzuzufügen, zu entfernen oder zu konfigurieren. Sie können außerdem Attribute auswählen, um sie als Ebene in einer neuen Hierarchie zu verwenden oder einer vorhandenen Hierarchie als Ebene hinzuzufügen.  
  
 Um die Attribute in einer Dimension anzuzeigen, öffnen Sie den Dimensions-Designer für die Dimension. Die in der Dimension enthaltenen Attribute werden im Dimensions-Designer auf der Registerkarte **Dimensionsstruktur** im Bereich **Attribute**  angezeigt. Sie zeigen, um zwischen einer Liste, Struktur- oder Rasteransicht wechseln können **Attribute anzeigen in** auf die **Dimension** Menü [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] , und klicken Sie dann auf einen der Befehle in der folgenden Tabelle gezeigt.  
  
|Attribute anzeigen in|Description|  
|------------------------|-----------------|  
|**Liste**|Zeigt die Attribute im Listenformat an.<br /><br /> Klicken Sie mit der rechten Maustaste auf ein Attribut, um es aus der Liste zu löschen, umzubenennen oder die Verwendung des Attributs zu ändern.<br /><br /> Verwenden Sie diese Ansicht zum Erstellen von Hierarchien. Attributinformationen und Elementeigenschaften werden nicht angezeigt.|  
|**Struktur**|Zeigen Sie die Attribute im Strukturformat an, wobei die Dimension als Knoten der obersten Ebene in der Struktur dargestellt wird. Verwenden Sie diese Ansicht zum Anzeigen und Erstellen von Elementeigenschaften. Mithilfe dieser Ansicht können Sie auch Hierarchien erstellen. Erweitern Sie ein Attribut, um seine Attributbeziehungen anzuzeigen oder um eine neue Attributbeziehung zu erstellen. Führen Sie hierzu folgende Aktionen aus:<br /><br /> Klicken Sie auf die Dimension, ein Attribut oder eine Elementeigenschaft, um die zugehörigen Eigenschaften im Fenster **Eigenschaften** anzuzeigen.<br /><br /> Klicken Sie mit der rechten Maustaste auf ein Attribut oder eine Elementeigenschaft, um das Attribut oder die Elementeigenschaft aus der Liste zu löschen, umzubenennen oder die Verwendung zu ändern.|  
|**Raster**|Zeigt die Attribute im Rasterformat an. Klicken Sie auf eine Zeile im Raster, um Eigenschaften für dieses Attribut anzuzeigen.  Verwenden Sie diese Ansicht zum Erstellen und Konfigurieren von Attributen. Das Raster zeigt die folgenden Spalten an:<br /><br /> **Namen**: Zeigt den Wert von der **Namen** Eigenschaft. Geben Sie einen anderen Namen ein, um die Einstellung zu ändern.<br /><br /> **Verwendung**: Gibt an, ob dies ein regulärer, Schlüssel, übergeordnete oder AccountType-Attribut ist. Klicken Sie auf einen Wert in dieser Spalte, um eine andere Einstellung auszuwählen.<br /><br /> **Typ**: Gibt die Business Intelligence-Kategorie für das Attribut an. Klicken Sie auf diese Zelle, um eine andere Einstellung auszuwählen.<br /><br /> **Schlüsselspalte**: Zeigt den OLE DB-Datentyp für die **KeyColumn** -Eigenschaft des Attributs. Diese Spalte kann nicht geändert werden.<br /><br /> **Namensspalte**: Gibt an, ob die **NameColumn** -eigenschaftseinstellung für das Attribut ist derselben Spalte befindet wie die Einstellung für die **KeyColumn** Eigenschaft. Diese Spalte kann nicht geändert werden.|  
  
 In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]kennzeichnen die in der folgenden Tabelle dargestellten Symbole Attribute gemäß ihrer Verwendung.  
  
|Symbol|Attributverwendung|  
|----------|---------------------|  
|![Symbol "Attribut"](../media/as-icon-attribute.gif "Attribut (Symbol)")|Regular oder AccountType|  
|![Schlüsselattribut (Symbol)](../media/as-icon-key-attribute.gif "Key-Attribut (Symbol)")|Key|  
|![Übergeordnetes Attribut (Symbol)](../media/as-icon-parent-attribute.gif "übergeordnete Attribut (Symbol)")|Parent|  
  
## <a name="see-also"></a>Siehe auch  
 [Dimensionsattributeigenschaften-Verweis](dimension-attribute-properties-reference.md)  
  
  