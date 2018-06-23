---
title: Manuelles verarbeiten Daten (SSAS – tabellarisch) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.bidtoolset.datarefreshprogressdb.f1
ms.assetid: 0918c04c-c1e6-45b4-acfa-96fa578e684b
caps.latest.revision: 17
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: edfb5ab290d6a5756e88f23497a4ea88c14db5d4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36162579"
---
# <a name="manually-process-data-ssas-tabular"></a>Manuelle Verarbeitung von Daten (SSAS – tabellarisch)
  In diesem Thema wird beschrieben, wie Arbeitsbereichsdaten in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]manuell verarbeitet werden.  
  
 Wenn Sie ein tabellarisches Modell erstellen, das externe Daten verwendet, können Sie die Daten mit dem Befehl Verarbeiten manuell aktualisieren. Sie können eine einzelne Tabelle, alle Tabellen im Modell oder eine oder mehrere Partitionen verarbeiten. Wenn Sie Daten verarbeiten, müssen Sie möglicherweise auch Daten neu berechnen.  Verarbeiten von Daten bedeutet, dass die aktuellen Daten aus den externen Quellen abgerufen werden. Neuberechnen bedeutet, dass das Ergebnis jeder Formel aktualisiert wird, die die Daten verwendet.  
  
 Abschnitte in diesem Thema:  
  
-   [Manuelle Verarbeitung von Daten](#bkmk_mahually_process)  
  
-   [Status der Datenverarbeitung](#bkmk_data_process_progress)  
  
##  <a name="bkmk_mahually_process"></a> Manuelle Verarbeitung von Daten  
  
#### <a name="to-process-data-for-a-single-table-or-all-tables-in-a-model"></a>So verarbeiten Sie Daten für eine einzelne Tabelle oder alle Tabellen in einem Modell  
  
1.  Klicken Sie im Modell-Designer auf die Tabelle, die Sie verarbeiten möchten.  
  
2.  Wählen Sie das Menü **Modell** . Klicken Sie dann auf **Verarbeiten**und danach auf **Verarbeiten** oder **Alles verarbeiten**.  
  
#### <a name="to-process-data-for-all-tables-using-the-same-connection"></a>So verarbeiten Sie Daten für alle Tabellen, die dieselbe Verbindung verwenden  
  
1.  Klicken Sie in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]im Menü **Modell** auf **Vorhandene Verbindungen**.  
  
2.  Wählen Sie im Dialogfeld **Vorhandene Verbindungen** eine Verbindung aus, und klicken Sie dann auf **Verarbeiten**.  
  
#### <a name="to-process-data-for-one-or-more-partitions"></a>So verarbeiten Sie Daten für eine oder mehrere Partitionen  
  
1.  Klicken Sie in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]im Modell-Designer auf das Menü **Modell** . Navigieren Sie dann zu **Verarbeiten**, und klicken Sie anschließend auf **Partitionen verarbeiten**.  
  
2.  Wählen Sie im Dialogfeld **Partitionen verarbeiten** unter **Modus**einen der folgenden Verarbeitungsmodi aus:  
  
    |Mode|Description|  
    |----------|-----------------|  
    |**Standard verarbeiten**|Erkennt den Verarbeitungsstatus eines Partitionsobjekts und führt die Verarbeitung durch, durch die nicht oder teilweise verarbeitete Partitionsobjekte in den Status "Vollständig verarbeitet" versetzt werden. Daten für leere Tabellen und Partitionen werden geladen, Hierarchien, berechnete Spalten und Beziehungen werden erstellt oder neu erstellt.|  
    |**Vollständig verarbeiten**|Verarbeitet ein Partitionsobjekt und alle darin enthaltenen Objekte. Wenn die Verarbeitungsmethode "Vollständig verarbeiten" für ein bereits verarbeitetes Objekt ausgeführt wird, löscht [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] alle Daten im Objekt und verarbeitet anschließend das Objekt. Diese Art der Verarbeitung ist erforderlich, wenn eine Änderung an der Objektstruktur vorgenommen wurde.|  
    |**Verarbeiten von Daten**|Lädt Daten in eine Partition oder Tabelle, ohne Hierarchien oder Beziehungen neu zu erstellen bzw. berechnete Spalten und Measures neu zu berechnen.|  
    |**Löschung verarbeiten**|Entfernt alle Daten aus einer Partition.|  
    |**Hinzufügung verarbeiten**|Aktualisiert die Partition inkrementell mit neuen Daten.|  
  
3.  Wählen Sie in der Liste der Partitionen die zu verarbeitende Partition aus, und klicken Sie auf **OK**.  
  
##  <a name="bkmk_data_process_progress"></a> Status der Datenverarbeitung  
 Im Dialogfeld **Status der Datenverarbeitung** können Sie die Verarbeitung von Daten überwachen, die Sie aus einer externen Quelle in das Modell importiert haben. Um dieses Dialogfeld zu öffnen, klicken Sie auf das Menü **Modell** und anschließend auf **Partitionen verarbeiten**, **Tabelle verarbeiten** oder **Alles verarbeiten**.  
  
 **Status**  
 Gibt an, ob der Verarbeitungsvorgang erfolgreich war.  
  
 **Details**  
 Listet die Tabellen und die Sichten, die importiert wurden, sowie die Anzahl von Zeilen auf, die importiert wurden, und stellt einen Link für einen Bericht zu Problemen bereit.  
  
 **Aktualisierung beenden**  
 Klicken Sie auf diese Option, um den Verarbeitungsvorgang anzuhalten. Diese Option ist nützlich, wenn der Vorgang zu lange dauert oder wenn es zu viele Fehler gibt.  
  
## <a name="see-also"></a>Siehe auch  
 [Daten verarbeiten &#40;SSAS – tabellarisch&#41;](process-data-ssas-tabular.md)   
 [Problembehandlung von Verarbeitungsdaten &#40;SSAS – tabellarisch&#41;](troubleshoot-process-data-ssas-tabular.md)  
  
  