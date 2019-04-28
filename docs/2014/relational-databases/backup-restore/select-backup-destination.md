---
title: Sicherungsziel auswählen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.selectbackupdest.f1
ms.assetid: f79e824b-1525-45de-8ede-513563af41b6
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: d9b4a0e07f32e074ff7e8875c263615bcebc12d1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62874879"
---
# <a name="select-backup-destination"></a>Sicherungsziel auswählen
  Wählen Sie im Dialogfeld **Sicherungsziel auswählen** ein Gerät als Sicherungsziel aus. Ein Sicherungsziel kann entweder ein Datenträger oder ein logisches Sicherungsmedium sein.  
  
 **So verwenden Sie SQL Server Management Studio zum Sichern einer Datenbank**  
  
-   [Erstellen einer vollständigen Datenbanksicherung &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md)  
  
-   [Erstellen einer differenziellen Datenbanksicherung &#40;SQL Server&#41;](create-a-differential-database-backup-sql-server.md)  
  
-   [Sichern von Dateien und Dateigruppen &#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md)  
  
-   [Sichern eines Transaktionsprotokolls &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md)  
  
## <a name="options"></a>Optionen  
 Die Optionen in diesem Dialogfeld sind davon abhängig, ob Sie ein Ziel auf einem Datenträger oder einem Band auswählen.  
  
 **Ziele auf dem Datenträger**  
 Zum Angeben eines Sicherungsziels wählen Sie eine der folgenden Optionen aus.  
  
|||  
|-|-|  
|**Dateiname**|Wählen Sie diese Option aus, um eine lokale Datei oder Remotedatei als Sicherungsziel im Textfeld einzugeben.<br /><br /> Klicken Sie zum Angeben einer lokalen Datei rechts vom Textfeld auf die Schaltfläche zum Durchsuchen, und wählen Sie dann auf den Festplatten des Computers, auf dem der Server ausgeführt wird, eine Datei aus. Sie können auch den vollständigen Pfad und Dateinamen direkt eingeben, z. B. `C:\Program Files\Microsoft SQL Server\MSSQL\Backup\AdventureWorksBackup.bak`.<br /><br /> Zum Angeben einer Remotedatei als Sicherungsziel geben Sie ihren vollqualifizierten UNC-Namen (Universal Naming Convention) ein. Weitere Informationen finden Sie unter [Sicherungsmedien &#40;SQL Server&#41;](backup-devices-sql-server.md)aufgezeichnet wurde.<br /><br /> **\*\* Wichtig \*\*** Beim Sichern von Daten über ein Netzwerk können Netzwerkfehler auftreten. Aus diesem Grund wird empfohlen, dass Sie den Sicherungsvorgang nach der Fertigstellung überprüfen. Weitere Informationen finden Sie unter [RESTORE VERIFYONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql).|  
|**Sicherungsmedium**|Wählen Sie diese Option aus, um ein logisches Sicherungsmedium auszuwählen.<br /><br /> Hinweis: Informationen zum Erstellen eines datenträgersicherungsmediums finden Sie unter [Definieren eines logischen Sicherungsmediums für eine Datenträgerdatei &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-disk-file-sql-server.md).|  
  
 **Ziele auf Band**  
 Gibt ein Sicherungsziel auf einem Bandlaufwerk an, das physisch mit dem Computer verbunden ist, auf dem der Server ausgeführt wird (d. h. die Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)]). Wählen Sie eine der folgenden Optionen.  
  
|||  
|-|-|  
|**Bandlaufwerk**|Wählen Sie diese Option aus, um ein Bandlaufwerk als Sicherungsziel aus der Liste der Bandlaufwerke auszuwählen, die physisch mit dem Computer verbunden sind, auf dem die Serverinstanz ausgeführt wird.<br /><br /> Hinweis: Bandsicherungsmedien auf Remotecomputern sind keine gültigen Sicherungsziele.|  
|**Sicherungsmedium**|Wählen Sie diese Option aus, um ein vorhandenes logisches Sicherungsmedium auszuwählen. Diese logischen Sicherungsmedien entsprechen Bandgeräten, die physisch mit dem Computer verbunden sind, auf dem die Serverinstanz ausgeführt wird.<br /><br /> Hinweis: Informationen zum Erstellen eines Bandsicherungsmediums finden Sie unter [Definieren eines logischen Sicherungsmediums für ein Bandlaufwerk &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-tape-drive-sql-server.md).|  
  
## <a name="see-also"></a>Siehe auch  
 [Sicherungsmedien &#40;SQL Server&#41;](backup-devices-sql-server.md)   
 [Mediensätze, Medienfamilien und Sicherungssätze &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md)  
  
  
