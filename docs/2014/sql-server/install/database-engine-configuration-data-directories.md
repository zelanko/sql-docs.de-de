---
title: Datenbank-Engine Konfiguration-Datenverzeichnisse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 9b1fa0fc-623b-479a-afc3-4f13bd850487
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: bfb62ec0bbd16a2b77e2f05f64d36ef31498a100
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66095901"
---
# <a name="database-engine-configuration---data-directories"></a>Konfiguration der Datenbank-Engine – Datenverzeichnisse
  Verwenden Sie diese Seite, um den Installationspfad für das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssDE](../../includes/ssde-md.md)]-Programm und die Datendateien anzugeben. Auf Grundlage des Typs der Installation schließt der unterstützte Speicher möglicherweise einen lokalen Datenträger, freigegebenen Speicher oder SMB-Dateiserver ein.  
  
 Um eine SMB-Dateifreigabe als Verzeichnis anzugeben, müssen Sie den unterstützten UNC-Pfad manuell eingeben. Das Navigieren zu einer SMB-Dateifreigabe wird nicht unterstützt. Das folgende Format ist ein unterstütztes UNC-Pfadformat einer SMB-Dateifreigabe: \\\\Servername\ShareName\\\...  
  
## <a name="stand-alone-instance-of-ssnoversion"></a>Eigenständige Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 In der folgenden Tabelle sind die unterstützten Speichertypen und die Standardverzeichnisse für eine eigenständige Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aufgeführt, die während des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Setups vom Benutzer konfigurierbar sind.  
  
## <a name="uielement-list"></a>Liste der Benutzeroberflächenelemente  
  
|Beschreibung|Unterstützter Speichertyp|Standardverzeichnis|Empfehlungen|  
|-----------------|----------------------------|-----------------------|---------------------|  
|Datenstammverzeichnis|Lokaler Datenträger, SMB-Datei Server, frei gegebener Speicher <sup>1</sup>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] C:\programmesetup [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \| konfiguriert ACLs für Verzeichnisse und unterbricht die Vererbung als Teil der Konfiguration.|  
|Benutzerdatenbankverzeichnis|Lokaler Datenträger, SMB-Datei Server, frei gegebener Speicher <sup>1</sup>|C:\Programme\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\mssql12. \<InstanceId> \MSSQL\Data|Welche Vorgehensweise für Benutzerdatenverzeichnisse empfohlen wird, hängt von der Arbeitsauslastung und den Leistungsanforderungen ab.|  
|Benutzerdatenbank-Protokollverzeichnis|Lokaler Datenträger, SMB-Datei Server, frei gegebener Speicher <sup>1</sup>|C:\Programme\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\mssql12. \<InstanceId> \MSSQL\Data|Stellen Sie sicher, dass ausreichend Speicherplatz für das Protokollverzeichnis verfügbar ist.|  
|Temporäres DB-Verzeichnis|Lokaler Datenträger, SMB-Datei Server, frei gegebener Speicher <sup>1</sup>|C:\Programme\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\mssql12. \<InstanceId> \MSSQL\Data|Welche Vorgehensweise für das Verzeichnis Temp empfohlen wird, hängt von der Arbeitsauslastung und den Leistungsanforderungen ab.|  
|Temporäres DB-Protokollverzeichnis|Lokaler Datenträger, SMB-Datei Server, frei gegebener Speicher <sup>1</sup>|C:\Programme\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\mssql12. \<InstanceId> \MSSQL\Data|Stellen Sie sicher, dass ausreichend Speicherplatz für das Protokollverzeichnis verfügbar ist.|  
|Sicherungsverzeichnis|Lokaler Datenträger, SMB-Datei Server, frei gegebener Speicher <sup>1</sup>|C:\Programme\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\mssql12. \<InstanceId> \mssql\backup|Legen Sie zur Vermeidung von Datenverlusten entsprechende Berechtigungen fest, und stellen Sie sicher, dass das Benutzerkonto für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Dienst über die erforderlichen Berechtigungen zum Schreiben im Sicherungsverzeichnis verfügt. Die Verwendung eines zugeordneten Laufwerks für Sicherungsverzeichnisse wird nicht unterstützt.|  
  
 <sup>1</sup> obwohl freigegebene Datenträger unterstützt werden, handelt es sich nicht um eine empfohlene Vorgehensweise für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]eine eigenständige Instanz von.  
  
