---
title: Checklisten für die Konfigurationen – Analytics Platform System | Microsoft-Dokumentation
description: Bietet Checklisten für die Aufgaben zum Konfigurieren von Analytics Platform System für Ihre eigene Umgebung erforderlich. Diese Aufgaben sind erforderlich, bevor Sie das Gerät verwenden können.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 9977ac8ea73e37afef85a46d6794ea5136357b44
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67961595"
---
# <a name="appliance-configuration-checklists-for-analytics-platform-system"></a>Checklisten für die Appliance Konfigurationen für Analytics Platform System
Bietet Checklisten für die Aufgaben zum Konfigurieren von Analytics Platform System für Ihre eigene Umgebung erforderlich. Diese Aufgaben sind erforderlich, bevor Sie das Gerät verwenden können.  
  
> [!WARNING]  
> Verwenden von Analytics Platform System**Configuration Manager** ist die beste Möglichkeit, und die einzige unterstützte Möglichkeit, für die Aufgaben im Tool verfügbar sind.  
  
## <a name="BeforeTasks"></a>Vorbereitungen  
  
### <a name="prerequisites"></a>Vorraussetzungen  
  
1.  Das Gerät im Rechenzentrum installiert, und eingeschaltet werden muss.  
  
2.  Stellen Sie sicher, dass Sie die folgende Informationen verfügen, die von Ihrem unabhängigen Hardwarehersteller bereitgestellt wird:  
  
    -   Externe IP-Adresse für den Knoten für die PDW-Steuerelement (*PDW_region -* CTL01)  
  
    -   Appliance-Domänenname  
  
    -   Benutzername und Kennwort für den Domänenadministrator appliance  
  
3.  Rufen Sie ein vertrauenswürdiges Zertifikat. Sie importieren diese in einem späteren Schritt, um Clients für die Verbindung zu ermöglichen die **Verwaltungskonsole** mit sicheren Verbindungen. Speichern Sie das Zertifikat mit dem Steuerungsknoten in eine kennwortgeschützte PFX-Datei.  
  
4.  Starten Sie den **Configuration Manager**, verwenden die folgenden Schritte aus:  
  
    1.  Verwendung **Remotedesktop** für die Verbindung mit dem Steuerungsknoten mit PDW (*PDW_region*-CTL01). (Möglicherweise müssen für die CTL01 eine Verbindung mit der externen IP-Adresse.)  
  
    2.  Starten Sie den **Configuration Manager** aus der **starten** Menü des Knotens PDW-Steuerelement. Der erste Bildschirm der Configuration Manager zeigt die Appliance-Topologie, die von Ihrem unabhängigen Hardwarehersteller erstellt wurde. Es ist eine Liste von der hardwareknoten, die von Ihrer SQL Server-PDW-Software, die als Teil Ihrer Appliance erkannt werden. Sie sollten keine Einstellungen auf dem Bildschirm Appliancetopologie ändern müssen.  
  
## <a name="CMTasks"></a>Ausführen von Aufgaben in Configuration Manager  
Die SQL Server PDW**Configuration Manager** (PDWCM) ist ein Tool für die Appliance-Verwaltung, die Systemadministratoren für SQL Server PDW Appliance auf Operationen ausführen und so ändern Sie die Einstellungen auf Gerät verwenden. Verwenden Sie z. B. PDWCM zum Zurücksetzen von Kennwörtern, Festlegen der Zeitzone, IP-Adresse ändern, Konfigurieren von SSL-Zertifikaten, den Remotezugriff über die Firewall aktivieren, starten oder beenden das Gerät, und legen sofortige Dateiinitialisierung ein.  
  
Verwendung **Configuration Manager** die folgenden Konfigurationsaufgaben ausführen.  
  
