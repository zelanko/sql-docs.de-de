---
title: FORE_COLOR und BACK_COLOR-Inhalte (MDX) | Microsoft-Dokumentation
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: bb721d04e32e584a312c779db3aadab2ab83ba19
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62806130"
---
# <a name="mdx-cell-properties---forecolor-and-backcolor-contents"></a>MDX – Zelleigenschaften: FORE_COLOR- und BACK_COLOR-Inhalte
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Die Zelleigenschaften **FORE_COLOR** und **BACK_COLOR** werden dazu verwendet, Farbinformationen für den Text bzw. den Hintergrund einer Zelle im RGB-Format (Rot-Grün-Blau) von Microsoft Windows zu speichern.  
  
 Der gültige Bereich für eine gewöhnliche RGB-Farbe ist 0 (null) bis 16.777.215 (&H00FFFFFF). Das höherwertige Byte einer Zahl in diesem Bereich entspricht immer 0. Die niederwertigen 3 Bytes bestimmen, vom niedrigsten zum höchsten Byte, den Anteil von Rot, Grün und Blau. Der rote, grüne und blaue Farbanteil werden jeweils durch eine Zahl zwischen 0 und 255 (&HFF) dargestellt.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden von Zelleneigenschaften &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-cell-properties-using-cell-properties.md)  
  
  
