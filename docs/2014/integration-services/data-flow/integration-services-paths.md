---
title: SQL Server Integration Services-Pfade | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- paths [Integration Services], about paths
- data flow [Integration Services], paths
- paths [Integration Services]
- destinations [Integration Services], paths
- sources [Integration Services], paths
ms.assetid: 6c4629a9-2ede-4011-9101-3b342249640e
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 832ea48478eb28b94caf292067344a3754040b2b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62901794"
---
# <a name="integration-services-paths"></a>SQL Server Integration Services-Pfade
  Ein Pfad verbindet zwei Komponenten in einem Datenfluss, indem die Ausgabe einer Datenflusskomponente mit der Eingabe einer anderen Komponente verbunden wird. Ein Pfad weist eine Quelle und ein Ziel auf. Wenn z. B. ein Pfad eine Verbindung mit einer OLE DB-Quelle und einer Transformation zum Sortieren herstellt, ist die OLE DB-Quelle die Quelle des Pfads, und die Transformation zum Sortieren ist das Ziel des Pfads. Die Quelle ist die Komponente, wo der Pfad beginnt, und das Ziel ist die Komponente, wo der Pfad endet.  
  
 Wenn Sie ein Paket im [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer ausführen, können Sie die Daten in einem Datenfluss anzeigen, indem Sie Daten-Viewer an einen Pfad anfügen. Ein Daten-Viewer kann zur Anzeige von Daten in einem Raster konfiguriert werden. Ein Daten-Viewer ist ein hilfreiches Tool zum Debuggen. Weitere Informationen finden Sie unter [Debugging Data Flow](../troubleshooting/debugging-data-flow.md).  
  
## <a name="configuration-of-the-path"></a>Konfiguration des Pfads  
 Der [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer stellt das Dialogfeld **Datenflusspfad-Editor** bereit, in dem Sie Pfadeigenschaften festlegen, die Metadaten der Datenspalten, die über den Pfad übergeben werden, anzeigen sowie Daten-Viewer konfigurieren können.  
  
 Zu den konfigurierbaren Pfadeigenschaften gehört der Name, die Beschreibung und die Anmerkung des Pfads. Pfade können auch programmgesteuert konfiguriert werden. Weitere Informationen finden Sie unter [Programmgesteuertes Verbinden von Datenflusskomponenten](../building-packages-programmatically/connecting-data-flow-components-programmatically.md).  
  
 Eine Pfadanmerkung zeigt den Namen der Pfadquelle oder den Pfadnamen in der Entwurfsoberfläche der Registerkarte **Datenfluss** im [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer an. Pfadanmerkungen sind mit den Anmerkungen vergleichbar, die Sie Datenflüssen, Ablaufsteuerungen und Ereignishandlern hinzufügen können. Der einzige Unterschied besteht darin, dass eine Pfadanmerkung einem Pfad hinzugefügt wird, während andere Anmerkungen auf den Registerkarten **Datenfluss**, **Ablaufsteuerung**und **Ereignishandler**des [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designers angezeigt werden.  
  
 Die Metadaten zeigen den Namen, den Datentyp, die Genauigkeit, die Dezimalstellen, die Länge, die Codepage und die Quellkomponente jeder Spalte in der Ausgabe der vorherigen Komponente an. Die Quellkomponente ist jene Datenflusskomponente, die die Spalte erstellt hat. Dies kann, muss aber nicht die erste Komponente im Datenfluss sein. Beispielsweise werden mit einer Transformation für UNION ALL und einer Transformation zum Sortieren eigene Spalten erstellt, die die Quelle der Ausgabespalten sind. Dagegen können Spalten mit einer Transformation für das Kopieren von Spalten durchlaufen werden, ohne sie zu ändern. Es können auch neue Spalten erstellt werden, indem Eingabespalten kopiert werden. Die Transformation für das Kopieren von Spalten ist nur für neue Spalten die Quellkomponente.  
  
 Sie können Eigenschaften mit dem [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer oder programmgesteuert festlegen.  
  
 Klicken Sie auf eines der folgenden Themen, um weitere Informationen zu den Eigenschaften zu erhalten, die Sie im Dialogfeld **Datenflusspfad-Editor** festlegen können:  
  
-   [Datenfluss Pfad-Editor &#40;Seite "Allgemein"&#41;](../general-page-of-integration-services-designers-options.md)  
  
-   [Datenfluss Pfad-Editor &#40;Seite "Metadaten"&#41;](../data-flow-path-editor-metadata-page.md)  
  
-   [Datenfluss Pfad-Editor &#40;Seite "Daten-Viewer"&#41;](../data-flow-path-editor-data-viewers-page.md)  
  
 Weitere Informationen zu den Eigenschaften, die Sie programmgesteuert festlegen können, finden Sie unter [Path Properties](../path-properties.md).  
  
## <a name="related-tasks"></a>Related Tasks  
  
-   [Anzeigen von Pfadmetadaten im Datenflusspfad-Editor](../view-path-metadata-in-the-data-flow-path-editor.md)  
  
-   [Verbinden von Komponenten in einem Datenfluss](connect-components-in-a-data-flow.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenfluss](data-flow.md)  
  
  
