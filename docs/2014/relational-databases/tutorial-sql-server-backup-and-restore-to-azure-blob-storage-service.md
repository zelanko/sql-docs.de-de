---
title: 'Tutorial: SQL Server-Sicherung und -Wiederherstellung mit dem Azure-BLOB-Speicherdienst | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 9e1d94ce-2c93-45d1-ae2a-2a7d1fa094c4
author: rothja
ms.author: jroth
ms.openlocfilehash: e3eee1449ec42285d5a95ac33d91f439dcd131ac
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85002488"
---
# <a name="tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service"></a>Tutorial: SQL Server-Sicherung und -Wiederherstellung mit dem Azure Blob Storage-Dienst
  Willkommen beim Tutorial zu den ersten Schritten mit SQL Server Sicherung und Wiederherstellung mit Azure BLOB Storage Dienst. In diesem Tutorial erfahren Sie, wie Sie Sicherungen in den Azure-BLOB-Speicherdienst schreiben und daraus wiederherstellen.  
  
## <a name="what-you-will-learn"></a>Lernziele  
 In diesem Lernprogramm erfahren Sie, wie Sie ein Windows-Speicherkonto, einen BLOB-Container und Anmeldeinformationen für den Zugriff auf das Speicherkonto erstellen, eine Sicherung in den BLOB-Dienst schreiben und eine einfache Wiederherstellung ausführen. Dieses Lernprogramm ist in vier Lektionen aufgeteilt:  
  
 [Lektion 1: Erstellen von Azure Storage Objekten](../tutorials/lesson-1-create-windows-azure-storage-objects.md)  
 In dieser Lektion erstellen Sie ein Azure-Speicherkonto und einen BLOB-Container.  
  
 [Lektion 2: Erstellen von SQL Server-Anmeldeinformationen](../tutorials/lesson-2-create-a-sql-server-credential.md)  
 In dieser Lektion erstellen Sie Anmeldeinformationen, um die Sicherheitsinformationen für den Zugriff auf das Azure-Speicherkonto zu speichern.  
  
 [Lektion 3: Schreiben einer vollständigen Datenbanksicherung in den Azure Blob Storage-Dienst](../tutorials/lesson-3-write-a-full-database-backup-to-the-windows-azure-blob-storage-service.md)  
 In dieser Lektion geben Sie eine T-SQL-Anweisung aus, um eine Sicherung der AdventureWorks2012-Datenbank in den Azure-BLOB-Speicherdienst zu schreiben.  
  
 [Lektion 4: Ausführen einer Wiederherstellung aus einer vollständigen Datenbanksicherung](../tutorials/lesson-4-perform-a-restore-from-a-full-database-backup.md)  
 In dieser Lektion geben Sie eine T-SQL-Anweisung aus, um die in der vorherigen Lektion erstellte Datenbanksicherung wiederherzustellen.  
  
### <a name="requirements"></a>Requirements (Anforderungen)  
 Um dieses Tutorial abzuschließen, müssen Sie mit den Sicherungs- und Wiederherstellungskonzepten in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] und der T-SQL-Syntax vertraut sein. Damit Sie dieses Lernprogramm ausführen können, muss Ihr System die folgenden Anforderungen erfüllen:  
  
-   Eine Instanz von [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] und die AdventureWorks2012-Datenbank sind installiert.  
  
     Die SQL Server-Instanz kann lokal oder auf einem virtuellen Azure-Computer gespeichert sein.  
  
     Anstelle von AdventureWorks2012 können Sie eine Benutzerdatenbank verwenden und die T-SQL-Syntax entsprechend ändern.  
  
-   Das zum Ausgeben von BACKUP- oder RESTORE-Befehlen verwendete Benutzerkonto sollte Mitglied der Datenbankrolle **db_backup operator** sein und über Berechtigungen zum **Ändern beliebiger Anmeldeinformationen** verfügen.  
  
### <a name="additional-reading"></a>Zusätzliche Lektüre  
 Die folgenden Themen werden empfohlen, um das Verständnis der Konzepte und bewährten Verfahren zu verbessern, die Sie bei [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Sicherungen im Azure-BLOB-Speicherdienst verwenden.  
  
1.  [SQL Server-Sicherung und -Wiederherstellung mit dem Microsoft Azure Blob Storage Service](backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)  
  
2.  [SQL Server-Sicherung über URLs – bewährte Methoden und Problembehandlung](backup-restore/sql-server-backup-to-url-best-practices-and-troubleshooting.md)  
  
  
