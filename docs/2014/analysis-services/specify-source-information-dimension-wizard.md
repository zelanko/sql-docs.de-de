---
title: Quell Informationen angeben (Dimensions-Assistent) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensionwizard.dimensionmaintable.f1
ms.assetid: 0538b490-5185-49e1-a783-4ce3539a0de5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 30234275a724dddce95cdad66e5e37a382a25e62
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66068177"
---
# <a name="specify-source-information-dimension-wizard"></a>Quellinformationen angeben (Dimensions-Assistent)
  Mithilfe der Seite **Hauptdimensionstabelle auswählen** können Sie die Datenquellensicht, die Hauptdimensionstabelle, die Schlüsselspalten und die Elementnamenspalte für die zu erstellende Dimension auswählen.  
  
 **So öffnen Sie den Dimensions-Assistenten**  
  
-   Klicken Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]im **Projektmappen-Explorer**mit der rechten Maustaste auf den Ordner **Dimensionen** eines [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Projekts, und klicken Sie anschließend auf **Neue Dimension**.  
  
## <a name="options"></a>Optionen  
 **Datenquellen Sicht**  
 Wählen Sie eine Datenquellensicht aus.  
  
 **Haupttabelle**  
 Wählen Sie eine Tabelle aus der ausgewählten Datenquellensicht aus, die als Haupttabelle für die Dimension verwendet werden soll.  
  
 **Schlüssel Spalten**  
 Wählen Sie die Schlüsselspalten aus der in **Haupttabelle** angegebenen Tabelle für das Schlüsselattribut der Dimension aus.  
  
> [!NOTE]  
>  Es können mehrere Spalten ausgewählt werden. Wenn eine Tabelle einen zusammengesetzten Primärschlüssel enthält, wählen Sie alle im zusammengesetzten Primärschlüssel enthaltenen Spalten aus. Wichtig ist die Reihenfolge der Schlüsselspalten.  
  
 **Namensspalte**  
 Wählen Sie die Spalte aus der in **Haupttabelle** angegebenen Tabelle aus, die die Elementnamen für die Dimension enthält. Es muss eine Namensspalte angegeben werden, wenn ein zusammengesetzter Schlüssel verwendet wird. Sie erstellen die Namensspalte für einen zusammengesetzten Schlüssel, indem Sie eine benannte Berechnung in der Datenquellensicht definieren, mit der die angegebenen Schlüsselspalten verkettet werden. Wenn ein einzelner Schlüssel verwendet wird, ist die Namensspalte optional.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Dimensions-Assistent F1-Hilfe](dimension-wizard-f1-help.md)   
 [Dimensionen &#40;Analysis Services Mehrdimensionale Daten&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)   
 [Dimensionen in mehrdimensionalen Modellen](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
