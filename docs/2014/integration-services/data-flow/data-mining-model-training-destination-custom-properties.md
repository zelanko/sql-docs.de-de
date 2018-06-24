---
title: Benutzerdefinierte Eigenschaften des Ziels des Data Mining-Modelltrainings | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f0a70216-fdac-44ae-af29-35f65626217c
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 17b2b721a5c90009fabca15864b62e71e0677251
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36056516"
---
# <a name="data-mining-model-training-destination-custom-properties"></a>Benutzerdefinierte Eigenschaften des Ziels des Data Mining-Modelltrainings
  Das Ziel des Data Mining-Modelltrainings verfügt sowohl über benutzerdefinierte Eigenschaften als auch über die Eigenschaften, die allen Datenflusskomponenten gemeinsam sind.  
  
 Die folgende Tabelle beschreibt die benutzerdefinierten Eigenschaften des Ziels des Data Mining-Modelltrainings. Alle Eigenschaften weisen Lese-/Schreibzugriff auf.  
  
|Eigenschaft|Datentyp|Description|  
|--------------|---------------|-----------------|  
|ASConnectionId|Zeichenfolge|Der eindeutige Bezeichner des Verbindungs-Managers.|  
|ASConnectionString|Zeichenfolge|Die Verbindungszeichenfolge zu einer Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] oder einem [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekt.|  
|ObjectRef|Zeichenfolge|Ein XML-Tag, das die Data Mining-Struktur identifiziert, die von der Transformation verwendet wird.|  
  
 Die Eingabe und die Eingabespalten des Ziels des Data Mining-Modelltrainings verfügen nicht über benutzerdefinierte Eigenschaften.  
  
 Weitere Informationen finden Sie unter [Data Mining Model Training Destination](data-mining-model-training-destination.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Common Properties](../common-properties.md)  
  
  