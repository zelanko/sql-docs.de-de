---
title: Metadaten (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
helpviewer_keywords:
- user-defined metadata [Master Data Services], about user-defined metadata
- metadata [Master Data Services], about metadata
- metadata [Master Data Services]
- user-defined metadata [Master Data Services]
ms.assetid: ac1aabe3-d8d4-4d7a-8954-50ee3c185d81
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 2050e1fe428108713d4cfed8473feec592bc1daa
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48185010"
---
# <a name="metadata-master-data-services"></a>Metadaten (Master Data Services)
  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] handelt es sich bei benutzerdefinierten Metadaten um Informationen, mit denen Sie die Modellobjekte beschreiben. Sie möchten z. B. die Besitzer eines bestimmten Modells oder einer Entität oder die Quellsysteme verfolgen, die Daten für eine Entität bereitstellen.  
  
 Benutzerdefinierte Metadaten wird von einem Modell mit dem Namen verwaltet **Metadaten**. Dieses Modell ist automatisch enthalten, wenn [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] installiert ist, und es ist allen anderen MDS-Modellen ähnlich, mit dem Unterschied, dass Sie keine Versionen erstellen können.  
  
 Nach dem Ausfüllen des Metadatenmodells mit benutzerdefinierten Metadaten können Sie sie in Abonnementsichten einfügen, damit sie von abonnierenden Systemen verwendet werden können.  
  
## <a name="metadata-entities"></a>Metadatenentitäten  
 Das Modell Metadaten umfasst fünf Entitäten, von denen jede einen Typ eines Masterdaten-Modellobjekts darstellt, das benutzerdefinierte Metadaten unterstützt. Z. B. die **Modell-Metadatendefinition** Entität enthält Elemente, die Modelle, darstellen und die **Attribut-Metadatendefinition** -Entität verfügt über Elemente, die alle Attribute in allen Modellen stehen.  
  
 Um Metadaten für ein Modellobjekt zu definieren, füllen Sie die Attribute eines dieser Elemente auf. Z. B. in der **Entitäts-Metadatendefinition** Entität können Sie die Description-Attribut des Price-Elements mit dem Text auffüllen: **der Produktpreis beim Verkauf an einen Kunden**.  
  
 Die Elemente im Metadatenmodell werden automatisch immer dann aktualisiert, wenn Modellobjekte, die benutzerdefinierte Metadaten unterstützen, hinzugefügt oder gelöscht werden.  
  
 Das Metadatenmodell darf nicht versionsspezifisch sein, über hinzugefügte oder geänderte Versionsflags verfügen oder als Modellbereitstellungspaket gespeichert werden. Es hat ansonsten jedoch die gleiche vollständige Funktionalität anderer Masterdatenmodelle. Sie könnten z. B. auf dem Metadatenmodell einen Satz von Geschäftsregeln implementieren, um Datenrichtlinien zu erzwingen.  
  
## <a name="customizing-your-metadata-model"></a>Anpassen des Metadatenmodells  
 Jede Metadaten-Definitionsentität schließt die Attribute Name, Code und Description ein. Sie möchten möglicherweise zusätzliche Attribute erstellen, um die Modellobjekte weiter zu beschreiben.  
  
 Sie könnten z. B. erstellen:  
  
-   Ein domänenbasiertes Attribut mit dem Namen "Besitzer", mit dem Sie den Besitzer jedes Modellobjekts verfolgen.  
  
-   Ein Freiformattribut mit dem Namen "Datum der letzten Überprüfung", mit dem Sie das Datum verfolgen, an dem ein Objekt zuletzt vom Besitzer überprüft wurde.  
  
-   Ein domänenbasiertes Attribut mit dem Namen Quellen, die Sie zum Nachverfolgen und verwalten die Quellsysteme, die Interaktion verwenden mit der [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] Instanz.  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Taskbeschreibung|Thema|  
|----------------------|-----------|  
|Fügen Sie einem Modellobjekt Metadaten hinzu.|[Hinzufügen von Metadaten &#40;Master Data Services&#41;](add-metadata-master-data-services.md)
)|  
  
## <a name="related-content"></a>Verwandte Inhalte  
  
-   [Exportieren von Daten &#40;Master Data Services&#41;](overview-exporting-data-master-data-services.md)  
  
  
