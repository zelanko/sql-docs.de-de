---
title: Dimensions Schlüssel und-Typ angeben (Dimensions-Assistent) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensionwizard.dimensionkeyandtype.f1
ms.assetid: d7d5db55-36c3-45f6-ade3-29aa516589c1
author: minewiskan
ms.author: owend
ms.openlocfilehash: 019c4ea2744ec27aa7dc24d5065c176551e8cbeb
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84940391"
---
# <a name="specify-dimension-key-and-type-dimension-wizard"></a>Dimensionsschlüssel und -typ angeben (Dimensions-Assistent)
  Auf der Seite **Dimensionsschlüssel und -typ angeben** können Sie das Schlüsselattribut der Dimension definieren und kennzeichnen, ob es sich um eine langsam veränderliche Dimension (Slowly Changing Dimension, SCD) handelt.  
  
> [!NOTE]  
>   Diese Seite wird nur angezeigt, wenn Sie auf der Seite **Erstellungsmethode auswählen** die Option **Dimension ohne eine Datenquelle erstellen** und auf der Seite **Dimensionstyp auswählen** die Option **Standarddimension** ausgewählt haben.  
  
## <a name="options"></a>Tastatur  
 **Schlüsselattribut**  
 Wählen Sie das Attribut aus, das als Schlüsselattribut der Dimension dienen soll.  
  
> [!NOTE]  
>  Wenn für die Dimension keine Attribute definiert wurden, ist für diese Option lediglich der Wert **Erstellen Sie das Schlüsselattribut automatisch** verfügbar. Sobald für die Dimension Attribute definiert sind, ist dieser Wert nicht mehr verfügbar.  
  
 **Dies ist eine veränderliche Dimension**  
 Wählen Sie diese Option aus, um zu kennzeichnen, dass es sich bei der Dimension um eine langsam veränderliche Dimension handelt. Wenn Sie diese Option auswählen, werden zusätzliche Spalten und Attribute erstellt, die verwendet werden können, um die Bewegungen der Elemente in den Hierarchien der Dimension im Verlauf der Zeit nachzuverfolgen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Dimensions-Assistent F1-Hilfe](dimension-wizard-f1-help.md)   
 [Dimensionen &#40;Analysis Services Mehrdimensionale Daten&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)   
 [Dimensionen in mehrdimensionalen Modellen](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
