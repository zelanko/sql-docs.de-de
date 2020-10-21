---
description: Benutzerdefinierte Eigenschaften des Ziels des Data Mining-Modelltrainings
title: Benutzerdefinierte Eigenschaften des Ziels des Data Mining-Modelltrainings | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: f0a70216-fdac-44ae-af29-35f65626217c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8ed5f1b09cbbaa4d20c891a03d9846949eedc8bc
ms.sourcegitcommit: cfa04a73b26312bf18d8f6296891679166e2754d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2020
ms.locfileid: "92196441"
---
# <a name="data-mining-model-training-destination-custom-properties"></a>Benutzerdefinierte Eigenschaften des Ziels des Data Mining-Modelltrainings

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  Das Ziel des Data Mining-Modelltrainings verfügt sowohl über benutzerdefinierte Eigenschaften als auch über die Eigenschaften, die allen Datenflusskomponenten gemeinsam sind.  
  
 Die folgende Tabelle beschreibt die benutzerdefinierten Eigenschaften des Ziels des Data Mining-Modelltrainings. Alle Eigenschaften weisen Lese-/Schreibzugriff auf.  
  
|Eigenschaft|Datentyp|BESCHREIBUNG|  
|--------------|---------------|-----------------|  
|ASConnectionId|String|Der eindeutige Bezeichner des Verbindungs-Managers.|  
|ASConnectionString|String|Die Verbindungszeichenfolge zu einer Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] oder einem [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekt.|  
|ObjectRef|String|Ein XML-Tag, das die Data Mining-Struktur identifiziert, die von der Transformation verwendet wird.|  
  
 Die Eingabe und die Eingabespalten des Ziels des Data Mining-Modelltrainings verfügen nicht über benutzerdefinierte Eigenschaften.  
  
 Weitere Informationen finden Sie unter [Data Mining Model Training Destination](../../integration-services/data-flow/data-mining-model-training-destination.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Common Properties](./set-the-properties-of-a-data-flow-component.md)  
  
