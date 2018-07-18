---
title: 'Tutorial: SQL Server-Datendateien im Windows Azure-Speicherdienst | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: e69be67d-da1c-41ae-8c9a-6b12c8c2fb61
caps.latest.revision: 7
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: f805d7a9b0997d9f5a7cecbf61b5120bdf09f3cd
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37323860"
---
# <a name="tutorial-sql-server-data-files-in-windows-azure-storage-service"></a>Lernprogramm: SQL Server-Datendateien im Windows Azure-Speicher
  Willkommen beim Lernprogramm für SQL Server-Datendateien im Windows Azure-Speicher. Dieses Lernprogramm hilft Ihnen, zu verstehen, wie Sie SQL Server-Datendateien direkt im Windows Azure-BLOB-Speicherdienst speichern.  
  
 Die Unterstützung der SQL Server-Integration für den Windows Azure-BLOB-Speicherdienst stellt eine Erweiterung von SQL Server 2014 dar. Eine Übersicht über die Funktionen und Vorteile der Verwendung dieser Funktionen finden Sie [SQL Server-Datendateien in Windows Azure](databases/sql-server-data-files-in-microsoft-azure.md).  
  
## <a name="what-you-will-learn"></a>Lernziele  
 In diesem Lernprogramm erfahren Sie in mehreren Lektionen, wie Sie SQL Server-Datendateien im Windows Azure-Speicherdienst speichern. Jede Lektion behandelt eine bestimmte Aufgabe. Zuerst wird erläutert, wie Sie in Windows Azure ein Speicherkonto und einen Container erstellen. Danach erfahren Sie, wie Sie SQL Server-Anmeldeinformationen erstellen, damit Sie SQL Server in den Windows Azure-Speicher integrieren können. Anschließend erstellen Sie eine Datenbank direkt im Windows Azure-Speicher. Außerdem werden im Lernprogramm Verschlüsselungs-, Migrations- sowie Sicherungs- und Wiederherstellungsszenarien behandelt.  
  
 Dieses Lernprogramm ist in neun Lektionen aufgeteilt:  
  
 **[Lektion 1: Erstellen von Windows Azure-Speicherkonto und Container](../tutorials/lesson-1-create-windows-azure-storage-account-and-container.md)**  
 In dieser Lektion erstellen Sie ein Windows Azure-Speicherkonto und einen Container.  
  
 **[Lektion 2. Erstellen Sie eine Richtlinie für Container und Generieren einer Shared Access Signature &#40;SAS&#41; Schlüssel](lesson-1-create-stored-access-policy-and-shared-access-signature.md)**  
 In dieser Lektion erstellen Sie eine Richtlinie für den BLOB-Container und generieren zusätzlich eine SAS (Shared Access Signature, Signatur für gemeinsamen Zugriff).  
  
 **[Lektion 3: Erstellen von SQL Server-Anmeldeinformationen](lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md)**  
 In dieser Lektion erstellen Sie Anmeldeinformationen, um die Sicherheitsinformationen für den Zugriff auf das Windows Azure-Speicherkonto zu speichern.  
  
 **[Lektion 4: Erstellen einer Datenbank in Windows Azure-Speicher](../relational-databases/lesson-3-database-backup-to-url.md)**  
 In dieser Lektion erstellen Sie mithilfe der FILENAME-Option von CREATE DATABASE eine Datenbank im Windows Azure-Speicher.  
  
 **[Lektion 5. &#40;Optional&#41; Verschlüsseln Ihrer Datenbank mithilfe von TDE](../relational-databases/lesson-4-restore-database-to-virtual-machine-from-url.md)**  
 In dieser Lektion verschlüsseln Sie die Datenbank mithilfe einer transparenten Datenverschlüsselung (TDE) und eines Serverzertifikats.  
  
 **[Lektion 6: Migrieren einer Datenbank aus einer Quelle lokalen zu einem Zielcomputer in Windows Azure](lesson-5-backup-database-using-file-snapshot-backup.md)**  
 In dieser Lektion migrieren Sie eine Datenbank mit der CREATE DATABASE FOR ATTACH-Option von der lokalen Umgebung zu einem virtuellen Computer in Windows Azure.  
  
 **[Lektion 7: Verschieben von Datendateien in Microsoft Azure Storage](../relational-databases/lesson-6-generate-activity-and-backup-log-using-file-snapshot-backup.md)**  
 In dieser Lektion verschieben Sie die Datendateien mit der ALTER DATABASE-Anweisung in den Windows Azure-Speicher.  
  
 **[Lektion 8: Wiederherstellen einer Datenbank in Windows Azure-Speicher](../relational-databases/lesson-7-restore-a-database-to-a-point-in-time.md)**  
 In dieser Lektion stellen Sie eine Datenbank mit der MOVE-Option von RESTORE DATABASE im Windows Azure-Speicher wieder her.  
  
 **[Lektion 9. Wiederherstellen einer Datenbank aus Windows Azure-Speicher](lesson-8-restore-as-new-database-from-log-backup.md)**  
 In dieser Lektion stellen Sie eine Datenbank mit der MOVE-Option von RESTORE DATABASE aus dem Windows Azure-Speicher wieder her.  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server-Datendateien in Microsoft Azure](databases/sql-server-data-files-in-microsoft-azure.md)  
  
  
