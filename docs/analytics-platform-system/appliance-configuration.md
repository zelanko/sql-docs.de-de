---
title: Checklisten für die Konfiguration
description: Enthält Checklisten für die Aufgaben, die erforderlich sind, um Analytics Platform System für Ihre eigene Umgebung zu konfigurieren. Diese Konfigurationsaufgaben sind erforderlich, bevor Sie das Gerät verwenden können.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 80fc899400be167badaae9d617d43a61e0d346b5
ms.sourcegitcommit: d587a141351e59782c31229bccaa0bff2e869580
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/22/2019
ms.locfileid: "74401467"
---
# <a name="appliance-configuration-checklists-for-analytics-platform-system"></a>Checklisten für die Gerätekonfiguration für Analytics Platform System
Enthält Checklisten für die Aufgaben, die erforderlich sind, um Analytics Platform System für Ihre eigene Umgebung zu konfigurieren. Diese Konfigurationsaufgaben sind erforderlich, bevor Sie das Gerät verwenden können.  
  
> [!WARNING]  
> Die Verwendung von Analytics Platform System**Configuration Manager** ist die beste Methode und die einzige unterstützte Methode, die im Tool verfügbaren Aufgaben auszuführen.  
  
## <a name="BeforeTasks"></a>Bevor Sie beginnen  
  
### <a name="prerequisites"></a>Voraussetzungen  
  
1.  Die Appliance muss im Rechenzentrum installiert und eingeschaltet werden.  
  
2.  Stellen Sie sicher, dass Sie über die folgenden Informationen verfügen, die von Ihrem IHV bereitgestellt werden:  
  
    -   Externe IP-Adresse für den PDW-Steuerungs Knoten (*PDW_region-* CTL01)  
  
    -   Anwendungs Domänen Name  
  
    -   Benutzername und Kennwort für den Anwendungs Domänen Administrator  
  
3.  Abrufen eines vertrauenswürdigen Zertifikats Dies importieren Sie in einem späteren Schritt, damit Clients eine Verbindung mit der **Verwaltungskonsole** mit sicheren Verbindungen herstellen können. Speichern Sie das Zertifikat auf dem Steuerungs Knoten in einer Kenn Wort geschützten PFX-Datei.  
  
4.  Starten Sie die **Configuration Manager**, indem Sie die folgenden Schritte ausführen:  
  
    1.  Verwenden Sie **Remotedesktop** , um eine Verbindung mit dem PDW-Steuerungs Knoten (*PDW_region*-CTL01) herzustellen. (Möglicherweise müssen Sie eine Verbindung mit der externen IP-Adresse für CTL01 herstellen.)  
  
    2.  Starten Sie den **Configuration Manager** über das **Startmenü** des PDW-Steuerelement Knotens. Auf dem ersten Bildschirm des Configuration Manager wird die Geräte Topologie angezeigt, die von Ihrem IHV erstellt wurde. Es handelt sich um eine Liste der Hardware Knoten, die von Ihrer SQL Server PDW Software als Teil Ihrer Appliance erkannt werden. Sie sollten keine Einstellungen auf dem Bildschirm "Geräte Topologie" ändern.  
  
## <a name="CMTasks"></a>Ausführen von Configuration Manager Tasks  
Der SQL Server PDW**Configuration Manager** (pdwcm) ist ein Tool zum Verwalten von Geräten, das SQL Server PDW Systemadministratoren zum Ausführen von Vorgängen auf Geräteebene und zum Ändern der Einstellungen auf Geräteebene verwenden. Verwenden Sie z. b. pdwcm, um Kenn Wörter zurückzusetzen, die Zeitzone festzulegen, IP-Adressen zu ändern, SSL-Zertifikate zu aktivieren, den Remote Zugriff über die Firewall zu aktivieren, die Appliance zu starten oder anzuhalten und die sofortige Datei Initialisierung festzulegen.  
  
Verwenden Sie **Configuration Manager** , um die folgenden Konfigurationsaufgaben auszuführen.  
  
