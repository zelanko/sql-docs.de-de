---
title: Measuregruppen (Registerkarte ' Partitionen ', Cube-Designer) (Analysis Services – mehrdimensionale Daten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.partitions.partitionspane.measuregroupdetail.f1
ms.assetid: 58e44b24-cfcd-4908-b445-d4374b961b98
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7ffd5b3ff4eb98c96e1832e353e64f1953bd62e9
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62727986"
---
# <a name="measure-groups-partitions-tab-cube-designer-analysis-services---multidimensional-data"></a>Measuregruppen (Registerkarte 'Partitionen', Cube-Designer) (Analysis Services – Mehrdimensionale Daten)
  Im Bereich **Measuregruppen** der Registerkarte **Partitionen** des Cube-Designers können Sie die Partitionen verwalten, die mit den einzelnen Measuregruppen verknüpft sind.  
  
## <a name="options"></a>Optionen  
 **Partitionen**  
 Zeigt ein Raster mit einer Liste von Partitionen an, von denen die ausgewählte Measuregruppe unterstützt wird. Das Raster enthält die folgenden Spalten:  
  
 **(Ordinal)**  
 Zeigt die Ordnungsposition der Partition innerhalb der Measuregruppe an.  
  
 Wählen Sie durch Klicken die gesamte Zeile für die Partition aus.  
  
 **Partitionsname**  
 Geben Sie den Namen der ausgewählten Partition ein.  
  
 **Quelle**  
 Geben Sie den Namen der Tabelle (für Tabellenbindungen) bzw. Abfrage (für Abfragebindungen) ein, in der die Faktentabellendaten für die ausgewählte Partition bereitgestellt werden.  
  
 Klicken Sie auf die Schaltfläche mit den drei **Punkten** , um das Dialogfeld **Partitionsquelle** anzuzeigen und die Quelle für die ausgewählte Partition zu definieren.  
  
 **Aggregation**  
 Zeigt den Aggregationsmodus und den Speichermodus der Partition an. Der Speichermodus wird zuerst angezeigt: ROLAP (Relational Online Analytical Processing), MOLAP (Multidimensional Online Analytical Processing) oder HOLAP (Hybrid Online Analytical Processing). Der Aggregationsmodus wird als Prozentwert der angeforderten Optimierung, als Measure des angeforderten bzw. verwendeten Leerzeichens oder als Anzahl der erstellten Aggregationen angezeigt. Klicken Sie auf die Schaltfläche mit den drei **Punkten** , um das Dialogfeld **Aggregationsentwurfs-Assistent** anzuzeigen und den Aggregationsentwurf für die angegebene Partition zu definieren.  
  
 **Beschreibung**  
 Geben Sie die optionale Beschreibung der Partition ein.  
  
 **Neue Partition...**  
 Klicken Sie auf diese Option, um den **Partitions-Assistent** anzuzeigen und in der ausgewählten Measuregruppe eine neue Partition zu erstellen.  
  
 **Speichereinstellungen...**  
 Klicken Sie auf diese Option, um das Dialogfeld **Speichereinstellungen** anzuzeigen, in dem Sie einen Speichermodus, das proaktive Zwischenspeichern und Benachrichtigungseigenschaften für die ausgewählte Partition angeben können.  
  
> [!NOTE]  
>  Diese Option ist nur aktiviert, wenn im Raster **Partitionen** der ausgewählten Measuregruppe alle Zellen einer Partition ausgewählt sind.  
  
 **Rückschreibeeinstellungen...**  
 Klicken Sie auf diese Option, um das Dialogfeld **Rückschreiben aktivieren/deaktivieren** anzuzeigen und Rückschreibeeinstellungen für die ausgewählte Measuregruppe anzugeben.  
  
## <a name="context-menu"></a>Kontextmenü  
 Das Kontextmenü können Sie anzeigen, indem Sie im Raster **Partitionen** einer ausgewählten Measuregruppe mit der rechten Maustaste auf eine Zeile klicken. Die folgenden Optionen sind im Kontextmenü verfügbar:  
  
|Option|Definition|  
|------------|----------------|  
|**Business Intelligence hinzufügen**|Klicken Sie auf diese Option, um **Businesss Intelligence-Assistent** anzuzeigen und dem Cube Business Intelligence-Funktionen hinzuzufügen. Weitere Informationen zum **Business Intelligence-Assistenten**finden Sie unter [Business Intelligence-Assistent (F1-Hilfe)](business-intelligence-wizard-f1-help.md).|  
|**Neue Partition**|Klicken Sie auf diese Option, um den **Partitions-Assistent** anzuzeigen und in der ausgewählten Measuregruppe eine neue Partition zu erstellen.|  
|**Partition umbenennen**|Wählen Sie diese Option aus, um die ausgewählte Partition umzubenennen.|  
|**Löschen**|Klicken Sie auf diese Option, um das Dialogfeld **Objekte löschen** anzuzeigen und die ausgewählte Aktion zu löschen.<br /><br /> Hinweis: Diese Option ist deaktiviert, wenn eine Rückschreibepartition ausgewählt wurde.|  
|**Entwerfen von Aggregationen**|Klicken Sie auf diese Option, um das Dialogfeld **Aggregationsentwurfs-Assistent** anzuzeigen und einen Aggregationsentwurf für die ausgewählte Partition zu erstellen.<br /><br /> Hinweis: Diese Option ist deaktiviert, wenn eine Rückschreibepartition ausgewählt wurde.|  
|**Speichereinstellungen**|Klicken Sie auf diese Option, um das Dialogfeld **Speichereinstellungen** anzuzeigen, in dem Sie einen Speichermodus, das proaktive Zwischenspeichern und Benachrichtigungseigenschaften für die ausgewählte Partition angeben können.|  
|**Rückschreibeeinstellungen**|Klicken Sie auf diese Option, um das Dialogfeld **Rückschreiben aktivieren/deaktivieren** anzuzeigen und Rückschreibeeinstellungen für die Measuregruppe anzugeben, in der die ausgewählte Partition enthalten ist.|  
|**Verwendungsbasierte Optimierung**|Klicken Sie auf diese Option, um das Dialogfeld **Assistent für verwendungsbasierte Optimierung** anzuzeigen und einen Aggregationsentwurf zu erstellen, der auf vorhandenen Verwendungsmustern für die ausgewählte Partition basiert.<br /><br /> Hinweis: Diese Option ist deaktiviert, wenn eine Rückschreibepartition ausgewählt wurde.|  
|**Verarbeiten**|Klicken Sie auf diese Option, um das Dialogfeld **Verarbeiten** anzuzeigen und die ausgewählte Partition zu verarbeiten.|  
|**Kopieren**|Diese Option ist deaktiviert.|  
|**Einfügen**|Diese Option ist deaktiviert.|  
|**Eigenschaften**|Wählen Sie diese Option aus, um für die ausgewählte Partition das Fenster **Eigenschaften** in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] anzuzeigen.|  
  
  
