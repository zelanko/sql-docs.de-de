---
title: Wählen Sie Umrechnungstyp (Business Intelligence-Assistent) | Microsoft Docs
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
- sql12.asvs.biwizard.currencyconversion.conversiontype.f1
ms.assetid: 2c664138-e8a1-4c47-8e7d-ee01c57e4692
caps.latest.revision: 23
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: ba4018a6ce30e4e7de4e0ca3e79ae07007015650
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36161895"
---
# <a name="select-conversion-type-business-intelligence-wizard"></a>Umrechnungstyp auswählen (Business Intelligence-Assistent)
  Auf der Seite **Umrechnungstyp auswählen** können Sie die Beziehung zwischen lokalen Währungen und Berichtswährungen für Transaktionen definieren, die in mehreren Währungen gespeichert werden. Eine lokale Währung ist die Währung, in der die Transaktionen für die auf der Seite **Measures auswählen** ausgewählten Measures gespeichert werden. Eine Berichtswährung ist die Währung, in die die auf der Seite **Measures auswählen** ausgewählten Transaktionen umgerechnet werden.  
  
> [!NOTE]  
>  Diese Seite wird nicht angezeigt, wenn der Business Intelligence-Assistent vom Dimensions-Designer aus oder durch Klicken mit der rechten Maustaste auf eine Dimension im Projektmappen-Explorer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]gestartet wurde.  
  
## <a name="options"></a>Tastatur  
 **m:n**  
 Speichert Transaktionen mithilfe lokaler Währungen. Mithilfe der Währungsumrechnungsfunktion werden solche Transaktionen in die Pivotwährung umgerechnet, die auf der Seite **Optionen für die Währungsumrechnung festlegen** angegeben ist, und danach in eine oder mehrere weitere Berichtswährungen.  
  
 Die Pivotwährung kann z. B. auf US-Dollar (USD) festgelegt werden, während in der Faktentabelle die Transaktionen in Euro (EUR), Australischen Dollar (AUD) und Mexikanischen Pesos (MXN) gespeichert werden. Durch das Auswählen dieser Option werden diese Transaktionen von ihren angegebenen lokalen Währungen in die Pivotwährung umgerechnet. Die konvertierten Transaktionen werden dann erneut aus der Pivotwährung in die angegebenen Berichtswährungen umgerechnet. Dadurch können Transaktionen in den angegebenen lokalen Währungen gespeichert und entweder in der angegebenen Pivotwährung oder in einer beliebigen anderen der auf der Seite **Währungen für die Berichterstellung angeben** angegebenen Berichtswährungen angezeigt werden.  
  
 **n:1**  
 Speichert Transaktionen mithilfe lokaler Währungen. Mit der Währungsumrechnungsfunktion werden solche Transaktionen in die Pivotwährung umgerechnet, die auf der Seite **Optionen für die Währungsumrechnung festlegen** angegeben wurde. Die Pivotwährung dient als einzige angegebene Berichtswährung.  
  
> [!NOTE]  
>  Wenn diese Option ausgewählt ist, wird die Seite **Währungen für die Berichterstellung angeben** nicht angezeigt.  
  
 Die Pivotwährung kann z. B. auf US-Dollar (USD) festgelegt werden, während in der Faktentabelle die Transaktionen in Euro (EUR), Australischen Dollar (AUD) und Mexikanischen Pesos (MXN) gespeichert werden. Durch das Auswählen dieser Option werden diese Transaktionen von den angegebenen lokalen Währungen in die Pivotwährung umgerechnet. Dadurch können diese Transaktionen in den angegebenen lokalen Währungen gespeichert und in der angegebenen Pivotwährung angezeigt werden.  
  
 **1:n**  
 Speichert Transaktionen in der Pivotwährung, die auf der Seite **Optionen für die Währungsumrechnung festlegen** angegeben ist, und danach in einen oder mehreren weiteren Berichtswährungen.  
  
> [!NOTE]  
>  Wenn diese Option ausgewählt ist, wird die Seite **Verweis auf lokale Währung definieren** nicht angezeigt.  
  
 Die Pivotwährung kann z. B. auf US-Dollar (USD) festgelegt werden, und die Transaktionen werden in der Faktentabelle in USD gespeichert. Durch das Auswählen dieser Option werden diese Transaktionen aus der Pivotwährung in die angegebenen Berichtswährungen umgerechnet. Dadurch können Transaktionen in der angegebenen Pivotwährung gespeichert und entweder in der angegebenen Pivotwährung oder in einer beliebigen anderen der auf der Seite **Währungen für die Berichterstellung angeben** angegebenen Berichtswährungen angezeigt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Business Intelligence-Assistent F1-Hilfe](business-intelligence-wizard-f1-help.md)   
 [Cube-Designer &#40;Analysis Services – mehrdimensionale Daten&#41;](cube-designer-analysis-services-multidimensional-data.md)   
 [Dimensions-Designer &#40;Analysis Services – mehrdimensionale Daten&#41;](dimension-designer-analysis-services-multidimensional-data.md)  
  
  