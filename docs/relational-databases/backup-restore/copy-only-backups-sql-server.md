---
title: Kopiesicherungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/30/2019
ms.prod: sql
ms.prod_service: backup-restore
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
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 1d95c1982d5809288b64f34cd1f6328b4ee00e4c
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "76941034"
---
# <a name="copy-only-backups"></a>Kopiesicherungen
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

Eine *Kopiesicherung* ist eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Sicherung, die unabhängig von der Sequenz von herkömmlichen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Sicherungen erstellt wird. Normalerweise wird beim Erstellen einer Sicherung die Datenbank geändert, und außerdem beeinflusst dies die Art und Weise, wie spätere Sicherungen wiederhergestellt werden. Manchmal kann es sich jedoch als nützlich erweisen, eine Datensicherung für einen bestimmten Zweck vorzunehmen, ohne die allgemeinen Sicherungs- und Wiederherstellungsprozeduren für die Datenbank zu beeinflussen. Kopiesicherungen eignen sich für diesen Zweck.
  
 Die folgenden Typen von Kopiesicherungen sind verfügbar:  
  
- Vollständige Kopiesicherungen (alle Wiederherstellungsmodelle)  
  
     Eine Kopiesicherung kann nicht als differenzielle Basis oder differenzielle Sicherung dienen und wirkt sich nicht auf die differenzielle Basis aus.  
  
     Die Wiederherstellung einer vollständigen Kopiesicherung entspricht der Wiederherstellung jeder anderen vollständigen Sicherung.  
  
- Protokollkopiesicherungen (nur vollständiges und massenprotokolliertes Wiederherstellungsmodell)  

     Eine Protokollkopiesicherung behält den vorhandenen Protokollarchivpunkt bei und wirkt sich daher nicht auf die Sequenz von regulären Protokollsicherungen aus. Protokollkopiesicherungen sind normalerweise nicht nötig. Erstellen Sie stattdessen eine neue routinemäßige Protokollsicherung (mithilfe von WITH NORECOVERY), und verwenden Sie dann diese Sicherung zusammen mit allen vorherigen Protokollsicherungen, die für die Wiederherstellungssequenz erforderlich sind. Eine Protokollkopiesicherung ist manchmal jedoch auch für das Ausführen einer Onlinewiederherstellung nützlich. Ein Beispiel dafür finden Sie unter [Beispiel: Onlinewiederherstellung einer Datei mit Lese-/Schreibzugriff &#40;vollständiges Wiederherstellungsmodell&#41;](../../relational-databases/backup-restore/example-online-restore-of-a-read-write-file-full-recovery-model.md).  

     Nach einer Kopiesicherung wird das Transaktionsprotokoll nie abgeschnitten.  
  
 Kopiesicherungen werden in der **is_copy_only** -Spalte der [backupset](../../relational-databases/system-tables/backupset-transact-sql.md) -Tabelle aufgezeichnet.  
 
 > [!IMPORTANT]  
> In verwalteten Azure-SQL-Datenbank-Instanzen kann keine Kopiesicherung für Datenbanken erstellt werden, die mit [TDE (Transparent Data Encryption) mit Verwaltung durch einen Dienst](https://docs.microsoft.com/azure/sql-database/transparent-data-encryption-azure-sql?tabs=azure-portal#service-managed-transparent-data-encryption) verschlüsselt sind. Bei TDE mit Verwaltung durch einen Dienst wird ein interner Schlüssel zum Verschlüsseln von Daten verwendet. Dieser Schlüssel kann nicht exportiert werden, weshalb Sie die Sicherung nicht woanders speichern können. Sie sollten stattdessen [TDE mit Verwaltung durch Kunden](https://docs.microsoft.com/azure/sql-database/transparent-data-encryption-byok-azure-sql) in Betracht ziehen, um Kopiesicherungen von verschlüsselten Datenbanken erstellen zu können, aber stellen Sie dabei sicher, dass Sie über einen Verschlüsselungsschlüssel für spätere Wiederherstellungen verfügen.
  
## <a name="to-create-a-copy-only-backup"></a>So erstellen Sie eine Kopiesicherung  
 Kopiesicherungen können mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]oder PowerShell erstellt werden.  

### <a name="examples"></a>Beispiele  
###  <a name="SSMSProcedure"></a> A. Verwendung von SQL Server Management Studio  
In diesem Beispiel wird eine Kopiesicherung der `Sales` -Datenbank auf dem Datenträger im standardmäßigen Sicherungsspeicherort gesichert.

1. Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer Instanz der SQL Server-Datenbank-Engine her, und erweitern Sie anschließend diese Instanz.

1. Erweitern Sie die **Datenbank**, klicken Sie mit der rechten Maustaste auf `Sales`,zeigen Sie auf **Tasks**, und klicken Sie anschließend auf **Sichern...** .

1. Aktivieren Sie auf der Seite **Allgemein** im Abschnitt **Quelle** das Kontrollkästchen **Kopiesicherung** .

1. Klicken Sie auf **OK**.

###  <a name="TsqlProcedure"></a>B. Verwenden von Transact-SQL  
In diesem Beispiel wird eine Kopiesicherung der `Sales` -Datenbank über den COPY_ONLY-Parameter erstellt.  Eine Kopiesicherung des Transaktionsprotokolls wird ebenfalls erstellt.

```sql
BACKUP DATABASE Sales
TO DISK = 'E:\BAK\Sales_Copy.bak'
WITH COPY_ONLY;

BACKUP LOG Sales
TO DISK = 'E:\BAK\Sales_LogCopy.trn'
WITH COPY_ONLY;
```
  
> [!NOTE]  
> COPY_ONLY ist wirkungslos, wenn gleichzeitig die Option DIFFERENTIAL angegeben wird.  

  
###  <a name="PowerShellProcedure"></a>C. PowerShell  
In diesem Beispiel wird eine Kopiesicherung der `Sales` -Datenbank über den -CopyOnly-Parameter erstellt.  
```powershell
Backup-SqlDatabase -ServerInstance 'SalesServer' -Database 'Sales' -BackupFile 'E:\BAK\Sales_Copy.bak' -CopyOnly
```  
  
##  <a name="RelatedTasks"></a> Verwandte Aufgaben  
 **So erstellen Sie eine vollständige oder Protokollsicherung**  
  
- [Erstellen einer vollständigen Datenbanksicherung &#40;SQL Server&#41;](../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)  
  
- [Sichern eines Transaktionsprotokolls &#40;SQL Server&#41;](../../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md)  

 **So zeigen Sie Kopiesicherungen an**  
  
- [backupset &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupset-transact-sql.md)  
  
 **Einrichten und Verwenden des SQL Server PowerShell-Anbieters**  
  
- [SQL Server PowerShell-Anbieter](../../relational-databases/scripting/sql-server-powershell-provider.md)  

## <a name="see-also"></a>Weitere Informationen  
 [Übersicht über Sicherungen &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-overview-sql-server.md)   
 [Wiederherstellungsmodelle &#40;SQL Server&#41;](../../relational-databases/backup-restore/recovery-models-sql-server.md)   
 [Kopieren von Datenbanken durch Sichern und Wiederherstellen](../../relational-databases/databases/copy-databases-with-backup-and-restore.md)   
 [Übersicht über Wiederherstellungsvorgänge &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-and-recovery-overview-sql-server.md)  
[BACKUP (Transact-SQL)](../../t-sql/statements/backup-transact-sql.md)  
[Backup-SqlDatabase](/powershell/module/sqlserver/backup-sqldatabase)

  
