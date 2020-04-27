---
title: Festlegen benutzerdefinierter Element Formeln für Attribute in einer Dimension | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Business Intelligence enhancements [Analysis Services], custom member formulas
- member formulas [Analysis Services]
- dimensions [Analysis Services], Business Intelligence enhancements
- custom member formulas [Analysis Services]
- CustomRollupColumn property
ms.assetid: c4467b08-ce59-4de7-a2d9-c22e246bdd52
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 08db0d81ac198795386391f977d09d20ff8d22ac
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66076881"
---
# <a name="set-custom-member-formulas-for-attributes-in-a-dimension"></a>Festlegen benutzerdefinierter Elementformeln für Attribute in einer Dimension
  Fügen Sie einem Cube oder einer Dimension eine Erweiterung für benutzerdefinierte Elementformeln hinzu, um die Standardaggregation, die einem Dimensionselement zugeordnet ist, durch die Ergebnisse eines MDX-Ausdrucks (Multidimensional Expressions) zu ersetzen. (Durch diese Erweiterung wird die `CustomRollupColumn`-Eigenschaft für ein angegebenes Attribut in einer Dimension festgelegt.)  
  
> [!NOTE]  
>  Benutzerdefinierte Formeln stehen nur für Dimensionen zur Verfügung, die auf bestehenden Datenquellen basieren. Bei Dimensionen, die ohne Datenquelle erstellt wurden, müssen Sie den Schemagenerierungs-Assistenten ausführen, um eine Datenquellensicht vor dem Hinzufügen einer benutzerdefinierten Elementformel zu erstellen.  
  
 Verwenden Sie zum Hinzufügen einer benutzerdefinierten Elementformel den Business Intelligence-Assistenten, und wählen Sie auf der Seite **Erweiterung auswählen** die Option **Benutzerdefinierte Elementformel erstellen** aus. Der Assistent führt Sie durch die Schritte zum Auswählen einer Dimension, auf die eine benutzerdefinierte Elementformel angewendet werden soll, sowie zum Aktivieren der Formel.  
  
## <a name="selecting-a-dimension"></a>Auswählen einer Dimension  
 Auf der ersten Seite des Assistenten unter **Benutzerdefinierte Elementformel erstellen** geben Sie die Dimension an, auf die eine benutzerdefinierte Elementformel angewendet werden soll. Durch Anwenden der benutzerdefinierten Elementformel auf die ausgewählte Dimension werden Änderungen an der Dimension vorgenommen. Diese Änderungen werden an alle Cubes vererbt, die die ausgewählte Dimension enthalten.  
  
## <a name="enabling-a-custom-member-formula"></a>Aktivieren einer benutzerdefinierten Elementformel  
 Auf der zweiten Seite unter **Benutzerdefinierte Elementformel erstellen** ordnen Sie die Quellspalte, die die benutzerdefinierte Elementformel enthält, einem oder mehreren Attributen in der Dimension zu. Aktivieren Sie in der **Attribut** -Spalte das Kontrollkästchen neben dem Attribut, das der Spalte mit der benutzerdefinierten Elementformel zugeordnet werden soll. Nach dem Auswählen der einzelnen Attribute zeigt der Assistent das Dialogfeld **Spalte auswählen** an. Klicken Sie in diesem Dialogfeld auf die Spalte in der Dimensionstabelle, die die Formel enthält. Wenn Sie eine Auswahl nach dem Schließen des Dialogfelds **Spalte auswählen** ändern möchten, klicken Sie auf die zu ändernde **Quellspaltenzelle** , und klicken Sie dann auf die Auslassungspunkte (**...**), um das Dialogfeld **Spalte auswählen** erneut zu öffnen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwenden des Business Intelligence-Assistenten zum Erweitern von Dimensionen](../use-the-business-intelligence-wizard-to-enhance-dimensions.md)  
  
  
