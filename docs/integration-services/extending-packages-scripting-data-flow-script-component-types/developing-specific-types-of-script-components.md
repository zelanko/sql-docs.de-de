---
title: Entwickeln bestimmter Typen von Skriptkomponenten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Script component [Integration Services], examples
ms.assetid: dfbbe959-6b4e-4b47-b9dd-bcc31929482d
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 87763f56dee2c8878ab0149d673d55be3e641ed8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65724322"
---
# <a name="developing-specific-types-of-script-components"></a>Entwickeln bestimmter Arten von Skriptkomponenten

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Bei der Skriptkomponente handelt es sich um ein konfigurierbares Tool, das Sie im Datenfluss eines Pakets verwenden können, um nahezu allen Anforderungen gerecht zu werden, die von den Quellen, Transformationen und Zielen nicht erfüllt werden, die in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] enthalten sind. Dieser Abschnitt enthält Codebeispiele für Skriptkomponenten, in denen die vier Optionen zum Konfigurieren der Skriptkomponente veranschaulicht werden:  
  
-   Als Quelle.  
  
-   Als Transformation mit synchronen Ausgaben.  
  
-   Als Transformation mit asynchronen Ausgaben.  
  
-   Als Ziel.  
  
 Weitere Beispiele von Skriptkomponenten finden Sie unter [Zusätzliche Skriptkomponentenbeispiele](../../integration-services/extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Erstellen einer Quelle mit der Skriptkomponente](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-source-with-the-script-component.md)  
 Erläutert und veranschaulicht, wie eine Datenflussquelle mithilfe der Skriptkomponente erstellt wird.  
  
 [Erstellen einer synchronen Transformation mit der Skriptkomponente](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)  
 Erläutert und veranschaulicht, wie eine Datenflusstransformation mit synchronen Ausgaben mithilfe der Skriptkomponente erstellt wird. Durch diese Art von Transformation werden Datenzeilen an Ort und Stelle beim Durchlaufen der Komponente geändert.  
  
 [Erstellen einer asynchronen Transformation mit der Skriptkomponente](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md)  
 Erläutert und veranschaulicht, wie eine Datenflusstransformation mit asynchronen Ausgaben mithilfe der Skriptkomponente erstellt wird. Bei dieser Art von Transformation müssen alle Datenzeilen gelesen werden, bevor den Daten, die die Komponente durchlaufen, weitere Informationen, z. B. berechnete Aggregate, hinzugefügt werden können.  
  
 [Erstellen eines Ziels mit der Skriptkomponente](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)  
 Erläutert und veranschaulicht, wie ein Datenflussziel mithilfe der Skriptkomponente erstellt wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Vergleichen von Skriptlösungen und benutzerdefinierten Objekten](../../integration-services/extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md)   
 [Entwickeln bestimmter Arten von Datenflusskomponenten](../../integration-services/extending-packages-custom-objects-data-flow-types/developing-specific-types-of-data-flow-components.md)  
  
  
