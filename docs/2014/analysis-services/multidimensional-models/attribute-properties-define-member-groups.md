---
title: Definieren von Elementgruppen | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- member groups [Analysis Services]
- grouping members
- DiscretizationMethod property
ms.assetid: 006cc915-c499-4781-b9a7-01ad31bebf6a
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 7b9daa1b369f1d42a4dbaea76060bdefe6741a18
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36160105"
---
# <a name="define-member-groups"></a>Definieren von Elementgruppen
  Wenn ein Attribut über viele Elemente verfügt, können Sie diese Elemente in Buckets gruppieren und so die Zahl derjenigen Elemente verringern, die Benutzer sehen, wenn sie die Daten einer Hierarchie durchsuchen. Sie können auch die Zahl der Buckets festlegen, in denen die Elemente Gruppen bilden und ein Benennungsschema für die Buckets vorgeben. Weitere Informationen finden Sie unter [Gruppieren von Attributelementen &#40;Diskretisierung&#41;](attribute-properties-group-attribute-members.md).  
  
 Sie gruppieren Elemente, indem Sie die **DiscretizationMethod** -Eigenschaft festlegen, auf die Sie im Fenster **Eigenschaften** in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]zugreifen können.  
  
 Wenn Sie Elementgruppen erstellen, sind Ihre Änderungen erst dann für Benutzer verfügbar, wenn Sie die Dimension verarbeitet haben. Weitere Informationen finden Sie unter [mehrdimensionalen Modell Objekt verarbeiten](processing-a-multidimensional-model-analysis-services.md).  
  
### <a name="to-create-member-groups"></a>So erstellen Sie eine Elementgruppe  
  
1.  Öffnen Sie die Dimension, mit der Sie arbeiten möchten. Standardmäßig wird die Registerkarte **Dimensionsstruktur** geöffnet.  
  
2.  Klicken Sie in **Attribute**mit der rechten Maustaste auf die Attribute, deren Elemente Sie gruppieren möchten, und klicken Sie anschließend auf **Eigenschaften**.  
  
3.  Wählen Sie in der Dropdownliste neben **DiscretizationMethod** eine Methode aus, nach der Sie die Elemente gruppieren. Weitere Informationen zu **DiscretizationMethod**-Einstellungen finden Sie unter [Gruppieren von Attributelementen &#40;Diskretisierung&#41;](attribute-properties-group-attribute-members.md).  
  
  