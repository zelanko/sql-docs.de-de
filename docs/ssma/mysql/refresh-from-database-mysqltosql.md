---
title: Aktualisieren aus der Datenbank (mysqltosql) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 59a6db8f-2db6-4071-9005-928a7231de92
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 5acc3153d7305f404c5fc6a0478b83cc0c98bad6
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68066703"
---
# <a name="refresh-from-database-mysqltosql"></a>Aktualisieren der Datenbank (MySqlToSql)
Im Dialogfeld **aus Datenbank aktualisieren** können Sie auswählen, welche Objekte aus der MySQL-Datenbank aktualisiert werden sollen. Zeilen im Dialogfeld sind basierend auf dem Status der Metadaten farblich codiert:  
  
-   Wenn die Objekt Metadaten lokal und in der MySQL-Datenbank geändert wurden, ist die Zeile blau.  
  
-   Wenn sich die Objekt Metadaten in der MySQL-Datenbank, aber nicht in SSMA geändert haben, wird die Zeile gelb angezeigt.  
  
-   Wenn sich die Objekt Metadaten lokal geändert haben, aber nicht in der MySQL-Datenbank, wird die Zeile grün angezeigt.  
  
-   Wenn das Objekt in der MySQL-Datenbank neu ist, ist die Zeile Rosa.  
  
Sie können im Dialogfeld **Projekteinstellungen** die Standardeinstellungen für die Objekt Aktualisierung angeben. Weitere Informationen finden Sie unter [Project Settings &#40;Synchronisierung&#41; &#40;mysqldesql&#41;](../../ssma/mysql/project-settings-synchronization-mysqltosql.md)  
  
Um auf das Dialogfeld **aus Datenbank aktualisieren** zuzugreifen, klicken Sie mit der rechten Maustaste auf ein Objekt im MySQL-metadatenexplorer, und klicken Sie auf **aus Datenbank aktualisieren**  
  
## <a name="options"></a>Optionen  
  
|||  
|-|-|  
|**Begriff**|**Definition**|  
|**Reduzieren (-)**|Reduzieren Sie alle Objektgruppen, um einzelne Objekte auszublenden.|  
|**Erweitern (+)**|Erweitern Sie alle Objektgruppen, um einzelne Objekte anzuzeigen.|  
|**Gleichwertige Objekte ausblenden/anzeigen**|Blendet Objekte aus der Liste aus, wenn die Objekt Metadaten in der MySQL-Datenbank und in SSMA identisch sind.|  
|**Aktualisieren aus der Datenbank (Pfeil Schaltfläche)**|Verwenden Sie die Pfeil Schaltfläche, um anzugeben, dass die Metadaten für die ausgewählten Objekte in SSMA aktualisiert werden sollen.|  
|**Nicht aus Datenbank aktualisieren (X-Schaltfläche)**|Verwenden Sie die Schaltfläche X, um anzugeben, dass die Metadaten für die ausgewählten Objekte in SSMA nicht aktualisiert werden sollen.|  
|**Legende**|Zeigt ein Dialogfeld für die **Legende** an. Die Legende enthält die Zuordnung zwischen Zeilen Farben und metadatenzuständen.<br /><br />Aktivieren Sie das Kontrollkästchen **am Anfang anzeigen** , um das Dialogfeld **Legende** oben im Dialogfeld **aus Datenbank aktualisieren** beizubehalten.|  
  
