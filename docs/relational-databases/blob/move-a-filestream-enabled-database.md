---
title: Verschieben einer FILESTREAM-aktivierten Datenbank | Microsoft-Dokumentation
description: Hier erfahren Sie, wie Sie eine Datenbank mit aktiviertem FILESTREAM verschieben können. Außerdem erfahren Sie, welche Transact-SQL-Skripts Sie im Abfrage-Editor von SQL Server Management Studio verwenden können.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], moving a FILESTREAM-enabled database
ms.assetid: dd4d270d-9283-431a-aa6b-e571fced1893
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 706581c6fa44170d1bf8b9901a2dec0b47574be8
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85631138"
---
# <a name="move-a-filestream-enabled-database"></a>Verschieben einer FILESTREAM-aktivierten Datenbank
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  In diesem Thema wird das Verschieben einer FILESTREAM-aktivierten Datenbank veranschaulicht.  
  
> [!NOTE]  
>  Für die Beispiele in diesem Thema benötigen Sie die Datenbank „Archive“, die unter [Erstellen einer FILESTREAM-aktivierten Datenbank](../../relational-databases/blob/create-a-filestream-enabled-database.md)erstellt wird.  
  
### <a name="to-move-a-filestream-enabled-database"></a>So verschieben Sie eine FILESTREAM-aktivierte Datenbank  
  
1.  Klicken Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]auf **Neue Abfrage** , um den Abfrage-Editor zu öffnen.  
  
2.  Kopieren Sie das folgende [!INCLUDE[tsql](../../includes/tsql-md.md)] -Skript in den Abfrage-Editor, und klicken Sie dann auf **Ausführen**. Mit diesem Skript wird der Speicherort der physischen Datenbankdateien angezeigt, die von der FILESTREAM-Datenbank verwendet werden.  
  
    ```sql  
    USE Archive  
    GO  
    SELECT type_desc, name, physical_name from sys.database_files  
    ```  
  
3.  Kopieren Sie das folgende [!INCLUDE[tsql](../../includes/tsql-md.md)] -Skript in den Abfrage-Editor, und klicken Sie dann auf **Ausführen**. Mit diesem Code wird die `Archive` -Datenbank offline geschaltet.  
  
    ```sql  
    USE master  
    EXEC sp_detach_db Archive  
    GO  
    ```  
  
4.  Erstellen Sie den Ordner `C:\moved_location`, und verschieben Sie dann die in Schritt 2 aufgeführten Dateien und Ordner in diesen Ordner.  
  
5.  Kopieren Sie das folgende [!INCLUDE[tsql](../../includes/tsql-md.md)] -Skript in den Abfrage-Editor, und klicken Sie dann auf **Ausführen**. Mit diesem Skript wird die `Archive` -Datenbank online geschaltet.  
  
    ```sql  
    CREATE DATABASE Archive ON  
    PRIMARY ( NAME = Arch1,  
        FILENAME = 'c:\moved_location\archdat1.mdf'),  
    FILEGROUP FileStreamGroup1 CONTAINS FILESTREAM( NAME = Arch3,  
        FILENAME = 'c:\moved_location\filestream1')  
    LOG ON  ( NAME = Archlog1,  
        FILENAME = 'c:\moved_location\archlog1.ldf')  
    FOR ATTACH  
    GO  
    ```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_detach_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-detach-db-transact-sql.md)  
  
  
