---
title: Configuration-Element (DTA)
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Configuration element
ms.assetid: 1478e56f-57c4-4441-bac9-1ac91453839b
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.openlocfilehash: 79073bca20afa853c1b6fbf548ed804f71f074fe
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "75307987"
---
# <a name="configuration-element-dta"></a>Configuration-Element (DTA)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Gibt eine benutzerdefinierte Konfiguration an, die aus vorhandenen und hypothetischen physischen Entwurfsstrukturen besteht, die der Datenbankoptimierungsratgeber beim Optimieren einer Arbeitsauslastung analysiert.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
<DTAInput>  
    <Server>...</Server>  
    <Workload>...</Workload>  
    <TuningOptions>...</TuningOptions  
    <Configuration [SpecificationMode="Relative" | "Absolute"]>  
    ...code removed here...  
    </Configuration>  
</DTAInput>  
```  
  
## <a name="element-attributes"></a>Elementattribute  
  
|Konfigurationsattribut|BESCHREIBUNG|  
|-----------------------------|-----------------|  
|**SpecificationMode**|Optional. Gibt an, ob der Datenbankoptimierungsratgeber die angegebene Konfiguration im Vergleich zur aktuellen vorhandenen Konfiguration oder als vollständig neue eigenständige Konfiguration analysieren soll. Mit einem **string** -Datentyp können Sie dieses Attribut mit einem der folgenden zulässigen Werte angeben:<br /><br /> **Relative**:<br />                  Wertet die angegebene Konfiguration im Vergleich zur aktuellen vorhandenen Konfiguration physischer Entwurfsstrukturen (Indizes, indizierte Sichten, Partitionierung) in der Datenbank aus, die optimiert wird. Beispiel:<br /><br /> `<Configuration SpecificationMode="Relative">`<br /><br /> **Absolute**:<br />                  Wertet die angegebene Konfiguration als eigenständige Konfiguration aus. Wenn der Absolute-Wert angegeben ist, wird die vorhandene Konfiguration nicht vom Datenbankoptimierungsratgeber berücksichtigt. Beispiel:<br /><br /> `<Configuration SpecificationMode="Absolute">`|  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|BESCHREIBUNG|  
|--------------------|-----------------|  
|**Datentyp und -länge**|Keine.|  
|**Standardwert**|Keine.|  
|**Vorkommen**|Optional. Einmalige Verwendung pro **DTAInput** -Element möglich.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Elemente|  
|------------------|--------------|  
|**Übergeordnetes Element**|[DTAInput-Element &#40;DTA&#41;](../../tools/dta/dtainput-element-dta.md)|  
|**Untergeordnete Elemente**|[Server-Element für Konfiguration &#40;DTA&#41;](../../tools/dta/server-element-for-configuration-dta.md)|  
  
## <a name="example"></a>Beispiel  
 Ein Beispiel für die Verwendung dieses Elements finden Sie unter [Beispiel für eine XML-Eingabedatei mit benutzerdefinierter Konfiguration &#40;DTA&#41;](../../tools/dta/xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [XML-Eingabedateireferenz &#40;Datenbankoptimierungsratgeber&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
