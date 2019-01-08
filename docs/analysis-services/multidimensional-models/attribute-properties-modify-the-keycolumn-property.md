---
title: Ändern der KeyColumn-Eigenschaft eines Attributs | Microsoft-Dokumentation
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4415c5dba3382e636488ac94408f163c8e54dc6f
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52539027"
---
# <a name="attribute-properties---modify-the-keycolumn-property"></a>Attributeigenschaften – Ändern der KeyColumn-Eigenschaft
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Sie können die **KeyColumns** -Eigenschaft eines Attributs ändern. Nehmen wir beispielsweise an, Sie möchten einen zusammengesetzten Schlüssel statt eines einzelnen Schlüssels für das Attribut verwenden.  
  
### <a name="to-modify-the-keycolumns-property-of-an-attribute"></a>So ändern Sie die KeyColumns-Eigenschaft eines Attributs  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]das Projekt, in dem Sie die **KeyColumns** -Eigenschaft ändern möchten.  
  
2.  Öffnen Sie den Dimensions-Designer, indem Sie eine der folgenden Aktionen ausführen:  
  
    -   Klicken Sie im **Projektmappen-Explorer**im Ordner **Dimensionen** mit der rechten Maustaste auf die Dimension, und klicken Sie anschließend entweder auf **Öffnen** oder **Sicht-Designer**.  
  
         -oder-  
  
    -   Im Cube-Designer auf die **Cubestruktur** Registerkarte, erweitern Sie dann die Cubedimension in der **Dimensionen** Bereich, und klicken Sie auf **bearbeiten \<Dimension >**.  
  
3.  Klicken Sie im Bereich **Attribute** der Registerkarte **Dimensionsstruktur** auf das Attribut, dessen **KeyColumns** -Eigenschaft Sie ändern möchten.  
  
4.  Klicken Sie im Fenster **Eigenschaften** auf den Wert für die **KeyColumns** -Eigenschaft.  
  
5.  Klicken Sie auf die Schaltfläche zum Durchsuchen **(...)** , die in der Wertzelle des Eigenschaftenfelds angezeigt wird.  
  
     Das Dialogfeld **Schlüsselspalten** wird geöffnet.  
  
6.  Um eine vorhandene Schlüsselspalte zu entfernen, wählen Sie die Spalte in der Liste **Schlüsselspalten** aus, und klicken Sie anschließend auf die Schaltfläche **\<** .  
  
7.  Um eine Schlüsselspalte hinzuzufügen, wählen Sie die Spalte in der Liste **Verfügbare Spalten** aus, und klicken Sie anschließend auf die Schaltfläche **>** .  
  
    > [!NOTE]  
    >  Wenn Sie mehrere Schlüsselspalten definieren, bestimmt die Reihenfolge, in der diese Spalten in der Liste **Schlüsselspalten** aufgeführt sind, die Anzeigereihenfolge. Beispielsweise verfügt ein <localizedText>Month</localizedText>-Attribut über zwei Schlüsselspalten: <localizedText>Month</localizedText> und <localizedText>Year</localizedText>. Wenn die &lt;localizedText&gt;Year&lt;/localizedText&gt;-Spalte in der Liste vor der &lt;localizedText&gt;Month&lt;/localizedText&gt;-Spalte steht, sortiert [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] zuerst nach Jahr und dann nach Monat. Wenn die &lt;localizedText&gt;Month&lt;/localizedText&gt;-Spalte vor der &lt;localizedText&gt;Year&lt;/localizedText&gt;-Spalte steht, sortiert [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] zuerst nach Monat und dann nach Jahr.  
  
8.  Um die Reihenfolge von Schlüsselspalten zu ändern, wählen Sie eine Spalte aus und klicken dann auf die Schaltfläche **Nach oben** oder **Nach unten** .  
  
## <a name="see-also"></a>Siehe auch  
 [Dimensionsattributeigenschaftenverweis](../../analysis-services/multidimensional-models/dimension-attribute-properties-reference.md)  
  
  
