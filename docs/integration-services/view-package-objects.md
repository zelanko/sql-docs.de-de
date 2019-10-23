---
title: Anzeigen von Paketobjekten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
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
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 28393d15ade12562dbcaa4af457bf0de0e51948b
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/26/2019
ms.locfileid: "71295024"
---
# <a name="view-package-objects"></a>Anzeigen von Paketobjekten

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Im [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer stellt die Registerkarte **Paket-Explorer** eine Explorer-Sicht des Pakets bereit. Diese Sicht gibt die Containerhierarchie der [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Architektur wieder. Der Paketcontainer befindet sich ganz oben in der Hierarchie, und Sie erweitern das Paket, um die Verbindungen, ausführbaren Dateien, Ereignishandler, Protokollanbieter, Rangfolgeneinschränkungen und Variablen im Paket anzuzeigen.  
  
 Die ausführbaren Dateien, also die Container und Tasks im Paket, können Ereignishandler, Rangfolgeneinschränkungen und Variablen einschließen. [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] unterstützt eine geschachtelte Hierarchie von Containern, und der For-Schleifencontainer, der Foreach-Schleifencontainer und der Sequenzcontainer können andere ausführbare Dateien einschließen.  
  
 Falls ein Paket einen Datenfluss enthält, wird im **Paket-Explorer** der Datenflusstask aufgelistet, und er enthält den Ordner **Komponenten** , in dem die Datenflusskomponenten aufgelistet werden.  
  
 Auf der Registerkarte **Paket-Explorer** können Sie Objekte in einem Paket löschen und auf das Fenster **Eigenschaften** zugreifen, um Objekteigenschaften anzuzeigen.  
  
 Das folgende Diagramm zeigt eine Strukturansicht eines einfachen Pakets.  
  
 ![Screenshot der Registerkarte „Package-Explorer“](../integration-services/media/packageexplorer.gif "Screenshot of the Package Explorer tab")  
  
## <a name="view-the-package-structure-and-content"></a>Anzeigen der Paketstruktur und des Paketinhalts  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]das [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt mit dem Paket, das Sie im Bereich **Paket-Explorer**anzeigen möchten.  
  
2.  Klicken Sie auf die Registerkarte **Paket-Explorer** .  
  
3.  Um den Inhalt der Ordner **Variablen**, **Rangfolgeneinschränkungen**, **Ereignishandler**, **Verbindungs-Manager**, **Protokollanbieter**oder **Ausführbare Dateien** anzuzeigen, erweitern Sie den entsprechenden Ordner.  
  
4.  Erweitern Sie in Abhängigkeit von der Paketstruktur Ordner der nächsten Ebene.  
  
## <a name="view-the-properties-of-a-package-object"></a>Anzeigen der Eigenschaften eines Paketobjekts
  
-   Klicken Sie mit der rechten Maustaste auf ein Objekt, und klicken Sie auf **Eigenschaften** , um das Fenster **Eigenschaften** zu öffnen.  
  
## <a name="delete-an-object-in-a-package"></a>Löschen eines Objekts in einem Paket  
  
-   Klicken Sie mit der rechten Maustaste auf ein Objekt, und klicken Sie anschließend auf **Löschen**. 
 
## <a name="see-also"></a>Weitere Informationen  
 [Integration Services-Tasks](../integration-services/control-flow/integration-services-tasks.md)   
 [SQL Server Integration Services-Container](../integration-services/control-flow/integration-services-containers.md)   
 [Rangfolgeneinschränkungen](../integration-services/control-flow/precedence-constraints.md)   
 [Integration Services-Variablen &#40;SSIS&#41;](../integration-services/integration-services-ssis-variables.md)   
 [Integration Services-Ereignishandler &#40;SSIS&#41;](../integration-services/integration-services-ssis-event-handlers.md)   
 [Integration Services-Protokollierung &#40;SSIS&#41;](../integration-services/performance/integration-services-ssis-logging.md)  
  
  
