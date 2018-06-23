---
title: FileTable-DDL, Funktionen, gespeicherte Prozeduren und Ansichten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-blob
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- FileTables [SQL Server], database objects
ms.assetid: 7e2e0f7f-94a8-4178-8bc7-d2e14ac8528c
caps.latest.revision: 12
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 0ff6be83b96817280fd09da5c17d7ee35e7be009
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36148150"
---
# <a name="filetable-ddl-functions-stored-procedures-and-views"></a>FileTable-DDL, Funktionen, gespeicherte Prozeduren und Sichten
  Listet die [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen und die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbankobjekte auf, die zur Unterstützung der FileTable-Funktion in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]hinzugefügt oder geändert wurden.  
  
 Die Spalte "Status" in den folgenden Tabellen gibt an, ob das Element in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]neu ist oder in früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vorhanden war und in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] geändert wurde, um die semantische Suche zu unterstützen.  
  
 Eine Liste der Anweisungen und Datenbankobjekte, die FILESTREAM unterstützen, finden Sie unter [FILESTREAM DDL, Functions, Stored Procedures, and Views](../views/views.md).  
  
##  <a name="ddl"></a> Transact-SQL-DDL-Anweisungen (Data Definition Language, Datendefinitionssprache)  
  
|Objekt|Status|Weitere Informationen|  
|------------|------------|----------------------|  
|[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)<br /><br /> [ALTER DATABASE SET-Optionen &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)|Geändert|[Aktivieren der erforderlichen Komponenten für FileTable](enable-the-prerequisites-for-filetable.md)<br /><br /> [Verwalten von FileTables](manage-filetables.md)|  
|[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)|Geändert|[Erstellen, Ändern und Löschen von FileTables](create-alter-and-drop-filetables.md)<br /><br /> [Verwalten von FileTables](manage-filetables.md)|  
|[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)|Geändert|[Aktivieren der erforderlichen Komponenten für FileTable](enable-the-prerequisites-for-filetable.md)|  
|[CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql)|Geändert|[Erstellen, Ändern und Löschen von FileTables](create-alter-and-drop-filetables.md)|  
|[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)<br /><br /> [RESTORE-Argumente &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql)|Geändert||  
  
##  <a name="func"></a> Funktionen  
  
|Objekt|Status|Weitere Informationen|  
|------------|------------|----------------------|  
|[FileTableRootPath &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/filetablerootpath-transact-sql)|**Hinzugefügt**|[Verwenden von Verzeichnissen und Pfaden in FileTables](work-with-directories-and-paths-in-filetables.md)|  
|[GetFileNamespacePath &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/getfilenamespacepath-transact-sql)|**Hinzugefügt**|[Verwenden von Verzeichnissen und Pfaden in FileTables](work-with-directories-and-paths-in-filetables.md)|  
|[GetPathLocator &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/getpathlocator-transact-sql)|**Hinzugefügt**|[Arbeiten mit Verzeichnissen und Pfaden in FileTables](work-with-directories-and-paths-in-filetables.md)|  
  
##  <a name="sproc"></a> Gespeicherte Prozeduren  
  
|Objekt|Status|Weitere Informationen|  
|------------|------------|----------------------|  
|[sp_kill_filestream_non_transacted_handles &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/filestream-and-filetable-sp-kill-filestream-non-transacted-handles)|**Hinzugefügt**|[Verwalten von FileTables](manage-filetables.md)|  
  
##  <a name="cv"></a> Katalogsichten  
  
|Objekt|Status|Weitere Informationen|  
|------------|------------|----------------------|  
|[sys.database_filestream_options &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-filestream-options-transact-sql)|**Hinzugefügt**|[Aktivieren der erforderlichen Komponenten für FileTable](enable-the-prerequisites-for-filetable.md)|  
|[sys.filetable_system_defined_objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-filetable-system-defined-objects-transact-sql)|**Hinzugefügt**|[Erstellen, Ändern und Löschen von FileTables](create-alter-and-drop-filetables.md)<br /><br /> [Verwalten von FileTables](manage-filetables.md)|  
|[sys.filetables &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-filetables-transact-sql)|**Hinzugefügt**|[Verwalten von FileTables](manage-filetables.md)|  
|[sys.tables &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-tables-transact-sql)|Geändert|[Verwalten von FileTables](manage-filetables.md)|  
  
##  <a name="dmv"></a> Dynamische Verwaltungssichten  
  
|Objekt|Status|Weitere Informationen|  
|------------|------------|----------------------|  
|[sys.dm_filestream_non_transacted_handles &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-filestream-non-transacted-handles-transact-sql)|**Hinzugefügt**|[Verwalten von FileTables](manage-filetables.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten von FileTables](manage-filetables.md)  
  
  
