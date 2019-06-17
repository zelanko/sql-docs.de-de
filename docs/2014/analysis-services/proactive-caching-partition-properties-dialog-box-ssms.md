---
title: Proaktives Zwischenspeichern (Dialogfeld Partitionseigenschaften) (SSMS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.partitionproperties.proactivecaching.f1
ms.assetid: ecba72a3-703f-4ede-9d85-9a3318a749e5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: cb486ec383ab6fa1684bd9d0e9b8f6bc67631eee
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66070705"
---
# <a name="proactive-caching-partition-properties-dialog-box-ssms"></a>Proaktives Zwischenspeichern (Dialogfeld Partitionseigenschaften) (SSMS)
  Mithilfe der Registerkarte **Proaktives Zwischenspeichern** des Dialogfelds **Partitionseigenschaften** in SQL Server Management Studio können Sie die Eigenschaften zur Speicherung und proaktiven Zwischenspeicherung einer Partition in einer Measuregruppe für einen Cube in einer [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank festlegen.  
  
## <a name="options"></a>Optionen  
 **Standardeinstellung**  
 Wählen Sie diese Option aus, um den Schieberegler **Standardeinstellung** zu aktivieren und vordefinierte Einstellungen für den Speichermodus und die Funktion proaktives Zwischenspeichern zu verwenden.  
  
 **Standardeinstellung**  
 Legen Sie eine der in der folgenden Tabelle aufgelisteten vordefinierten Einstellungen fest.  
  
|Einstellung|Description|  
|-------------|-----------------|  
|**Echtzeit-ROLAP**|Wählen Sie diese Einstellung aus, um die folgenden Einstellungen für die Speicherung und das proaktive Zwischenspeichern zu verwenden:<br /><br /> ROLAP-Speichermodus<br /><br /> Aktiviert die proaktive Zwischenspeicherung.<br /><br /> Löscht veraltete Zwischenspeicherinhalte mit einer Latenzzeit von 0 Sekunden.<br /><br /> Schaltet das Objekt sofort online.|  
|**Echtzeit-HOLAP**|Wählen Sie diese Einstellung aus, um die folgenden Einstellungen für die Speicherung und das proaktive Zwischenspeichern zu verwenden:<br /><br /> HOLAP-Speichermodus<br /><br /> Aktiviert die proaktive Zwischenspeicherung.<br /><br /> Löscht veraltete Zwischenspeicherinhalte mit einer Latenzzeit von 0 Sekunden.<br /><br /> Aktualisiert den Zwischenspeicher bei Änderungen der Daten mit einem Ruheintervall von null (0) Sekunden und ohne Ruhe-Überschreibungsintervall.<br /><br /> Schaltet das Objekt sofort online.|  
|**MOLAP mit niedriger Latenzzeit**|Wählen Sie diese Einstellung aus, um die folgenden Einstellungen für die Speicherung und das proaktive Zwischenspeichern zu verwenden:<br /><br /> MOLAP-Speichermodus<br /><br /> Aktiviert die proaktive Zwischenspeicherung.<br /><br /> Löscht veraltete Zwischenspeicherinhalte mit einer Latenzzeit von 30 Minuten.<br /><br /> Aktualisiert den Zwischenspeicher bei Änderungen der Daten mit einem Ruheintervall von 10 Sekunden und einem Ruhe-Überschreibungsintervall von 10 Minuten.<br /><br /> Aktualisiert den Zwischenspeicher bei Änderungen der Daten mit einem Ruheintervall von 10 Sekunden und einem Ruhe-Überschreibungsintervall von 10 Minuten.<br /><br /> Schaltet das Objekt sofort online.|  
|**MOLAP mit mittlerer Latenzzeit**|Wählen Sie sofort online UseBrings-Objekt.<br /><br /> die folgenden Speicher und die Einstellungen für das proaktive Zwischenspeichern:<br /><br /> MOLAP-Speichermodus<br /><br /> Aktiviert die proaktive Zwischenspeicherung.<br /><br /> Löscht veraltete Zwischenspeicherinhalte mit einer Latenzzeit von 4 Stunden.<br /><br /> Aktualisiert den Zwischenspeicher bei Änderungen der Daten mit einem Ruheintervall von 10 Sekunden und einem Ruhe-Überschreibungsintervall von 10 Minuten.<br /><br /> Schaltet das Objekt sofort online.|  
|**Automatische MOLAP**|Wählen Sie diese Einstellung aus, um die folgenden Einstellungen für die Speicherung und das proaktive Zwischenspeichern zu verwenden:<br /><br /> MOLAP-Speichermodus<br /><br /> Aktiviert die proaktive Zwischenspeicherung.<br /><br /> Aktualisiert den Zwischenspeicher bei Änderungen der Daten mit einem Ruheintervall von null (0) Sekunden und ohne Ruhe-Überschreibungsintervall.|  
|**Geplante MOLAP**|Wählen Sie diese Einstellung aus, um die folgenden Einstellungen für die Speicherung und das proaktive Zwischenspeichern zu verwenden:<br /><br /> MOLAP-Speichermodus<br /><br /> Aktiviert die proaktive Zwischenspeicherung.<br /><br /> Aktualisiert den Zwischenspeicher in regelmäßigen Abständen mit einem Neuerstellungsintervall von einem Tag.|  
|**MOLAP**|Wählen Sie diese Einstellung aus, um die folgenden Einstellungen für die Speicherung und das proaktive Zwischenspeichern zu verwenden:<br /><br /> MOLAP-Speichermodus|  
  
 **Benutzerdefinierte Einstellung**  
 Wählen Sie diese Option aus, um die Einstellungen für Speichermodus, proaktives Zwischenspeichern und Benachrichtigungsoptionen explizit festzulegen.  
  
 **Options**  
 Klicken Sie hier, um das Dialogfeld **Speicheroptionen** anzuzeigen und Speichermodus, proaktives Zwischenspeichern und Benachrichtigungsoptionen explizit festzulegen. Weitere Informationen zum Dialogfeld **Speicheroptionen** finden Sie unter [Speicheroptionen &#40;Dialogfeld, Analysis Services – mehrdimensionale Daten&#41;](storage-options-dialog-box-analysis-services-multidimensional-data.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Proaktives Zwischenspeichern &#40;Partitionen&#41;](multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md)   
 [Partitionieren Sie im Dialogfeld Eigenschaften von &#40;SSMS&#41;](partition-properties-dialog-box-ssms.md)   
 [Auswahl &#40;Partitionieren Sie im Dialogfeld Eigenschaften von&#41; &#40;SSMS&#41;](selection-partition-properties-dialog-box-ssms.md)   
 [Allgemeine &#40;Partitionieren Sie im Dialogfeld Eigenschaften von&#41; &#40;SSMS&#41;](general-partition-properties-dialog-box-ssms.md)   
 [Fehlerkonfiguration für Cubes, Partitionen und Dimensionsverarbeitung &#40;SSAS – mehrdimensional&#41;](multidimensional-models/error-configuration-for-cube-partition-and-dimension-processing.md)  
  
  
