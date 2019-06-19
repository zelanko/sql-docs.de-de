---
title: Verschieben einer FILESTREAM-aktivierten Datenbank | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: 57a5984aebfc2261c5b6f524dd111e8ba786733a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65094141"
---
# <a name="move-a-filestream-enabled-database"></a>Verschieben einer FILESTREAM-aktivierten Datenbank
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
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
  
  