## <a name="failover-cluster-instance-of-ssnoversion"></a>[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Failoverclusterinstanz  
 In der folgenden Tabelle sind die unterstützten Speichertypen und die Standardverzeichnisse für eine Failoverclusterinstanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aufgeführt, die während des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Setups vom Benutzer konfigurierbar sind.  
  
|Beschreibung|Unterstützter Speichertyp|Standardverzeichnis|Empfehlungen|  
|-----------------|----------------------------|-----------------------|---------------------|  
|Datenstammverzeichnis|Freigegebener Speicher, SMB-Dateiserver|\<Laufwerk:>\Programme\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\\<br /><br /> Tipp: Wenn "Freigegebener Datenträger" auf der Seite **Datenträgerauswahl für Cluster** ausgewählt wurde, ist der Standard der erste freigegebene Datenträger. Dieses Feld ist standardmäßig leer, wenn keine Auswahl auf der Seite **Datenträgerauswahl für Cluster** getroffen wurde.|Das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Setup konfiguriert Zugriffssteuerungslisten für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Verzeichnisse und unterbricht während der Konfiguration die Vererbung.|  
|Benutzerdatenbankverzeichnis|Freigegebener Speicher, SMB-Dateiserver|\<Laufwerk: >Programme\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\mssql12. \<InstanceId> \MSSQL\Data<br /><br /> Tipp: Wenn "Freigegebener Datenträger" auf der Seite **Datenträgerauswahl für Cluster** ausgewählt wurde, ist der Standard der erste freigegebene Datenträger. Dieses Feld ist standardmäßig leer, wenn keine Auswahl auf der Seite **Datenträgerauswahl für Cluster** getroffen wurde.|Welche Vorgehensweise für Benutzerdatenverzeichnisse empfohlen wird, hängt von der Arbeitsauslastung und den Leistungsanforderungen ab.|  
|Benutzerdatenbank-Protokollverzeichnis|Freigegebener Speicher, SMB-Dateiserver|\<Laufwerk: > \Programme\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\mssql12. \<InstanceId> \MSSQL\Data<br /><br /> Tipp: Wenn "Freigegebener Datenträger" auf der Seite **Datenträgerauswahl für Cluster** ausgewählt wurde, ist der Standard der erste freigegebene Datenträger. Dieses Feld ist standardmäßig leer, wenn keine Auswahl auf der Seite **Datenträgerauswahl für Cluster** getroffen wurde.|Stellen Sie sicher, dass ausreichend Speicherplatz für das Protokollverzeichnis verfügbar ist.|  
|Temporäres DB-Verzeichnis|Lokaler Datenträger, freigegebener Speicher, SMB-Dateiserver|\<Laufwerk: > \Programme\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\mssql12. \<InstanceId> \MSSQL\Data<br /><br /> Tipp: Wenn "Freigegebener Datenträger" auf der Seite **Datenträgerauswahl für Cluster** ausgewählt wurde, ist der Standard der erste freigegebene Datenträger. Dieses Feld ist standardmäßig leer, wenn keine Auswahl auf der Seite **Datenträgerauswahl für Cluster** getroffen wurde.|Stellen Sie sicher, dass das angegebene Verzeichnis für alle Clusterknoten gültig ist. Sind die tempdb-Verzeichnisse auf dem Failoverzielknoten während des Failovers nicht verfügbar, wird die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Ressource nicht online geschaltet.|  
|Temporäres DB-Protokollverzeichnis|Lokaler Datenträger, freigegebener Speicher, SMB-Dateiserver|\<Laufwerk: > \Programme\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\mssql12. \<InstanceId> \MSSQL\Data<br /><br /> Tipp: Wenn "Freigegebener Datenträger" auf der Seite **Datenträgerauswahl für Cluster** ausgewählt wurde, ist der Standard der erste freigegebene Datenträger. Dieses Feld ist standardmäßig leer, wenn keine Auswahl auf der Seite **Datenträgerauswahl für Cluster** getroffen wurde.|Stellen Sie sicher, dass das angegebene Verzeichnis für alle Clusterknoten gültig ist. Sind die tempdb-Verzeichnisse auf dem Failoverzielknoten während des Failovers nicht verfügbar, wird die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Ressource nicht online geschaltet.|  
|Sicherungsverzeichnis|Lokaler Datenträger, freigegebener Speicher, SMB-Dateiserver|\<Laufwerk: > \Programme\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\mssql12. \<InstanceId> \mssql\backup<br /><br /> Tipp: Wenn "Freigegebener Datenträger" auf der Seite **Datenträgerauswahl für Cluster** ausgewählt wurde, ist der Standard der erste freigegebene Datenträger. Dieses Feld ist standardmäßig leer, wenn keine Auswahl auf der Seite **Datenträgerauswahl für Cluster** getroffen wurde.|Legen Sie zur Vermeidung von Datenverlusten entsprechende Berechtigungen fest, und stellen Sie sicher, dass das Benutzerkonto für den SQL Server-Dienst über die erforderlichen Berechtigungen zum Schreiben im Sicherungsverzeichnis verfügt. Die Verwendung eines zugeordneten Laufwerks für Sicherungsverzeichnisse wird nicht unterstützt.|  
  
