---
title: Bearbeiten oder Löschen von Partitionen (analyisis Services-Multidimensional) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- modifying partitions
- partitions [Analysis Services], modifying
ms.assetid: fb7a64ca-d021-4926-b92d-83476fbc40a3
author: minewiskan
ms.author: owend
ms.openlocfilehash: cad4c1f70743cafcc428835b3dcd11e2fa26ee79
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84546772"
---
# <a name="edit-or-delete-partitions-analyisis-services---multidimensional"></a>Bearbeiten oder Löschen von Partitionen (Analyisis Services – Mehrdimensional)
  Cubepartitionen werden über die Registerkarte **Partitionen** im Cube-Designer von [!INCLUDE[ssBIDevStudio](../../../includes/ssbidevstudio-md.md)]geändert. Auf der Registerkarte **Partitionen** werden die Partitionen für alle Measuregruppen in einem Cube aufgeführt. Ebenfalls werden die Rückschreibepartitionen mit aktiviertem Rückschreiben aufgeführt.

 Um die Partitionen für eine beliebige Measure-Gruppe zu bearbeiten, erweitern Sie die Gruppe Measure auf der Registerkarte **Partitionen** . Partitionen für eine Measure-Gruppe werden nach Ordinalzahl in einem Tabellenformat mit den in der folgenden Tabelle aufgeführten Spalten aufgelistet.

 Die Einstellungen für eine verknüpfte Measuregruppe müssen im Quellcube bearbeitet werden.

 Das Löschen von Partitionen erfolgt automatisch, wenn Sie eine Quellpartition mit einer Zielpartition zusammenführen. Die als Quelle angegebene Partition wird nach Ende der Zusammenführung gelöscht. Sie können die Partitionen auch manuell in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] oder auf der Registerkarte Partitionen in [!INCLUDE[ssBIDevStudio](../../../includes/ssbidevstudio-md.md)]löschen. Klicken Sie mit der rechten Maustaste darauf, und wählen Sie **Löschen**aus. Zur Erinnerung: Beim Löschen einer Partition werden auch Daten und Aggregationen entfernt. Zur Vorsicht sollten Sie eine neuere Datenbanksicherung erstellen, falls Sie das Löschen später rückgängig machen müssen.

> [!NOTE]
>  Alternativ können Sie XMLA-Skripts verwenden, um die Erstellung, das Zusammenführen und das Löschen von Partitionen zu automatisieren. XMLA-Skripts können in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]oder in benutzerdefinierten SSIS-Paketen, die als geplanter Task ablaufen, erstellt und ausgeführt werden. Weitere Informationen finden Sie unter [Automate Analysis Services Administrative Tasks with SSIS](../instances/automate-analysis-services-administrative-tasks-with-ssis.md).

## <a name="partition-source"></a>Partitionsquelle
 Gibt die Quelltabelle oder benannte Abfrage für die Partition an. Klicken Sie auf die Zelle, und klicken Sie anschließend auf die Schaltfläche zum Durchsuchen (**...**), um die Quelltabelle zu ändern.

 ![Quellspalte im Bereich "Partition"](../media/ssas-partitionsource.png "Quellspalte im Bereich "Partition"")

 Wenn die Partition auf einer Abfrage basiert, klicken Sie auf die Schaltfläche zum Durchsuchen (**...**), um die Abfrage zu bearbeiten. Dadurch wird die **Source** -Eigenschaft der Partition bearbeitet. Weitere Informationen finden Sie unter [Ändern einer Partitions Quelle für die Verwendung einer anderen Fakten Tabelle](change-a-partition-source-to-use-a-different-fact-table.md).

 Sie können eine Tabelle in der Datenquellensicht angeben, die die gleiche Struktur wie die ursprüngliche Quelltabelle (in der externen Datenquelle, aus der die Daten abgerufen werden) aufweist. Bei der Quelle kann es sich um eine beliebige Datenquelle oder Datenquellensicht der Cubedatenbank handeln.

## <a name="storage-settings"></a>Speichereinstellungen
 Im Cube-Designer auf der Registerkarte Partitionen können Sie auf **Speichereinstellungen** klicken, um eine der Standardeinstellungen für MOLAP-, ROLAP- oder HOLAP-Speicher auszuwählen, oder um benutzerdefinierte Einstellungen für den Speichermodus und das proaktive Zwischenspeichern zu konfigurieren. Die Standardmethode ist MOLAP, da sie die schnellste Abfrageleistung bietet. Weitere Informationen zu den einzelnen Einstellungen finden Sie unter [Festlegen des Partitionsspeichers &#40;Analysis Services – mehrdimensional&#41;](set-partition-storage-analysis-services-multidimensional.md).

 Speicher kann für jede Partition einer einzelnen Measuregruppe eines Cubes separat konfiguriert werden. Sie können auch die Standardspeichereinstellungen für einen Cube oder für eine Measuregruppe konfigurieren. Der Speicher wird im Cube-Assistenten auf der Registerkarte **Partitionen** konfiguriert.

## <a name="see-also"></a>Weitere Informationen
 [Erstellen und Verwalten einer lokalen Partition &#40;Analysis Services&#41;](create-and-manage-a-local-partition-analysis-services.md) [Entwerfen von Aggregationen &#40;Analysis Services-multidimensionalen&#41;Mergepartitionen](designing-aggregations-analysis-services-multidimensional.md) [in Analysis Services &#40;&#41;SSAS-Multidimensional](merge-partitions-in-analysis-services-ssas-multidimensional.md)


