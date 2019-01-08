---
title: SQL Server-Sicherung und-Wiederherstellung mit Windows Azure Blob Storage-Dienst | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 6a0c9b6a-cf71-4311-82f2-12c445f63935
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 52f1bdf9e748625e1310210c98beeb4401a5dd81
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/13/2018
ms.locfileid: "53353151"
---
# <a name="sql-server-backup-and-restore-with-windows-azure-blob-storage-service"></a>SQL Server-Sicherung und -Wiederherstellung mit dem Windows Azure-BLOB-Speicherdienst
  In diesem Thema werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherung und-Wiederherstellung aus der [Windows Azure-Blob-Speicherdienst](http://www.windowsazure.com/develop/net/how-to-guides/blob-storage/). Darüber hinaus werden die Vorteile zusammengefasst, die die Verwendung des Windows Azure-BLOB-Diensts bei der Speicherung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Sicherungen bietet.  
  
 SQL Server unterstützt das Speichern von Sicherungen im Windows Azure-BLOB-Speicherdienst auf folgende Weise:  
  
-   **Verwalten von Sicherungen in Windows Azure:** Mithilfe derselben Methoden, die für DISK- und TAPE-Sicherungen verwendet werden, können Sie jetzt im Microsoft Azure-Speicher sichern, indem Sie die URL als Sicherungsziel angeben.  Mithilfe dieser Funktion können Sie manuelle Sicherungen ausführen oder eine eigene Sicherungsstrategie konfigurieren, wie auch für einen lokalen Speicher oder andere externe Optionen. Diese Funktion wird auch als **SQL Server-Sicherung über URLs**bezeichnet. Weitere Informationen finden Sie unter [SQL Server Backup to URL](sql-server-backup-to-url.md). Diese Funktion ist in SQL Server 2012 SP1 CU2 oder höher verfügbar.  
  
    > [!NOTE]  
    >  Für SQL Server-Versionen vor SQL Server 2014 können Sie das Add-In SQL Server Backup to Windows Azure Tool verwenden, um Sicherungen schnell und einfach im Windows Azure-Speicher zu erstellen. Weitere Informationen finden Sie im [Download Center](https://go.microsoft.com/fwlink/?LinkID=324399).  
  
-   **Verwalten von SQL Server-Sicherungen in Microsoft Azure können Sie:** Mit dieser Funktion können Sie SQL Server konfigurieren, um die Sicherungsstrategie zu verwalten und Sicherungen für eine einzelne oder mehrere Datenbanken zu planen oder um Standardwerte auf Instanzebene festzulegen. Dieses Feature wird als bezeichnet **[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]**. Weitere Informationen finden Sie unter [SQL Server Managed Backup für Windows Azure](sql-server-managed-backup-to-microsoft-azure.md). Diese Funktion ist in SQL Server 2014 oder höher verfügbar.  
  
## <a name="benefits-of-using-the-windows-azure-blob-service-for-includessnoversionincludesssnoversion-mdmd-backups"></a>Vorteile bei der Verwendung des Windows Azure-BLOB-Diensts für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Sicherungen  
  
-   Flexibler, zuverlässiger und unbegrenzter externer Speicher: Die Speicherung von Sicherungen im Microsoft Azure-BLOB-Dienst ist eine bequeme, flexible und benutzerfreundliche Möglichkeit, Daten extern zu speichern. Das Einrichten eines Offsitespeichers für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherungen muss nicht schwieriger sein als das Bearbeiten vorhandener Skripts/Aufträge. Die räumliche Entfernung zwischen Offsitespeicher und Produktionsdatenbank ist in der Regel so groß, dass ein Notfall niemals Auswirkungen auf beide Standorte hat. Indem Sie den BLOB-Speicher auf geografisch verteilte Standorte replizieren, erhalten Sie bei einem Notfall, der die gesamte Region betreffen könnte, eine zusätzliche Schutzebene. Darüber hinaus sind Sicherungen an jedem Standort jederzeit verfügbar und können problemlos für die Wiederherstellung genutzt werden.  
  
-   Sicherungsarchiv: Der Microsoft Azure-BLOB-Speicherdienst bietet eine bessere Alternative zur Bandsicherung, die häufig zum Archivieren von Sicherungen verwendet wird. Bandspeichermedien müssen unter gleichzeitiger Berücksichtigung von Sicherheitsvorkehrungen u. U. physisch an einen externen Standort umgelagert werden. Die Speicherung von Sicherungen im Windows Azure-BLOB-Speicher ist eine direkte, hoch verfügbare und dauerhafte Archivierungslösung für Ihre Daten.  
  
-   Keine zusätzliche Hardwareverwaltung: Mit Windows Azure-Diensten entsteht kein Mehraufwand durch die Hardwareverwaltung. Windows Azure-Dienste übernehmen die Hardwareverwaltung und ermöglichen die Georeplikation, um Redundanz und Schutz vor Hardwarefehlern zu gewährleisten.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanzen, die auf einem virtuellen Windows Azure-Computer ausgeführt werden, können derzeit unter Verwendung von Windows Azure-BLOB-Speicherdiensten gesichert werden, indem angefügte Datenträger erstellt werden. Die Anzahl der Datenträger, die an einen virtuellen Computer in Windows Azure angefügt werden können, ist allerdings begrenzt. Bei einer sehr großen Instanz beträgt die maximale Anzahl 16 Datenträger, während kleinere Instanzen weniger Datenträger unterstützen. Die Beschränkung auf 16 Datenträger kann durch eine direkte Sicherung im Windows Azure-BLOB-Speicher umgangen werden.  
  
     Darüber hinaus steht die Sicherungsdatei, die jetzt im Windows Azure-BLOB-Speicherdienst gespeichert wird, direkt einem lokalen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder einem anderen, auf einem virtuellen Computer in Windows Azure ausgeführten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zur Verfügung, ohne dass Datenbanken angefügt/getrennt oder die VHD heruntergeladen und angefügt werden muss.  
  
-   Kostenvorteile: Sie zahlen nur für den genutzten Dienst. Die Option kann genauso kosteneffizient wie eine externe Sicherungs-/Archivierungslösung sein. Finden Sie unter den [Windows Azure Überlegungen zur Abrechnung](#Billing) Abschnitt, um weitere Informationen und Links.  
  
##  <a name="Billing"></a> Überlegungen zur Abrechnung in Windows Azure:  
 Auf Grundlage der Speicherkosten für Windows Azure können Sie die Kosten für die Erstellung und Speicherung von Sicherungen in Windows Azure ableiten.  
  
 Die [Windows Azure-Preisrechner](https://go.microsoft.com/fwlink/?LinkId=277060) können Ihre Kosten zu schätzen.  
  
 **Speicher:** Gebühren richten sich nach dem genutzten Speicherplatz sowie dem Grad der Redundanz und werden gestaffelt abgerechnet. Weitere Details und aktuelle Informationen finden Sie im Abschnitt **Datenverwaltung** des Artikels [Preisdetails](https://go.microsoft.com/fwlink/?LinkId=277059) .  
  
 **Datenübertragungen:** In Microsoft Azure eingehende Datenübertragungen sind kostenfrei. Ausgehende Übertragungen werden nach Bandbreitennutzung und einer regionsspezifischen Staffelung berechnet. Weitere Informationen finden Sie im Abschnitt [Datenübertragungen](https://go.microsoft.com/fwlink/?LinkId=277061) des Artikels zu Preisdetails.  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server-URL-Sicherung – bewährte Methoden und Problembehandlung](sql-server-backup-to-url-best-practices-and-troubleshooting.md)   
 [Sichern und Wiederherstellen von Systemdatenbanken &#40;SQL Server&#41;](back-up-and-restore-of-system-databases-sql-server.md)   
 [Tutorial: SQL Server-Sicherung und-Wiederherstellung im Windows Azure-Blob-Speicherdienst](../tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service.md)   
 [SQL Server-Sicherung über URLs](sql-server-backup-to-url.md)  
  
  
