---
title: Verarbeiten von Tabellenmodellpartitionen (SSAS – tabellarisch) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 6c498d2b-22d6-4661-bc21-2ee708336c8b
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c4cabfe4f0d28bb74ae1fae0b84de758e7dca565
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66066829"
---
# <a name="process-tabular-model-partitions-ssas-tabular"></a>Verarbeiten von Tabellenmodellpartitionen (SSAS – tabellarisch)
  Durch Partitionen wird eine Tabelle logisch unterteilt. Jede Partition kann unabhängig von anderen Partitionen verarbeitet (aktualisiert) werden. In den Tasks in diesem Thema wird beschrieben, wie Partitionen in einer Modelldatenbank mithilfe des Dialogfelds **Partition(en) verarbeiten** in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]verarbeitet werden.  
  
###  <a name="bkmk_create_new"></a> So verarbeiten Sie eine Partition  
  
1.  Klicken Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]mit der rechten Maustaste auf die Tabelle, die die zu verarbeitenden Partitionen enthält, und klicken Sie anschließend auf **Partitionen**.  
  
2.  Klicken Sie im Dialogfeld **Partitionen** unter **Partitionen**auf die Schaltfläche Verarbeiten.  
  
3.  In der **Partition(en)** Dialogfeld die **Modus** Listenfeld eine der folgenden Verarbeitungsmodi aus:  
  
    |Modus|Beschreibung|  
    |----------|-----------------|  
    |**Standard verarbeiten**|Erkennt den Verarbeitungsstatus eines Partitionsobjekts und führt die Verarbeitung durch, durch die nicht oder teilweise verarbeitete Partitionsobjekte in den Status "Vollständig verarbeitet" versetzt werden. Daten für leere Tabellen und Partitionen werden geladen, Hierarchien, berechnete Spalten und Beziehungen werden erstellt oder neu erstellt.|  
    |**Vollständig verarbeiten**|Verarbeitet ein Partitionsobjekt und alle darin enthaltenen Objekte. Wenn die Verarbeitungsmethode "Vollständig verarbeiten" für ein bereits verarbeitetes Objekt ausgeführt wird, löscht [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] alle Daten im Objekt und verarbeitet anschließend das Objekt. Diese Art der Verarbeitung ist erforderlich, wenn eine Änderung an der Objektstruktur vorgenommen wurde.|  
    |**Verarbeiten von Daten**|Lädt Daten in eine Partition oder Tabelle, ohne Hierarchien oder Beziehungen neu zu erstellen bzw. berechnete Spalten und Measures neu zu berechnen.|  
    |**Löschung verarbeiten**|Entfernt alle Daten aus einer Partition.|  
    |**Hinzufügung verarbeiten**|Aktualisiert die Partition inkrementell mit neuen Daten.|  
  
4.  Wählen Sie in der Spalte der Kontrollkästchen unter **Verarbeiten** die Partitionen aus, die im ausgewählten Modus verarbeitet werden sollen, und klicken Sie dann auf **OK**.  
  
## <a name="see-also"></a>Siehe auch  
 [Tabellenmodellpartitionen &#40;SSAS – tabellarisch&#41;](partitions-ssas-tabular.md)   
 [Erstellen und Verwalten von Tabellenmodellpartitionen &#40;SSAS – tabellarisch&#41;](create-and-manage-tabular-model-partitions-ssas-tabular.md)  
  
  
