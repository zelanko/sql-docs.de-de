---
title: Kopiesicherungen (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- copy-only backups [SQL Server]
- COPY_ONLY option [BACKUP statement]
- backups [SQL Server], copy-only backups
ms.assetid: f82d6918-a5a7-4af8-868e-4247f5b00c52
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 96267b98d7e17b920e0a7cee70b69e4c964584e4
ms.sourcegitcommit: f912c101d2939084c4ea2e9881eb98e1afa29dad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2019
ms.locfileid: "72798005"
---
# <a name="copy-only-backups-sql-server"></a>Kopiesicherungen [SQL Server]
  Eine *Kopiesicherung* ist eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Sicherung, die unabhängig von der Sequenz herkömmlicher [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Sicherungen erstellt wird. Normalerweise wird beim Erstellen einer Sicherung die Datenbank geändert, und außerdem beeinflusst dies die Art und Weise, wie spätere Sicherungen wiederhergestellt werden. Manchmal kann es sich jedoch als nützlich erweisen, eine Datensicherung für einen bestimmten Zweck vorzunehmen, ohne die allgemeinen Sicherungs- und Wiederherstellungsprozeduren für die Datenbank zu beeinflussen. Kopiesicherungen eignen sich für diesen Zweck.  
  
 Die folgenden Typen von Kopiesicherungen sind verfügbar:  
  
-   Vollständige Kopiesicherungen (alle Wiederherstellungsmodelle)  
  
     Eine Kopiesicherung kann nicht als differenzielle Basis oder differenzielle Sicherung dienen und wirkt sich nicht auf die differenzielle Basis aus.  
  
     Die Wiederherstellung einer vollständigen Kopiesicherung entspricht der Wiederherstellung jeder anderen vollständigen Sicherung.  
  
-   Protokollkopiesicherungen (nur vollständiges und massenprotokolliertes Wiederherstellungsmodell)  
  
     Eine Protokollkopiesicherung behält den vorhandenen Protokollarchivpunkt bei und wirkt sich daher nicht auf die Sequenz von regulären Protokollsicherungen aus. Protokollkopiesicherungen sind normalerweise nicht nötig. Erstellen Sie stattdessen eine neue routinemäßige Protokollsicherung (mithilfe von WITH NORECOVERY), und verwenden Sie dann diese Sicherung zusammen mit allen vorherigen Protokollsicherungen, die für die Wiederherstellungssequenz erforderlich sind. Eine Protokollkopiesicherung ist manchmal jedoch auch für das Ausführen einer Onlinewiederherstellung nützlich. Siehe auch [Beispiel: Onlinewiederherstellung einer Datei mit Lese-/Schreibzugriff &#40;vollständiges Wiederherstellungsmodell&#41;](example-online-restore-of-a-read-write-file-full-recovery-model.md).  
  
     Nach einer Kopiesicherung wird das Transaktionsprotokoll nie abgeschnitten.  
  
 Kopiesicherungen werden in der **is_copy_only** -Spalte der [backupset](/sql/relational-databases/system-tables/backupset-transact-sql) -Tabelle aufgezeichnet.  
  
## <a name="to-create-a-copy-only-backup"></a>So erstellen Sie eine Kopiesicherung  
 Kopiesicherungen können mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)]oder PowerShell erstellt werden.  
  
###  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
1.  Wählen Sie im Dialogfeld **Datenbank sichern** auf der Seite **Allgemein** die Option **Kopiesicherung** aus.  
  
###  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 Die grundlegende [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Syntax lautet wie folgt:  
  
-   Für eine vollständige Kopiesicherung:  
  
     Backup Database *database_name* to \<backup_device*>* ... mit COPY_ONLY...  
  
    > [!NOTE]  
    >  COPY_ONLY ist wirkungslos, wenn gleichzeitig die Option DIFFERENTIAL angegeben wird.  
  
-   Für eine Protokollkopiesicherung:  
  
     Backup log *database_name* to *\<* backup_device*>* ... mit COPY_ONLY...  
  
###  <a name="PowerShellProcedure"></a> PowerShell  
  
Verwenden Sie das `Backup-SqlDatabase`-Cmdlet mit dem `-CopyOnly`-Parameter.  
  
##  <a name="RelatedTasks"></a> Verwandte Aufgaben  

### <a name="to-create-a-full-or-log-backup"></a>So erstellen Sie eine vollständige oder Protokollsicherung
  
-   [Erstellen einer vollständigen Datenbanksicherung &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md)  
  
-   [Sichern eines Transaktionsprotokolls &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md)  
  
### <a name="to-view-copy-only-backups"></a>So zeigen Sie Kopiesicherungen an
  
-   [backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql)  
  
### <a name="to-set-up-and-use-the-sql-server-powershell-provider"></a>Einrichten und Verwenden des SQL Server PowerShell-Anbieters
  
-   [SQL Server PowerShell-Anbieter](../../powershell/sql-server-powershell-provider.md)  

## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Übersicht über Sicherungen &#40;SQL Server&#41;](backup-overview-sql-server.md)   
 [Wiederherstellungsmodelle &#40;SQL Server&#41;](recovery-models-sql-server.md)   
 [Kopieren von Datenbanken durch Sichern und Wiederherstellen](../databases/copy-databases-with-backup-and-restore.md)   
 [Übersicht über Wiederherstellungsvorgänge &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md)  
