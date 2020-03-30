---
title: RESTORE REWINDONLY (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- RESTORE_REWINDONLY_TSQL
- RESTORE REWINDONLY
dev_langs:
- TSQL
helpviewer_keywords:
- closing backup devices
- backup devices [SQL Server], rewinding
- media [SQL Server]
- open back devices
- rewinding backup devices
- RESTORE REWINDONLY statement
ms.assetid: 7f825b40-2264-4608-9809-590d0f09d882
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0b70fdfc02e876310841bde3646aab9620c56951
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "68082498"
---
# <a name="restore-statements---rewindonly-transact-sql"></a>RESTORE-Anweisungen - REWINDONLY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Führt das Zurückspulen und Schließen der angegebenen Bandmedien aus, die durch mit der Option NOREWIND ausgeführte BACKUP- oder RESTORE-Anweisungen offen geblieben sind. Diese Option wird nur für Bandmedien verwendet.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
RESTORE REWINDONLY   
FROM <backup_device> [ ,...n ]  
[ WITH {UNLOAD | NOUNLOAD}]  
}   
[;]  
  
<backup_device> ::=  
{   
   { logical_backup_device_name |  
      @logical_backup_device_name_var }  
   | TAPE = { 'physical_backup_device_name' |  
       @physical_backup_device_name_var }   
}   
```  
  
## <a name="arguments"></a>Argumente  
 **\<backup_device> ::=** 
  
 Gibt das logische oder physische Sicherungsmedium an, das für den Wiederherstellungsvorgang verwendet wird.  
  
 { *logical_backup_device_name* |  **@** _logical\_backup\_device\_name\_var_ }  
 Dies ist der logische Name der von **sp_addumpdevice** erstellten Sicherungsmedien, von denen die Datenbank wiederhergestellt wird. Der Name muss den Regeln für Bezeichner entsprechen. Bei Angabe in Form einer Variablen ( **@** _logical\_backup\_device\_name\_var_) kann der Name des Sicherungsmediums entweder als Zeichenfolgenkonstante ( **@** _logical\_backup\_device\_name\_var_ = _logical\_backup\_device\_name_) oder als Variable eines Zeichenfolgen-Datentyps (mit Ausnahme der Datentypen **ntext** oder **text**) angegeben werden.  
  
 {DISK | TAPE } **=** { **'** _physical\_backup\_device\_name_ **'**  |  **@** _physical\_backup\_device\_name\_var_ }  
 Ermöglicht die Wiederherstellung von Sicherungen von den angegebenen Datenträgern- oder Bandmedien. Die Gerätetypen von Datenträgern und Bändern müssen durch die tatsächlichen Namen des Geräts angegeben werden (z.B. vollständiger Pfad und Dateiname): DISK = 'C:\Programme\Microsoft SQL Server\MSSQL\BACKUP\Mybackup.bak' oder TAPE = '\\\\.\TAPE0'. Bei Angabe in Form einer Variablen ( **@** _physical\_backup\_device\_name\_var_) kann der Gerätename entweder als Zeichenfolgenkonstante ( **@** _physical\_backup\_device\_name\_var_ = '*physical_backup_device_name*') oder als Variable eines Zeichenfolgen-Datentyps (mit Ausnahme der Datentypen **ntext** oder **text**) angegeben werden.  
  
 Wenn Sie einen Netzwerkserver mit einem UNC-Namen (der einen Computernamen enthalten muss) verwenden, geben Sie die Geräteart Datenträger (DISK) an. Weitere Informationen zum Verwenden von UNC-Namen finden Sie unter [Sicherungsmedien &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-devices-sql-server.md).  
  
 Das Konto, unter dem Sie Microsoft SQL Server ausführen, muss Lesezugriff auf den Remotecomputer oder Netzwerkserver besitzen, damit ein RESTORE-Vorgang ausgeführt werden kann.  
  
 *n*  
 Dies ist ein Platzhalter, der anzeigt, dass mehrere Sicherungsmedien und logische Sicherungsmedien angegeben werden können. Die maximale Anzahl von Sicherungsmedien oder logischen Sicherungsmedien beträgt **64**.  
  
 Ob für eine Wiederherstellungssequenz so viele Sicherungsmedien erforderlich sind, wie beim Erstellen des Mediensatzes verwendet wurden, zu dem die Sicherungen gehören, hängt davon ab, ob die Wiederherstellung offline oder online erfolgt. Bei der Offlinewiederherstellung kann eine Sicherung mit weniger Medien wiederhergestellt werden, als zum Erstellen der Sicherung erforderlich waren. Für eine Onlinewiederherstellung sind alle Sicherungsmedien der Sicherung erforderlich. Einer Wiederherstellungsversuch mit weniger Medien erzeugt einen Fehler.  
  
 Weitere Informationen finden Sie unter [Sicherungsmedien &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-devices-sql-server.md)aufgezeichnet wurde.  
  
> [!NOTE]  
>  Bei der Wiederherstellung einer Sicherung aus einem gespiegelten Mediensatz können Sie für jede Medienfamilie jeweils nur einen einzigen Spiegel angeben. Wenn Fehler auftreten, können jedoch mithilfe des oder der anderen Spiegel einige Wiederherstellungsprobleme schnell gelöst werden. Sie können ein beschädigtes Medienvolume durch das entsprechende Volume eines anderen Spiegels ersetzen. Beachten Sie, dass Sie bei einer Offlinewiederherstellung von weniger Medien als Medienfamilien wiederherstellen können, aber jede Familie wird nur einmal verarbeitet.  
  
 **WITH Options**  
  
 UNLOAD  
 Gibt an, dass das Band automatisch zurückgespult und ausgeworfen wird, wenn der RESTORE-Vorgang vollständig ausgeführt ist. UNLOAD wird standardmäßig festgelegt, wenn eine neue Benutzersitzung gestartet wird. Diese Option bleibt festgelegt, bis NOUNLOAD angegeben wird. Diese Option wird nur für Bandmedien verwendet. Die Option wird ignoriert, wenn ein anderes Medium als ein Bandlaufwerk für RESTORE verwendet wird.  
  
 NOUNLOAD  
 Gibt an, dass das Band nach einem RESTORE-Vorgang nicht automatisch aus dem Bandlaufwerk ausgeworfen wird. NOUNLOAD bleibt festgelegt, bis UNLOAD angegeben wird.  
  
## <a name="general-remarks"></a>Allgemeine Hinweise  
 RESTORE REWINDONLY ist eine Alternative zu RESTORE LABELONLY FROM TAPE = \<Name> WITH REWIND. Die dynamische Verwaltungssicht [sys.dm_io_backup_tapes](../../relational-databases/system-dynamic-management-views/sys-dm-io-backup-tapes-transact-sql.md) stellt eine Liste offener Bandlaufwerke bereit.  
  
## <a name="security"></a>Sicherheit  
  
### <a name="permissions"></a>Berechtigungen  
 Jeder Benutzer kann RESTORE REWINDONLY verwenden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md)   
 [Mediensätze, Medienfamilien und Sicherungssätze &#40;SQL Server&#41;](../../relational-databases/backup-restore/media-sets-media-families-and-backup-sets-sql-server.md)   
 [RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md)   
 [Sicherungsverlauf und Headerinformationen &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-history-and-header-information-sql-server.md)  
  
  

