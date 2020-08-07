---
title: Aktualisieren aus der Datenbank (DB2ToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 613a8368-b372-443f-8252-fb6dc31a003d
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 2efc0667bd69e43cfe3d3246c0622fad18ff21e3
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2020
ms.locfileid: "87933361"
---
# <a name="refresh-from-database-db2tosql"></a>Aktualisieren aus der Datenbank (DB2ToSQL)
Im Dialogfeld **aus Datenbank aktualisieren** können Sie auswählen, welche Objekte aus der DB2-Datenbank aktualisiert werden sollen. Zeilen im Dialogfeld sind basierend auf dem Status der Metadaten farblich codiert:  
  
-   Wenn die Objekt Metadaten lokal und in der DB2-Datenbank geändert wurden, ist die Zeile blau.  
  
-   Wenn sich die Objekt Metadaten in der DB2-Datenbank, aber nicht in SSMA geändert haben, wird die Zeile gelb angezeigt.  
  
-   Wenn sich die Objekt Metadaten lokal geändert haben, aber nicht in der DB2-Datenbank, wird die Zeile grün angezeigt.  
  
-   Wenn das Objekt in der DB2-Datenbank neu ist, ist die Zeile Rosa.  
  
Sie können im Dialogfeld **Projekteinstellungen** die Standardeinstellungen für die Objekt Aktualisierung angeben. Weitere Informationen finden Sie unter [Project Settings&#40;Synchronisierung&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-synchronization-db2tosql.md).  
  
Um auf das Dialogfeld **aus Datenbank aktualisieren** zuzugreifen, klicken Sie mit der rechten Maustaste auf ein Objekt im DB2 Metadata Explorer, und klicken Sie auf **aus Datenbank aktualisieren**.  
  
## <a name="options"></a>Optionen  
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
  
