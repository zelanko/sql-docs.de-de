---
title: Datenbank-Engine – Serverkonfiguration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 9b1fa0fc-623b-479a-afc3-4f13bd850487
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0b223c3ef9c6b4a8085c6575f827ae5e9e276ad9
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/13/2018
ms.locfileid: "53365512"
---
# <a name="database-engine-configuration---data-directories"></a>Konfiguration der Datenbank-Engine – Datenverzeichnisse
  Verwenden Sie diese Seite, um den Installationspfad für das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssDE](../../includes/ssde-md.md)]-Programm und die Datendateien anzugeben. Auf Grundlage des Typs der Installation schließt der unterstützte Speicher möglicherweise einen lokalen Datenträger, freigegebenen Speicher oder SMB-Dateiserver ein.  
  
 Um eine SMB-Dateifreigabe als Verzeichnis anzugeben, müssen Sie den unterstützten UNC-Pfad manuell eingeben. Das Navigieren zu einer SMB-Dateifreigabe wird nicht unterstützt. Das folgende Format ist ein unterstütztes UNC-Pfadformat einer SMB-Dateifreigabe: \\\\Servername\ShareName\\\...  
  
## <a name="stand-alone-instance-of-includessnoversionincludesssnoversion-mdmd"></a>Eigenständige Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 In der folgenden Tabelle sind die unterstützten Speichertypen und die Standardverzeichnisse für eine eigenständige Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aufgeführt, die während des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Setups vom Benutzer konfigurierbar sind.  
  
## <a name="uielement-list"></a>Liste der Benutzeroberflächenelemente  
  
