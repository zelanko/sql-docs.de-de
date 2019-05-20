---
title: Entwickeln bestimmter Typen von Datenflusskomponenten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data flow task [Integration Services], components
- components [Integration Services], data flow
- data flow [Integration Services], components
ms.assetid: 348e219a-b8ff-425e-b9c6-811880101c54
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 4850e6ef36dfae483180c25b8e1f1ec68f8d2b39
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2019
ms.locfileid: "65724852"
---
# <a name="developing-specific-types-of-data-flow-components"></a>Entwickeln bestimmter Arten von Datenflusskomponenten

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Dieser Abschnitt befasst sich mit den Besonderheiten der Entwicklung von Quellkomponenten, Transformationskomponenten mit synchronen und asynchronen Ausgaben sowie Zielkomponenten.  
  
 Weitere Informationen zur Entwicklung von Komponenten im Allgemeinen finden Sie unter [Entwickeln einer benutzerdefinierten Datenflusskomponente](../../integration-services/extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Entwickeln einer benutzerdefinierten Quellkomponente](../../integration-services/extending-packages-custom-objects-data-flow-types/developing-a-custom-source-component.md)  
 Enthält Informationen zur Entwicklung einer Komponente, die auf Daten einer externen Datenquelle zugreift und diese Downstreamkomponenten im Datenfluss zur Verfügung stellt.  
  
 [Entwickeln einer benutzerdefinierten Transformationskomponente mit synchronen Ausgaben](../../integration-services/extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md)  
 Enthält Informationen zur Entwicklung einer Transformationskomponente, deren Ausgaben synchron zu den Eingaben sind. Diese Komponenten fügen dem Datenfluss keine Daten hinzu, sondern verarbeiten durchlaufende Daten.  
  
 [Entwickeln einer benutzerdefinierten Transformationskomponente mit asynchronen Ausgaben](../../integration-services/extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-asynchronous-outputs.md)  
 Enthält Informationen zur Entwicklung einer Transformationskomponente, deren Ausgaben nicht synchron zu den Eingaben sind. Diese Komponenten empfangen Daten von Upstreamkomponenten, fügen jedoch dem Datenfluss auch Daten hinzu.  
  
 [Entwickeln einer benutzerdefinierten Zielkomponente](../../integration-services/extending-packages-custom-objects-data-flow-types/developing-a-custom-destination-component.md)  
 Enthält Informationen zur Entwicklung einer Komponente, die Zeilen von Upstreamkomponenten im Datenfluss erhält und diese in eine externe Datenquelle schreibt.  
  
## <a name="reference"></a>Verweis  
 <xref:Microsoft.SqlServer.Dts.Pipeline>  
 Enthält die Klassen und Schnittstellen zur Erstellung benutzerdefinierter Datenflusskomponenten.  
  
 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper>  
 Enthält die nicht verwalteten Klassen und Schnittstellen des Datenflusstasks. Entwickler verwenden diese sowie den verwalteten <xref:Microsoft.SqlServer.Dts.Pipeline>-Namespace bei der programmgesteuerten Erstellung eines Datenflusses oder von benutzerdefinierten Datenflusskomponenten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Vergleichen von Skriptlösungen und benutzerdefinierten Objekten](../../integration-services/extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md)   
 [Entwickeln bestimmter Arten von Skriptkomponenten](../../integration-services/extending-packages-scripting-data-flow-script-component-types/developing-specific-types-of-script-components.md)  
  
  
