---
title: Ändern der KeyColumn-Eigenschaft eines Attributs | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- binding attributes [Analysis Services]
- attributes [Analysis Services], binding
- key columns [Analysis Services]
ms.assetid: a2643be4-8123-4cc3-baf9-e5ec54a1669d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 5c5effed34dda946d3c65028aa5834f4fbddf7cd
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66077252"
---
# <a name="modify-the-keycolumn-property-of-an-attribute"></a>Ändern der KeyColumns-Eigenschaft eines Attributs
  Sie können die **KeyColumns** -Eigenschaft eines Attributs ändern. Nehmen wir beispielsweise an, Sie möchten einen zusammengesetzten Schlüssel statt eines einzelnen Schlüssels für das Attribut verwenden.  
  
### <a name="to-modify-the-keycolumns-property-of-an-attribute"></a>So ändern Sie die KeyColumns-Eigenschaft eines Attributs  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]das Projekt, in dem Sie die **KeyColumns** -Eigenschaft ändern möchten.  
  
2.  Öffnen Sie den Dimensions-Designer, indem Sie eine der folgenden Aktionen ausführen:  
  
    -   Klicken Sie im **Projektmappen-Explorer**im Ordner **Dimensionen** mit der rechten Maustaste auf die Dimension, und klicken Sie anschließend entweder auf **Öffnen** oder **Sicht-Designer**.  
  
         -oder-  
  
    -   Im Cube-Designer auf die **Cubestruktur** Registerkarte, erweitern Sie dann die Cubedimension in der **Dimensionen** Bereich, und klicken Sie auf **bearbeiten \<Dimension >** .  
  
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
 [Dimensionsattributeigenschaftenverweis](dimension-attribute-properties-reference.md)  
  
  
