---
title: Replikation mit Abonnenten von speicheroptimierten Tabellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
ms.assetid: 1a8e6bc7-433e-471d-b646-092dc80a2d1a
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0ee585f9773858848f213b3eeef6e995aedfb53f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63250880"
---
# <a name="replication-to-memory-optimized-table-subscribers"></a>Replikation mit Abonnenten von speicheroptimierten Tabellen
  Die Tabellen, die als Transaktionsreplikationsabonnenten fungieren, können (mit Ausnahme der Peer-zu-Peer-Transaktionsreplikation) als speicheroptimierte Tabellen konfiguriert werden. Andere Replikationskonfigurationen sind mit speicheroptimierten Tabellen nicht kompatibel.  
  
## <a name="configuring-a-memory-optimized-table-as-a-subscriber"></a>Konfigurieren einer speicheroptimierten Tabelle als Abonnent  
 Führen Sie die folgenden Schritte aus, um eine speicheroptimierte Tabelle als Abonnenten zu konfigurieren.  
  
 **Erstellen und Aktivieren einer Veröffentlichung**  
  
1.  Erstellen einer Veröffentlichung  
  
2.  Fügen Sie der Veröffentlichung Artikel hinzu. Verwenden Sie für den `@upd_cmd`-Parameter die SCALL- oder SQL-Konvention.  
  
    ```  
    EXEC sp_addarticle  
        @publication = N'Publication1',  
        @article = N'Mem_Table',  
        @source_owner = N'dbo',  
        @source_object = N'Mem_Table',  
        @type = N'logbased',  
        @description = null,  
        @creation_script = null,  
        @pre_creation_cmd = N'none',  
        @schema_option = 0x00000000080050DF,  
        @identityrangemanagementoption = N'manual',  
        @destination_table = N'Mem_Table',  
        @destination_owner = N'dbo',  
        @vertical_partition = N'false',  
        @ins_cmd = N'CALL sp_MSins_Mem_Table',  
        @del_cmd = N'CALL sp_MSdel_Mem_Table',  
        @upd_cmd = N'SCALL sp_MSupd_Mem_Table';  
    GO  
    ```  
  
 **Generieren Sie eine Momentaufnahme und passen Sie des Schemas an**  
  
1.  Erstellen Sie einen Momentaufnahmeauftrag, und generieren Sie eine Momentaufnahme.  
  
    ```  
    EXEC sp_addpublication_snapshot @publication = N'Publication1', @frequency_type = 1;  
    EXEC sp_startpublication_snapshot @publication = N'Publication1';  
    ```  
  
2.  Navigieren Sie zum Ordner für Momentaufnahmen. Der Standardspeicherort lautet "c:\Programme\Microsoft c:\Programme\Microsoft SQL Server\MSSQL12. \<Instanz > \MSSQL\repldata\unc\XXX\YYYYMMDDHHMMSS\\".  
  
3.  Suchen Sie die **. SCH** -Datei für die Tabelle, und klicken Sie in Management Studio zu öffnen. Ändern Sie das Tabellenschema, und aktualisieren Sie die gespeicherte Prozedur, wie im Folgenden beschrieben.  
  
     Werten Sie die in der IDX-Datei definierten Indizes aus. Ändern Sie `CREATE TABLE`, um die erforderlichen Indizes, die Einschränkungen, den Primärschlüssel und die speicheroptimierte Syntax anzugeben. Für speicheroptimierte Tabellen dürfen Indexspalten NICHT NULL sein, und Indexspalten von Zeichentypen müssen Unicode sein und eine BIN2-Sortierung aufweisen. Siehe das unten stehende Beispiel:  
  
    ```  
    SET ANSI_PADDING ON;  
    GO  
  
    SET ANSI_NULLS ON;  
    GO  
  
    SET QUOTED_IDENTIFIER ON;  
    GO  
  
    CREATE TABLE [dbo].[Mem_Table]([c1] [int] NOT NULL,  
        [c2] [float] NOT NULL,  
        [c3] [decimal](10, 2) NOT NULL,  
        [c4] [nvarchar](5) COLLATE SQL_Latin1_General_CP850_BIN2 NOT NULL,  
        INDEX [hash_index_sample_memoryoptimizedtable_c2] HASH (c2) WITH (BUCKET_COUNT = 1024),  
        INDEX [index_sample_memoryoptimizedtable_c3] NONCLUSTERED ([c3]),  
        INDEX [nvarchar_index_sample_memoryoptimizedtable_c4] ([c4]),  
        CONSTRAINT [PK_sample_memoryoptimizedtable] PRIMARY KEY NONCLUSTERED ([c1])) WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA);  
    GO  
    ```  
  
