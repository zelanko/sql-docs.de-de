---
title: Datenbank-Speicherort | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- databases [Analysis Services], storage location
ms.assetid: cf88c62e-581e-42f2-846f-a9bf1d7c3292
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 15b50e0cd8b030c6026dfa46c92a2d52dbcb2e5a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48216540"
---
# <a name="database-storage-location"></a>Datenbankspeicherort
  Es gibt oftmals Situationen, in denen ein [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbankadministrator (DBA) eine bestimmte Datenbank außerhalb des Datenordners des Servers speichern möchte. Diese Situationen werden oft von Unternehmensanforderungen bestimmt, wie Verbesserung der Leistung oder Erweiterung des Speichers. In diesen Situationen ermöglicht die `DbStorageLocation`-Datenbankeigenschaft dem [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Datenbankadministrator, für den Datenbankspeicherort einen lokalen Datenträger oder ein Netzwerkgerät anzugeben.  
  
## <a name="dbstoragelocation-database-property"></a>DbStorageLocation-Datenbankeigenschaft  
 Die `DbStorageLocation` -Datenbankeigenschaft gibt an, den Ordner, in denen [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] erstellt und verwaltet alle Daten und Metadaten-Datenbankdateien. Alle Metadatendateien werden gespeichert, auf die `DbStorageLocation` gespeichert, mit Ausnahme der datenbankmetadatendatei, die im Datenordner Servers gespeichert wird. Es gibt zwei wichtige Überlegungen beim Festlegen des Werts der `DbStorageLocation` Datenbankeigenschaft:  
  
-   Die `DbStorageLocation` -Datenbankeigenschaft muss auf einen vorhandenen UNC-Ordnerpfad oder eine leere Zeichenfolge festgelegt werden. Bei dem vorgegebenen Datenordner des Servers handelt es sich um eine leere Zeichenfolge. Wenn der Ordner nicht vorhanden ist, wird ein Fehler ausgelöst, beim Ausführen einer `Create`, `Attach`, oder `Alter` Befehl.  
  
-   Die `DbStorageLocation` Datenbankeigenschaft kann nicht festgelegt werden, um auf den Datenordner des Servers oder einen zugehörigen Unterordner verweist. Wenn der Speicherort auf den Datenordner des Servers oder einen zugehörigen Unterordner verweist, wird beim Ausführen des Befehls `Create`, `Attach` oder `Alter` ein Fehler ausgelöst.  
  
> [!IMPORTANT]  
>  Es wird empfohlen, den UNC-Pfad auf die Verwendung eines Storage Area Networks (SAN), iSCSI-basierten Netzwerks oder eines lokalen Datenträgers festzulegen. Jeder UNC-Pfad zu einer Netzwerkfreigabe bzw. jede Remotespeicherlösung mit hoher Latenzzeit führt zu einer Installation, die nicht unterstützt wird.  
  
### <a name="dbstoragelocation-compared-to-storagelocation"></a>DbStorageLocation im Vergleich zu StorageLocation  
 `DbStorageLocation` gibt den Ordner an, in dem alle Datenbankdaten- und Metadatendateien gespeichert sind. `StorageLocation` gibt den Ordner an, in dem eine oder mehrere Partitionen eines Cubes gespeichert sind. `StorageLocation` kann unabhängig von `DbStorageLocation` festgelegt werden. Diese Entscheidung wird vom [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbankadministrator auf Grundlage der erwarteten Ergebnisse getroffen. Häufig kommt es bei der Verwendung der einen oder der anderen Eigenschaft zu Überlappungen.  
  
## <a name="dbstoragelocation-usage"></a>Verwendung von DbStorageLocation  
 Die `DbStorageLocation` -Datenbankeigenschaft wird als Teil des verwendet eine `Create` -Datenbankbefehls in einer `Detach` / `Attach` Sequenz in ein `Backup` / `Restore` -Datenbankbefehlen , oder in einem `Synchronize` -Datenbankbefehls. Eine Änderung der `DbStorageLocation`-Datenbankeigenschaft wird als strukturelle Änderung des Datenbankobjekts betrachtet. Dies bedeutet, dass alle Metadaten neu erstellt und die Daten erneut verarbeitet werden müssen.  
  
> [!IMPORTANT]  
>  Der Datenbankspeicherort sollte nicht mit einem `Alter`-Befehl geändert werden. Stattdessen empfehlen wir die Verwendung einer Sequenz von `Detach` / `Attach` Datenbank-Befehlsfolge (finden Sie unter [Verschieben einer Analysis Services-Datenbank](move-an-analysis-services-database.md), [Anfügen und Trennen von Analysis Services-Datenbanken](attach-and-detach-analysis-services-databases.md)).  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.AnalysisServices.Database.DbStorageLocation%2A>   
 [Anfügen und Trennen von Analysis Services-Datenbanken](attach-and-detach-analysis-services-databases.md)   
 [Verschieben einer Analysis Services-Datenbank](move-an-analysis-services-database.md)   
 [DbStorageLocation-Element](../xmla/xml-elements-properties/dbstoragelocation-element.md)   
 [Create-Element &#40;XMLA&#41;](../xmla/xml-elements-commands/create-element-xmla.md)   
 [Attach-Element](../xmla/xml-elements-commands/attach-element.md)   
 [Synchronize-Element &#40;XMLA&#41;](../xmla/xml-elements-commands/synchronize-element-xmla.md)  
  
  
