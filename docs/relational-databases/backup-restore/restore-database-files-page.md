---
title: Datenbank wiederherstellen (Seite „Dateien“) | Microsoft-Dokumentation
description: Verwenden Sie bei der Wiederherstellung einer Datenbank in SQL Server die Seite „Dateien“ des Dialogfelds „Datenbank wiederherstellen“, um spezifische zu wiederherstellende Dateien innerhalb der Datenbank zu verwalten.
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql13.swb.restoredb.files.f1
- sql13.swb.restoredb.files.f1 in the code
ms.assetid: 714c36ea-a9f9-43a4-99f9-a6f73d1baf8e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ab1cedc6960052ec8a9007b72d9062b8fc818ab7
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85737724"
---
# <a name="restore-database-files-page"></a>Datenbank wiederherstellen (Seite Dateien)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Auf der Seite **Dateien** des Dialogfelds **Datenbank wiederherstellen** können Sie die Dateien verwalten, die Sie für die Wiederherstellung in der Datenbank ausgewählt haben.  
  
## <a name="options"></a>Tastatur  
  
### <a name="restore-database-files-as"></a>Datenbankdateien wiederherstellen als  
 Mit dieser Option weisen Sie den wiederhergestellten Dateien den neuen Dateipfad zu und verwalten den Pfad.  
  
 **Alle Dateien verschieben in Ordner**  
 Wiederhergestellte Dateien werden verschoben.  
  
|Option|BESCHREIBUNG|  
|------------|-----------------|  
|**Datendateiordner**|Geben Sie den Namen des Datendateiordners ein, in den die wiederhergestellten Datendateien verschoben werden sollen, oder navigieren Sie zu diesem.|  
|**Protokolldateiordner**|Geben Sie den Ordner mit den Protokolldateien ein, in den die wiederhergestellte Protokolldatei verschoben werden soll, oder navigieren Sie zu diesem.|  
  
 **Logischer Dateiname**  
 Zeigt eine Zeile für jede wiederherzustellende Datenbankdatei an.  
  
 **Dateityp**  
 Zeigt den Dateityp an.  
  
 **Originaldateiname**  
 Zeigt den ursprünglichen Dateipfad für die wiederhergestellte Datei an.  
  
 **Wiederherstellen als**  
 Die Dateinamen werden aufgeführt, unter denen die wiederhergestellten Dateien gespeichert werden sollen. Geben Sie den richtigen Dateinamen ein, oder suchen Sie nach diesem.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank wiederherstellen &#40;Seite „Allgemein“&#41;](../../relational-databases/backup-restore/restore-database-general-page.md)   
 [Datenbank wiederherstellen &#40;Seite „Optionen“&#41;](../../relational-databases/backup-restore/restore-database-options-page.md)   
 [RESTORE-Argumente &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-arguments-transact-sql.md)   
 [Definieren eines logischen Sicherungsmediums für ein Bandlaufwerk &#40;SQL Server&#41;](../../relational-databases/backup-restore/define-a-logical-backup-device-for-a-tape-drive-sql-server.md)   
 [RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md)  
  
  