4.  Wenn Sie die SCALL-Konvention für den `@upd_cmd`-Parameter verwenden, navigieren Sie zur Schemadatei (.sch), und ändern Sie die Table Update-Anweisung in `create procedure [sp_MSupd_<SCHEMA><TABLE_NAME>]`, um Primärschlüsselspalten zu entfernen.  
  
     Um Primärschlüsselupdates zu unterstützen, können Sie die UPDATE-Anweisung für Primärschlüssel wie folgt durch eine benutzerdefinierte gespeicherte Updateprozedur ersetzen:  
  
    1.  Wählen Sie fehlende Spaltenwerte aus (SCALL gibt nur die Spalte an, die beim Updatevorgang berücksichtigt wird).  
  
    2.  Löschen Sie den vorhandenen Datensatz.  
  
    3.  Fügen Sie einen neuen Datensatz mit den bereitgestellten neuen Werten ein, einschließlich des neuen Primärschlüssels.  
  
     Die ursprüngliche Updateprozedur sieht folgendermaßen aus:  
  
    ```  
    create procedure [sp_MSupd_Mem_Table]  
                   @c1 int = NULL,  
                   @c2 float = NULL,  
                   @c3 decimal(10,2) = NULL,  
                   @c4 nvarchar(5) = NULL,  
                   @pkc1 int = NULL,  
                   @bitmap binary(1)  
    as  
    begin    
    if (substring(@bitmap,1,1) & 1 = 1)  
    begin   
    update [dbo].[Mem_Table] set  
                   [c1] = case substring(@bitmap,1,1) & 1 when 1 then @c1 else [c1] end,  
                   [c2] = case substring(@bitmap,1,1) & 2 when 2 then @c2 else [c2] end,  
                   [c3] = case substring(@bitmap,1,1) & 4 when 4 then @c3 else [c3] end,  
                   [c4] = case substring(@bitmap,1,1) & 8 when 8 then @c4 else [c4] end  
    where [c1] = @pkc1  
    if @@rowcount = 0  
        if @@microsoftversion>0x07320000  
            exec sp_MSreplraiserror 20598  
    end    
    else  
    begin   
    update [dbo].[Mem_Table] set  
                   [c2] = case substring(@bitmap,1,1) & 2 when 2 then @c2 else [c2] end,  
                   [c3] = case substring(@bitmap,1,1) & 4 when 4 then @c3 else [c3] end,  
                   [c4] = case substring(@bitmap,1,1) & 8 when 8 then @c4 else [c4] end  
    where [c1] = @pkc1  
    if @@rowcount = 0  
        if @@microsoftversion>0x07320000  
            exec sp_MSreplraiserror 20598  
    end   
    end   
    go  
    ```  
  
     Der Primärschlüssel sollte nie für einen Verleger aktualisiert werden. Kommentieren Sie das Update solcher Spalten in der Updateprozedur wie folgt aus:  
  
    ```  
    create procedure [sp_MSupd_Mem_Table]  
                   @c1 int = NULL,  
                   @c2 float = NULL,  
                   @c3 decimal(10,2) = NULL,  
                   @c4 nvarchar(5) = NULL,  
                   @pkc1 int = NULL,  
                   @bitmap binary(1)  
    as  
    begin    
    if (substring(@bitmap,1,1) & 1 = 1)  
    begin   
    update [dbo].[Mem_Table] set  
    --             [c1] = case substring(@bitmap,1,1) & 1 when 1 then @c1 else [c1] end,  
                   [c2] = case substring(@bitmap,1,1) & 2 when 2 then @c2 else [c2] end,  
                   [c3] = case substring(@bitmap,1,1) & 4 when 4 then @c3 else [c3] end,  
                   [c4] = case substring(@bitmap,1,1) & 8 when 8 then @c4 else [c4] end  
    where [c1] = @pkc1  
    if @@rowcount = 0  
        if @@microsoftversion>0x07320000  
            exec sp_MSreplraiserror 20598  
    end    
    else  
    begin   
    update [dbo].[Mem_Table] set  
                   [c2] = case substring(@bitmap,1,1) & 2 when 2 then @c2 else [c2] end,  
                   [c3] = case substring(@bitmap,1,1) & 4 when 4 then @c3 else [c3] end,  
                   [c4] = case substring(@bitmap,1,1) & 8 when 8 then @c4 else [c4] end  
    where [c1] = @pkc1  
    if @@rowcount = 0  
        if @@microsoftversion>0x07320000  
            exec sp_MSreplraiserror 20598  
    end   
    end   
    go  
    ```  
  
     Um Updates des Primärschlüssels zu unterstützen, ändern Sie die Updateprozedur wie folgt  
  
    ```  
    create procedure [sp_MSupd_Mem_Table]  
                   @c1 int = NULL,  
                   @c2 float = NULL,  
                   @c3 decimal(10,2) = NULL,  
                   @c4 nvarchar(5) = NULL,  
                    @pkc1 int = NULL,  
                   @bitmap binary(1)  
    as  
    begin    
    if (substring(@bitmap,1,1) & 1 = 1)  
    begin   
    select  
                   @c1 = case substring(@bitmap,1,1) & 1 when 1 then @c1 else [c1] end,  
                   @c2 = case substring(@bitmap,1,1) & 2 when 2 then @c2 else [c2] end,  
                   @c3 = case substring(@bitmap,1,1) & 4 when 4 then @c3 else [c3] end,  
                   @c4 = case substring(@bitmap,1,1) & 8 when 8 then @c4 else [c4] end  
    from [dbo].[Mem_Table] where [c1] = @pkc1  
    if @@rowcount <> 0 begin  
            delete [dbo].[Mem_Table] where [c1] = @pkc1  
            if @@rowcount <> 0  
                   insert into [dbo].[Mem_Table]([c1],  
                           [c2],  
                           [c3],  
                           [c4]) values (  
                           @c1,  
                           @c2,  
                           @c3,  
                           @c4  
                   )   
    end  
    if @@rowcount = 0  
        if @@microsoftversion>0x07320000  
            exec sp_MSreplraiserror 20598  
    end    
    else  
    begin   
    update [dbo].[Mem_Table] set  
                   [c2] = case substring(@bitmap,1,1) & 2 when 2 then @c2 else [c2] end,  
                   [c3] = case substring(@bitmap,1,1) & 4 when 4 then @c3 else [c3] end,  
                   [c4] = case substring(@bitmap,1,1) & 8 when 8 then @c4 else [c4] end  
    where [c1] = @pkc1  
    if @@rowcount = 0  
        if @@microsoftversion>0x07320000  
            exec sp_MSreplraiserror 20598  
    end   
    end   
    go  
    ```  
  
