---
title: 'Tutorial: SQL Server von Datendateien in Azure Storage Dienst | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: e69be67d-da1c-41ae-8c9a-6b12c8c2fb61
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: a15f6735ef0ef79b7eb953445c926f60f6bfb12e
ms.sourcegitcommit: 3b1f873f02af8f4e89facc7b25f8993f535061c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2019
ms.locfileid: "70176085"
---
# <a name="tutorial-sql-server-data-files-in-azure-storage-service"></a>Tutorial: SQL Server-Datendateien im Azure Storage-Dienst
  Willkommen beim Tutorial SQL Server Datendateien in Azure Storage Dienst. In diesem Tutorial erfahren Sie, wie Sie SQL Server Datendateien direkt im Azure-BLOB-Speicherdienst speichern.  
  
 Die Unterstützung der SQL Server Integration für den Azure BLOB Storage-Dienst ist eine SQL Server 2014-Erweiterung. Eine Übersicht über die Funktionen und Vorteile der Verwendung dieser Funktion finden Sie unter [SQL Server von Datendateien in Azure](databases/sql-server-data-files-in-microsoft-azure.md).  
  
## <a name="what-you-will-learn"></a>Lernziele  
 In diesem Tutorial wird gezeigt, wie Sie SQL Server Datendateien in mehreren Lektionen in Azure Storage Dienst speichern. Jede Lektion behandelt eine bestimmte Aufgabe. Zunächst erfahren Sie, wie Sie ein Speicherkonto und einen Container in Azure erstellen. Anschließend erfahren Sie, wie Sie eine SQL Server Anmelde Informationen erstellen, damit Sie SQL Server in Azure Storage integrieren können. Anschließend erstellen Sie eine Datenbank direkt in Azure Storage. Außerdem werden im Lernprogramm Verschlüsselungs-, Migrations- sowie Sicherungs- und Wiederherstellungsszenarien behandelt.  
  
 Dieses Lernprogramm ist in neun Lektionen aufgeteilt:  
  
 **[Lektion 1: Erstellen Azure Storage Kontos und Containers](../tutorials/lesson-1-create-windows-azure-storage-account-and-container.md)**  
 In dieser Lektion erstellen Sie ein Azure Storage Konto und einen Container.  
  
 **[Lektion 2. Erstellen einer Richtlinie für einen Container und generieren &#40;eines&#41; Shared Access Signature SAS-Schlüssels](lesson-1-create-stored-access-policy-and-shared-access-signature.md)**  
 In dieser Lektion erstellen Sie eine Richtlinie für den BLOB-Container und generieren zusätzlich eine SAS (Shared Access Signature, Signatur für gemeinsamen Zugriff).  
  
 **[Lektion 3: Erstellen eines SQL Server Anmelde Informationen](lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md)**  
 In dieser Lektion erstellen Sie Anmeldeinformationen, um die Sicherheitsinformationen für den Zugriff auf das Azure-Speicherkonto zu speichern.  
  
 **[Lektion 4: Erstellen einer Datenbank in Azure Storage](../relational-databases/lesson-3-database-backup-to-url.md)**  
 In dieser Lektion erstellen Sie eine Datenbank in Azure Storage mithilfe der Option Create Database filename.  
  
 **Lektion 5. &#40;Optionales&#41; Verschlüsseln der Datenbank mit TDE**  
 In dieser Lektion verschlüsseln Sie die Datenbank mithilfe einer transparenten Datenverschlüsselung (TDE) und eines Serverzertifikats.  
  
 **[Lektion 6: Migrieren einer Datenbank von einem lokalen Quellcomputer zu einem Zielcomputer in Azure](lesson-5-backup-database-using-file-snapshot-backup.md)**  
 In dieser Lektion migrieren Sie eine Datenbank von einem lokalen Standort zu einem virtuellen Computer in Azure mithilfe der Option Create Database for Attach.  
  
 **[Lektion 7: Verschieben Sie die Datendateien in Azure Storage](../relational-databases/lesson-6-generate-activity-and-backup-log-using-file-snapshot-backup.md)**  
 In dieser Lektion verschieben Sie die Datendateien mithilfe der ALTER DATABASE-Anweisung in Azure Storage.  
  
 **[Lektion 8: Wiederherstellen einer Datenbank auf Azure Storage](../relational-databases/lesson-7-restore-a-database-to-a-point-in-time.md)**  
 In dieser Lektion stellen Sie eine Datenbank mithilfe der Move-Option RESTORE DATABASE auf Azure Storage wieder her.  
  
 **[Lektion 9. Wiederherstellen einer Datenbank aus Azure Storage](lesson-8-restore-as-new-database-from-log-backup.md)**  
 In dieser Lektion stellen Sie eine Datenbank aus Azure Storage mithilfe der Option zum Verschieben von Datenbanken wieder her.  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server von Datendateien in Azure](databases/sql-server-data-files-in-microsoft-azure.md)  
  
  
