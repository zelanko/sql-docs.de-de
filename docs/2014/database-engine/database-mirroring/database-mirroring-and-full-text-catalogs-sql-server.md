---
title: Datenbankspiegelung und Volltextkataloge (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], interoperability
- full-text catalogs [SQL Server], database mirroring
- catalogs [SQL Server], database mirroring
ms.assetid: e34072ae-fe8a-462d-bb03-02fa0987f793
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: e90e2386fcd6c6d2f71e1cea31f253f8baac9195
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62807294"
---
# <a name="database-mirroring-and-full-text-catalogs-sql-server"></a>Datenbankspiegelung und Volltextkataloge (SQL Server)
  Führen Sie zum Erstellen einer Datenbankspiegelung mit einem Volltextkatalog den üblichen Sicherungsvorgang aus, um eine vollständige Sicherung der Prinzipaldatenbank zu erstellen, und stellen Sie die Sicherung wieder her, um die Datenbank auf den Spiegelserver zu kopieren. Weitere Informationen finden Sie unter [Vorbereiten einer Spiegeldatenbank auf die Spiegelung &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md)verwendet.  
  
## <a name="full-text-catalog-and-indexes-before-failover"></a>Volltextkataloge und -indizes vor dem Failover  
 In einer neu erstellten Spiegeldatenbank ist der Volltextkatalog mit jenem Volltextkatalog identisch, der während der Datenbanksicherung verwendet wurde. Nach Beginn der Datenbankspiegelung werden alle durch DDL-Anweisungen (CREATE FULLTEXT CATALOG, ALTER FULLTEXT CATALOG, DROP FULLTEXT CATALOG) vorgenommenen Änderungen an der Katalogebene protokolliert und an den Spiegelserver gesendet, um in der Spiegeldatenbank wiedergegeben zu werden. Änderungen auf Indexebene werden jedoch nicht in der Spiegeldatenbank reproduziert, da sie nicht auf dem Prinzipalserver protokolliert werden. Daher ist der Inhalt des Volltextkatalogs in der Spiegeldatenbank nicht mehr mit dem Volltextkatalog in der Prinzipaldatenbank synchron, wenn sich letzterer ändert.  
  
## <a name="full-text-indexes-after-failover"></a>Volltextindizes nach einem Failover  
 Nach einem Failover ist in folgenden Situationen eine vollständige Durchforstung des Volltextindexes auf dem neuen Prinzipalserver erforderlich oder zumindest nützlich:  
  
-   Wenn die Änderungsnachverfolgung für den Volltextindex AUSgeschaltet ist, müssen Sie eine vollständige Durchforstung für diesen Index durchführen. Verwenden Sie dazu die folgende Anweisung:  
  
     ALTER FULLTEXT INDEX ON *Tabellenname* START FULL POPULATION  
  
-   Wenn für einen Volltextindex die automatische Änderungsnachverfolgung konfiguriert ist, wird der Volltextindex automatisch synchronisiert. Durch die Synchronisierung wird jedoch die Leistung des Volltextindexes beeinträchtigt. Verlangsamt sich die Ausführung übermäßig, können Sie eine vollständige Durchforstung verursachen, indem Sie die Änderungsnachverfolgung ausschalten und anschließend wieder die automatische Änderungsnachverfolgung festlegen:  
  
    -   So schalten Sie die Änderungsnachverfolgung aus:  
  
         ALTER FULLTEXT INDEX ON *Tabellenname* SET CHANGE_TRACKING OFF  
  
    -   So legen Sie die automatische Änderungsnachverfolgung fest:  
  
         ALTER FULLTEXT INDEX ON *Tabellenname* SET CHANGE_TRACKING AUTO  
  
    > [!NOTE]  
    >   Wenn Sie sehen möchten, ob die automatische Änderungsnachverfolgung aktiviert ist, können Sie die [OBJECTPROPERTYEX](/sql/t-sql/functions/objectproperty-transact-sql) -Funktion zum Abfragen der **TableFullTextBackgroundUpdateIndexOn** -Eigenschaft der Tabelle verwenden.  
  
 Weitere Informationen finden Sie unter [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql).  
  
> [!NOTE]  
>  Das Starten eines Durchforstungsvorgangs nach einem Failover funktioniert gleichermaßen wie das Starten eines Durchforstungsvorgangs nach einer Wiederherstellung.  
  
## <a name="after-forcing-service"></a>Nach dem Erzwingen des Diensts  
 Führen Sie einen vollständige Durchforstung durch, nachdem die Ausführung des Diensts auf dem Spiegelserver (mit möglichem Datenverlust) erzwungen wurde. Die zu verwendende Methode zum Starten einer vollständigen Durchforstung hängt davon ab, ob für den betroffenen Volltextindex die Änderungsnachverfolgung aktiviert ist. Weitere Informationen finden Sie weiter oben in diesem Thema unter "Volltextindizes nach einem Failover".  
  
## <a name="see-also"></a>Weitere Informationen  
 [ALTER FULLTEXT Index &#40;Transact-SQL-&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql)   
 [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql)   
 [DROP FULLTEXT Index &#40;Transact-SQL-&#41;](/sql/t-sql/statements/drop-fulltext-index-transact-sql)   
 [Daten Bank Spiegelung &#40;SQL Server&#41;](database-mirroring-sql-server.md)   
 [Sichern und Wiederherstellen von Volltextkatalogen und Indizes](../../relational-databases/indexes/indexes.md)  
  
  
