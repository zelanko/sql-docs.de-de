---
title: RESTORE-Anweisungen für das Wiederherstellen und Verwalten von Sicherungen (T-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/30/2018
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- restoring files [SQL Server], RESTORE statement
- RESTORE statement, about restore operations
- database restores [SQL Server], RESTORE statement
- restoring databases [SQL Server], RESTORE statement
- database backups [SQL Server], RESTORE statement
- backing up databases [SQL Server], RESTORE statement
- file restores [SQL Server], RESTORE statement
- transaction log backups [SQL Server], RESTORE statement
ms.assetid: fb29a151-f312-4f85-b857-5deeca0de8ce
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: d094b8540609810d134c52fb5755b21db4fc0f6b
ms.sourcegitcommit: 83f061304fedbc2801d8d6a44094ccda97fdb576
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/20/2019
ms.locfileid: "65947113"
---
# <a name="restore-statements-for-restoring-recovering-and-managing-backups-transact-sql"></a>RESTORE-Anweisungen für das Wiederherstellen und Verwalten von Sicherungen (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdbmi-xxxx-xxx-md.md )]

  In diesem Abschnitt werden die RESTORE-Anweisungen für Sicherungen beschrieben. Neben der RESTORE {DATABASE | LOG}-Hauptanweisung für das Wiederherstellen von Sicherungen unterstützen eine Reihe von RESTORE-Hilfsanweisungen Sie beim Verwalten von Sicherungen und Planen von Wiederherstellungssequenzen. Zu den RESTORE-Hilfsbefehlen gehören: RESTORE FILELISTONLY, RESTORE HEADERONLY, RESTORE LABELONLY, RESTORE REWINDONLY und RESTORE VERIFYONLY.  
  
> [!IMPORTANT]  
>  In früheren Versionen von SQL Server konnte jeder Benutzer mit den Transact-SQL-Anweisungen RESTORE FILELISTONLY, RESTORE HEADERONLY, RESTORE LABELONLY und RESTORE VERIFYONLY Informationen zu Sicherungssätzen und Sicherungsgeräten erhalten. Da diese Anweisungen jedoch Informationen zum Inhalt der Sicherungsdateien zurückgeben, erfordern sie in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] und späteren Versionen die CREATE DATABASE-Berechtigung. Dadurch werden Ihre Sicherungsdateien und Sicherungsinformationen umfassender geschützt als in vorherigen Versionen. Informationen über diese Berechtigung finden Sie unter [GRANT (Datenbankberechtigungen) &#40;Transact-SQL&#41;](../../t-sql/statements/grant-database-permissions-transact-sql.md).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|-Anweisung.|und Beschreibung|  
|---------------|-----------------|  
|[RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md)|Beschreibt die Transact-SQL-Anweisungen RESTORE DATABASE und RESTORE LOG, die für die Wiederherstellung einer Datenbank mithilfe von mit dem BACKUP-Befehl erstellten Sicherungen verwendet werden. RESTORE DATABASE wird für Datenbanken unter allen Wiederherstellungsmodellen verwendet. RESTORE LOG wird nur unter dem vollständigen und dem massenprotokollierten Wiederherstellungsmodell verwendet. Mithilfe von RESTORE DATABASE kann außerdem eine Datenbank mit einer Datenbankmomentaufnahme wiederhergestellt werden.|  
|[RESTORE-Argumente &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-arguments-transact-sql.md)|Dokumentiert die Argumente, die in den Abschnitten "Syntax" der RESTORE-Anweisung beschrieben werden, sowie die der zugeordneten Gruppe von Hilfsanweisungen: RESTORE FILELISTONLY, RESTORE HEADERONLY, RESTORE LABELONLY, RESTORE REWINDONLY und RESTORE VERIFYONLY. Die meisten der Argumente werden nur von einer Untermenge dieser sechs Anweisungen unterstützt. Die Unterstützung für jedes Argument wird in der Beschreibung des Arguments angezeigt.|  
|[RESTORE FILELISTONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-filelistonly-transact-sql.md)|Beschreibt die Transact-SQL-Anweisung RESTORE FILELISTONLY, mit deren Hilfe ein Resultset zurückgegeben wird, das eine Liste der in dem Sicherungssatz enthaltenen Datenbank- und Protokolldateien enthält.|  
|[RESTORE HEADERONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-headeronly-transact-sql.md)|Beschreibt die Transact-SQL-Anweisung RESTORE HEADERONLY, mit deren Hilfe ein Resultset zurückgegeben wird, das die gesamten Sicherungsheaderinformationen für alle Sicherungssätze auf einem bestimmten Sicherungsmedium enthält.|  
|[RESTORE LABELONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-labelonly-transact-sql.md)|Beschreibt die Transact-SQL-Anweisung RESTORE LABELONLY, mit deren Hilfe ein Resultset zurückgegeben wird, das Informationen über die durch das Sicherungsmedium identifizierten Sicherungsmedien enthält.|  
|[RESTORE REWINDONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-rewindonly-transact-sql.md)|Beschreibt die Transact-SQL-Anweisung RESTORE REWINDONLY, mit deren Hilfe Bandmedien, die nach dem Ausführen der Anweisungen BACKUP oder RESTORE mit der NOREWIND-Option geöffnet blieben, zurückgespult und geschlossen werden.|  
|[RESTORE VERIFYONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-verifyonly-transact-sql.md)|Beschreibt die Transact-SQL-Anweisung RESTORE VERIFYONLY, mit deren Hilfe die Sicherung überprüft, aber nicht wiederhergestellt wird. Außerdem wird überprüft, ob der Sicherungssatz vollständig ist und die gesamte Sicherung gelesen werden kann. Diese Anweisung versucht nicht, die Struktur der Daten zu überprüfen.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sichern und Wiederherstellen von SQL Server-Datenbanken](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)  
  
  
