---
title: Verarbeiten von Datenbank, Tabelle oder Partition | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- SQL12.ASVS.SSMS.PARTITIONS.PROCESSINGOPTIONS.IMBI.F1
ms.assetid: 307d69c3-cabb-4dfa-b90c-9852492c1213
author: minewiskan
ms.author: owend
ms.openlocfilehash: 08c0856df10c2b70dc58ab1b52b0b7a4a1041e1b
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84938741"
---
# <a name="process-database-table-or-partition"></a>Verarbeiten von Datenbank, Tabelle oder Partition
  In den Tasks in diesem Thema wird beschrieben, wie tabellarische Modell Datenbanken, Tabellen oder Partitionen mithilfe des Dialog Felds **verarbeiten \<object> ** in manuell verarbeitet werden [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] .  
  
 Weitere Informationen zur Verarbeitung von tabellarischen Modellen finden Sie unter [Verarbeiten von Daten &#40;SSAS – tabellarisch&#41;](../process-data-ssas-tabular.md).  
  
##  <a name="tasks"></a><a name="bkmk_process_tasks"></a>Erfüllen  
  
###  <a name="to-process-a-database"></a><a name="bkmk_process_db"></a>So verarbeiten Sie eine Datenbank  
  
1.  Klicken Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]mit der rechten Maustaste auf die Datenbank, die Sie verarbeiten möchten, und klicken Sie anschließend auf **Datenbank verarbeiten**.  
  
2.  Wählen Sie im Dialogfeld **Datenbank verarbeiten** im Listenfeld **Modus** einen der folgenden Verarbeitungsmodi aus:  
  
    |Mode|Beschreibung|  
    |----------|-----------------|  
    |**Standard verarbeiten**|Erkennt den Verarbeitungsstatus von Datenbankobjekten und führt die Verarbeitung durch, mit der nicht verarbeitete oder teilweise verarbeitete Objekte in den vollständig verarbeiteten Status versetzt werden. Daten für leere Tabellen und Partitionen werden geladen, Hierarchien, berechnete Spalten und Beziehungen werden erstellt oder neu erstellt (neu berechnet).|  
    |**Vollständig verarbeiten**|Verarbeitet eine Datenbank und alle in ihr enthaltenen Objekte. Wenn die Verarbeitungsmethode "Vollständig verarbeiten" für ein bereits verarbeitetes Objekt ausgeführt wird, löscht [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] alle Daten im Objekt und verarbeitet anschließend das Objekt. Diese Art der Verarbeitung ist erforderlich, wenn eine Änderung an der Objektstruktur vorgenommen wurde. Diese Option erfordert die meisten Ressourcen.|  
    |**Löschung verarbeiten**|Entfernt alle Daten aus Datenbankobjekten.|  
    |**Neuberechnung verarbeiten**|Aktualisiert und berechnet Hierarchien, Beziehungen und berechnete Spalten neu.|  
  
3.  Wählen Sie in der Spalte der Kontrollkästchen unter **Verarbeiten** die Partitionen aus, die im ausgewählten Modus verarbeitet werden sollen, und klicken Sie dann auf **OK**.  
  
###  <a name="to-process-a-table"></a><a name="bkmk_process_table"></a>So verarbeiten Sie eine Tabelle  
  
1.  Erweitern Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]in der tabellarischen Modelldatenbank, die die zu verarbeitende Tabelle enthält, den Knoten **Tabellen** , klicken Sie mit der rechten Maustaste auf die zu verarbeitende Tabelle, und klicken Sie anschließend auf **Tabelle verarbeiten**.  
  
