---
title: FORE_COLOR und BACK_COLOR Inhalt (MDX) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- FORE_COLOR contents
- backgrounds [MDX]
- cells [MDX]
- colors [MDX]
- storing cell color information
- cell backgrounds
- BACK_COLOR contents
ms.assetid: ff8f40cb-2ac4-4fc2-9761-7f1b14c17c8c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ecd8bb157d7b501d29230c91d87f148ae738ff45
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66074411"
---
# <a name="fore_color-and-back_color-contents-mdx"></a>FORE_COLOR- und BACK_COLOR-Inhalte (MDX)
  Die Zelleigenschaften `FORE_COLOR` und `BACK_COLOR` werden dazu verwendet, Farbinformationen für den Text bzw. den Hintergrund einer Zelle im RGB-Format (Rot-Grün-Blau) von Microsoft Windows zu speichern.  
  
 Der gültige Bereich für eine gewöhnliche RGB-Farbe ist 0 (null) bis 16.777.215 (&H00FFFFFF). Das höherwertige Byte einer Zahl in diesem Bereich entspricht immer 0. Die niederwertigen 3 Bytes bestimmen, vom niedrigsten zum höchsten Byte, den Anteil von Rot, Grün und Blau. Der rote, grüne und blaue Farbanteil werden jeweils durch eine Zahl zwischen 0 und 255 (&HFF) dargestellt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwenden von Zelleneigenschaften &#40;MDX&#41;](mdx-cell-properties-using-cell-properties.md)  
  
  
