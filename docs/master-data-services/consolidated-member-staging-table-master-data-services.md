---
description: Konsolidierte Elementstagingtabelle (Master Data Services)
title: Konsolidierte Elementstagingtabelle
ms.custom: ''
ms.date: 04/01/2016
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- database [Master Data Services], attributes staging table
- attributes staging table [Master Data Services]
ms.assetid: 070681ed-be99-49ae-93bd-6402f2134ace
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: b0104722d3fcea882b08aab3f44becc334b2d52c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429982"
---
# <a name="consolidated-member-staging-table-master-data-services"></a>Konsolidierte Elementstagingtabelle (Master Data Services)

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  Verwenden Sie die konsolidierte Elementstagingtabelle (stg.name_Consolidated) in der [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Datenbank, um konsolidierte Elemente zu erstellen, zu aktualisieren, zu deaktivieren und zu löschen. Sie können sie auch zum Aktualisieren von Attributwerten für konsolidierte Elemente verwenden.  
  
##  <a name="table-columns"></a><a name="TableColumns"></a> Tabellen Spalten  
 In der folgenden Tabelle wird erläutert, wofür jedes der Felder in der Stagingtabelle "Konsolidiert" verwendet wird.  
  
|Spaltenname|Beschreibung|  
|-----------------|-----------------|  
|**ID**|Ein automatisch zugewiesener Bezeichner. Geben Sie in diesem Feld keinen Wert ein. Wenn der Batch nicht verarbeitet wurde, ist dieses Feld leer.|  
|**ImportType**<br /><br /> Erforderlich|Bestimmt, wie verfahren wird, wenn bereitgestellte Daten Daten entsprechen, die bereits in der Datenbank [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] vorhanden sind.<br /><br /> **0**: Erstellen neuer Elemente. Ersetzen Sie MDS-Daten durch bereitgestellte Daten, aber nur, wenn die bereitgestellten Daten ungleich NULL sind. NULL-Werte werden ignoriert. Um einen Attributwert in NULL zu ändern, verwenden Sie **~NULL~**.<br /><br /> **1**: Ausschließliches Erstellen neuer Elemente. Fehler bei Updates vorhandener MDS-Daten.<br /><br /> **2**: Erstellen neuer Elemente. Ersetzen von MDS-Daten durch bereitgestellte Daten. Wenn Sie NULL-Werte importieren, überschreiben diese vorhandene MDS-Werte.<br /><br /> **3**: Deaktivieren des Elements basierend auf dem Codewert. Alle Attribute, Hierarchie- und Auflistungsmitgliedschaften sowie Transaktionen werden beibehalten, sind aber nicht mehr auf der Benutzeroberfläche verfügbar. Wenn das Element als domänenbasierter Attributwert eines anderen Elements verwendet wird, tritt ein Fehler beim Deaktivieren auf.<br /><br /> **4**: Dauerhaftes Löschen des Elements basierend auf dem Codewert. Alle Attribute, Hierarchie- und Auflistungsmitgliedschaften sowie Transaktionen werden dauerhaft gelöscht. Wenn das Element als domänenbasierter Attributwert eines anderen Elements verwendet wird, tritt ein Fehler beim Löschen auf.|  
|**ImportStatus_ID**<br /><br /> Erforderlich|Der Status des Importvorgangs. Mögliche Werte:<br /><br /> **0**geben Sie an, um anzuzeigen, dass der Datensatz für den Stagingprozess bereit ist.<br /><br /> **1**: wird automatisch zugewiesen und gibt an, dass der Stagingprozess für den Datensatz erfolgreich war.<br /><br /> **2**: wird automatisch zugewiesen, und gibt an, dass der Stagingprozess für den Datensatz nicht erfolgreich war.|  
|**Batch_ID**<br /><br /> Wird nur vom Webdienst benötigt|Ein automatisch zugewiesener Bezeichner, der Datensätze für das Staging gruppiert. Alle Elemente im Batch werden diesem Bezeichner zugewiesen, der in der [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] -Benutzeroberfläche in der **ID** -Spalte angezeigt wird.<br /><br /> Wenn der Batch nicht verarbeitet wurde, ist dieses Feld leer.|  
|**BatchTag**<br /><br /> Erforderlich, außer vom Webdienst|Ein eindeutiger Name für den Batch (bis zu 50 Zeichen).|  
|**HierarchyName**<br /><br /> Erforderlich|Der explizite Name der Hierarchie. Jedes konsolidierte Element kann nur einer Hierarchie angehören.|  
|**ErrorCode**|Zeigt einen Fehlercode an. Informationen zu Datensätzen mit einer **ImportStatus_ID** von **2**, finden Sie unter [Fehler des Stagingprozesses &#40;Master Data Services&#41;](../master-data-services/staging-process-errors-master-data-services.md).|  
|**Code**<br /><br /> Erforderlich, es sei denn, Codes werden automatisch für **ImportType1** oder **2** generiert. Weitere Informationen finden Sie unter [Automatische Codeerstellung &#40;Master Data Services&#41;](../master-data-services/automatic-code-creation-master-data-services.md).|Ein eindeutiger Code für das Element.|  
|**Name**<br /><br /> Optional|Ein Name für das Element.|  
|**NewCode**|Nur verwenden, wenn Sie den Elementcode ändern.|  
|\<Attribute name>|Für jedes Attribut in der Entität ist eine Spalte vorhanden. Verwenden Sie dieses mit einem **ImportType** von **0** oder **2**. Geben Sie für Freiformattribute den neuen Text oder Zeichenfolgenwert für das Attribut an. Für domänenbasierte Attribute geben Sie den Code für das Element an, das als Attribut verwendet wird. Bei Linkattributen muss die URL mit **https://** beginnen.<br /><br /> <br /><br /> Hinweis: Sie können keine Dateiattribute bereitstellen.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Übersicht: Importieren von Daten aus Tabellen &#40;Master Data Services&#41;](../master-data-services/overview-importing-data-from-tables-master-data-services.md)   
 [Anzeigen von Fehlern, die während des Stagings &#40;Master Data Services auftreten&#41;](../master-data-services/view-errors-that-occur-during-staging-master-data-services.md)   
 [Fehler des Stagingprozesses &#40;Master Data Services&#41;](../master-data-services/staging-process-errors-master-data-services.md)  
  
  
