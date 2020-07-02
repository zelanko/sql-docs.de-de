---
title: Gespeicherte System Prozeduren für FILESTREAM und FILETABLE (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- FileTables [SQL Server], catalog views
ms.assetid: 2c83a4a7-720b-4435-a3b5-788c29f56949
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e0c7697c6c65f6d39de4d5f52ea2fdb85ea4e218
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85731793"
---
# <a name="filestream-and-filetable-system-stored-procedures-transact-sql"></a>Gespeicherte Systemprozeduren für Filestream und FileTable (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  In diesem Abschnitt werden die gespeicherten System Prozeduren der FILETABLE-Funktion und der FileStream-Funktion beschrieben.  

## <a name="filestream-and-filetable-system-stored-procedures"></a>Gespeicherte System Prozeduren für FILESTREAM und FILETABLE
  [sp_filestream_force_garbage_collection (Transact-SQL)](filestream-and-filetable-sp-filestream-force-garbage-collection.md)

   Erzwingt die Ausführung des FILESTREAM-Garbage Collectors und löscht alle nicht benötigten FILESTREAM-Dateien.

  [sp_kill_filestream_non_transacted_handles (Transact-SQL)](filestream-and-filetable-sp-kill-filestream-non-transacted-handles.md)

  Schließt nicht transaktionale Dateihandles für FileTable-Daten.


## <a name="see-also"></a>Weitere Informationen
[Filestream](../../relational-databases/blob/filestream-sql-server.md)
<br>[Filetables](../../relational-databases/blob/filetables-sql-server.md)
<br>[Dynamische Verwaltungssichten für Filestream und FileTable (Transact-SQL)](../system-dynamic-management-views/filestream-and-filetable-dynamic-management-views-transact-sql.md)
<br>[Filestream- und FileTable-Katalogsichten (Transact-SQL)](../system-catalog-views/filestream-and-filetable-catalog-views-transact-sql.md)
  
  