|Description|Unterstützter Speichertyp|Standardverzeichnis|Empfehlungen|  
|-----------------|----------------------------|-----------------------|---------------------|  
|Datenstammverzeichnis|Lokaler Datenträger, SMB-Dateiserver, freigegebener Speicher <sup>1</sup>|C:\Program Files\\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \| [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup konfiguriert Zugriffssteuerungslisten für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Verzeichnisse und unterbricht die Vererbung im Rahmen der Konfiguration.|  
|Benutzerdatenbankverzeichnis|Lokaler Datenträger, SMB-Dateiserver, freigegebener Speicher <sup>1</sup>|C:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL12.\< InstanceID > \MSSQL\Data|Welche Vorgehensweise für Benutzerdatenverzeichnisse empfohlen wird, hängt von der Arbeitsauslastung und den Leistungsanforderungen ab.|  
|Benutzerdatenbank-Protokollverzeichnis|Lokaler Datenträger, SMB-Dateiserver, freigegebener Speicher <sup>1</sup>|C:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL12.\< InstanceID > \MSSQL\Data|Stellen Sie sicher, dass ausreichend Speicherplatz für das Protokollverzeichnis verfügbar ist.|  
|Temporäres DB-Verzeichnis|Lokaler Datenträger, SMB-Dateiserver, freigegebener Speicher <sup>1</sup>|C:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL12.\< InstanceID > \MSSQL\Data|Welche Vorgehensweise für das Verzeichnis Temp empfohlen wird, hängt von der Arbeitsauslastung und den Leistungsanforderungen ab.|  
|Temporäres DB-Protokollverzeichnis|Lokaler Datenträger, SMB-Dateiserver, freigegebener Speicher <sup>1</sup>|C:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL12.\< InstanceID > \MSSQL\Data|Stellen Sie sicher, dass ausreichend Speicherplatz für das Protokollverzeichnis verfügbar ist.|  
|Sicherungsverzeichnis|Lokaler Datenträger, SMB-Dateiserver, freigegebener Speicher <sup>1</sup>|C:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL12.\< InstanceID > \MSSQL\Backup|Legen Sie zur Vermeidung von Datenverlusten entsprechende Berechtigungen fest, und stellen Sie sicher, dass das Benutzerkonto für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Dienst über die erforderlichen Berechtigungen zum Schreiben im Sicherungsverzeichnis verfügt. Die Verwendung eines zugeordneten Laufwerks für Sicherungsverzeichnisse wird nicht unterstützt.|  
  
 <sup>1</sup> Obwohl freigegebene Datenträger unterstützt werden, ist es nicht empfohlen für eine eigenständige Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="failover-cluster-instance-of-includessnoversionincludesssnoversion-mdmd"></a>[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Failoverclusterinstanz  
 In der folgenden Tabelle sind die unterstützten Speichertypen und die Standardverzeichnisse für eine Failoverclusterinstanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aufgeführt, die während des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Setups vom Benutzer konfigurierbar sind.  
  
|Description|Unterstützter Speichertyp|Standardverzeichnis|Empfehlungen|  
|-----------------|----------------------------|-----------------------|---------------------|  
|Datenstammverzeichnis|Freigegebener Speicher, SMB-Dateiserver|\<Laufwerk:>\Programme\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\\<br /><br /> Tipp: Wenn freigegebener Datenträger ausgewählt wurde, auf die **Datenträgerauswahl für Cluster** Seite, der Standardwert ist der erste freigegebene Datenträger. Dieses Feld ist standardmäßig leer, wenn keine Auswahl auf der Seite **Datenträgerauswahl für Cluster** getroffen wurde.|Das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Setup konfiguriert Zugriffssteuerungslisten für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Verzeichnisse und unterbricht während der Konfiguration die Vererbung.|  
|Benutzerdatenbankverzeichnis|Freigegebener Speicher, SMB-Dateiserver|\<Laufwerk: > Programme\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL12.\< InstanceID > \MSSQL\Data<br /><br /> Tipp: Wenn freigegebener Datenträger ausgewählt wurde, auf die **Datenträgerauswahl für Cluster** Seite, der Standardwert ist der erste freigegebene Datenträger. Dieses Feld ist standardmäßig leer, wenn keine Auswahl auf der Seite **Datenträgerauswahl für Cluster** getroffen wurde.|Welche Vorgehensweise für Benutzerdatenverzeichnisse empfohlen wird, hängt von der Arbeitsauslastung und den Leistungsanforderungen ab.|  
|Benutzerdatenbank-Protokollverzeichnis|Freigegebener Speicher, SMB-Dateiserver|\<Laufwerk: > \Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL12.\< InstanceID > \MSSQL\Data<br /><br /> Tipp: Wenn freigegebener Datenträger ausgewählt wurde, auf die **Datenträgerauswahl für Cluster** Seite, der Standardwert ist der erste freigegebene Datenträger. Dieses Feld ist standardmäßig leer, wenn keine Auswahl auf der Seite **Datenträgerauswahl für Cluster** getroffen wurde.|Stellen Sie sicher, dass ausreichend Speicherplatz für das Protokollverzeichnis verfügbar ist.|  
|Temporäres DB-Verzeichnis|Lokaler Datenträger, freigegebener Speicher, SMB-Dateiserver|\<Laufwerk: > \Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL12.\< InstanceID > \MSSQL\Data<br /><br /> Tipp: Wenn freigegebener Datenträger ausgewählt wurde, auf die **Datenträgerauswahl für Cluster** Seite, der Standardwert ist der erste freigegebene Datenträger. Dieses Feld ist standardmäßig leer, wenn keine Auswahl auf der Seite **Datenträgerauswahl für Cluster** getroffen wurde.|Stellen Sie sicher, dass das angegebene Verzeichnis für alle Clusterknoten gültig ist. Sind die tempdb-Verzeichnisse auf dem Failoverzielknoten während des Failovers nicht verfügbar, wird die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Ressource nicht online geschaltet.|  
|Temporäres DB-Protokollverzeichnis|Lokaler Datenträger, freigegebener Speicher, SMB-Dateiserver|\<Laufwerk: > \Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL12.\< InstanceID > \MSSQL\Data<br /><br /> Tipp: Wenn freigegebener Datenträger ausgewählt wurde, auf die **Datenträgerauswahl für Cluster** Seite, der Standardwert ist der erste freigegebene Datenträger. Dieses Feld ist standardmäßig leer, wenn keine Auswahl auf der Seite **Datenträgerauswahl für Cluster** getroffen wurde.|Stellen Sie sicher, dass das angegebene Verzeichnis für alle Clusterknoten gültig ist. Sind die tempdb-Verzeichnisse auf dem Failoverzielknoten während des Failovers nicht verfügbar, wird die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Ressource nicht online geschaltet.|  
|Sicherungsverzeichnis|Lokaler Datenträger, freigegebener Speicher, SMB-Dateiserver|\<Laufwerk: > \Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL12.\< InstanceID > \MSSQL\Backup<br /><br /> Tipp: Wenn freigegebener Datenträger ausgewählt wurde, auf die **Datenträgerauswahl für Cluster** Seite, der Standardwert ist der erste freigegebene Datenträger. Dieses Feld ist standardmäßig leer, wenn keine Auswahl auf der Seite **Datenträgerauswahl für Cluster** getroffen wurde.|Legen Sie zur Vermeidung von Datenverlusten entsprechende Berechtigungen fest, und stellen Sie sicher, dass das Benutzerkonto für den SQL Server-Dienst über die erforderlichen Berechtigungen zum Schreiben im Sicherungsverzeichnis verfügt. Die Verwendung eines zugeordneten Laufwerks für Sicherungsverzeichnisse wird nicht unterstützt.|  
  
## <a name="security-considerations"></a>Überlegungen zur Sicherheit  
 Das Setup konfiguriert Zugriffssteuerungslisten für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Verzeichnisse und unterbricht während der Konfiguration die Vererbung.  
  
 Die folgenden Empfehlungen gelten für den SMB-Dateiserver:  
  
-   Das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienstkonto muss ein Domänenkonto sein, wenn ein SMB-Dateiserver verwendet wird.  
  
-   Das Konto, das verwendet wurde, um [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zu installieren, muss über FULL CONTROL NTFS-Berechtigungen für den als Datenverzeichnis verwendeten SMB-Dateifreigabeordner verfügen.  
  
-   Dem Konto, das für die Installation von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet wird, müssen SeSecurityPrivilege-Berechtigungen auf dem SMB-Dateiserver zugewiesen werden. Diese Berechtigung weisen Sie zu, indem Sie die Konsole "Lokale Sicherheitsrichtlinie" auf dem Dateiserver verwenden, um der Richtlinie zum [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verwalten von Überwachungs- und Sicherheitsprotokollen **das** -Setupkonto hinzuzufügen. Diese Einstellung ist im Abschnitt **Zuweisen von Benutzerrechten** unter **Lokale Richtlinien** in der Konsole **Lokale Sicherheitsrichtlinie** verfügbar.  
  
## <a name="notes"></a>Hinweise  
  
-   Wenn Sie Funktionen zu einer vorhandenen Installation hinzufügen, können Sie den Speicherort einer vorher installierten Funktion nicht ändern und auch keinen Speicherort für eine neue Funktion angeben.  
  
-   Wenn Sie keine Standardverzeichnisse angeben, sollten Sie sicherstellen, dass die Installationsordner nur für die Instanz [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verwendet werden. Keines der Verzeichnisse in diesem Dialogfeld sollte gemeinsam mit Verzeichnissen anderer Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] genutzt werden. Die [!INCLUDE[ssDE](../../includes/ssde-md.md)] - und [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Komponenten in einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sollten ebenfalls in separaten Verzeichnissen installiert werden.  
  
-   Programmdateien und Datendateien können in den folgenden Situationen nicht installiert werden:  
  
    -   Auf einem Wechseldatenträger  
  
    -   In einem Dateisystem, in dem die Komprimierung verwendet wird  
  
    -   In einem Verzeichnis, in dem sich Systemdateien befinden  
  
    -   Auf einem zugeordneten Netzlaufwerk auf einer Failoverclusterinstanz  
  
## <a name="see-also"></a>Siehe auch  
 [Dateispeicherorte für Standard- und benannte Instanzen von SQL Server](../../../2014/sql-server/install/file-locations-for-default-and-named-instances-of-sql-server.md)   
 [Share and NTFS Permissions on a File Server (Share- und NTFS-Berechtigung für einen Dateiserver)](https://go.microsoft.com/fwlink/?LinkID=206571)  
  
  
