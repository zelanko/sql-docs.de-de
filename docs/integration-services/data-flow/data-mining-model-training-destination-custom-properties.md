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
ms.openlocfilehash: 6427b808d31c9b1938b093da2bdf14d59bec90cc
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88457362"
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Common Properties](https://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
  