2.  Wählen Sie im Dialogfeld **Tabelle verarbeiten** im Listenfeld **Modus** einen der folgenden Verarbeitungsmodi aus:  
  
    |Mode|Beschreibung|  
    |----------|-----------------|  
    |**Standard verarbeiten**|Erkennt den Verarbeitungsstatus eines Tabellenobjekts und führt die Verarbeitung durch, die nicht verarbeitete oder teilweise verarbeitete Objekte in den Status Vollständig verarbeitet bringt. Daten für leere Tabellen und Partitionen werden geladen, Hierarchien, berechnete Spalten und Beziehungen werden erstellt oder neu erstellt (neu berechnet).|  
    |**Vollständig verarbeiten**|Verarbeitet ein Tabellenobjekt und alle darin enthaltenen Objekte. Wenn die Verarbeitungsmethode "Vollständig verarbeiten" für ein bereits verarbeitetes Objekt ausgeführt wird, löscht [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] alle Daten im Objekt und verarbeitet anschließend das Objekt. Diese Art der Verarbeitung ist erforderlich, wenn eine Änderung an der Objektstruktur vorgenommen wurde. Diese Option erfordert die meisten Ressourcen.|  
    |**Verarbeiten von Daten**|Lädt Daten in eine Tabelle, ohne Hierarchien oder Beziehungen neu zu erstellen bzw. berechnete Spalten und Measures neu zu berechnen.|  
    |**Löschung verarbeiten**|Entfernt alle Daten aus einer Tabelle und vorhandenen Tabellenpartitionen.|  
    |**Defragmentierung verarbeiten**|Defragmentiert die Indizes der Erweiterungstabellen.|  
  
3.  Überprüfen Sie in der Spalte der Kontrollkästchen die Tabelle und wählen Sie optional zusätzlich zu verarbeitende Tabellen aus, und klicken Sie dann auf **OK**.  
  
###  <a name="to-process-one-or-more-partitions"></a><a name="bkmk_process_partition"></a> So verarbeiten Sie eine oder mehrere Partitionen  
  
1.  Klicken Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]mit der rechten Maustaste auf die Tabelle, die die zu verarbeitenden Partitionen enthält, und klicken Sie anschließend auf **Partitionen**.  
  
2.  Klicken Sie im Dialogfeld **Partitionen** unter den Partitionen auf die Schaltfläche **Verarbeiten**.  
  
3.  Wählen Sie im Dialogfeld **Partition verarbeiten** im Listenfeld **Modus** einen der folgenden Verarbeitungsmodi aus:  
  
    |Mode|Beschreibung|  
    |----------|-----------------|  
    |**Standard verarbeiten**|Erkennt den Verarbeitungsstatus eines Partitionsobjekts und führt die Verarbeitung durch, durch die nicht oder teilweise verarbeitete Partitionsobjekte in den Status "Vollständig verarbeitet" versetzt werden. Daten für leere Tabellen und Partitionen werden geladen, Hierarchien, berechnete Spalten und Beziehungen werden erstellt oder neu erstellt (neu berechnet).|  
    |**Vollständig verarbeiten**|Verarbeitet ein Partitionsobjekt und alle darin enthaltenen Objekte. Wenn die Verarbeitungsmethode "Vollständig verarbeiten" für ein bereits verarbeitetes Objekt ausgeführt wird, löscht [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] alle Daten im Objekt und verarbeitet anschließend das Objekt. Diese Art der Verarbeitung ist erforderlich, wenn eine Änderung an der Objektstruktur vorgenommen wurde.|  
    |**Verarbeiten von Daten**|Lädt Daten in eine Partition oder Tabelle, ohne Hierarchien oder Beziehungen neu zu erstellen bzw. berechnete Spalten und Measures neu zu berechnen.|  
    |**Löschung verarbeiten**|Entfernt alle Daten aus einer Partition.|  
    |**Hinzufügung verarbeiten**|Aktualisiert die Partition inkrementell mit neuen Daten.|  
  
4.  Wählen Sie in der Spalte der Kontrollkästchen unter **Verarbeiten** die Partitionen aus, die im ausgewählten Modus verarbeitet werden sollen, und klicken Sie dann auf **OK**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Tabellarische Modell Partitionen &#40;tabellarischen SSAS-&#41;](tabular-model-partitions-ssas-tabular.md)   
 [Erstellen und Verwalten von Tabellenmodellpartitionen &#40;SSAS – tabellarisch&#41;](create-and-manage-tabular-model-partitions-ssas-tabular.md)  
  
  
