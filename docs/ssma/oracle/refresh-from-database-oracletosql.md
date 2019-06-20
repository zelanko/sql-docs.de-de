---
title: Refresh from Database (OracleToSQL) aktualisieren | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 84492f44-c368-4c75-954d-7307a2d2bbc0
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: decc6e25cc8480dfaf041a79baa0972bdd78e569
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62625860"
---
# <a name="refresh-from-database-oracletosql"></a>Aktualisieren der Datenbank (OracleToSQL)
Die **Refresh from Database aktualisieren** Dialogfeld können Sie auswählen, welche Objekte aus der Oracle-Datenbank zu aktualisieren. Zeilen in das Dialogfeld sind farbcodiert, abhängig vom Status der Metadaten:  
  
-   Wenn die Metadaten des Objekts lokal und in der Oracle-Datenbank geändert hat, ist die Zeile blau.  
  
-   Wenn die Metadaten des Objekts in der Oracle-Datenbank aber nicht in SSMA geändert hat, ist die Zeile gelb.  
  
-   Wenn die Metadaten des Objekts wurde lokal geändert, aber nicht in der Oracle-Datenbank, die Zeile grün ist.  
  
-   Wenn das Objekt in der Oracle-Datenbank neu ist, ist die Zeile rosa.  
  
Sie können angeben, Einstellungen für die Aktualisierung von Standard-Objekt in der **Projekteinstellungen** Dialogfeld. Weitere Informationen finden Sie unter [Projekteinstellungen&#40;Synchronisierung&#41; &#40;OracleToSQL&#41;](../../ssma/oracle/project-settings-synchronization-oracletosql.md).  
  
Für den Zugriff auf die **Refresh from Database aktualisieren** mit der rechten Maustaste ein Objekt in der Oracle-Metadaten-Explorer, und klicken Sie im Dialogfeld **Refresh from Database aktualisieren**.  
  
## <a name="options"></a>Optionen  
**Reduzieren (-)**  
Alle Objektgruppen zum Ausblenden von einzelnen Objekten zu reduzieren.  
  
**Erweitern (+)**  
Erweitern Sie alle Objektgruppen, um einzelne Objekte anzuzeigen.  
  
**Gleiche Objekte ein-/ausblenden**  
Objekte aus der Liste wird ausgeblendet, wenn die Metadaten des Objekts in der Oracle-Datenbank und in SSMA ist.  
  
**Refresh from Database (Pfeilschaltfläche) aktualisieren**  
Verwenden Sie die Pfeiltaste klicken, um anzugeben, dass die Metadaten für die ausgewählten Objekte in SSMA aktualisiert werden sollen.  
  
**Aus Datenbank werden nicht aktualisiert werden (X-Schaltfläche)**  
Verwenden Sie die X-Schaltfläche, um anzugeben, dass die Metadaten für die ausgewählten Objekte nicht soll, können Sie in der SSMA aktualisiert werden.  
  
**Legende**  
Zeigt eine **Legende** Dialogfeld. Die Legende enthält die Zuordnung zwischen Zeilenfarben und Metadaten-Status.  
  
Zu den **Legende** im Dialogfeld auf der Basis von der **aus Datenbank aktualisieren** wählen Sie im Dialogfeld die **oben anzeigen** Kontrollkästchen.  
  
