---
title: -Attribut Daten Attributdatenübersetzung (Dialogfeld) (Analysis Services – mehrdimensionale Daten) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.dimensiondesigner.dimensionstoragesettings.f1
helpviewer_keywords:
- Attribute Data Translation dialog box
ms.assetid: bed286de-1e9b-49de-b09e-3cd076aba152
caps.latest.revision: 22
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 1b8d7f28696e04045ca5ac3f11bf38d4c67f60c2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36148503"
---
# <a name="attribute-data-translation-dialog-box-analysis-services---multidimensional-data"></a>Dialogfeld 'Attributdatenübersetzung' (Analysis Services – Mehrdimensionale Daten)
  Mithilfe des Dialogfelds **Attributdatenübersetzung** können Sie die Spalte festlegen, in der die Übersetzungsbeschriftungsdaten enthalten sind, sowie die Sortierung und Sortierreihenfolge, die für die übersetzten Daten verwendet werden sollen. Das Dialogfeld **Attributdatenübersetzung** können Sie wie folgt aufrufen:  
  
-   Klicken Sie auf der Seite **Übersetzungen** von **Dimensions-Designer** im Bereich für die **Symbolleiste** auf **Neue Beschriftungsspalte** oder **Beschriftungsspalte bearbeiten**.  
  
-   Klicken Sie auf der Registerkarte **Übersetzungen** von **Dimension Designer** mit der rechten Maustaste in den Bereich für **Übersetzungsdetails** , und wählen Sie **Neue Beschriftungsspalte** oder **Beschriftungsspalte bearbeiten**aus.  
  
## <a name="options"></a>Tastatur  
 **Attribut**  
 Zeigt das ausgewählte Attribut an.  
  
 **Sprache**  
 Zeigt die ausgewählte Sprache an.  
  
 **Übersetzte Beschriftung**  
 Legt die aktuelle Beschriftung für das ausgewählte Attribut fest.  
  
 **Übersetzungsspalten**  
 Legt die Spalte fest, in der die übersetzte Beschriftung gespeichert wird. Es kann nur eine Spalte ausgewählt werden. Angezeigt werden alle verknüpften Tabellen, auf die von der primären Dimensionstabelle verwiesen wird.  
  
 **Sortierungskennzeichner**  
 Legt den Sortierungskennzeichner für das ausgewählte Attribut fest. Standardmäßig ist die aktuelle Windows-Sortierung ausgewählt. Klicken Sie auf den Pfeil nach unten, um eine der verfügbaren Sortierungen auszuwählen.  
  
 **Binär (Binary)**  
 Wählen Sie diese Option aus, um die Daten basierend auf den für jedes Zeichen definierten Bitmustern zu sortieren und zu vergleichen. Die binäre Sortierreihenfolge unterscheidet nach Groß-/Kleinschreibung (Kleinbuchstaben kommen immer vor Großbuchstaben) und Akzenten. Dies ist die schnellste Sortierreihenfolge.  
  
 Wenn diese Option nicht ausgewählt ist, werden von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] die Sortier- und Vergleichsregeln verwendet, die in Wörterbüchern für die zugeordnete Sprache oder das Alphabet definiert sind.  
  
> [!NOTE]  
>  Wenn diese Option ausgewählt ist, sind die Optionen **Unterscheidung nach Groß-/Kleinschreibung**, **Unterscheidung nach Akzent**, **Unterscheidung nach Kana**und **Unterscheidung nach Breite** deaktiviert.  
  
 **Groß-/Kleinschreibung unterschieden**  
 Wählen Sie diese Option aus, um Daten auf der Grundlage der Wörterbuchregeln zu sortieren und zu vergleichen, die für die zugeordnete Sprache oder das Alphabet bereitgestellt werden, und um zwischen Groß- und Kleinschreibung zu unterscheiden.  
  
 Wenn nicht ausgewählt, betrachtet [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] die Groß- und Kleinschreibungsversionen von Buchstaben als gleich. [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] definiert, ob Kleinbuchstaben niedriger oder höher als Großbuchstaben einsortiert, wenn stehen keine **Groß-/Kleinschreibung** nicht ausgewählt ist.  
  
 **Unterscheidung nach Akzent**  
 Wählen Sie diese Option aus, um Daten auf der Grundlage der Wörterbuchregeln zu sortieren und zu vergleichen, die für die zugeordnete Sprache oder das Alphabet bereitgestellt werden, und um zwischen Buchstaben mit und ohne Akzent zu unterscheiden. Beispielsweise ist 'a' nicht mit 'á' identisch.  
  
 Wenn diese Option nicht ausgewählt ist, werden die Zeichen mit und ohne Akzent von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] als identisch betrachtet.  
  
 **Kana vertrauliche**  
 Wählen Sie diese Option aus, um Daten basierend auf den für die zugehörige Sprache oder das Alphabet bereitgestellten Wörterbuchregeln zu sortieren und zu vergleichen und zwischen den beiden japanischen Kanazeichentypen zu unterscheiden: Hiragana und Katakana.  
  
 Wenn diese Option nicht ausgewählt ist, werden Hiragana- und Katakanazeichen von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] als identisch betrachtet.  
  
 **Breite unterschieden**  
 Wählen Sie diese Option aus, um Daten auf der Grundlage der Wörterbuchregeln zu sortieren und zu vergleichen, die für die zugeordnete Sprache oder das Alphabet bereitgestellt werden, und um zwischen einem Einzelbytezeichen (halbe Breite) und demselben Zeichen als Doppelbytezeichen (ganze Breite) zu unterscheiden.  
  
 Wenn diese Option nicht ausgewählt ist, werden die Single-Byte- und die Double-Byte-Darstellung desselben Zeichens von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] als identisch betrachtet.  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services-Designer und-Dialogfelder &#40;mehrdimensionale Daten&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Übersetzungsdetails &#40;Registerkarte Übersetzungen, Dimensions-Designer&#41; &#40;Analysis Services – mehrdimensionale Daten&#41;](translation-details-dimension-designer-analysis-services-multidimensional-data.md)  
  
  