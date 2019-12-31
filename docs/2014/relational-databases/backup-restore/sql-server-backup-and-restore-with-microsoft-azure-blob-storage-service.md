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
manager: craigg
ms.openlocfilehash: 38c92e397c971f6e9976bb857c63410fa60b7e85
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75232433"
---
# <a name="sql-server-backup-and-restore-with-azure-blob-storage-service"></a>SQL Server-Sicherung und -Wiederherstellung mit dem Azure Blob Storage-Dienst
  Dieses Thema enthält [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eine Einführung in Sicherungen und Wiederherstellungen aus dem [Azure BLOB Storage-Dienst](https://www.windowsazure.com/develop/net/how-to-guides/blob-storage/). Außerdem finden Sie hier eine Zusammenfassung der Vorteile der Verwendung des Azure-BLOB- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Dienstanbieter zum Speichern von Sicherungen.  
  
 SQL Server unterstützt das Speichern von Sicherungen im Azure-BLOB-Speicherdienst auf folgende Weise:  
  
-   **Verwalten Sie Ihre Sicherungen in Azure:** Mithilfe derselben Methoden, die für die Sicherung auf einem Datenträger und Band verwendet werden, können Sie jetzt in Azure Storage sichern, indem Sie die URL als Sicherungs Ziel angeben.  Mithilfe dieser Funktion können Sie manuelle Sicherungen ausführen oder eine eigene Sicherungsstrategie konfigurieren, wie auch für einen lokalen Speicher oder andere externe Optionen. Diese Funktion wird auch als **SQL Server-Sicherung über URLs**bezeichnet. Weitere Informationen finden Sie unter [SQL Server-URL-Sicherung](sql-server-backup-to-url.md). Diese Funktion ist in SQL Server 2012 SP1 CU2 oder höher verfügbar.  
  
    > [!NOTE]  
    >  Für SQL Server Versionen vor SQL Server 2014 können Sie das Add-in SQL Server Backup to Azure-Tool verwenden, um schnell und einfach Sicherungen in Azure Storage zu erstellen. Weitere Informationen finden Sie im [Download Center](https://go.microsoft.com/fwlink/?LinkID=324399).  
  
-   **Verwalten Sie SQL Server Sicherungen in Azure:** Konfigurieren Sie SQL Server, um die Sicherungsstrategie zu verwalten und Sicherungen für eine einzelne Datenbank oder mehrere Datenbanken zu planen oder um Standardwerte auf Instanzebene festzulegen. Diese Funktion wird als **[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]** bezeichnet. Weitere Informationen finden [Sie unter SQL Server verwaltete Sicherung in Azure](sql-server-managed-backup-to-microsoft-azure.md). Diese Funktion ist in SQL Server 2014 oder höher verfügbar.  
  
## <a name="benefits-of-using-the-azure-blob-service-for-includessnoversionincludesssnoversion-mdmd-backups"></a>Vorteile der Verwendung des Azure-BLOB- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Dienstanbieter für Sicherungen  
  
-   Flexibler, zuverlässiger und unbegrenzter externer Speicher: das Speichern von Sicherungen im Azure-BLOB-Dienst kann eine bequeme, flexible und leicht zu verwendende externe Option sein. Das Einrichten eines Offsitespeichers für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherungen muss nicht schwieriger sein als das Bearbeiten vorhandener Skripts/Aufträge. Offsitespeicher sollte normalerweise weit genug vom Standort der Produktionsdatenbank entfernt sein, um zu verhindern, dass ein einziger Notfall sich auf beide Standorte (den des Offsitespeichers und den der Produktionsdatenbank) auswirkt. Indem Sie den BLOB-Speicher auf geografisch verteilte Standorte replizieren, erhalten Sie bei einem Notfall, der die gesamte Region betreffen könnte, eine zusätzliche Schutzebene. Darüber hinaus sind Sicherungen an jedem Standort jederzeit verfügbar und können problemlos für die Wiederherstellung genutzt werden.  
  
-   Sicherungs Archiv: der Azure BLOB Storage-Dienst bietet eine bessere Alternative zur häufig verwendeten Band Option zum Archivieren von Sicherungen. Bandspeicher muss ggf. physisch an einen Offsitestandort transportiert werden und erfordert Schutzmaßnahmen für die Medien. Die Speicherung von Sicherungen in Azure Blob Storage stellt eine sofortige, hochverfügbare und dauerhafte Archivierungsoption dar.  
  
-   Kein zusätzlicher Aufwand für die Hardware Verwaltung: Es gibt keinen mehr Aufwand für die Hardware Verwaltung mit Azure-Diensten. Azure-Dienste verwalten die Hardware und stellen geografische Replikation für Redundanz und Schutz vor Hardwareausfällen zur Verfügung.  
  
-   Derzeit können für Instanzen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von, die auf einem virtuellen Azure-Computer ausgeführt werden, die Sicherung in Azure BLOB Storage-Dienste durch Erstellen angefügter Datenträger erfolgen. Die Anzahl der Datenträger, die Sie an einen virtuellen Azure-Computer anfügen können, ist jedoch begrenzt. Bei einer sehr großen Instanz beträgt die maximale Anzahl 16 Datenträger, während kleinere Instanzen weniger Datenträger unterstützen. Indem Sie eine direkte Sicherung auf Azure BLOB Storage aktivieren, können Sie den Grenzwert von 16 Datenträgern umgehen.  
  
     Außerdem ist die Sicherungsdatei, die jetzt im Azure BLOB Storage-Dienst gespeichert ist, direkt für eine lokale [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder eine andere [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , die auf einem virtuellen Azure-Computer ausgeführt wird, verfügbar, ohne dass Datenbanken angefügt/getrennt oder die VHD heruntergeladen und angefügt werden muss.  
  
-   Kostenvorteile: Sie zahlen nur für den genutzten Dienst. Die Option kann genauso kosteneffizient wie eine Offsitesicherungs-/-archivierungslösung sein. Weitere Informationen und Links finden Sie im Abschnitt [Überlegungen zur Azure-Abrechnung](#Billing) .  
  
##  <a name="Billing"></a>Überlegungen zur Azure-Abrechnung:  
 Wenn Sie die Azure-Speicherkosten verstehen, können Sie die Kosten für das Erstellen und Speichern von Sicherungen in Azure Vorhersagen.  
  
 Der [Azure-Preisrechner](https://go.microsoft.com/fwlink/?LinkId=277060) kann Ihnen helfen, ihre Kosten zu schätzen.  
  
 **Speicher:** Die Gebühren basieren auf dem verwendeten Speicherplatz und werden anhand einer gestaffelten Skala und der Redundanz Ebene berechnet. Weitere Details und aktuelle Informationen finden Sie im Abschnitt **Datenverwaltung** des Artikels [Preisdetails](https://go.microsoft.com/fwlink/?LinkId=277059) .  
  
 **Datenübertragungen:** Eingehende Datenübertragungen an Azure sind kostenlos. Ausgehende Übertragungen werden nach Bandbreitennutzung und einer regionsspezifischen Staffelung berechnet. Weitere Informationen finden Sie im Abschnitt [Datenübertragungen](https://go.microsoft.com/fwlink/?LinkId=277061) des Artikels zu Preisdetails.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Bewährte Methoden und Problembehandlung bei der SQL Server Backup-URL](sql-server-backup-to-url-best-practices-and-troubleshooting.md)   
 [Sichern und Wiederherstellen von System Datenbanken &#40;SQL Server&#41;](back-up-and-restore-of-system-databases-sql-server.md)   
 [Tutorial: SQL Server sichern und Wiederherstellen Azure BLOB Storage Dienstanbieter](../tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service.md)   
 [SQL Server Sicherung auf URL](sql-server-backup-to-url.md)  
  