5.  Erstellen der Abonnentendatenbank mithilfe der **elevate_to_snapshot_isolation** aus, und legen Sie die standardsortierung auf Latin1_General_CS_AS_KS_WS, wenn die Nichtunicode-Zeichendatentypen verwenden.  
  
    ```  
    CREATE DATABASE [Sub]   
    CONTAINMENT = NONE   
    ON PRIMARY ( NAME = [Sub], FILENAME = [C:\Program Files\Microsoft SQL Server\MSSQL12\MSSQL\DATA\Sub.mdf]),   
    FILEGROUP [mem] CONTAINS MEMORY_OPTIMIZED_DATA ( NAME = [mem],   
    FILENAME = [C:\Program Files\Microsoft SQL Server\MSSQL12\MSSQL\DATA\Sub])  
    LOG ON ( NAME = [Sub_log], FILENAME = [C:\Program Files\Microsoft SQL Server\MSSQL12\MSSQL\DATA\Sub.ldf])  
    COLLATE Latin1_General_CS_AS_KS_WS;  
  
    ALTER DATABASE [Sub] SET MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT = ON;  
    GO  
    ```  
  
6.  Wenden Sie das Schema auf die Datenbank eines Abonnenten an, und speichern Sie das Schema für die zukünftige Verwendung.  
  
7.  Laden Sie die Verlegerdaten (Quelldaten) in den Abonnenten. Die Daten dürfen beim Verleger nicht geändert werden, bis Sie ein Abonnement hinzufügen.  Sie können BCP verwenden, wie unten veranschaulicht:  
  
    ```  
    bcp Pub.dbo.Mem_Table out Mem_Table.bcp -S. -T -C1252 -n  
    bcp Sub.dbo.Mem_Table in Mem_Table.bcp -S. -T -C1252 -n  
    ```  
  
