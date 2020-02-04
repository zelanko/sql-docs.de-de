---
title: Entfernen von Verknüpfungen
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- removing joins
- joins [SQL Server], removing
- deleting joins
ms.assetid: ccc212a1-fd13-48d6-85e5-5ff310c34bbd
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.openlocfilehash: df6fe66cdc1b503342ed4a7bcf765307f38a0cf7
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "75255212"
---
# <a name="remove-joins-visual-database-tools"></a>Entfernen von Joins (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Wenn Tabellen nicht über einen inneren oder äußeren Join miteinander verknüpft werden sollen, können Sie den Join zwischen diesen Tabellen entfernen. Sie können z. B. einen Join entfernen, die der [Abfrage- und Ansicht-Designer](../../ssms/visual-db-tools/query-and-view-designer-tools-visual-database-tools.md) automatisch zwischen zwei Tabellen erstellt hat.  
  
> [!NOTE]  
> Durch das Entfernen eines Joins aus einer Abfrage wird die zugrunde liegende Beziehung in der Datenbank nicht geändert.  
  
Wenn zwei verknüpfte Tabellen Teil der Abfrage sind und Sie alle Joinbedingungen zwischen diesen entfernen, entsteht die resultierende Abfrage als Produkt aus beiden Tabellen, d.h. sie wird als CROSS JOIN bezeichnet.  
  
### <a name="to-remove-a-join"></a>So entfernen Sie einen Join  
  
-   Markieren Sie im [Diagrammbereich](../../ssms/visual-db-tools/diagram-pane-visual-database-tools.md)die Joinlinie für den zu entfernenden Join, und drücken Sie anschließend die ENTF-TASTE. Sie können mehrere Joinlinien gleichzeitig markieren und löschen.  
  
Der Abfrage- und Sicht-Designer entfernt die Joinlinie und ändert die Anweisung im [SQL-Bereich](../../ssms/visual-db-tools/sql-pane-visual-database-tools.md).  
  
## <a name="see-also"></a>Weitere Informationen  
[Automatisches Verknüpfen von Tabellen &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/join-tables-automatically-visual-database-tools.md)  
[Manuelles Verknüpfen von Tabellen &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/join-tables-manually-visual-database-tools.md)  
[Erstellen von Abfragen mit Joins &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/query-with-joins-visual-database-tools.md)  
  