|Konfigurationstask|Beschreibung|  
|----------------------|---------------|  
|Machen Sie sich mit den Namen der physischen Komponenten vertraut.|[PDW und Appliance Fabric physische Komponenten &#40;Analytics Platform System&#41;](pdw-and-appliance-fabric-physical-components.md)|  
|Starten Sie SQL Server PDW Configuration Manager|[Starten Sie die Configuration Manager &#40;Analytics-Platt Form System&#41;](launch-the-configuration-manager.md)|  
|Ändern des Domänen Administrator Kennworts|Das Gerät verfügt über eine private Windows-Active Directory Domain Services, die verwendet wird, um Knoten innerhalb des Geräts zu authentifizieren.<br /><br />Ihr IHV hat das Gerät mit einem Standard Kennwort für den Domänen Administrator eingerichtet. Dies muss in ein sicheres Kennwort geändert werden.<br /><br />Der **Configuration Manager** ist die einzige Möglichkeit, das Domänen Administrator Kennwort zu ändern.<br /><br />Weitere Informationen finden Sie unter [Zurücksetzen von Kenn Wörtern &#40;Analytics Platform System&#41;](password-reset.md).|  
|Ändern des Kennworts für die **sa** -Anmeldung|SQL Server PDW hat eine Systemadministrator Anmeldung mit dem Namen **sa**. Die **sa** -Anmeldung verfügt über alle Berechtigungen. Sie kann jegliche Berechtigung erteilen, verweigern oder widerrufen. Außerdem werden alle System Sichten angezeigt.<br /><br />Weitere Informationen finden Sie unter [Zurücksetzen von Kenn Wörtern &#40;Analytics Platform System&#41;](password-reset.md).|  
|Festlegen der Zeitzone für die Appliance|Legen Sie die Uhrzeit (lokal oder eine andere gewünschte Zeit) für alle Geräteknoten fest.<br /><br />Weitere Informationen finden Sie unter [Appliance Time Zone Configuration &#40;Analytics Platform System&#41;](appliance-time-zone-configuration.md).|  
|Angeben der extern ausgerichteten Netzwerkeinstellungen für das SQL Server PDW Appliance|[Geräte Netzwerkkonfiguration &#40;Analytics-Platt Form System&#41;](appliance-network-configuration.md)|  
|Importieren eines Sicherheitszertifikats für die Verwaltungskonsole|Ein Zertifikat kann Secure Sockets Layer (SSL)-Verbindungen über HTTPS zum [Überwachen der Appliance mithilfe der Verwaltungskonsole &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)bereitstellen. Standardmäßig enthält die- **Verwaltungskonsole** ein selbst signiertes Zertifikat, das Datenschutz, aber keine Server Authentifizierung bereitstellt. Dieses Zertifikat gibt auch einen Fehler in Internet Explorer zurück, der besagt, dass ein Problem mit dem Sicherheitszertifikat dieser Website vorliegt, wenn der Benutzer eine Verbindung herstellt. Obwohl bei dieser Verbindung Daten zwischen dem Client und dem Server verschlüsselt werden, ist die Verbindung von Angreifern immer noch gefährdet.<br /><br />SQL Server PDW Administratoren sollten umgehend ein Zertifikat abrufen, das mit einer vertrauenswürdigen Zertifizierungsstelle verkettet ist, die von Clients erkannt wird, um eine sichere Verbindung zu erhalten und den Fehler zu entfernen, den Internet Explorer meldet. Hierfür ist ein voll qualifizierter Domänen Name erforderlich, der die virtuelle IP-Adresse des Steuer Knotens (empfohlen) oder einen Zertifikat Namen zuordnet, der mit dem Wert übereinstimmt, der von den Benutzern in den Adress leisten des Browsers für den Zugriff auf die Verwaltungskonsole<br /><br />Verwenden Sie die **Configuration Manager** , um vertrauenswürdige Zertifikate hinzuzufügen oder zu entfernen. Die direkte Verwendung des Microsoft Windows HTTP Services Certificate Configuration Tool`winHttpCertCfg.exe`() zum Verwalten von Zertifikaten wird nicht unterstützt.<br /><br />Weitere Informationen finden Sie unter [PDW-Zertifikat Bereitstellung &#40;Analytics Platform System&#41;](pdw-certificate-provisioning.md).|
|Funktions Wechsel|Zeigt Informationen zu Funktions Switches an, die in Analytics Platform System AU7 eingeführt wurden. Verwenden Sie diese Seite, um Features und Einstellungen in Analytics Platform System zu aktualisieren oder zu aktivieren bzw. zu deaktivieren. Zum Ändern von Funktions switchwerten ist ein Dienst Neustart erforderlich.<br /><br />Weitere Informationen finden Sie unter [PDW-Funktions Wechsel &#40;Analytics Platform System&#41;](appliance-feature-switch.md).|
|Aktivieren oder Deaktivieren von Windows-Firewallregeln, die den Zugriff auf bestimmte Ports auf der SQL Server PDW Appliance zulassen oder verhindern.|Ihr IHV konfiguriert und aktiviert die Firewallregeln, die für eine ordnungsgemäße Ausführung des Geräts erforderlich sind. In den meisten Fällen werden Firewallregeln nicht aktiviert bzw. deaktiviert.<br /><br />Weitere Informationen finden Sie unter [PDW Firewall Configuration &#40;Analytics Platform System&#41;](pdw-firewall-configuration.md).|  
|Starten und Abbrechen der SQL Server PDW Appliance|Beendet oder startet die SQL Server PDW Appliance. Weitere Informationen finden Sie unter [PDW-Dienst Status &#40;Analytics Platform System&#41;](pdw-services-status.md).|  
|Überprüfen der sofortigen Datei Initialisierungs Optionen mithilfe des Dialog Felds " **Berechtigungen** "|Die sofortige Datei Initialisierung ist ein SQL Server Feature, mit dem Datendatei Vorgänge schneller ausgeführt werden können. Sie wird nur auf SQL Server PDW aktiviert, wenn dem Netzwerkdienst Konto die Berechtigung SE_MANAGE_VOLUME_NAME gewährt wurde. Sie ist standardmäßig deaktiviert.<br /><br />Weitere Informationen finden Sie unter [Konfiguration der sofortigen Datei Initialisierung &#40;Analytics Platform System&#41;](instant-file-initialization-configuration.md).|  
|Wiederherstellen der Master-Datenbank aus einer Sicherung|Löscht die aktuelle **Master** -Datenbank und ersetzt Sie durch eine Sicherung. Weitere Informationen finden Sie unter [Wiederherstellen der Master-Datenbank &#40;Analytics Platform System&#41;](restore-the-master-database.md).|  
  
## <a name="AddTasks"></a>Ausführen zusätzlicher Konfigurationsaufgaben  
Nachdem Sie die **Configuration Manager** Aufgaben ausgeführt haben, führen Sie die folgende Liste mit zusätzlichen Konfigurationsaufgaben aus. Einige dieser Aufgaben sind optional.  
  
|Konfigurationstask|Beschreibung|  
|----------------------|---------------|  
|Antivirussoftware von Drittanbietern kann auf der SQL Server PDW Appliance für extern ausgerichtete Knoten installiert und konfiguriert werden.<br /><br />(Optional)|Weitere Informationen finden Sie unter [Antivirus Software &#40;Analytics Platform System&#41;](antivirus-software.md).|  
|Das Kennwort für DSRM kann geändert werden.<br /><br />(Optional)|Weitere Informationen finden Sie unter [Festlegen des Administrator Kennworts für die Anmeldung bei AD-Knoten im Verzeichnisdienst-Wiederherstellungs Modus &#40;DSRM&#41; &#40;Analytics-Platt Form System&#41;](set-admin-password-for-logging-on-to-ad-nodes-in-directory-services-restore-mode.md).|  
|Konfigurieren des Geräts für den Empfang von Software Updates<br /><br />(Empfohlen)|Die Appliance muss so konfiguriert werden, dass Sie Updates für die SQL Server PDW und die zugrunde liegende Software empfängt.<br /><br />Weitere Informationen finden Sie unter [Konfigurieren von Windows Server Update Services &#40;WSUS&#41; &#40;Analytics Platform System&#41;](configure-windows-server-update-services-wsus.md). Weitere Informationen zu WSUS finden Sie unter [Software Wartung &#40;Analytics Platform System&#41;](software-servicing.md).|  
|Konfigurieren Sie die Konnektivität mit externen Daten, wie z. b. Hadoop oder Azure BLOB Storage.<br /><br />(Optional)|Weitere Informationen finden Sie unter [Konfigurieren der polybase-Konnektivität mit externen Daten &#40;Analytics Platform System&#41;](configure-polybase-connectivity-to-external-data.md).|  
|Konfigurieren von Antivirensoftware<br /><br />(Optional)|Antivirenlösungen von Drittanbietern können verwendet werden, um extern ausgerichtete Knoten zu schützen, dies ist jedoch nicht erforderlich. Befolgen Sie die Richtlinien in.|  
|Konfigurieren von InfiniBand-Netzwerkadaptern auf Sicherungs-und lade Servern<br /><br />(Optional)|Zum Konfigurieren von Sicherungs-und lade Servern für das Herstellen einer Verbindung mit SQL Server PDW über das InfiniBand-Netzwerk müssen Sie die Netzwerkadapter so konfigurieren, dass das Appliance-DNS die InfiniBand-Verbindung mit dem momentan aktiven InfiniBand-Netzwerk auflösen kann.|  
|Konfigurieren, um Telemetriedaten an Microsoft zu senden<br /><br />(Optional)|Zum Konfigurieren von Analytics Platform System zum Senden von Telemetriedaten an Microsoft müssen Sie ein PowerShell-Skript auf dem Steuer Knoten ausführen. Spezifische Anweisungen finden Sie unter [Senden von telemetriefeedback an Microsoft &#40;SQL Server PDW&#41;](send-telemetry-feedback-to-microsoft-sql-server-pdw.md).|  
  
## <a name="see-also"></a>Weitere Informationen  
[Antivirensoftware &#40;Analytics-Platt Form System&#41;](antivirus-software.md)  
[InfiniBand-Netzwerkadapter &#40;SQL Server PDW konfigurieren&#41;](configure-infiniband-network-adapters.md)  
  
