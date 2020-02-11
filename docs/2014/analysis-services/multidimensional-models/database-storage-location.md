---
title: Speicherort der Datenbank | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- databases [Analysis Services], storage location
ms.assetid: cf88c62e-581e-42f2-846f-a9bf1d7c3292
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2dd3659aed11e4e1cee791fcb5e541471320c82a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66075900"
---
# <a name="database-storage-location"></a>Datenbankspeicherort
  Es gibt oftmals Situationen, in denen ein [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbankadministrator (DBA) eine bestimmte Datenbank außerhalb des Datenordners des Servers speichern möchte. Diese Situationen werden oft von Unternehmensanforderungen bestimmt, wie Verbesserung der Leistung oder Erweiterung des Speichers. In diesen Situationen ermöglicht die `DbStorageLocation`-Datenbankeigenschaft dem [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Datenbankadministrator, für den Datenbankspeicherort einen lokalen Datenträger oder ein Netzwerkgerät anzugeben.  
  
## <a name="dbstoragelocation-database-property"></a>DbStorageLocation-Datenbankeigenschaft  
 Die `DbStorageLocation`-Datenbankeigenschaft gibt den Ordner an, in dem [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] alle Datenbankdaten und Metadatendateien erstellt und verwaltet. Alle Metadatendateien werden im `DbStorageLocation`-Ordner gespeichert, mit Ausnahme der Datenbank-Metadatendatei. Diese wird im Datenordner des Servers abgelegt. Es gibt zwei wichtige Überlegungen beim Festlegen des Werts der `DbStorageLocation`-Datenbankeigenschaft:  
  
-   Die `DbStorageLocation`-Datenbankeigenschaft muss auf einen vorhandenen UNC-Ordnerpfad oder eine leere Zeichenfolge festgelegt werden. Bei dem vorgegebenen Datenordner des Servers handelt es sich um eine leere Zeichenfolge. Wenn der Ordner nicht vorhanden ist, wird beim Ausführen eines `Create`-, `Attach`-oder `Alter` -Befehls ein Fehler ausgelöst.  
  
-   Darüber hinaus kann die `DbStorageLocation`-Datenbankeigenschaft nicht so festgelegt werden, dass sie auf den Datenordner des Servers oder einen zugehörigen Unterordner verweist. Wenn der Speicherort auf den Datenordner des Servers oder einen zugehörigen Unterordner verweist, wird beim Ausführen des Befehls `Create`, `Attach` oder `Alter` ein Fehler ausgelöst.  
  
> [!IMPORTANT]  
>  Es wird empfohlen, den UNC-Pfad auf die Verwendung eines Storage Area Networks (SAN), iSCSI-basierten Netzwerks oder eines lokalen Datenträgers festzulegen. Jeder UNC-Pfad zu einer Netzwerkfreigabe bzw. jede Remotespeicherlösung mit hoher Latenzzeit führt zu einer Installation, die nicht unterstützt wird.  
  
### <a name="dbstoragelocation-compared-to-storagelocation"></a>DbStorageLocation im Vergleich zu StorageLocation  
 
  `DbStorageLocation` gibt den Ordner an, in dem alle Datenbankdaten- und Metadatendateien gespeichert sind. `StorageLocation` gibt den Ordner an, in dem eine oder mehrere Partitionen eines Cubes gespeichert sind. 
  `StorageLocation` kann unabhängig von `DbStorageLocation` festgelegt werden. Diese Entscheidung wird vom [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbankadministrator auf Grundlage der erwarteten Ergebnisse getroffen. Häufig kommt es bei der Verwendung der einen oder der anderen Eigenschaft zu Überlappungen.  
  
## <a name="dbstoragelocation-usage"></a>Verwendung von DbStorageLocation  
 Die `DbStorageLocation` Database-Eigenschaft wird als Teil eines `Create` Daten Bank Befehls in einer `Detach` / `Attach` Sequenz von Daten Bank Befehlen, `Backup` / `Restore` in einer Sequenz von Daten Bank Befehlen `Synchronize` oder in einem Datenbankbefehl verwendet. Eine Änderung der `DbStorageLocation`-Datenbankeigenschaft wird als strukturelle Änderung des Datenbankobjekts betrachtet. Dies bedeutet, dass alle Metadaten neu erstellt und die Daten erneut verarbeitet werden müssen.  
  
> [!IMPORTANT]  
>  Der Datenbankspeicherort sollte nicht mit einem `Alter`-Befehl geändert werden. Stattdessen wird die Verwendung einer Sequenz von Daten Bank Befehlen `Detach` / `Attach` empfohlen (Weitere Informationen finden Sie unter [Verschieben einer Analysis Services-Datenbank](move-an-analysis-services-database.md), [Anfügen und trennen von Analysis Services Datenbanken](attach-and-detach-analysis-services-databases.md)).  
  
## <a name="see-also"></a>Weitere Informationen  
 <xref:Microsoft.AnalysisServices.Database.DbStorageLocation%2A>   
 [Anfügen und trennen von Analysis Services Datenbanken](attach-and-detach-analysis-services-databases.md)   
 [Verschieben einer Analysis Services Datenbank](move-an-analysis-services-database.md)   
 [Dbstorageloation-Element](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/dbstoragelocation-element)   
 [Create Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla)   
 [Attach-Element](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/attach-element)   
 [Element &#40;XMLA synchronisieren&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/synchronize-element-xmla)  
  
  
