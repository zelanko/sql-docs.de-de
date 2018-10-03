---
title: Refresh from Database (MySQLToSQL)) aktualisieren | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 59a6db8f-2db6-4071-9005-928a7231de92
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 690d12a2f5f397256760c1c0cf5e2ee954d90843
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47746438"
---
# <a name="refresh-from-database-mysqltosql"></a>Aktualisieren der Datenbank (MySqlToSql)
Die **Refresh from Database aktualisieren** Dialogfeld können Sie auswählen, welche Objekte aus der MySQL-Datenbank zu aktualisieren. Zeilen in das Dialogfeld sind farbcodiert, abhängig vom Status der Metadaten:  
  
-   Wenn die Metadaten des Objekts lokal und in der MySQL-Datenbank geändert hat, ist die Zeile blau.  
  
-   Wenn die Metadaten des Objekts in der MySQL-Datenbank aber nicht in SSMA geändert hat, ist die Zeile gelb.  
  
-   Wenn die Metadaten des Objekts wurde lokal geändert, aber nicht in der MySQL-Datenbank, die Zeile grün angezeigt wird.  
  
-   Wenn das Objekt in der MySQL-Datenbank neu ist, ist die Zeile rosa.  
  
Sie können angeben, Einstellungen für die Aktualisierung von Standard-Objekt in der **Projekteinstellungen** Dialogfeld. Weitere Informationen finden Sie unter [Projekteinstellungen &#40;Synchronisierung&#41; &#40;MySQLToSQL&#41;](../../ssma/mysql/project-settings-synchronization-mysqltosql.md)  
  
Für den Zugriff auf die **Refresh from Database aktualisieren** mit der rechten Maustaste ein Objekt in der MySQL-Metadaten-Explorer, und klicken Sie im Dialogfeld **Refresh from Database aktualisieren**.  
  
## <a name="options"></a>Tastatur  
  
|||  
|-|-|  
|**Begriff**|**Definition**|  
|**Reduzieren (-)**|Alle Objektgruppen zum Ausblenden von einzelnen Objekten zu reduzieren.|  
|**Erweitern (+)**|Erweitern Sie alle Objektgruppen, um einzelne Objekte anzuzeigen.|  
|**Gleiche Objekte ein-/ausblenden**|Objekte aus der Liste wird ausgeblendet, wenn die Metadaten des Objekts in der MySQL-Datenbank und in SSMA ist.|  
|**Refresh from Database (Pfeilschaltfläche) aktualisieren**|Verwenden Sie die Pfeiltaste klicken, um anzugeben, dass die Metadaten für die ausgewählten Objekte in SSMA aktualisiert werden sollen.|  
|**Aus Datenbank werden nicht aktualisiert werden (X-Schaltfläche)**|Verwenden Sie die X-Schaltfläche, um anzugeben, dass die Metadaten für die ausgewählten Objekte nicht soll, können Sie in der SSMA aktualisiert werden.|  
|**Legende**|Zeigt eine **Legende** Dialogfeld. Die Legende enthält die Zuordnung zwischen Zeilenfarben und Metadaten-Status.<br /><br />Zu den **Legende** im Dialogfeld auf der Basis von der **aus Datenbank aktualisieren** wählen Sie im Dialogfeld die **oben anzeigen** Kontrollkästchen.|  
  