8.  Konfigurieren Sie den Artikel neu, um Schemaänderungen beim Abonnenten zu deaktivieren:  
  
    ```  
    EXEC sp_changearticle  
        @publication = N'Publication1',  
        @article = N'Mem_Table',  
        @property = N'schema_option',  
        @value = 0,  
        @force_invalidate_snapshot = 1,  
        @force_reinit_subscription = 1;  
    GO  
    ```  
  
 **Fügen Sie keine Synchronisierung Abonnement hinzu.**  
  
 Fügen Sie ein "No sync"-Abonnement hinzu.  
  
```  
EXEC sp_addsubscription  
    @publication = N' Publication1',  
    @subscriber = @@ServerName,  
    @destination_db = N'Sub',  
    @subscription_type = N'Push',  
    @sync_type = N'replication support only',  
    @article = N'all',  
    @update_mode = N'read only',  
    @subscriber_type = 0;  
GO  
```  
  
 Speicheroptimierte Tabellen empfangen nun Updates vom Verleger.  
  
## <a name="restrictions"></a>Restrictions  
 Es wird nur die unidirektionale Transaktionsreplikation unterstützt. Die Peer-zu-Peer-Transaktionsreplikation wird nicht unterstützt.  
  
 Speicheroptimierte Tabellen können nicht veröffentlicht werden.  
  
 Replikationstabellen auf dem Verteiler können nicht als speicheroptimierte Tabellen konfiguriert werden.  
  
 Die Mergereplikation kann speicheroptimierte Tabellen einschließen.  
  
 Auf dem Abonnenten können die Tabellen, die bei einer Transaktionsreplikation berücksichtigt werden, als speicheroptimierte Tabellen konfiguriert werden. Die Abonnententabellen müssen jedoch die Anforderungen für speicheroptimierte Tabellen erfüllen. Dies erfordert folgende Einschränkungen.  
  
-   Zum Erstellen einer speicheroptimierten Tabelle auf einem Transaktionsreplikationsabonnenten müssen die Momentaufnahme-Schemadateien, mit denen die speicheroptimierten Tabellen erstellt werden, manuell geändert werden. Weitere Informationen finden Sie unter [Ändern einer Schemadatei](#Schema).  
  
-   Tabellen, die mit speicheroptimierten Tabellen auf einem Abonnenten repliziert werden, sind auf das Limit von 8060 Byte pro Zeile für speicheroptimierte Tabellen beschränkt.  
  
-   Tabellen, die mit speicheroptimierten Tabellen auf Abonnenten repliziert werden, sind auf die Datentypen beschränkt, die für speicheroptimierte Tabellen zulässig sind. Weitere Informationen finden Sie unter [Supported Data Types](../in-memory-oltp/supported-data-types-for-in-memory-oltp.md).  
  
-   Es gelten Einschränkungen für das Aktualisieren des Primärschlüssels von Tabellen, die mit einer speicheroptimierten Tabelle auf einem Abonnenten repliziert werden. Weitere Informationen finden Sie unter [Replizieren von Änderungen mit einem Primärschlüssel](#PrimaryKey).  
  
-   Fremdschlüssel, UNIQUE-Einschränkung, Trigger, Schemaänderungen, ROWGUIDCOL, berechnete Spalten, die Datenkomprimierung, Aliasdatentypen, Versionsverwaltung und Sperren werden in speicheroptimierte Tabellen nicht unterstützt. Weitere Informationen finden Sie unter [Von In-Memory OLTP nicht unterstützte T-SQL-Konstrukte](../in-memory-oltp/transact-sql-constructs-not-supported-by-in-memory-oltp.md) .  
  
##  <a name="Schema"></a> Ändern einer Schemadatei  
  
-   Gruppierte Indizes werden nicht unterstützt. Ändern Sie alle gruppierten Indizes in nicht gruppierte Indizes.  
  
-   Alle Spalten im Schlüssel eines Indexes müssen als `NOT NULL` angegeben werden.  
  
-   Bei Verwendung der Option für speicheroptimierte Tabellen `DURABILITY = SCHEMA_AND_DATA` muss die Tabelle einen nicht gruppierten Primärschlüsselindex aufweisen.  
  
-   ANSI_PADDING muss auf ON festgelegt sein.  
  
##  <a name="PrimaryKey"></a> Replizieren von Änderungen mit einem Primärschlüssel  
 Der Primärschlüssel einer speicheroptimierten Tabelle kann nicht aktualisiert werden. Wenn Sie ein Primärschlüsselupdate auf einem Abonnenten replizieren möchten, ändern Sie die gespeicherte Updateprozedur so, dass der Updatevorgang als DELETE/INSERT-Paar übermittelt wird.  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server-Replikation](sql-server-replication.md)  
  
  
