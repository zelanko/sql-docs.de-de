---
title: Anzeigen von Paketobjekten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
ms.openlocfilehash: ffe46be35db26186f715b18ba6114732d130e02e
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85439877"
---
# <a name="view-package-objects"></a>Anzeigen von Paketobjekten
  Im [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer stellt die Registerkarte **Paket-Explorer** eine Explorer-Sicht des Pakets bereit. Diese Sicht gibt die Containerhierarchie der [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Architektur wieder. Der Paketcontainer befindet sich ganz oben in der Hierarchie, und Sie erweitern das Paket, um die Verbindungen, ausführbaren Dateien, Ereignishandler, Protokollanbieter, Rangfolgeneinschränkungen und Variablen im Paket anzuzeigen.

 Die ausführbaren Dateien, also die Container und Tasks im Paket, können Ereignishandler, Rangfolgeneinschränkungen und Variablen einschließen. [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] unterstützt eine geschachtelte Hierarchie von Containern, und der For-Schleifencontainer, der Foreach-Schleifencontainer und der Sequenzcontainer können andere ausführbare Dateien einschließen.

 Falls ein Paket einen Datenfluss enthält, wird im **Paket-Explorer** der Datenflusstask aufgelistet, und er enthält den Ordner **Komponenten** , in dem die Datenflusskomponenten aufgelistet werden.

 Auf der Registerkarte **Paket-Explorer** können Sie Objekte in einem Paket löschen und auf das Fenster **Eigenschaften** zugreifen, um Objekteigenschaften anzuzeigen.

 Das folgende Diagramm zeigt eine Strukturansicht eines einfachen Pakets.

 ![Screenshot der Registerkarte „Paket-Explorer“](media/packageexplorer.gif "Screenshot der Registerkarte „Paket-Explorer“")

### <a name="to-view-package-content"></a>So zeigen Sie den Paketinhalt an

-   [Anzeigen von Paketobjekten im Paket-Explorer](../../2014/integration-services/view-package-objects-in-package-explorer.md)

## <a name="see-also"></a>Weitere Informationen
 [Integration Services Tasks](control-flow/integration-services-tasks.md) [Integration Services Container](control-flow/integration-services-containers.md) Rang folgen [Einschränkungen](control-flow/precedence-constraints.md) [Integration Services &#40;SSIS-&#41; Variablen](integration-services-ssis-variables.md) Integration Services &#40;von SSIS- [&#41; Ereignis Handlern](integration-services-ssis-event-handlers.md) Integration Services &#40;[Protokollierung von SSIS&#41;](performance/integration-services-ssis-logging.md)


