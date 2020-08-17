---
description: Aktualisieren der Datenbank (OracleToSQL)
title: Aktualisieren aus der Datenbank (oracletosql) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 84492f44-c368-4c75-954d-7307a2d2bbc0
author: nahk-ivanov
ms.author: alexiva
manager: alexiva
ms.openlocfilehash: 66bb67e64f3b95b78cdcf78d84145df25a02d4b2
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88320176"
---
# <a name="refresh-from-database-oracletosql"></a>Aktualisieren der Datenbank (OracleToSQL)
Im Dialogfeld **aus Datenbank aktualisieren** können Sie auswählen, welche Objekte aus der Oracle-Datenbank aktualisiert werden sollen. Zeilen im Dialogfeld sind basierend auf dem Status der Metadaten farblich codiert:  
  
-   Wenn die Objekt Metadaten lokal und in der Oracle-Datenbank geändert wurden, ist die Zeile blau.  
  
-   Wenn sich die Objekt Metadaten in der Oracle-Datenbank, aber nicht in SSMA geändert haben, wird die Zeile gelb angezeigt.  
  
-   Wenn sich die Objekt Metadaten lokal geändert haben, aber nicht in der Oracle-Datenbank, ist die Zeile grün.  
  
-   Wenn das Objekt in der Oracle-Datenbank neu ist, ist die Zeile Rosa.  
  
Sie können im Dialogfeld **Projekteinstellungen** die Standardeinstellungen für die Objekt Aktualisierung angeben. Weitere Informationen finden Sie unter [Project Settings&#40;Synchronisierung&#41; &#40;oracleto SQL&#41;](../../ssma/oracle/project-settings-synchronization-oracletosql.md).  
  
Um auf das Dialogfeld **aus Datenbank aktualisieren** zuzugreifen, klicken Sie mit der rechten Maustaste auf ein Objekt im Oracle Metadata Explorer, und klicken Sie dann auf **aus Datenbank aktualisieren**.  
  
## <a name="options"></a>Tastatur  
**Reduzieren (-)**  
Reduzieren Sie alle Objektgruppen, um einzelne Objekte auszublenden.  
  
**Erweitern (+)**  
Erweitern Sie alle Objektgruppen, um einzelne Objekte anzuzeigen.  
  
**Gleichwertige Objekte ausblenden/anzeigen**  
Blendet Objekte aus der Liste aus, wenn die Objekt Metadaten in der Oracle-Datenbank und in SSMA identisch sind.  
  
**Aktualisieren aus der Datenbank (Pfeil Schaltfläche)**  
Verwenden Sie die Pfeil Schaltfläche, um anzugeben, dass die Metadaten für die ausgewählten Objekte in SSMA aktualisiert werden sollen.  
  
**Nicht aus Datenbank aktualisieren (X-Schaltfläche)**  
Verwenden Sie die Schaltfläche X, um anzugeben, dass die Metadaten für die ausgewählten Objekte in SSMA nicht aktualisiert werden sollen.  
  
**Legende**  
Zeigt ein Dialogfeld für die **Legende** an. Die Legende enthält die Zuordnung zwischen Zeilen Farben und metadatenzuständen.  
  
Aktivieren Sie das Kontrollkästchen **am Anfang anzeigen** , um das Dialogfeld **Legende** oben im Dialogfeld **aus Datenbank aktualisieren** beizubehalten.  
  
