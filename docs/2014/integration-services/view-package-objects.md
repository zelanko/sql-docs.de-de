---
title: Anzeigen von Paketobjekten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Integration Services packages, properties
- properties [Integration Services]
- Package Explorer window [Integration Services]
- packages [Integration Services], properties
- explorer view [Integration Services]
- SSIS packages, properties
- viewing package objects
- SQL Server Integration Services packages, properties
ms.assetid: a85c0245-0a68-4eb0-83b1-9b11df80bd10
caps.latest.revision: 34
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 0128e5236f517ba9d466f8517145fa44170d0657
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36162738"
---
# <a name="view-package-objects"></a>Anzeigen von Paketobjekten
  Im [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer stellt die Registerkarte **Paket-Explorer** eine Explorer-Sicht des Pakets bereit. Diese Sicht gibt die Containerhierarchie der [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Architektur wieder. Der Paketcontainer befindet sich ganz oben in der Hierarchie, und Sie erweitern das Paket, um die Verbindungen, ausführbaren Dateien, Ereignishandler, Protokollanbieter, Rangfolgeneinschränkungen und Variablen im Paket anzuzeigen.  
  
 Die ausführbaren Dateien, also die Container und Tasks im Paket, können Ereignishandler, Rangfolgeneinschränkungen und Variablen einschließen. [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] unterstützt eine geschachtelte Hierarchie von Containern, und der For-Schleifencontainer, der Foreach-Schleifencontainer und der Sequenzcontainer können andere ausführbare Dateien einschließen.  
  
 Falls ein Paket einen Datenfluss enthält, wird im **Paket-Explorer** der Datenflusstask aufgelistet, und er enthält den Ordner **Komponenten** , in dem die Datenflusskomponenten aufgelistet werden.  
  
 Auf der Registerkarte **Paket-Explorer** können Sie Objekte in einem Paket löschen und auf das Fenster **Eigenschaften** zugreifen, um Objekteigenschaften anzuzeigen.  
  
 Das folgende Diagramm zeigt eine Strukturansicht eines einfachen Pakets.  
  
 ![Screenshot der Registerkarte „Package-Explorer“](media/packageexplorer.gif "Screenshot of the Package Explorer tab")  
  
### <a name="to-view-package-content"></a>So zeigen Sie den Paketinhalt an  
  
-   [Anzeigen von Paketobjekten im Paket-Explorer](../../2014/integration-services/view-package-objects-in-package-explorer.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Integration Services-Tasks](control-flow/integration-services-tasks.md)   
 [Integration Services-Container](control-flow/integration-services-containers.md)   
 [Rangfolgeneinschränkungen](control-flow/precedence-constraints.md)   
 [Integrationsservices &#40;SSIS&#41; Variablen](integration-services-ssis-variables.md)   
 [Integration Services-Ereignishandler &#40;SSIS&#41;](integration-services-ssis-event-handlers.md)   
 [Integration Services-Protokollierung &#40;SSIS&#41;](performance/integration-services-ssis-logging.md)  
  
  