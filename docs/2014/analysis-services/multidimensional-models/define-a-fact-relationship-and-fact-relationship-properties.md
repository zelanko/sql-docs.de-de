---
title: Definieren von Fakten Beziehungen und Fakten Beziehungs Eigenschaften | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- fact dimensions [Analysis Services]
ms.assetid: d8e41724-da77-4ac1-bc42-956b5d91ea5d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 471a65cb8f7560b409e6ddf8f73969d83d42a346
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66075785"
---
# <a name="define-a-fact-relationship-and-fact-relationship-properties"></a>Definieren von Faktenbeziehungen und Faktenbeziehungseigenschaften
  Wenn Sie eine neue Cubedimension oder eine neue Measuregruppe definieren, versucht [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], zu erkennen, ob eine Faktendimensionsbeziehung vorhanden ist, und legt dann die Einstellung für die Dimensionsverwendung auf `Fact` fest. Sie können eine Faktendimensionsbeziehung im Cube-Designer auf der Registerkarte **Dimensionsverwendung** anzeigen oder bearbeiten. Die Faktenbeziehung zwischen einer Dimension und einer Measuregruppe besitzt die folgenden Einschränkungen:  
  
-   Eine Cubedimension kann nur über eine Faktenbeziehung zu einer bestimmten Measuregruppe verfügen.  
  
-   Eine Cubedimension kann über separate Faktenbeziehungen zu mehreren Measuregruppen verfügen.  
  
-   Beim Granularitätsattribut der Beziehung muss es sich um das Schlüsselattribut (z. B. Transaction Number) für die Dimension handeln. Hierdurch wird eine 1:1-Beziehung zwischen der Dimension und den Fakten in der Faktentabelle erstellt.  
  
  
