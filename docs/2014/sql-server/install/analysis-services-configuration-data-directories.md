---
title: Analysis Services-Konfiguration – Datenverzeichnisse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: ef732855-b7af-4f40-a619-5573c1c354bb
author: heidisteen
ms.author: heidist
manager: craigg
ms.openlocfilehash: f01bec92621022c875ff43c479356df1a35b8157
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48147680"
---
# <a name="analysis-services-configuration---data-directories"></a>Konfigurationseigenschaften von Analysis Services – Datenverzeichnisse
  Die in der folgenden Tabelle angegebenen Standardverzeichnisse können beim Setup von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vom Benutzer konfiguriert werden: Die Berechtigung zum Zugriff auf diese Dateien wird den lokalen Administratoren und Mitgliedern der Sicherheitsgruppe SQLServerMSASUser $\<instance> gewährt, die während des Setups erstellt und bereitgestellt wird.  
  
## <a name="uielement-list"></a>Liste der Benutzeroberflächenelemente  
  
|Description|Standardverzeichnis|Empfehlungen|  
|-----------------|-----------------------|---------------------|  
|Datenstammverzeichnis|C:\Programme\Microsoft c:\Programme\Microsoft SQL Server\MSAS12. \<InstanceID > \OLAP\Data\|stellen Sie sicher, dass der Ordner "\Programme\Microsoft SQL Server\" durch entsprechend eingeschränkte Berechtigungen geschützt wird. Die Leistung von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ist in vielen Konfigurationen von der Leistung des Speichers abhängig, in dem sich das Datenverzeichnis befindet. Platzieren Sie dieses Verzeichnis im Speicher mit der höchsten Leistung, der mit dem System verknüpft ist. Stellen Sie für Failoverclusterinstallationen sicher, dass Datenverzeichnisse auf dem freigegebenen Datenträger platziert werden.|  
|Protokolldateiverzeichnis|C:\Programme\Microsoft c:\Programme\Microsoft SQL Server\MSAS12. \<InstanceID > \OLAP\Log\|Dies ist das Verzeichnis für [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Protokolldateien, und fügt das FlightRecorder-Protokoll. Wenn Sie die Dauer von Flight Recorder erhöhen, stellen Sie sicher, dass für das Protokollverzeichnis genügend Speicherplatz zur Verfügung steht.|  
|Temporäres Verzeichnis|C:\Programme\Microsoft c:\Programme\Microsoft SQL Server\MSAS12. \<InstanceID > \OLAP\Temp\|platzieren Sie das Temp-Verzeichnis auf der leistungsstarken Speichersubsystem.|  
|Sicherungsverzeichnis|C:\Programme\Microsoft c:\Programme\Microsoft SQL Server\MSAS12. \<InstanceID > \OLAP\Backup\|Dies ist das Verzeichnis für [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] standardsicherungsdateien. Bei einer PowerPivot für SharePoint-Installation werden in diesem Verzeichnis zudem die PowerPivot-Datendateien des PowerPivot-Systemdiensts zwischengespeichert.<br /><br /> Stellen Sie sicher, dass zur Vermeidung von Datenverlusten entsprechende Berechtigungen festgelegt wurden und die Benutzergruppe für den [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Dienst über die erforderlichen Berechtigungen zum Schreiben im Sicherungsverzeichnis verfügt. Die Verwendung eines zugeordneten Laufwerks für Sicherungsverzeichnisse wird nicht unterstützt.|  
  
## <a name="notes"></a>Hinweise  
  
-   Auf einer SharePoint-Farm bereitgestellte [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Instanzen speichern Anwendungsdateien, Datendateien und Eigenschaften in Inhaltsdatenbanken und Dienstanwendungsdatenbanken.  
  
-   Wenn Sie Funktionen zu einer vorhandenen Installation hinzufügen, können Sie den Speicherort einer vorher installierten Funktion nicht ändern und auch keinen Speicherort für eine neue Funktion angeben.  
  
-   Wenn Sie keine Standardverzeichnisse angeben, sollten Sie sicherstellen, dass die Installationsordner nur für die Instanz [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verwendet werden. Keines der Verzeichnisse in diesem Dialogfeld sollte gemeinsam mit Verzeichnissen anderer Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] genutzt werden. Die [!INCLUDE[ssDE](../../includes/ssde-md.md)] - und [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Komponenten in einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sollten ebenfalls in separaten Verzeichnissen installiert werden.  
  
-   Programmdateien und Datendateien können in den folgenden Situationen nicht installiert werden:  
  
    -   Auf einem Wechseldatenträger  
  
    -   In einem Dateisystem, in dem die Komprimierung verwendet wird  
  
    -   In einem Verzeichnis, in dem sich Systemdateien befinden  
  
## <a name="see-also"></a>Siehe auch  
 [Dateispeicherorte für Standard- und benannte Instanzen von SQL Server](../../../2014/sql-server/install/file-locations-for-default-and-named-instances-of-sql-server.md)  
  
  
