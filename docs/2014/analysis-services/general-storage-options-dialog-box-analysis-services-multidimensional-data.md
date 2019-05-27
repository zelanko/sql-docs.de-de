---
title: Allgemein (Optionsdialogfeld) (Analysis Services – mehrdimensionale Daten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.partitiondesigner.partitionstoragesettings.setstorageoptions.storage.f1
ms.assetid: ee1fac79-ae15-4c3c-9a98-33db04388817
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3c7ddd5311232ae12b3eb9f66adc0cd1f5714b32
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66081012"
---
# <a name="general-storage-options-dialog-box-analysis-services---multidimensional-data"></a>Allgemein (Dialogfeld „Speicheroptionen“) (Analysis Services – Mehrdimensionale Daten)
  Mithilfe der Registerkarte **Allgemein** im Dialogfeld **Speicheroptionen** in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] können Sie die Einstellungen für den Speichermodus und das proaktive Zwischenspeichern für eine Dimension, einen Cube, eine Measuregruppe oder eine Partition festlegen.  
  
> [!NOTE]  
>  Sie sollten mit den Funktionen für den Speichermodus und das proaktive Zwischenspeichern vertraut sein, bevor Sie Änderungen an diesen Einstellungen vornehmen. Weitere Informationen finden Sie unter [Proaktives Zwischenspeichern &#40;Partitionen&#41;](multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md).  
  
## <a name="options"></a>Optionen  
  
|Begriff|Definition|  
|----------|----------------|  
|**Speichermodus**|Wählt den für das Objekt zu verwendenden Speichermodus aus.<br /><br /> **MOLAP**<br /> Für das Objekt wird die mehrdimensionale OLAP (MOLAP)-Speicherung verwendet.<br /><br /> **HOLAP**<br /> Für das Objekt wird die hybride OLAP (HOLAP)-Speicherung verwendet.<br /><br /> **ROLAP**<br /> Für das Objekt wird die relationale OLAP (ROLAP)-Speicherung verwendet.|  
|**Proaktives Zwischenspeichern aktivieren**|Aktiviert die proaktive Zwischenspeicherung.<br /><br /> Hinweis: Wenn diese Option nicht ausgewählt ist, sind alle Optionen außer **Speichermodus** sind deaktiviert.|  
|**Aktualisieren Sie den Cache bei datenänderungen**|Aktualisieren Sie mithilfe der auf der Registerkarte **Benachrichtigungen** ausgewählten Benachrichtigungsmethode bei jeder empfangenen Benachrichtigung das MOLAP-Image für das Objekt. Weitere Informationen zur Registerkarte **Benachrichtigungen** finden Sie unter [Benachrichtigungen &#40;Dialogfeld „Speicheroptionen“&#41; &#40;Analysis Services – Mehrdimensionale Daten&#41;](notifications-storage-options-dialog-analysis-services-multidimensional-data.md).<br /><br /> Hinweis: Diese Option ist deaktiviert, es sei denn, **proaktives Zwischenspeichern aktivieren** ausgewählt ist.|  
|**Ruheintervall**|Legt das Mindestintervall und die Zeiteinheit für die Inaktivität des Objekts fest, bevor das proaktive Zwischenspeichern mit dem Erstellen eines neuen MOLAP-Images für das Objekt beginnt.<br /><br /> Hinweis: Diese Option ist deaktiviert, es sei denn, **Cache bei datenänderungen aktualisieren** ausgewählt ist.|  
|**Ruhe-überschreibungsintervall**|Legt das Maximumintervall und die Zeiteinheit nach dem Empfangen einer Benachrichtigung für das Objekt fest, nach der das proaktive Zwischenspeichern unabhängig von der aktuellen Aktivität des Objekts mit dem Erstellen eines neuen MOLAP-Images für das Objekt beginnt. Benachrichtigungen, die nach Ende des Intervalls empfangen werden, brechen den durch dieses Intervall ausgelösten MOLAP-Imageprozess nicht ab.<br /><br /> Hinweis: Diese Option ist deaktiviert, es sei denn, **Cache bei datenänderungen aktualisieren** ausgewählt ist. Beachten Sie auch, die diese Option nicht festgelegt werden soll wenn **Speichermodus** nastaven NA hodnotu **HOLAP**.|  
|**Veralteten Cache löschen**|Gibt den Zeitraum zwischen dem Start des Erstellens eines neuen MOLAP-Caches und dem Entfernen des vorhandenen MOLAP-Caches an.<br /><br /> Hinweis: Diese Option ist deaktiviert, es sei denn, **proaktives Zwischenspeichern aktivieren** ausgewählt ist. Beachten Sie auch, die diese Option nicht festgelegt werden soll wenn **Speichermodus** auf HOLAP festgelegt ist.|  
|**Latenzzeit**|Wählt das Intervall und die Zeiteinheiten für den Zeitraum zwischen dem Start des Erstellens eines neuen MOLAP-Caches und dem Entfernen des vorhandenen MOLAP-Caches aus.<br /><br /> Hinweis: Diese Option ist deaktiviert, es sei denn, **veralteten Cache löschen** ausgewählt ist. Beachten Sie auch, die diese Option nicht festgelegt werden soll wenn **Speichermodus** nastaven NA hodnotu **HOLAP**.|  
|**Cache regelmäßig aktualisieren**|Aktualisiert das MOLAP-Image in regelmäßigen Abständen, unabhängig von einer Benachrichtigung.<br /><br /> Hinweis: Diese Option ist deaktiviert, es sei denn, **proaktives Zwischenspeichern aktivieren** ausgewählt ist. Beachten Sie auch, die diese Option nicht festgelegt werden soll wenn **Speichermodus** nastaven NA hodnotu **HOLAP**.|  
|**Neuerstellungsintervall**|Wählt das Intervall und die Zeiteinheiten für die Periode aus, nach der [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] nach dem Erstellen eines neuen MOLAP-Images den MOLAP-Imageprozess für das Objekt erneut startet, unabhängig von einer Benachrichtigung. Benachrichtigungen, die nach Ende des Intervalls empfangen werden, brechen den durch dieses Intervall ausgelösten MOLAP-Imageprozess nicht ab.<br /><br /> Hinweis: Diese Option ist deaktiviert, es sei denn, **Cache regelmäßig aktualisieren** ausgewählt ist. Beachten Sie auch, die diese Option nicht festgelegt werden soll wenn **Speichermodus** nastaven NA hodnotu **HOLAP**.|  
|**Sofort online schalten**|Schaltet Objekte sofort online. Wenn diese Option festgelegt ist, verwenden Objekte die zugrunde liegende ROLAP-Speicherung zum Auflösen von Abfragen, während der MOLAP-Cache erneut erstellt wird. Wenn diese Option nicht festgelegt ist, werden Objekte erst online geschaltet, nachdem der MOLAP-Cache für das Objekt vollständig ist.|  
|**ROLAP-Aggregationen aktivieren**|Verwendet für die zugrunde liegende Datenquelle materialisierte Sichten zum Speichern von Aggregationen.<br /><br /> Hinweis: Wenn die zugrunde liegende Datenquelle materialisierte Sichten nicht unterstützt, tritt ein Fehler, wenn das Objekt verarbeitet wird.|  
|**Einstellungen auf Dimensionen anwenden**|Wendet die Einstellungen für den Speichermodus und das proaktive Zwischenspeichern auf verknüpfte Dimensionen an.|  
  
## <a name="see-also"></a>Siehe auch  
 [Dialogfeld "Speicheroptionen" &#40;Analysis Services – mehrdimensionale Daten&#41;](storage-options-dialog-box-analysis-services-multidimensional-data.md)   
 [Benachrichtigungen &#40;im Dialogfeld "Speicheroptionen"&#41; &#40;Analysis Services – mehrdimensionale Daten&#41;](notifications-storage-options-dialog-analysis-services-multidimensional-data.md)  
  
  
