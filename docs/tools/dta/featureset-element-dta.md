---
title: FeatureSet-Element (DTA)
description: Im dta-Hilfsprogramm enthält das FeatureSet-Element die physischen Entwurfsstrukturen, die der Datenbankoptimierungsratgeber bei der Analyse verwendet.
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- FeatureSet element
ms.assetid: f2070c53-4a5c-4c11-ac38-96ee200c84f0
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.openlocfilehash: e7cf111f19344ae1364252d34801677c58326120
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85643870"
---
# <a name="featureset-element-dta"></a>FeatureSet-Element (DTA)

 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

Enthält die physischen Entwurfsstrukturen (Indizes oder indizierte Sichten), die der Datenbankoptimierungsratgeber bei der Analyse verwenden soll.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <FeatureSet>...</FeatureSet>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|BESCHREIBUNG|  
|--------------------|-----------------|  
|**Datentyp und -länge**|**string**, keine maximale Länge.|  
|**Zulässige Werte**|**IDX_IV**<br /> Indizes und indizierte Sichten.<br /><br /> **IDX**<br /> Nur Indizes.<br /><br /> **IV**<br /> Nur indizierte Sichten.<br /><br /> **NCL_IDX**<br /> Nur nicht gruppierte Indizes.<br /><br /> Verwenden Sie einen dieser Werte mit diesem Element.|  
|**Standardwert**|**IDX**|  
|**Vorkommen**|Einmalig erforderlich für jedes **TuningOptions** -Element, es sei denn, das **DropOnlyMode** -Element wird verwendet. Wird das **DropOnlyMode** -Element verwendet, kann das **FeatureSet**-Element nicht verwendet werden. Diese Elemente schließen sich gegenseitig aus.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Elemente|  
|------------------|--------------|  
|**Übergeordnetes Element**|[TuningOptions-Element &#40;DTA&#41;](../../tools/dta/tuningoptions-element-dta.md)|  
|**Untergeordnete Elemente**|Keine.|  
  
## <a name="example"></a>Beispiel  
 Ein Beispiel für die Verwendung dieses Elements finden Sie unter [Beispiel für eine einfache XML-Eingabedatei &#40;DTA&#41;](../../tools/dta/simple-xml-input-file-sample-dta.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [XML-Eingabedateireferenz &#40;Datenbankoptimierungsratgeber&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
