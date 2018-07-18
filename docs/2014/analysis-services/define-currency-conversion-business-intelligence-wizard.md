---
title: Definieren der Währungsumrechnung (Business Intelligence-Assistent) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.asvs.biwizard.currencyconversion.existingscriptpage.f1
ms.assetid: 37dd65b7-9d8d-44ad-b316-96a92c622472
caps.latest.revision: 21
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ce1916bd988d23dfd33f689f189436a50408a207
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37159511"
---
# <a name="define-currency-conversion-business-intelligence-wizard"></a>Währungsumrechnung definieren (Business Intelligence-Assistent)
  Auf der Seite **Währungsumrechnung definieren** können Sie das MDX-Skript (Multidimensional Expressions) überprüfen, in dem die vom Business Intelligence-Assistenten erzeugte Währungsumrechnungsfunktion enthalten ist. Mithilfe dieses vom Assistenten erzeugten MDX-Skripts können Sie die zuvor definierte Währungsumrechnungsfunktion im MDX-Skript des Cubes entweder überschreiben oder durch Anfügen erweitern.  
  
> [!NOTE]  
>  Diese Seite wird nur angezeigt, wenn der Business Intelligence-Assistent im MDX-Skript des Cubes mindestens eine zuvor definierte Währungsumrechnung erkennt. Währungsumrechnungen sind im MDX-Skript eines Cubes durch folgende Kommentare gekennzeichnet:  
>   
>  `//<Currency conversion>`  
>   
>  `...`  
>   
>  `[MDX statements for the currency conversion]`  
>   
>  `...`  
>   
>  `//</Currency conversion>`  
>   
>  Wenn Sie diese Kommentare ändern oder löschen, können durch den Business Intelligence-Assistenten keine zuvor definierten Währungsumrechnungen erkannt werden.  
  
## <a name="options"></a>Tastatur  
 **Neues Währungsumrechnungsskript**  
 Zeigt das von der aktuellen Sitzung des Business Intelligence-Assistenten erzeugte MDX-Skript an.  
  
 **Vorhandenes Währungsumrechnungsskript überschreiben**  
 Wählen Sie diese Option aus, um das unter **Vorhandenes Währungsumrechnungsskript** aufgelistete MDX-Skript mit dem im Feld **Neues Währungsumrechnungsskript**angezeigte MDX-Skript zu überschreiben.  
  
 **Fügen Sie nach**  
 Wählen Sie diese Option aus, um das unter **Neues Währungsumrechnungsskript** aufgelistete MDX-Skript an das im Feld **Vorhandenes Währungsumrechnungsskript**angezeigte MDX-Skript anzufügen. Das angefügte Skript wird in einem neuen Abschnitt angezeigt.  
  
 **Vorhandenes Währungsumrechnungsskript**  
 Wählen Sie den Abschnitt des vorhandenen MDX-Skripts mit der zuvor definierten Währungsumrechnungsfunktion aus, der jetzt überschrieben oder angefügt werden soll.  
  
## <a name="see-also"></a>Siehe auch  
 [Business Intelligence-Assistent F1-Hilfe](business-intelligence-wizard-f1-help.md)   
 [Cube-Designer &#40;Analysis Services – mehrdimensionale Daten&#41;](cube-designer-analysis-services-multidimensional-data.md)   
 [Dimensions-Designer &#40;Analysis Services – mehrdimensionale Daten&#41;](dimension-designer-analysis-services-multidimensional-data.md)  
  
  
