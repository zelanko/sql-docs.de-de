---
title: Skalierbarkeit | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/27/2015
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: a4891c57-56bb-49f4-9bb5-f11b745279e5
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 2762e024f3a94ed20c900833e56840b67af1685d
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "68111783"
---
# <a name="scalability"></a>Skalierbarkeit
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] wurde die Skalierbarkeit der Speicherung auf Datenträgern für speicheroptimierte Tabellen verbessert. 

## <a name="multiple-threads-to-persist-memory-optimized-tables"></a>Mehrere Threads zur dauerhaften Speicherung speicheroptimierter Tabellen  
  
In [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] gab es einen einzigen Offline-Prüfpunktthread, der das Transaktionsprotokoll auf Änderungen an speicheroptimierten Tabellen überprüft und diese dauerhaft in Prüfpunktdateien gespeichert hat (z.B. Daten- und Änderungsdateien). Auf Computern mit einer größeren Anzahl von Kernen kann der einzelne Offline-Prüfpunktthread hinterherhinken.  
  
Ab [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] sind mehrere gleichzeitig ausgeführte Threads dafür zuständig, Änderungen an speicheroptimierten Tabellen dauerhaft zu speichern.  
  
## <a name="multi-threaded-recovery"></a>Multithread-Wiederherstellung
In der vorherigen Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]erfolgte die Protokollanwendung im Rahmen eines Wiederherstellungsvorgangs mit einem einzigen Thread. Ab [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] werden mehrere Threads für die Protokollanwendung verwendet.  
  
## <a name="merge-operation"></a>Zusammenführungsvorgang  
Der Zusammenführungsvorgang wird jetzt mit mehreren Threads durchgeführt.  
   
> [!NOTE]
> Die manuelle Zusammenführung wurde deaktiviert, da durch die Verwendung mehrerer Threads davon auszugehen ist, dass die Last bewältigt wird. 

## <a name="dynamic-management-views"></a>Dynamische Verwaltungssichten  
Die dynamischen Verwaltungssichten [sys.dm_db_xtp_checkpoint_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-checkpoint-stats-transact-sql.md) und [sys.dm_db_xtp_checkpoint_files &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-checkpoint-files-transact-sql.md) wurden in erheblichem Umfang geändert.  

## <a name="storage-management"></a>Speicherverwaltung
Die In-Memory-OLTP-Engine verwendet weiterhin eine speicheroptimierte Dateigruppe, die auf FILESTREAM basiert. Die einzelnen Dateien in der Dateigruppe wurden jedoch von FILESTREAM entkoppelt. Diese Dateien werden vollständig von der In-Memory-OLTP-Engine verwaltet (beispielsweise hinsichtlich der Erstellung, Löschung und Speicherbereinigung). 

> [!NOTE]
> [DBCC SHRINKFILE &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-shrinkfile-transact-sql.md) wird nicht unterstützt.  
  
## <a name="see-also"></a>Weitere Informationen   
[Erstellen und Verwalten von Speicher für speicheroptimierte Objekte](../../relational-databases/in-memory-oltp/creating-and-managing-storage-for-memory-optimized-objects.md)     
[Database Files and Filegroups](../../relational-databases/databases/database-files-and-filegroups.md)    
[ALTER DATABASE-Optionen Datei und Dateigruppe (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-file-and-filegroup-options.md)    