|Konfigurationstask|Beschreibung|  
|----------------------|---------------|  
|Mit dem Namen der physischen Komponenten vertraut zu machen|[Physische Komponenten von PDW und Appliance Fabric &#40;Analytics Platform System&#41;](pdw-and-appliance-fabric-physical-components.md)|  
|Starten Sie SQL Server PDW-Konfigurations-Manager|[Starten Sie den Konfigurations-Manager &#40;Analytics Platform System&#41;](launch-the-configuration-manager.md)|  
|Das Administratorkennwort für die Domäne ändern|Das Gerät verfügt über einen privaten Windows Active Directory Domain Services, die verwendet wird, um Knoten in der Anwendung zu authentifizieren.<br /><br />Ihrem unabhängigen Hardwarehersteller richten Sie das Gerät mit einem Standardadministratorkennwort für die Domäne ein. Dies muss in ein Kennwort geändert werden, die sicher ist.<br /><br />Die **Configuration Manager** ist die einzige unterstützte Weg, um das Administratorkennwort für die Domäne ändern.<br /><br />Weitere Informationen finden Sie unter [Zurücksetzen des Kennworts &#40;Analytics Platform System&#41;](password-reset.md).|  
|Ändern des Kennworts für die **sa** Anmeldung|SQL Server PDW ist eine System-administratoranmeldung, die mit dem Namen **sa**. Die **sa** Anmeldung verfügt über alle Berechtigungen. Sie können zu gewähren, verweigern oder widerrufen keine Berechtigung. Sie können auch alle Systemsichten finden Sie unter.<br /><br />Weitere Informationen finden Sie unter [Zurücksetzen des Kennworts &#40;Analytics Platform System&#41;](password-reset.md).|  
|Festlegen der Zeitzone der appliance|Legen Sie die Uhrzeit (lokal oder andere gewünschte) für alle applianceknoten an.<br /><br />Weitere Informationen finden Sie unter [Zeitzone Anwendungskonfiguration &#40;Analytics Platform System&#41;](appliance-time-zone-configuration.md).|  
|Geben Sie extern ausgerichtete Netzwerkeinstellungen für die SQL Server-PDW-appliance|[Appliance-Netzwerkkonfiguration &#40;Analytics Platform System&#41;](appliance-network-configuration.md)|  
|Importieren Sie ein Sicherheitszertifikat, das für die Verwaltungskonsole|Ein Zertifikat bieten Secure Sockets Layer (SSL)-Verbindungen über HTTPS an die [Überwachen der Appliance mithilfe der Verwaltungskonsole &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md). In der Standardeinstellung die **Verwaltungskonsole** enthält ein selbst signiertes Zertifikat, das Datenschutz, aber keine Serverauthentifizierung bereitstellt. Dieses Zertifikat gibt auch einen Fehler in Internet Explorer mit dem Hinweis zurück: "Es besteht ein Problem mit dem Sicherheitszertifikat der Website" Wenn der Benutzer eine Verbindung herstellt. Obwohl dieser Verbindung gesendeten Daten zwischen dem Client und Server verschlüsselt, ist die Verbindung immer noch durch Angreifer gefährdet.<br /><br />SQL Server-PDW-Administratoren sollten sofort ein Zertifikat zu erhalten, ist mit einer vertrauenswürdigen Zertifizierungsstelle, die von Clients, um eine sichere Verbindung hergestellt, und entfernen den Fehler, den Internet Explorer meldet erkannt, verkettet. Dies erfordert einen vollqualifizierten Domänennamen, der des steuerknoten virtuelle IP-Adresse (empfohlen) zugeordnet ist, oder ein Zertifikatsname, der mit dem Wert übereinstimmt, den Benutzer in ihrer browseradresse eingeben Balken, um die Verwaltungskonsole zugreifen.<br /><br />Verwenden der **Configuration Manager** hinzufügen oder Entfernen vertrauenswürdiger Zertifikate. Direkt mithilfe des Konfigurationstools für Microsoft Windows HTTP-Dienste-Zertifikat (`winHttpCertCfg.exe`) zum Verwalten von Zertifikaten werden nicht unterstützt.<br /><br />Weitere Informationen finden Sie unter [PDW-Zertifikatbereitstellung &#40;Analytics Platform System&#41;](pdw-certificate-provisioning.md).|
|Feature-Switch|Zeigt Informationen zu Features, die in Analytics Platform System AU7 eingeführt werden. Mithilfe dieser Seite zu aktualisieren oder zu aktivieren/deaktivieren Features und Einstellungen in Analytics Platform System. Ändern von Werten der Feature-Switch erfordert einen Neustart des Diensts.<br /><br />Weitere Informationen finden Sie unter [PDW-Feature-Switch &#40;Analytics Platform System&#41;](appliance-feature-switch.md).|
|Aktivieren oder Deaktivieren von Windows-Firewall-Regeln, die zulassen oder verhindern den Zugriff auf bestimmte Ports auf der SQL Server-PDW-Appliance.|Ihrem unabhängigen Hardwarehersteller konfigurieren und aktivieren die Firewall-Regeln, die erforderlich sind, damit das Gerät ordnungsgemäß funktioniert. In den meisten Fällen werden Sie nicht aktivieren oder deaktivieren Sie Firewallregeln.<br /><br />Weitere Informationen finden Sie unter [PDW-Firewallkonfiguration &#40;Analytics Platform System&#41;](pdw-firewall-configuration.md).|  
|Starten Sie und beenden Sie die SQL Server-PDW-appliance|Beendet oder startet die SQL Server-PDW-Appliance. Weitere Informationen finden Sie unter [PDW-Dienststatus &#40;Analytics Platform System&#41;](pdw-services-status.md).|  
|Überprüfen Sie sofortige Dateiinitialisierung Optionen mithilfe der **Berechtigungen** (Dialogfeld)|Sofortige Dateiinitialisierung ist eine SQL Server-Funktion, mit dem Daten-Dateivorgänge, schneller ausgeführt werden kann. Es ist in SQL Server PDW nur aktiviert, wenn das NETZWERKDIENST-Konto die Berechtigung SE_MANAGE_VOLUME_NAME erteilt wurde. Es ist standardmäßig deaktiviert.<br /><br />Weitere Informationen finden Sie unter [sofortige Initialisierung-Dateikonfiguration &#40;Analytics Platform System&#41;](instant-file-initialization-configuration.md).|  
|Wiederherstellen Sie den master-Datenbank aus einer Sicherung|Löscht die aktuelle **master** -Datenbank und ersetzt diese durch eine Sicherung. Weitere Informationen finden Sie unter [Wiederherstellen der Master-Datenbank &#40;Analytics Platform System&#41;](restore-the-master-database.md).|  
  
## <a name="AddTasks"></a>Weitere Konfigurationsaufgaben  
Nach dem Ausführen der **Configuration Manager** Aufgaben, die folgende Liste von zusätzlichen Konfigurationsaufwand. Einige dieser Aufgaben sind optional.  
  
|Konfigurationstask|Beschreibung|  
|----------------------|---------------|  
|Antivirus-Software von Drittanbietern kann auf die SQL Server PDW Appliance für extern ausgerichtete Knoten konfiguriert und installiert werden.<br /><br />(Optional)|Weitere Informationen finden Sie unter [Antivirusprogrammen &#40;Analytics Platform System&#41;](antivirus-software.md).|  
|Das Kennwort für den Verzeichnisdienst-Wiederherstellungsmodus kann geändert werden.<br /><br />(Optional)|Weitere Informationen finden Sie unter [Admin-Kennwort festlegen, für die Anmeldung bei AD-Knoten im Wiederherstellungsmodus für Verzeichnisdienste &#40;DSRM&#41; &#40;Analytics Platform System&#41;](set-admin-password-for-logging-on-to-ad-nodes-in-directory-services-restore-mode.md).|  
|Konfigurieren Sie die Appliance, um Softwareupdates zu erhalten.<br /><br />(Empfohlen)|Das Gerät muss konfiguriert werden, um Updates für die SQL Server PDW und die zugrunde liegende Software zu erhalten.<br /><br />Weitere Informationen finden Sie unter [Konfigurieren von Windows Server Update Services &#40;WSUS&#41; &#40;Analytics Platform System&#41;](configure-windows-server-update-services-wsus.md). Weitere Informationen zu WSUS finden Sie unter [Softwarewartung &#40;Analytics Platform System&#41;](software-servicing.md).|  
|Konfigurieren Sie Verbindungen zu externen Daten wie z. B. Hadoop oder Azure Blob Storage.<br /><br />(Optional)|Weitere Informationen finden Sie unter [Konfigurieren von PolyBase-Konnektivität für externe Daten &#40;Analytics Platform System&#41;](configure-polybase-connectivity-to-external-data.md).|  
|Konfigurieren von Antivirensoftware<br /><br />(Optional)|Anderer Anbieter Virenschutzlösungen können verwendet werden, um externe Knoten zu schützen, aber es ist nicht erforderlich. Befolgen Sie die Richtlinien in aus.|  
|Konfigurieren von InfiniBand-Netzwerkadapter für die Sicherung und beim Laden von Servern<br /><br />(Optional)|Zum Konfigurieren von Sicherung und Laden von Servern, zur Verbindung mit SQL Server PDW mit InfiniBand-Netzwerk müssen Sie so konfigurieren Sie den Netzwerkadapter so, dass die Appliance DNS für das die InfiniBand-Verbindung mit dem derzeit aktiven InfiniBand-Netzwerk auflösen kann.|  
|Konfigurieren Sie zum Senden von Telemetriedaten an Microsoft<br /><br />(Optional)|Um Analytics Platform System zum Senden von Telemetriedaten an Microsoft konfigurieren zu können, müssen Sie ein PowerShell-Skript auf dem steuerknoten ausgeführt. Ausführliche Anweisungen finden Sie unter [Senden von Telemetriefeedback an Microsoft &#40;SQL Server PDW&#41;](send-telemetry-feedback-to-microsoft-sql-server-pdw.md).|  
  
## <a name="see-also"></a>Siehe auch  
[Antivirus-Software &#40;Analytics Platform System&#41;](antivirus-software.md)  
[Konfigurieren Sie InfiniBand-Netzwerkadapter &#40;SQLServer PDW&#41;](configure-infiniband-network-adapters.md)  
  
