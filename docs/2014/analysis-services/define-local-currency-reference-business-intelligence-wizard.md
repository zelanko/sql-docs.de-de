---
title: Verweis auf lokale Währung definieren (Business Intelligence-Assistent) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.biwizard.currencyconversion.localcurrency.f1
ms.assetid: 74993b0d-dfca-476b-acba-d66c593680a5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 558e2c7d62edcb9fb314b49d41fd7bd15413218d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66082180"
---
# <a name="define-local-currency-reference-business-intelligence-wizard"></a>Verweis auf lokale Währung definieren (Business Intelligence-Assistent)
  Definieren Sie mithilfe der Seite **Verweis auf lokale Währung definieren** die lokalen Währungen für die Währungsumrechnungsfunktion, die für den auf der Seite **Umrechnungstyp auswählen** angegebenen m:n- oder n:1-Umrechnungstyp verwendet wird. Eine lokale Währung ist die Währung, in der die Transaktionen für die auf der Seite **Measures auswählen** ausgewählten Measures gespeichert werden.  
  
> [!NOTE]  
>  Diese Seite wird nicht angezeigt, wenn der Business Intelligence-Assistent vom Dimensions-Designer aus oder durch Klicken mit der rechten Maustaste auf eine Dimension im Projektmappen-Explorer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]gestartet wurde. Des Weiteren wird diese Seite nicht angezeigt, wenn auf der Seite **Umrechnungstyp auswählen** die Option **1:n** ausgewählt wurde.  
  
## <a name="options"></a>Optionen  
 **Bezeichner in der Faktentabelle**  
 Wählen Sie diese Option aus, um ein Attribut anzugeben, durch das Währungsbezeichner für lokale Währungen in einer Währungsdimension bereitgestellt werden, auf die die Faktentabelle verweist, in der die auf der Seite **Measures auswählen** ausgewählten Measures enthalten sind. (Eine Währungs Dimension in einer Dimension `Type` , deren-Eigenschaft auf *Currency*festgelegt ist.)  
  
 Verwenden Sie diese Option, wenn die lokale Währung für diese Transaktion durch die Transaktion selbst bestimmt wird. Beispielsweise verfügt die Internet [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Sales-Measure[!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]-Gruppe in der-Beispieldatenbank über eine reguläre Dimensions Beziehung mit der Currency-Dimension. Die Faktentabelle für diese Measuregruppe enthält eine Fremdschlüsselspalte, die auf die Währungsbezeichner in der Dimensionstabelle für diese Dimension verweist.  
  
 **Währungsdimension und Attribut, auf die in den Faktendaten verwiesen wird**  
 Wählen Sie das Währungsattribut innerhalb einer Währungsdimension aus, deren Mitglieder die Währungsbezeichner für lokale Währungen darstellen. (Ein Währungs Attribut ist eines, `Type` dessen-Eigenschaft auf *Currency*festgelegt ist.)  
  
> [!NOTE]  
>   Diese Option ist nicht verfügbar, wenn die Option **Bezeichner in der Faktentabelle** nicht ausgewählt ist.  
  
 **Attribute in der Dimensionstabelle**  
 Mithilfe dieser Option können Sie ein Attribut aus einer Dimension angeben, die sich auf die Measuregruppe bezieht, in der Währungsbezeichner für lokale Währungen enthalten sind.  
  
 Verwenden Sie diese Option, wenn die lokale Währung für diese Transaktion durch die Beziehung zwischen einer Transaktion und einer anderen Geschäftseinheit, beispielsweise einem Standort, bestimmt wird. In der [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Beispieldatenbank verfügt die Finanz[!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]Berichterstattungs-Measure-Gruppe z. b. über eine referenzierte Dimensions Beziehung zur Currency-Dimension über die Organisations Dimension. Das bedeutet, dass die Faktentabelle für die Measuregruppe Finanzbericht eine Fremdschlüsselspalte enthält, die auf Mitglieder in der Dimensionstabelle für die Organisationsdimension verweist. Die Dimensionstabelle für die Organisationsdimension wiederum enthält eine Fremdschlüsselspalte, die auf die Währungsbezeichner in der Dimensionstabelle für die Währungsdimension verweist.  
  
 **Dimensionsattribut, das auf die Währung verweist**  
 Wählen Sie das Attribut innerhalb einer Dimension aus, deren Mitglieder auf die Währungsbezeichner für lokale Währungen verweisen.  
  
> [!NOTE]  
>   Diese Option ist nicht verfügbar, wenn die Option **Attribute in der Dimensionstabelle** nicht ausgewählt ist.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Business Intelligence Wizard (F1-Hilfe)](business-intelligence-wizard-f1-help.md)   
 [Cube-Designer &#40;Analysis Services Mehrdimensionale Daten&#41;](cube-designer-analysis-services-multidimensional-data.md)   
 [Der Dimensions-Designer &#40;Analysis Services Mehrdimensionale Daten&#41;](dimension-designer-analysis-services-multidimensional-data.md)  
  
  
