---
title: Stagingtabelle für Beziehungen (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- relationships staging table [Master Data Services]
- database [Master Data Services], relationships table
ms.assetid: e19b6002-67bd-4e7d-9f19-ecb455522b1a
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: c5d37385494fc4853f47ec8e1fe883d3ff00f0e2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36046239"
---
# <a name="relationship-staging-table-master-data-services"></a>Stagingtabelle für Beziehungen (Master Data Services)
  Ändern Sie den Speicherort von Elementen in einer expliziten Hierarchie anhand der Beziehung der Elemente untereinander, indem Sie die Stagingtabelle für Beziehungen (stg.name_Relationship) in der [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Datenbank verwenden.  
  
##  <a name="TableColumns"></a> Tabellenspalten  
 Die folgende Tabelle erklärt, wofür jedes der Felder in der Stagingtabelle für Beziehungen verwendet wird.  
  
|Spaltenname|Description|  
|-----------------|-----------------|  
|**ID**|Ein automatisch zugewiesener Bezeichner. Geben Sie in diesem Feld keinen Wert ein. Wenn der Batch nicht verarbeitet wurde, ist dieses Feld leer.|  
|**RelationshipType**<br /><br /> Required|Der festgelegte Beziehungstyp. Folgende Werte sind möglich:<br /><br /> **1**: übergeordnet<br /><br /> **2**: gleichgeordnet (auf gleicher Ebene)|  
|**ImportStatus_ID**<br /><br /> Required|Der Status des Importvorgangs. Folgende Werte sind möglich:<br /><br /> **0**geben Sie an, um anzuzeigen, dass der Datensatz für den Stagingprozess bereit ist.<br /><br /> **1**: wird automatisch zugewiesen und gibt an, dass der Stagingprozess für den Datensatz erfolgreich war.<br /><br /> **2**: wird automatisch zugewiesen, und gibt an, dass der Stagingprozess für den Datensatz nicht erfolgreich war.|  
|**Batch_ID**<br /><br /> Wird nur vom Webdienst benötigt|Ein automatisch zugewiesener Bezeichner, der Datensätze für das Staging gruppiert. Alle Elemente im Batch werden diesem Bezeichner zugewiesen, der in der [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] -Benutzeroberfläche in der **ID** -Spalte angezeigt wird.<br /><br /> Wenn der Batch nicht verarbeitet wurde, ist dieses Feld leer.|  
|**BatchTag**<br /><br /> Erforderlich, außer vom Webdienst|Ein eindeutiger Name für den Batch (bis zu 50 Zeichen).|  
|**HierarchyName**<br /><br /> Required|Der explizite Name der Hierarchie. Jedes konsolidierte Element kann nur einer Hierarchie angehören.|  
|**ParentCode**<br /><br /> Required|Für über- und untergeordnete Beziehungen der Code für das konsolidierte Element, das als übergeordnetes Element des untergeordneten Blattes oder konsolidierten Elements fungiert.<br /><br /> Für gleichgeordnete Beziehungen der Code für eines der gleichgeordneten Elemente.|  
|**ChildCode**<br /><br /> Required|Für über- und untergeordnete Beziehungen der Code für das konsolidierte Element oder Blattelement, das als untergeordnetes Element fungiert.<br /><br /> Für gleichgeordnete Beziehungen der Code für eines der gleichgeordneten Elemente.|  
|**Sortierreihenfolge**<br /><br /> Optional|Eine ganze Zahl, die die Reihenfolge des Elements im Verhältnis zu den anderen Elementen unter dem übergeordneten Element angibt. Jedes untergeordnete Element sollte über einen eindeutigen Bezeichner verfügen.|  
|**ErrorCode**|Zeigt einen Fehlercode an. Informationen zu Datensätzen mit einer **ImportStatus_ID** von **2**, finden Sie unter [Staging Process Errors &#40;Master Data Services&#41;](staging-process-errors-master-data-services.md).|  
  
## <a name="see-also"></a>Siehe auch  
 [Verschieben von expliziten Hierarchieelementen mithilfe des Stagingprozesses &#40;Master Data Services&#41;](/sql/2014/master-data-services/add-update-and-delete-data-master-data-services)   
 [Datenimport &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md)   
 [Anzeigen von Fehlern, die während des Stagingprozesses auftreten &#40;Master Data Services&#41;](view-errors-that-occur-during-staging-master-data-services.md)   
 [Stagingfehler Prozess &#40;Master Data Services&#41;](staging-process-errors-master-data-services.md)  
  
  
