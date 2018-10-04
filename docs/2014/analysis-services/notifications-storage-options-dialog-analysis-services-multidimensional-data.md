---
title: Benachrichtigungen (Optionsdialogfeld) (Analysis Services – mehrdimensionale Daten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.partitiondesigner.partitionstoragesettings.setstorageoptions.notifications.f1
ms.assetid: 5675cdbf-bfaa-4b6e-b716-31b8e9da72b4
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f6ba7fd0995066b90ef984f8dfa436864e06db95
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48193700"
---
# <a name="notifications-storage-options-dialog-box-analysis-services---multidimensional-data"></a>Benachrichtigungen (Dialogfeld 'Speicheroptionen') (Analysis Services – Mehrdimensionale Daten)
  Mithilfe des Dialogfelds **Benachrichtigungen** des Dialogfelds **Speicheroptionen** in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] können Sie die Benachrichtigungsmethode und die damit verbundenen Einstellungen für eine Dimension, einen Cube, eine Measuregruppe oder eine Partition festlegen.  
  
> [!NOTE]  
>  Sie sollten mit den Funktionen für den Speichermodus und das proaktive Zwischenspeichern vertraut sein, bevor Sie Änderungen an diesen Einstellungen vornehmen. Weitere Informationen finden Sie unter [Proaktives Zwischenspeichern &#40;Partitionen&#41;](multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md).  
  
## <a name="options"></a>Tastatur  
  
|Begriff|Definition|  
|----------|----------------|  
|**Speichermodus**|Wählt den für das Objekt zu verwendenden Speichermodus aus.<br /><br /> **MOLAP**<br /> Für das Objekt wird die mehrdimensionale OLAP (MOLAP)-Speicherung verwendet.<br /><br /> **HOLAP**<br /> Für das Objekt wird die hybride OLAP (HOLAP)-Speicherung verwendet.<br /><br /> **ROLAP**<br /> Für das Objekt wird die relationale OLAP (ROLAP)-Speicherung verwendet.|  
|**Proaktives Zwischenspeichern aktivieren**|Aktiviert die proaktive Zwischenspeicherung.<br /><br /> Hinweis: Wenn diese Option nicht ausgewählt ist, sind alle Optionen mit Ausnahme von **Speichermodus** deaktiviert.|  
|**SQL Server**|Verwendet einen speziellen Ablaufverfolgungsmechanismus für [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , um Änderungen an den zugrunde liegenden Tabellen für das Objekt zu identifizieren.|  
|**Nachverfolgungstabellen angeben**|Geben Sie die zugrunde liegenden Tabellen an, in denen das Objekt nachverfolgt werden soll. Geben Sie anschließend eine durch Semikolons (;) unterteilte Liste der Tabellen ein, oder klicken Sie auf die Schaltfläche mit den Auslassungspunkten **(…)**, um das Dialogfeld **Relationale Objekte** aufzurufen und die Tabellen auszuwählen, die nachverfolgt werden sollen. Weitere Informationen finden Sie unter [Dialogfeld „Relationale Objekte“ &#40;Analysis Services – Mehrdimensionale Daten&#41;](relational-objects-dialog-box-analysis-services-multidimensional-data.md).<br /><br /> Wenn diese Option nicht ausgewählt ist, versucht [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] die Liste der zugrunde liegenden Tabellen zu bestimmen, für die eine Nachverfolgung für das Objekt durchgeführt werden soll, wenn bestimmte Anforderungen erfüllt sind. Weitere Informationen zu diesen Anforderungen finden Sie unter [Proaktives Zwischenspeichern &#40;Partitionen&#41;](multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md).|  
|**Client initiiert**|Wählen, das XML für Analysis (XMLA)-Befehl verwenden `NotifyTableChange`, um Änderungen an den zugrunde liegenden Tabellen für das Objekt zu identifizieren. Diese Option ist normalerweise ausgewählt, wenn Sie die Verwendung eines Client-basierten Benachrichtigungsprozesses planen.|  
|**Nachverfolgungstabellen angeben**|Wählen Sie diese Option aus, um die zugrunde liegenden Tabellen anzugeben, in denen das Objekt nachverfolgt werden soll. Geben Sie anschließend eine durch Semikolons (;) unterteilte Liste der Tabellen ein, oder klicken Sie auf die Schaltfläche mit den Auslassungspunkten (**...**), um das Dialogfeld **Relationale Objekte** aufzurufen, und wählen Sie die Tabellen aus, die nachverfolgt werden sollen. Weitere Informationen finden Sie unter [Dialogfeld „Relationale Objekte“ &#40;Analysis Services – Mehrdimensionale Daten&#41;](relational-objects-dialog-box-analysis-services-multidimensional-data.md).<br /><br /> Wenn diese Option nicht ausgewählt ist, versucht [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] die Liste der zugrunde liegenden Tabellen zu bestimmen, für die eine Nachverfolgung für das Objekt durchgeführt werden soll, wenn bestimmte Anforderungen erfüllt sind. Weitere Informationen zu diesen Anforderungen finden Sie unter [Proaktives Zwischenspeichern &#40;Partitionen&#41;](multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md).|  
|**Geplantes Abrufen**|Verwendet einen Abrufmechanismus zum Identifizieren von Änderungen, indem eine Reihe von Abfragen der zugrunde liegenden Tabellen für das Objekt ausgeführt werden.|  
|**Abrufintervall**|Gibt das Intervall und die Zeiteinheiten für den Zeitraum an, nach dessen Ablauf [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] die im Abrufraster definierten Abrufabfragen und Verarbeitungsabfragen ausführt.|  
|**Inkrementelle Updates aktivieren**|Aktualisiert den MOLAP-Cache inkrementell für ein Objekt, das auf einem Satz von Abruf- und Verarbeitungsabfragen basiert, mit denen nur zusätzliche Daten identifiziert werden können. Wenn diese Option ausgewählt ist, wird die Abrufabfrage mit einer Tabellen in der Datenquellensicht verknüpft. Mithilfe der Verarbeitungsabfrage wird dann der aktuelle Wert der Abrufabfrage mit dem gespeicherten Wert der zuvor ausgeführten Abrufabfrage verglichen, um so Änderungen zu identifizieren.<br /><br /> Wenn diese Option nicht ausgewählt ist, wird der MOLAP-Cache vollständig aktualisiert. Mithilfe der Abrufabfrage können erfolgte Änderungen identifiziert werden. Verarbeitungsabfragen oder Tabellenbezeichner sind nicht erforderlich.|  
|**Abrufraster**|Enthält die Abrufabfragen, die Verarbeitungsabfragen und die Tabellenbezeichner, die von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] verwendet werden, um die Datenquelle abzurufen und Änderungen zu identifizieren, die an den zugrunde liegenden Tabellen für das Objekt vorgenommen wurden. Das Raster enthält die folgenden Spalten:<br /><br /> **Abrufabfrage**: Geben Sie die zum Identifizieren von Änderungen für das Objekt dem Abrufintervall entsprechend ausgeführte Singleton-Abfrage ein, oder klicken Sie auf die Schaltfläche mit den Auslassungspunkten (**...** ) zum Öffnen der **Abrufabfrage erstellen** Dialogfeld ein, und die Singleton-Abfrage zu definieren. Weitere Informationen finden Sie unter [Dialogfeld „Abrufabfrage erstellen“ &#40;Analysis Services – Mehrdimensionale Daten&#41;](create-polling-query-dialog-box-analysis-services-multidimensional-data.md). Wenn **Inkrementelle Updates aktivieren** ausgewählt ist, gibt die Abrufabfrage einen Wert zurück, durch den der letzte Datensatz identifiziert wird, der der unter **Tabelle**angegebenen Tabelle hinzugefügt wurde. Wenn **Inkrementelle Updates aktivieren** nicht ausgewählt ist, gibt die Abrufabfrage einen Wert zurück, durch den die aktuell in der Tabelle enthalten Anzahl von Datensätzen identifiziert wird.<br /><br /> **Verarbeitungsabfrage**: Geben Sie die abzurufenden neue Datensätze aus der Tabelle identifiziert, dem Abrufintervall entsprechend ausgeführte Abfrage **Tabelle**, oder klicken Sie auf die Schaltfläche mit den Auslassungspunkten (**...** ) zum Öffnen der **Verarbeitungsabfrage erstellen** Dialogfeld ein, und die Abfrage zu definieren. Weitere Informationen finden Sie unter [Dialogfeld „Verarbeitungsabfrage erstellen“ &#40;Analysis Services – Mehrdimensionale Daten&#41;](create-processing-query-dialog-box-analysis-services-multidimensional-data.md). Die Abfrage sollte so parametrisiert sein, dass zwei Parameter akzeptiert werden: der vorige Wert, der durch die Abfrage in **Abrufabfrage** zurückgegeben wurde, sowie der aktuelle Wert, der durch die Abfrage in **Abrufabfrage**zurückgegeben wird. Mithilfe dieser Parameter können nur die Datensätze identifiziert und extrahiert werden, die während des Abfragezeitraumes hinzugefügt wurden. Beachten Sie, dass diese Option nur aktiviert ist, wenn **Inkrementelle Updates aktivieren** ausgewählt wird.<br /><br /> **Tabelle**: Geben Sie den Bezeichner der Tabelle für die die Abfrage in **Abrufabfrage** den letzten Datensatz nachverfolgen, oder klicken Sie auf die Schaltfläche mit den Auslassungspunkten (**...** ) zum Öffnen der **Tabelle suchen** Dialogfeld und die Tabelle auszuwählen. Weitere Informationen finden Sie unter [Dialogfeld „Tabelle suchen“ &#40;Analysis Services – Mehrdimensionale Daten&#41;](find-table-dialog-box-analysis-services-multidimensional-data.md).|  
  
## <a name="see-also"></a>Siehe auch  
 [Dialogfeld "Speicheroptionen" &#40;Analysis Services – mehrdimensionale Daten&#41;](storage-options-dialog-box-analysis-services-multidimensional-data.md)  
  
  
