---
title: Aktualisieren aus der Datenbank (DB2ToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 613a8368-b372-443f-8252-fb6dc31a003d
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: a53c3005aca2e599d8ceb0b973a58bcf2ca5e14c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68060132"
---
# <a name="refresh-from-database-db2tosql"></a>Aktualisieren aus der Datenbank (DB2ToSQL)
Im Dialogfeld **aus Datenbank aktualisieren** können Sie auswählen, welche Objekte aus der DB2-Datenbank aktualisiert werden sollen. Zeilen im Dialogfeld sind basierend auf dem Status der Metadaten farblich codiert:  
  
-   Wenn die Objekt Metadaten lokal und in der DB2-Datenbank geändert wurden, ist die Zeile blau.  
  
-   Wenn sich die Objekt Metadaten in der DB2-Datenbank, aber nicht in SSMA geändert haben, wird die Zeile gelb angezeigt.  
  
-   Wenn sich die Objekt Metadaten lokal geändert haben, aber nicht in der DB2-Datenbank, wird die Zeile grün angezeigt.  
  
-   Wenn das Objekt in der DB2-Datenbank neu ist, ist die Zeile Rosa.  
  
Sie können im Dialogfeld **Projekteinstellungen** die Standardeinstellungen für die Objekt Aktualisierung angeben. Weitere Informationen finden Sie unter [Project Settings&#40;Synchronisierung&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-synchronization-db2tosql.md).  
  
Um auf das Dialogfeld **aus Datenbank aktualisieren** zuzugreifen, klicken Sie mit der rechten Maustaste auf ein Objekt im DB2 Metadata Explorer, und klicken Sie auf **aus Datenbank aktualisieren**.  
  
## <a name="options"></a>Tastatur  
**Reduzieren (-)**  
Reduzieren Sie alle Objektgruppen, um einzelne Objekte auszublenden.  
  
**Erweitern (+)**  
Erweitern Sie alle Objektgruppen, um einzelne Objekte anzuzeigen.  
  
**Gleichwertige Objekte ausblenden/anzeigen**  
Blendet Objekte aus der Liste aus, wenn die Objekt Metadaten in der DB2-Datenbank und in SSMA identisch sind.  
  
**Aktualisieren aus der Datenbank (Pfeil Schaltfläche)**  
Verwenden Sie die Pfeil Schaltfläche, um anzugeben, dass die Metadaten für die ausgewählten Objekte in SSMA aktualisiert werden sollen.  
  
**Nicht aus Datenbank aktualisieren (X-Schaltfläche)**  
Verwenden Sie die Schaltfläche X, um anzugeben, dass die Metadaten für die ausgewählten Objekte in SSMA nicht aktualisiert werden sollen.  
  
**Legende**  
Zeigt ein Dialogfeld für die **Legende** an. Die Legende enthält die Zuordnung zwischen Zeilen Farben und metadatenzuständen.  
  
Aktivieren Sie das Kontrollkästchen **am Anfang anzeigen** , um das Dialogfeld **Legende** oben im Dialogfeld **aus Datenbank aktualisieren** beizubehalten.  
  
