---
title: Wiederherstellung fortsetzen | Microsoft-Dokumentation
description: Verwenden Sie in SQL Server das Dialogfeld Wiederherstellung fortsetzen, um anzugeben, ob der nächste Sicherungs Satz wieder hergestellt werden soll.
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.continuerestore.f1
ms.assetid: 987ac05f-57c0-49a9-9903-9889717aae4f
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: cd26a49b87615114b36c3fe57c7c6b50fbdbe7b0
ms.sourcegitcommit: 553d5b21bb4bf27e232b3af5cbdb80c3dcf24546
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/06/2020
ms.locfileid: "82849588"
---
# <a name="continue-with-restore"></a>Wiederherstellung fortsetzen
  Mithilfe des Dialogfelds **Wiederherstellung fortsetzen** können Sie angeben, ob der nächste Sicherungssatz wiederhergestellt werden soll. Zum Verzögern des Wiederherstellungsvorgangs, z. B. zum Wechseln von Bändern, klicken Sie erst dann auf **OK**, wenn der Vorgang fortgesetzt werden soll.  
  
 Wenn Sie auf **Nein** klicken, wird die Wiederherstellungssequenz beendet, und die Datenbank bleibt im Wiederherstellungsstatus. Verwenden Sie je nach Bedarf den Task **Datenbank wiederherstellen** oder **Transaktionsprotokoll wiederherstellen** , um die Wiederherstellung zu einem späteren Zeitpunkt fortzusetzen.  
  
## <a name="options"></a>Optionen  
 **Mediensatz**  
 Zeigt den Namen des nächsten Mediensatzes an (sofern verfügbar).  
  
 **Sicherungs Satz**  
 Zeigt den Namen des Sicherungssatzes an.  
  
 **Sicherungs Satz Beschreibung**  
 Zeigt eine Beschreibung des Sicherungssatzes an.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Anzeigen der Inhalte eines Sicherungsbands oder einer -datei &#40;SQL Server&#41;](../relational-databases/backup-restore/view-the-contents-of-a-backup-tape-or-file-sql-server.md)   
 [Anzeigen der Eigenschaften und des Inhalts eines logischen Sicherungsmediums &#40;SQL Server&#41;](../relational-databases/backup-restore/view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)   
 [Wiederherstellen einer Datenbanksicherung &#40;SQL Server Management Studio&#41;](../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md)   
 [Wiederherstellen einer Transaktionsprotokollsicherung &#40;SQL Server&#41;](../relational-databases/backup-restore/restore-a-transaction-log-backup-sql-server.md)  
  
  
