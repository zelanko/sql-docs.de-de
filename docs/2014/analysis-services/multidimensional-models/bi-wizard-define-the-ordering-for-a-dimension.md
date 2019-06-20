---
title: Definieren der Reihenfolge für eine Dimension | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- OrderBy property
- dimensions [Analysis Services], ordering
- Business Intelligence enhancements [Analysis Services], ordering
- dimensions [Analysis Services], Business Intelligence enhancements
- ordering dimensions [Analysis Services]
- OrderByAttributeID property
ms.assetid: c42fbd58-244d-4e0a-b715-6f919cbc3ad9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 05e75eb726d67e992a0a9320be8d23bbc547bedb
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66076859"
---
# <a name="define-the-ordering-for-a-dimension"></a>Definieren der Reihenfolge für eine Dimension
  Fügen Sie einem Cube oder einer Dimension die Erweiterung für die Attributreihenfolge hinzu, um anzugeben, wie die Elemente eines Attributs sortiert werden sollen. Elemente können nach dem Namen oder dem Schlüssel des Attributs oder dem Namen bzw. dem Schlüssel eines anderen Attributs (auf Basis einer Attributbeziehung) sortiert werden. Standardmäßig sind Elemente nach dem Namen sortiert. Diese Erweiterung ändert die Eigenschaftseinstellungen `OrderBy` und `OrderByAttributeID` für Attribute in einer Dimension.  
  
 Verwenden Sie zum Hinzufügen der Attributreihenfolge den Business Intelligence-Assistenten, und wählen Sie auf der Seite **Erweiterung auswählen** die Option **Attributreihenfolge angeben** aus. Der Assistent führt Sie durch die Schritte zum Auswählen einer Dimension, auf die die Attributreihenfolge angewendet werden soll, und zum Angeben der Reihenfolge der Attribute für die ausgewählte Dimension.  
  
## <a name="selecting-a-dimension"></a>Auswählen einer Dimension  
 Auf der ersten Seite des Assistenten, der Seite **Attributreihenfolge angeben** , geben Sie die Dimension an, auf die die Attributreihenfolge angewendet werden soll. Durch Anwenden der Attributreihenfolge auf die ausgewählte Dimension werden Änderungen an der Dimension vorgenommen. Diese Änderungen werden an alle Cubes vererbt, die die ausgewählte Dimension enthalten.  
  
## <a name="specifying-ordering"></a>Angeben der Reihenfolge  
 Auf der zweiten Seite des Assistenten, **Attributreihenfolge angeben** ,  geben Sie an, wie die Attribute in der Dimension sortiert werden.  
  
 In der **Reihenfolgenattribut** -Spalte können Sie das Attribut für die Reihenfolge ändern. Wenn das Attribut, das Sie verwenden, um die Elemente sortiert werden sollen, nicht in der Liste ist, scrollen Sie nach unten, und wählen Sie dann  **\<neues Attribut... >** zum Öffnen der **wählen Sie eine Spalte** Sie können im Dialogfeld Wählen Sie eine Spalte in einer Dimensionstabelle. Durch Auswählen einer Spalte mithilfe des Dialogfelds **Spalte auswählen** wird ein zusätzliches Attribut erstellt, mit dem die Elemente eines Attributs sortiert werden können.  
  
 In der **Kriterien** -Spalte können Sie dann auswählen, ob die Elemente des Attributs entweder nach **Schlüssel** oder nach **Name**sortiert werden sollen.  
  
  
