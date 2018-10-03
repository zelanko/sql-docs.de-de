---
title: Definieren von faktenbeziehungen und Faktenbeziehungseigenschaften | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- fact dimensions [Analysis Services]
ms.assetid: d8e41724-da77-4ac1-bc42-956b5d91ea5d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6663b3a488ff073c823ad8f67ef3a1d120c4a268
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48197421"
---
# <a name="define-a-fact-relationship-and-fact-relationship-properties"></a>Definieren von Faktenbeziehungen und Faktenbeziehungseigenschaften
  Wenn Sie eine neue Cubedimension oder eine neue Measuregruppe definieren, versucht [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], zu erkennen, ob eine Faktendimensionsbeziehung vorhanden ist, und legt dann die Einstellung für die Dimensionsverwendung auf `Fact` fest. Sie können eine Faktendimensionsbeziehung im Cube-Designer auf der Registerkarte **Dimensionsverwendung** anzeigen oder bearbeiten. Die Faktenbeziehung zwischen einer Dimension und einer Measuregruppe besitzt die folgenden Einschränkungen:  
  
-   Eine Cubedimension kann nur über eine Faktenbeziehung zu einer bestimmten Measuregruppe verfügen.  
  
-   Eine Cubedimension kann über separate Faktenbeziehungen zu mehreren Measuregruppen verfügen.  
  
-   Beim Granularitätsattribut der Beziehung muss es sich um das Schlüsselattribut (z. B. Transaction Number) für die Dimension handeln. Hierdurch wird eine 1:1-Beziehung zwischen der Dimension und den Fakten in der Faktentabelle erstellt.  
  
  
