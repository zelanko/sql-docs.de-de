---
title: 'Tutorial: SQL Server-Sicherung und-Wiederherstellung im Windows Azure Blob Storage-Dienst | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 9e1d94ce-2c93-45d1-ae2a-2a7d1fa094c4
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 2216674bec52dd4d4800aa1b03aa4a2834667974
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62524050"
---
# <a name="tutorial-sql-server-backup-and-restore-to-windows-azure-blob-storage-service"></a>Tutorial: SQL Server-Sicherung und-Wiederherstellung im Windows Azure-Blob-Speicherdienst
  Willkommen bei den ersten Schritten mit der SQL Server-Sicherung und -Wiederherstellung im Lernprogramm für den Windows Azure-BLOB-Speicherdienst. In diesem Lernprogramm erfahren Sie, wie Sie Sicherungen in den Windows Azure-BLOB-Speicherdienst schreiben und daraus wiederherstellen.  
  
## <a name="what-you-will-learn"></a>Lernziele  
 In diesem Lernprogramm erfahren Sie, wie Sie ein Windows-Speicherkonto, einen BLOB-Container und Anmeldeinformationen für den Zugriff auf das Speicherkonto erstellen, eine Sicherung in den BLOB-Dienst schreiben und eine einfache Wiederherstellung ausführen. Dieses Lernprogramm ist in vier Lektionen aufgeteilt:  
  
 [Lektion 1: Erstellen von Windows Azure-Speicherobjekten](../tutorials/lesson-1-create-windows-azure-storage-objects.md)  
 In dieser Lektion erstellen Sie ein Windows Azure-Speicherkonto und einen BLOB-Container.  
  
 [Lektion 2: Erstellen von SQL Server-Anmeldeinformationen](../tutorials/lesson-2-create-a-sql-server-credential.md)  
 In dieser Lektion erstellen Sie Anmeldeinformationen, um die Sicherheitsinformationen für den Zugriff auf das Windows Azure-Speicherkonto zu speichern.  
  
 [Lektion 3: Schreiben Sie eine vollständige Datenbanksicherung in den Windows Azure-Blob-Speicherdienst](../tutorials/lesson-3-write-a-full-database-backup-to-the-windows-azure-blob-storage-service.md)  
 In dieser Lektion geben Sie eine T-SQL-Anweisung aus, um eine Sicherung der AdventureWorks2012-Datenbank in den Windows Azure-BLOB-Speicherdienst zu schreiben.  
  
 [Lektion 4: Ausführen einer Wiederherstellung von einer vollständigen Datenbanksicherung](../tutorials/lesson-4-perform-a-restore-from-a-full-database-backup.md)  
 In dieser Lektion geben Sie eine T-SQL-Anweisung aus, um die in der vorherigen Lektion erstellte Datenbanksicherung wiederherzustellen.  
  
### <a name="requirements"></a>Anforderungen  
 Um dieses Tutorial abzuschließen, müssen Sie mit den Sicherungs- und Wiederherstellungskonzepten in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] und der T-SQL-Syntax vertraut sein. Damit Sie dieses Lernprogramm ausführen können, muss Ihr System die folgenden Anforderungen erfüllen:  
  
-   Eine Instanz von [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]und die AdventureWorks2012-Datenbank sind installiert.  
  
     Die SQL Server-Instanz kann lokal oder auf einem virtuellen Windows Azure-Computer gespeichert sein.  
  
     Anstelle von AdventureWorks2012 können Sie eine Benutzerdatenbank verwenden und die T-SQL-Syntax entsprechend ändern.  
  
-   Das zum Ausgeben von BACKUP- oder RESTORE-Befehlen verwendete Benutzerkonto sollte Mitglied der Datenbankrolle **db_backup operator** sein und über Berechtigungen zum **Ändern beliebiger Anmeldeinformationen** verfügen.  
  
### <a name="additional-reading"></a>Zusätzliches Lesematerial  
 Die folgenden Themen werden empfohlen, um das Verständnis der Konzepte und bewährten Verfahren zu verbessern, die Sie bei [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Sicherungen im Windows Azure-BLOB-Speicherdienst verwenden.  
  
1.  [SQL Server-Sicherung und -Wiederherstellung mit dem Microsoft Azure Storage-Dienst](backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)  
  
2.  [SQL Server-URL-Sicherung – bewährte Methoden und Problembehandlung](backup-restore/sql-server-backup-to-url-best-practices-and-troubleshooting.md)  
  
  
