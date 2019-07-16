---
title: Refresh from Database (DB2ToSQL) aktualisieren | Microsoft-Dokumentation
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68060132"
---
# <a name="refresh-from-database-db2tosql"></a>Refresh from Database (DB2ToSQL) aktualisieren
Die **Refresh from Database aktualisieren** Dialogfeld können Sie auswählen, welche Objekte von der DB2-Datenbank zu aktualisieren. Zeilen in das Dialogfeld sind farbcodiert, abhängig vom Status der Metadaten:  
  
-   Wenn die Metadaten des Objekts lokal und in der DB2-Datenbank geändert hat, ist die Zeile blau.  
  
-   Wenn die Metadaten des Objekts in der DB2-Datenbank aber nicht in SSMA geändert hat, ist die Zeile gelb.  
  
-   Wenn die Metadaten des Objekts wurde lokal geändert, aber nicht in der DB2-Datenbank, die Zeile grün ist.  
  
-   Wenn das Objekt in der DB2-Datenbank neu ist, ist die Zeile rosa.  
  
Sie können angeben, Einstellungen für die Aktualisierung von Standard-Objekt in der **Projekteinstellungen** Dialogfeld. Weitere Informationen finden Sie unter [Projekteinstellungen&#40;Synchronisierung&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-synchronization-db2tosql.md).  
  
Für den Zugriff auf die **Refresh from Database aktualisieren** mit der rechten Maustaste ein Objekt in der DB2-Metadaten-Explorer, und klicken Sie im Dialogfeld **Refresh from Database aktualisieren**.  
  
## <a name="options"></a>Optionen  
**Reduzieren (-)**  
Alle Objektgruppen zum Ausblenden von einzelnen Objekten zu reduzieren.  
  
**Erweitern (+)**  
Erweitern Sie alle Objektgruppen, um einzelne Objekte anzuzeigen.  
  
**Gleiche Objekte ein-/ausblenden**  
Objekte aus der Liste wird ausgeblendet, wenn die Metadaten des Objekts in der DB2-Datenbank und in SSMA ist.  
  
**Refresh from Database (Pfeilschaltfläche) aktualisieren**  
Verwenden Sie die Pfeiltaste klicken, um anzugeben, dass die Metadaten für die ausgewählten Objekte in SSMA aktualisiert werden sollen.  
  
**Aus Datenbank werden nicht aktualisiert werden (X-Schaltfläche)**  
Verwenden Sie die X-Schaltfläche, um anzugeben, dass die Metadaten für die ausgewählten Objekte nicht soll, können Sie in der SSMA aktualisiert werden.  
  
**Legende**  
Zeigt eine **Legende** Dialogfeld. Die Legende enthält die Zuordnung zwischen Zeilenfarben und Metadaten-Status.  
  
Zu den **Legende** im Dialogfeld auf der Basis von der **aus Datenbank aktualisieren** wählen Sie im Dialogfeld die **oben anzeigen** Kontrollkästchen.  
  
