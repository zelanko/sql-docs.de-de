---
title: Definieren der Verweis auf lokale Währung (Business Intelligence-Assistent) | Microsoft Docs
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
- sql12.asvs.biwizard.currencyconversion.localcurrency.f1
ms.assetid: 74993b0d-dfca-476b-acba-d66c593680a5
caps.latest.revision: 24
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 10810e19ec00aa77a14cb5a21789dfee1f9ae09a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36047025"
---
# <a name="define-local-currency-reference-business-intelligence-wizard"></a>Verweis auf lokale Währung definieren (Business Intelligence-Assistent)
  Definieren Sie mithilfe der Seite **Verweis auf lokale Währung definieren** die lokalen Währungen für die Währungsumrechnungsfunktion, die für den auf der Seite **Umrechnungstyp auswählen** angegebenen m:n- oder n:1-Umrechnungstyp verwendet wird. Eine lokale Währung ist die Währung, in der die Transaktionen für die auf der Seite **Measures auswählen** ausgewählten Measures gespeichert werden.  
  
> [!NOTE]  
>  Diese Seite wird nicht angezeigt, wenn der Business Intelligence-Assistent vom Dimensions-Designer aus oder durch einen Rechtsklick auf eine Dimension im Projektmappen-Explorer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] gestartet wurde. Des Weiteren wird diese Seite nicht angezeigt, wenn auf der Seite **Umrechnungstyp auswählen** die Option **1:n** ausgewählt wurde.  
  
## <a name="options"></a>Tastatur  
 **Bezeichner in der Faktentabelle**  
 Wählen Sie diese Option aus, um ein Attribut anzugeben, durch das Währungsbezeichner für lokale Währungen in einer Währungsdimension bereitgestellt werden, auf die die Faktentabelle verweist, in der die auf der Seite **Measures auswählen** ausgewählten Measures enthalten sind. (Eine Währung in einer Kontodimension, deren `Type` -Eigenschaftensatz auf *Währung*.)  
  
 Verwenden Sie diese Option, wenn die lokale Währung für diese Transaktion durch die Transaktion selbst bestimmt wird. In der [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Beispieldatenbank[!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]verfügt die Measuregruppe Internet Sales über eine reguläre Dimensionsbeziehung mit der Währungsdimension. Die Faktentabelle für diese Measuregruppe enthält eine Fremdschlüsselspalte, die auf die Währungsbezeichner in der Dimensionstabelle für diese Dimension verweist.  
  
 **Währungsdimension und Attribut, die auf den Faktendaten verwiesen wird**  
 Wählen Sie das Währungsattribut innerhalb einer Währungsdimension aus, deren Mitglieder die Währungsbezeichner für lokale Währungen darstellen. (Ein währungsattribut ist eines, dessen `Type` -Eigenschaftensatz auf *Währung*.)  
  
> [!NOTE]  
>  Diese Option ist nicht verfügbar, wenn die Option **Bezeichner in der Faktentabelle** nicht ausgewählt ist.  
  
 **Attribute in der Dimensionstabelle**  
 Mithilfe dieser Option können Sie ein Attribut aus einer Dimension angeben, die sich auf die Measuregruppe bezieht, in der Währungsbezeichner für lokale Währungen enthalten sind.  
  
 Verwenden Sie diese Option, wenn die lokale Währung für diese Transaktion durch die Beziehung zwischen einer Transaktion und einer anderen Geschäftseinheit, beispielsweise einem Standort, bestimmt wird. In der [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Beispieldatenbank[!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]besitzt beispielsweise die Measuregruppe Finanzbericht eine Dimensionsbeziehung zur Währungsdimension, auf die durch die Organsiationsdimension verwiesen wird. Das bedeutet, dass die Faktentabelle für die Measuregruppe Finanzbericht eine Fremdschlüsselspalte enthält, die auf Mitglieder in der Dimensionstabelle für die Organisationsdimension verweist. Die Dimensionstabelle für die Organisationsdimension wiederum enthält eine Fremdschlüsselspalte, die auf die Währungsbezeichner in der Dimensionstabelle für die Währungsdimension verweist.  
  
 **Dimensionsattribut, die Währung verweist**  
 Wählen Sie das Attribut innerhalb einer Dimension aus, deren Mitglieder auf die Währungsbezeichner für lokale Währungen verweisen.  
  
> [!NOTE]  
>  Diese Option ist nicht verfügbar, wenn die Option **Attribute in der Dimensionstabelle** nicht ausgewählt ist.  
  
## <a name="see-also"></a>Siehe auch  
 [Business Intelligence-Assistent F1-Hilfe](business-intelligence-wizard-f1-help.md)   
 [Cube-Designer &#40;Analysis Services – mehrdimensionale Daten&#41;](cube-designer-analysis-services-multidimensional-data.md)   
 [Dimensions-Designer &#40;Analysis Services – mehrdimensionale Daten&#41;](dimension-designer-analysis-services-multidimensional-data.md)  
  
  