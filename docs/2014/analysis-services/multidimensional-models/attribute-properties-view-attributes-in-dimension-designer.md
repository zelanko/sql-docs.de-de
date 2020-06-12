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
ms.openlocfilehash: 22e837aa038cb30947632194d829a383afcf4a82
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84544725"
---
# <a name="view-attributes-in-dimension-designer"></a>Anzeigen von Attributen im Dimensions-Designer
  Attribute werden für Dimensionsobjekte erstellt. Sie können Attribute mithilfe des Dimensions-Designers in anzeigen und konfigurieren [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Die in einer Dimension enthaltenen Attribute werden im Dimensions-Designer auf der Registerkarte **Dimensionsstruktur** im Bereich **Attribute** angezeigt. Verwenden Sie diesen Bereich, um Attribute hinzuzufügen, zu entfernen oder zu konfigurieren. Sie können außerdem Attribute auswählen, um sie als Ebene in einer neuen Hierarchie zu verwenden oder einer vorhandenen Hierarchie als Ebene hinzuzufügen.

 Um die Attribute in einer Dimension anzuzeigen, öffnen Sie den Dimensions-Designer für die Dimension. Die in der Dimension enthaltenen Attribute werden im Dimensions-Designer auf der Registerkarte **Dimensionsstruktur** im Bereich **Attribute**  angezeigt. Sie können zwischen einer Listen-, Struktur-oder Rasteransicht wechseln. zeigen Sie dazu im Menü **Dimension** von auf **Attribute anzeigen in** , [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] und klicken Sie dann auf einen der in der folgenden Tabelle aufgeführten Befehle.

|Attribute anzeigen in|Beschreibung|
|------------------------|-----------------|
|**Liste**|Zeigt die Attribute im Listenformat an.<br /><br /> Klicken Sie mit der rechten Maustaste auf ein Attribut, um es aus der Liste zu löschen, umzubenennen oder die Verwendung des Attributs zu ändern.<br /><br /> Verwenden Sie diese Ansicht zum Erstellen von Hierarchien. Attributinformationen und Elementeigenschaften werden nicht angezeigt.|
|**Linde**|Zeigen Sie die Attribute im Strukturformat an, wobei die Dimension als Knoten der obersten Ebene in der Struktur dargestellt wird. Verwenden Sie diese Ansicht zum Anzeigen und Erstellen von Elementeigenschaften. Mithilfe dieser Ansicht können Sie auch Hierarchien erstellen. Erweitern Sie ein Attribut, um seine Attributbeziehungen anzuzeigen oder um eine neue Attributbeziehung zu erstellen. Führen Sie hierzu folgende Aktionen aus:<br /><br /> Klicken Sie auf die Dimension, ein Attribut oder eine Elementeigenschaft, um die zugehörigen Eigenschaften im Fenster **Eigenschaften** anzuzeigen.<br /><br /> Klicken Sie mit der rechten Maustaste auf ein Attribut oder eine Elementeigenschaft, um das Attribut oder die Elementeigenschaft aus der Liste zu löschen, umzubenennen oder die Verwendung zu ändern.|
|**Raster**|Zeigt die Attribute im Rasterformat an. Klicken Sie auf eine Zeile im Raster, um Eigenschaften für dieses Attribut anzuzeigen.  Verwenden Sie diese Ansicht zum Erstellen und Konfigurieren von Attributen. Das Raster zeigt die folgenden Spalten an:<br /><br /> **Name**: zeigt den Wert der **Name** -Eigenschaft an. Geben Sie einen anderen Namen ein, um die Einstellung zu ändern.<br /><br /> Syntax **: gibt**an, ob es sich um ein reguläres, Schlüssel-, übergeordnetes oder AccountType-Attribut handelt. Klicken Sie auf einen Wert in dieser Spalte, um eine andere Einstellung auszuwählen.<br /><br /> **Type**: gibt die Business Intelligence Kategorie für das Attribut an. Klicken Sie auf diese Zelle, um eine andere Einstellung auszuwählen.<br /><br /> **Key Column**: zeigt den OLE DB Datentyp für die **KeyColumn** -Eigenschaft des Attributs an. Diese Spalte kann nicht geändert werden.<br /><br /> **Name Column**: gibt an, ob die **namecolenn** -Eigenschafts Einstellung für das Attribut dieselbe Spalte wie die Einstellung für die **KeyColumn** -Eigenschaft ist. Diese Spalte kann nicht geändert werden.|

 In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]kennzeichnen die in der folgenden Tabelle dargestellten Symbole Attribute gemäß ihrer Verwendung.

|Symbol|Attributverwendung|
|----------|---------------------|
|![Attribut (Symbol)](../media/as-icon-attribute.gif "Attribut (Symbol)")|Regular oder AccountType|
|![Schlüsselattribut (Symbol)](../media/as-icon-key-attribute.gif "Schlüsselattribut (Symbol)")|Schlüssel|
|![Übergeordnetes Attribut (Symbol)](../media/as-icon-parent-attribute.gif "Übergeordnetes Attribut (Symbol)")|Parent|

## <a name="see-also"></a>Weitere Informationen
 [Dimensionsattributeigenschaftenverweis](dimension-attribute-properties-reference.md)


