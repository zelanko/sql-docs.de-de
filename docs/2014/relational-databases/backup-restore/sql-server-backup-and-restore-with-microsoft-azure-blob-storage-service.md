---
title: SQL Server sichern und Wiederherstellen mit Azure BLOB Storage Dienst | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 6a0c9b6a-cf71-4311-82f2-12c445f63935
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4ba066136493c2a429b1193d9846f4183f781846
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84956480"
---
# <a name="sql-server-backup-and-restore-with-azure-blob-storage-service"></a>SQL Server-Sicherung und -Wiederherstellung mit dem Azure Blob Storage-Dienst
  Dieses Thema enthält eine Einführung [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in Sicherungen und Wiederherstellungen aus dem [Azure BLOB Storage-Dienst](https://www.windowsazure.com/develop/net/how-to-guides/blob-storage/). Außerdem finden Sie hier eine Zusammenfassung der Vorteile der Verwendung des Azure-BLOB-Dienstanbieter zum Speichern von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Sicherungen.  
  
 SQL Server unterstützt das Speichern von Sicherungen im Azure-BLOB-Speicherdienst auf folgende Weise:  
  
-   **Verwalten Sie Ihre Sicherungen in Azure:** Mithilfe derselben Methoden, die für die Sicherung auf einem Datenträger und Band verwendet werden, können Sie jetzt in Azure Storage sichern, indem Sie die URL als Sicherungs Ziel angeben.  Mithilfe dieser Funktion können Sie manuelle Sicherungen ausführen oder eine eigene Sicherungsstrategie konfigurieren, wie auch für einen lokalen Speicher oder andere externe Optionen. Diese Funktion wird auch als **SQL Server-Sicherung über URLs**bezeichnet. Weitere Informationen finden Sie unter [SQL Server Backup to URL](sql-server-backup-to-url.md). Diese Funktion ist in SQL Server 2012 SP1 CU2 oder höher verfügbar.  
  
    > [!NOTE]  
    >  Für SQL Server Versionen vor SQL Server 2014 können Sie das Add-in SQL Server Backup to Azure-Tool verwenden, um schnell und einfach Sicherungen in Azure Storage zu erstellen. Weitere Informationen finden Sie im [Download Center](https://go.microsoft.com/fwlink/?LinkID=324399).  
  
-   **Verwalten Sie SQL Server Sicherungen in Azure:** Konfigurieren Sie SQL Server, um die Sicherungsstrategie zu verwalten und Sicherungen für eine einzelne Datenbank oder mehrere Datenbanken zu planen oder um Standardwerte auf Instanzebene festzulegen. Diese Funktion wird als bezeichnet **[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]** . Weitere Informationen finden [Sie unter SQL Server verwaltete Sicherung in Azure](sql-server-managed-backup-to-microsoft-azure.md). Diese Funktion ist in SQL Server 2014 oder höher verfügbar.  
  
## <a name="benefits-of-using-the-azure-blob-service-for-ssnoversion-backups"></a>Vorteile der Verwendung des Azure-BLOB-Dienstanbieter für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Sicherungen  
  
-   Flexibler, zuverlässiger und unbegrenzter externer Speicher: das Speichern von Sicherungen im Azure-BLOB-Dienst kann eine bequeme, flexible und leicht zu verwendende externe Option sein. Das Einrichten eines Offsitespeichers für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherungen muss nicht schwieriger sein als das Bearbeiten vorhandener Skripts/Aufträge. Die räumliche Entfernung zwischen Offsitespeicher und Produktionsdatenbank ist in der Regel so groß, dass ein Notfall niemals Auswirkungen auf beide Standorte hat. Indem Sie den BLOB-Speicher auf geografisch verteilte Standorte replizieren, erhalten Sie bei einem Notfall, der die gesamte Region betreffen könnte, eine zusätzliche Schutzebene. Darüber hinaus sind Sicherungen an jedem Standort jederzeit verfügbar und können problemlos für die Wiederherstellung genutzt werden.  
  
-   Sicherungs Archiv: der Azure BLOB Storage-Dienst bietet eine bessere Alternative zur häufig verwendeten Band Option zum Archivieren von Sicherungen. Bandspeichermedien müssen unter gleichzeitiger Berücksichtigung von Sicherheitsvorkehrungen u. U. physisch an einen externen Standort umgelagert werden. Die Speicherung von Sicherungen in Azure Blob Storage stellt eine sofortige, hochverfügbare und dauerhafte Archivierungsoption dar.  
  
-   Kein zusätzlicher Aufwand für die Hardware Verwaltung: Es gibt keinen mehr Aufwand für die Hardware Verwaltung mit Azure-Diensten. Azure-Dienste verwalten die Hardware und stellen geografische Replikation für Redundanz und Schutz vor Hardwareausfällen zur Verfügung.  
  
-   Derzeit können für Instanzen von, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die auf einem virtuellen Azure-Computer ausgeführt werden, die Sicherung in Azure BLOB Storage-Dienste durch Erstellen angefügter Datenträger erfolgen. Die Anzahl der Datenträger, die Sie an einen virtuellen Azure-Computer anfügen können, ist jedoch begrenzt. Bei einer sehr großen Instanz beträgt die maximale Anzahl 16 Datenträger, während kleinere Instanzen weniger Datenträger unterstützen. Indem Sie eine direkte Sicherung auf Azure BLOB Storage aktivieren, können Sie den Grenzwert von 16 Datenträgern umgehen.  
  
     Außerdem ist die Sicherungsdatei, die jetzt im Azure BLOB Storage-Dienst gespeichert ist, direkt für eine lokale [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder eine andere, die auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] einem virtuellen Azure-Computer ausgeführt wird, verfügbar, ohne dass Datenbanken angefügt/getrennt oder die VHD heruntergeladen und angefügt werden muss.  
  
-   Kostenvorteile: Sie zahlen nur für den genutzten Dienst. Die Option kann genauso kosteneffizient wie eine externe Sicherungs-/Archivierungslösung sein. Weitere Informationen und Links finden Sie im Abschnitt [Überlegungen zur Azure-Abrechnung](#Billing) .  
  
##  <a name="azure-billing-considerations"></a><a name="Billing"></a>Überlegungen zur Azure-Abrechnung:  
 Wenn Sie die Azure-Speicherkosten verstehen, können Sie die Kosten für das Erstellen und Speichern von Sicherungen in Azure Vorhersagen.  
  
 Der [Azure-Preisrechner](https://go.microsoft.com/fwlink/?LinkId=277060) kann Ihnen helfen, ihre Kosten zu schätzen.  
  
 **Speicher:** Gebühren richten sich nach dem genutzten Speicherplatz sowie dem Grad der Redundanz und werden gestaffelt abgerechnet. Weitere Details und aktuelle Informationen finden Sie im Abschnitt **Datenverwaltung** des Artikels [Preisdetails](https://go.microsoft.com/fwlink/?LinkId=277059) .  
  
 **Datenübertragungen:** Eingehende Datenübertragungen an Azure sind kostenlos. Ausgehende Übertragungen werden nach Bandbreitennutzung und einer regionsspezifischen Staffelung berechnet. Weitere Informationen finden Sie im Abschnitt [Datenübertragungen](https://go.microsoft.com/fwlink/?LinkId=277061) des Artikels zu Preisdetails.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server-URL-Sicherung – bewährte Methoden und Problembehandlung](sql-server-backup-to-url-best-practices-and-troubleshooting.md)   
 [Sichern und Wiederherstellen von Systemdatenbanken &#40;SQL Server&#41;](back-up-and-restore-of-system-databases-sql-server.md)   
 [Tutorial: SQL Server sichern und Wiederherstellen Azure BLOB Storage Dienstanbieter](../tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service.md)   
 [SQL Server-Sicherung über URL](sql-server-backup-to-url.md)  
  
