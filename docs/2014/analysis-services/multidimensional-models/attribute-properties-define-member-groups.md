---
title: Definieren von Elementgruppen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- member groups [Analysis Services]
- grouping members
- DiscretizationMethod property
ms.assetid: 006cc915-c499-4781-b9a7-01ad31bebf6a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2da7f19fa9626792a117ffa0108a28c50f32c5f5
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66077299"
---
# <a name="define-member-groups"></a>Definieren von Elementgruppen
  Wenn ein Attribut über viele Elemente verfügt, können Sie diese Elemente in Buckets gruppieren und so die Zahl derjenigen Elemente verringern, die Benutzer sehen, wenn sie die Daten einer Hierarchie durchsuchen. Sie können auch die Zahl der Buckets festlegen, in denen die Elemente Gruppen bilden und ein Benennungsschema für die Buckets vorgeben. Weitere Informationen finden Sie unter [Gruppieren von Attributelementen &#40;Diskretisierung&#41;](attribute-properties-group-attribute-members.md).  
  
 Sie gruppieren Elemente, indem Sie die **DiscretizationMethod** -Eigenschaft festlegen, auf die Sie im Fenster **Eigenschaften** in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]zugreifen können.  
  
 Wenn Sie Elementgruppen erstellen, sind Ihre Änderungen erst dann für Benutzer verfügbar, wenn Sie die Dimension verarbeitet haben. Weitere Informationen finden Sie unter mehr [dimensionale Modell Objekt Verarbeitung](processing-a-multidimensional-model-analysis-services.md).  
  
### <a name="to-create-member-groups"></a>So erstellen Sie eine Elementgruppe  
  
1.  Öffnen Sie die Dimension, mit der Sie arbeiten möchten. Standardmäßig wird die Registerkarte **Dimensionsstruktur** geöffnet.  
  
2.  Klicken Sie in **Attribute**mit der rechten Maustaste auf die Attribute, deren Elemente Sie gruppieren möchten, und klicken Sie anschließend auf **Eigenschaften**.  
  
3.  Wählen Sie in der Dropdownliste neben **DiscretizationMethod**eine Methode aus, nach der Sie die Elemente gruppieren. Weitere Informationen zu **DiscretizationMethod**-Einstellungen finden Sie unter [Gruppieren von Attributelementen &#40;Diskretisierung&#41;](attribute-properties-group-attribute-members.md).  
  
  