## <a name="security-considerations"></a>Überlegungen zur Sicherheit  
 Das Setup konfiguriert Zugriffssteuerungslisten für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Verzeichnisse und unterbricht während der Konfiguration die Vererbung.  
  
 Die folgenden Empfehlungen gelten für den SMB-Dateiserver:  
  
-   Das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienstkonto muss ein Domänenkonto sein, wenn ein SMB-Dateiserver verwendet wird.  
  
-   Das Konto, das verwendet wurde, um [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zu installieren, muss über FULL CONTROL NTFS-Berechtigungen für den als Datenverzeichnis verwendeten SMB-Dateifreigabeordner verfügen.  
  
-   Dem Konto, das für die Installation von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet wird, müssen SeSecurityPrivilege-Berechtigungen auf dem SMB-Dateiserver zugewiesen werden. Um diese Berechtigung zu erteilen, verwenden Sie die Konsole für lokale Sicherheitsrichtlinien auf dem Dateiserver [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , um das Setup Konto der Richtlinie zum Verwalten von Überwachungs **-und Sicherheitsprotokollen** hinzuzufügen. Diese Einstellung ist im Abschnitt **Zuweisen von Benutzerrechten** unter **Lokale Richtlinien** in der Konsole **Lokale Sicherheitsrichtlinie** verfügbar.  
  
## <a name="notes"></a>Notizen  
  
-   Wenn Sie Funktionen zu einer vorhandenen Installation hinzufügen, können Sie den Speicherort einer vorher installierten Funktion nicht ändern und auch keinen Speicherort für eine neue Funktion angeben.  
  
-   Wenn Sie keine Standardverzeichnisse angeben, sollten Sie sicherstellen, dass die Installationsordner nur für die Instanz [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verwendet werden. Keines der Verzeichnisse in diesem Dialogfeld sollte gemeinsam mit Verzeichnissen anderer Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]genutzt werden. Die [!INCLUDE[ssDE](../../includes/ssde-md.md)]- und [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Komponenten in einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sollten ebenfalls in separaten Verzeichnissen installiert werden.  
  
-   Programmdateien und Datendateien können in den folgenden Situationen nicht installiert werden:  
  
    -   Auf einem Wechseldatenträger  
  
    -   In einem Dateisystem, in dem die Komprimierung verwendet wird  
  
    -   In einem Verzeichnis, in dem sich Systemdateien befinden  
  
    -   Auf einem zugeordneten Netzlaufwerk auf einer Failoverclusterinstanz  
  
## <a name="see-also"></a>Weitere Informationen  
 [Dateispeicher Orte für Standard Instanzen und benannte Instanzen von SQL Server](../../../2014/sql-server/install/file-locations-for-default-and-named-instances-of-sql-server.md)   
 [Share and NTFS Permissions on a File Server (Share- und NTFS-Berechtigung für einen Dateiserver)](https://go.microsoft.com/fwlink/?LinkID=206571)  
  
  
