---
title: Abrufen & Konfigurieren von Backup Server
description: In diesem Artikel wird beschrieben, wie ein nicht-Appliance-Windows-System als Sicherungs Server für die Verwendung mit den Sicherungs-und Wiederherstellungs Funktionen in Analytics Platform System (APS) und parallel Data Warehouse (PDW) konfiguriert wird.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: e160c606b19933934ec844b477ffec08475307d8
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "74401497"
---
# <a name="acquire-and-configure-a-backup-server-for-parallel-data-warehouse"></a>Erwerben und Konfigurieren eines Sicherungs Servers für parallele Data Warehouse
In diesem Artikel wird beschrieben, wie ein nicht-Appliance-Windows-System als Sicherungs Server für die Verwendung mit den Sicherungs-und Wiederherstellungs Funktionen in Analytics Platform System (APS) und parallel Data Warehouse (PDW) konfiguriert wird.  
  
  
## <a name="backup-server-basics"></a><a name="Basics"></a>Grundlagen zu Sicherungs Servern  
Der Sicherungs Server:  
  
-   Wird von Ihrem eigenen IT-Team bereitgestellt und verwaltet.  
  
-   Erfordert keine PDW-spezifische Software oder Tools. PDW installiert keine Software auf dem Sicherungs Server.  
  
-   Befindet sich in einem eigenen nicht-Appliance-Rack und kann nicht innerhalb der APS-Appliance platziert werden.  
  
-   Kann mit dem Gerät InfiniBand-Netzwerk verbunden werden. Sicherungen können über Infiniband oder Ethernet ausgeführt werden. InfiniBand wird aus Leistungsgründen empfohlen.  
  
-   Befindet sich in ihrer eigenen Kunden Domäne und nicht in der Appliance-Domäne. Zwischen Ihrer Kunden Domäne und der Appliance-Domäne besteht keine Vertrauensstellung.  
  
-   Hostet eine Sicherungsdatei Freigabe, bei der es sich um eine Windows-Dateifreigabe handelt, die das SMB-Netzwerkprotokoll (Server Message Block) verwendet. Die Berechtigungen für die Sicherungsdatei Freigabe geben einem Windows-Domänen Benutzer (in der Regel ein dedizierter Sicherungs Benutzer) die Möglichkeit, Sicherungs-und Wiederherstellungs Vorgänge auf der Freigabe auszuführen. Die Anmelde Informationen für den Benutzernamen und das Kennwort des Windows-Domänen Benutzers werden in PDW gespeichert, damit PDW Sicherungs-und Wiederherstellungs Vorgänge auf der Sicherungsdatei Freigabe ausführen kann.  
  
## <a name="step-1-determine-capacity-requirements"></a><a name="Step1"></a>Schritt 1: Ermitteln der Kapazitätsanforderungen  
Die Systemanforderungen für den Sicherungs Server hängen fast vollständig von ihrer eigenen Arbeitsauslastung ab. Vor dem Erwerb oder der Bereitstellung eines Sicherungs Servers müssen Sie Ihre Kapazitätsanforderungen ermitteln. Der Sicherungs Server muss nicht ausschließlich für Sicherungen reserviert werden, solange die Leistung und die Speicheranforderungen der Arbeitsauslastung erfüllt werden. Sie können auch über mehrere Sicherungs Server verfügen, um die einzelnen Datenbanken auf einem von mehreren Servern zu sichern und wiederherzustellen.  
  
Verwenden Sie das [Arbeitsblatt zur Kapazitätsplanung für Sicherungs Server](backup-capacity-planning-worksheet.md) , um Ihre Kapazitätsanforderungen zu ermitteln.  
  
## <a name="step-2-acquire-the-backup-server"></a><a name="Step2"></a>Schritt 2: beschaffen des Sicherungs Servers  
Nachdem Sie nun ihre Kapazitätsanforderungen besser verstanden haben, können Sie die Server und Netzwerkkomponenten planen, die Sie erwerben oder bereitstellen müssen. Fügen Sie die folgende Liste von Anforderungen in Ihren Kauf Plan ein, und erwerben Sie dann Ihren Server, oder stellen Sie einen vorhandenen Server bereit.  
  
### <a name="software-requirements"></a>Softwareanforderungen  
Ein beliebiger Dateiserver, der das Windows-Dateifreigabe Protokoll (SMB) verwendet.  
  
Wir empfehlen Windows Server 2012 oder höher, um Folgendes zu tun:  
  
-   Profitieren Sie von den Leistungsvorteilen der vorab Zuordnung von Dateien über SMB.  
  
-   Verwenden Sie die sofortige Datei Initialisierung (IFI) für Sicherungs Vorgänge. Ihr IT-Team verwaltet diese Einstellung auf dem Sicherungs Server. Mit dem PDW-Configuration Manager (dwconfig. exe) wird IFI auf dem Sicherungs Server nicht festgelegt oder gesteuert. In früheren Versionen von Windows ist kein IFI vorhanden, Sie können jedoch weiterhin als Sicherungs Server verwendet werden.  
  
### <a name="networking-requirements"></a>Netzwerkanforderungen  
InfiniBand ist zwar nicht erforderlich, wird jedoch als Verbindungstyp für Sicherungs Server empfohlen. So bereiten Sie die Verbindung zwischen dem Lade Server und dem Gerät InfiniBand-Netzwerk vor:  
  
1.  Planen Sie, den Server so nah wie möglich zu verbinden, damit Sie ihn mit den InfiniBand-Switches der Anwendung verbinden können. Weitere Informationen von Mellanox-Technologien zu InfiniBand finden Sie im Whitepaper [Introduction to InfiniBand (Einführung in InfiniBand](https://www.mellanox.com/pdf/whitepapers/IB_Intro_WP_190.pdf)).  
  
2.  Erwerben Sie den Netzwerkadapter "Mellanox ConnectX-3 FDR InfiniBand Single" oder "Dual Port". Es wird empfohlen, den Netzwerkadapter mit zwei Ports für die Fehlertoleranz während der Datenübertragung zu erwerben. Für hohe Verfügbarkeit ist ein Netzwerkadapter mit zwei Ports erforderlich.  
  
3.  Erwerben Sie 2 FDR InfiniBand-Kabel für eine Dual-Port-Karte oder 1 FDR InfiniBand-Kabel für eine einzelne Port Karte. Die FDR InfiniBand-Kabel verbinden den Lade Server mit dem Gerät InfiniBand-Netzwerk. Die Länge des Kabels hängt von der Entfernung zwischen dem Lade Server und den InfiniBand-Switches der Anwendung gemäß ihrer Umgebung ab.  
  
## <a name="step-3-connect-the-server-to-the-infiniband-networks"></a><a name="Step3"></a>Schritt 3: Verbinden des Servers mit den InfiniBand-Netzwerken  
Verwenden Sie diese Schritte, um den Lade Server mit dem InfiniBand-Netzwerk zu verbinden. Wenn der Server das InfiniBand-Netzwerk nicht verwendet, überspringen Sie diesen Schritt.  
  
1.  Verbinden Sie den Server in der Nähe des Geräts, sodass Sie es mit dem InfiniBand-Netzwerkgerät verbinden können.  
  
2.  Installieren Sie den InfiniBand-Netzwerkadapter "Mellanox ConnectX-3" in den Lade Server.  
  
3.  Verwenden Sie die FDR-Kabel, um den InfiniBand-Netzwerkadapter mit einem der beiden InfiniBand-Switches im ersten Geräte Gestell zu verbinden.  
  
4.  Installieren und konfigurieren Sie den entsprechenden Windows-Treiber für den InfiniBand-Netzwerkadapter.  
  
    -   InfiniBand-Treiber für Windows werden von der openfabrics Alliance entwickelt, einem Branchen Konsortium von InfiniBand-Anbietern.  Der richtige Treiber wurde möglicherweise mit dem InfiniBand-Netzwerkadapter verteilt. Andernfalls kann der Treiber von www.openfabrics.org heruntergeladen werden.  
  
5.  Konfigurieren Sie die InfiniBand-und DNS-Einstellungen für die Netzwerkadapter. Konfigurations Anweisungen finden Sie unter [Konfigurieren von InfiniBand-Netzwerkadaptern](configure-infiniband-network-adapters.md).  
  
## <a name="step-4-configure-the-backup-file-share"></a><a name="Step4"></a>Schritt 4: Konfigurieren der Sicherungsdatei Freigabe  
PDW greift über eine UNC-Dateifreigabe auf den Backup-Server zu. So richten Sie die Dateifreigabe ein:  
  
1.  Erstellen Sie einen Ordner auf dem Sicherungs Server, um die Sicherungen zu speichern.  
  
2.  Erstellen Sie eine Dateifreigabe, die als Sicherungs Freigabe bezeichnet wird, für den Sicherungsordner.  
  
3.  Legen Sie ein Windows-Domänen Konto in ihrer Kunden Domäne fest, das Sie für die Durchführung von Sicherungen und Wiederherstellungen verwenden möchten, oder erstellen Sie es. Aus Sicherheitsgründen empfiehlt es sich, ein dediziertes Konto als Sicherungs Benutzer zu verwenden.  
  
4.  Fügen Sie der Sicherungs Freigabe Berechtigungen hinzu, sodass nur vertrauenswürdige Konten und ein Domänen Sicherungs Konto auf den Freigabe Speicherort zugreifen, Sie lesen und in diesen schreiben können.  
  
5.  Fügen Sie PDW die Anmelde Informationen für das Sicherungs Domänen Konto hinzu.  
  
    Beispiel:  
  
    ```sql  
    EXEC sp_pdw_add_network_credentials '10.192.147.63', 'seattle\david', '********';  
    ```  
  
    Weitere Informationen finden Sie in den folgenden gespeicherten Prozeduren:  
  
    -   [sp_pdw_add_network_credentials](../relational-databases/system-stored-procedures/sp-pdw-add-network-credentials-sql-data-warehouse.md)  
  
    -   [sp_pdw_remove_network_credentials](../relational-databases/system-stored-procedures/sp-pdw-remove-network-credentials-sql-data-warehouse.md)  
  
## <a name="step-5-start-backing-up-your-data"></a><a name="Step5"></a>Schritt 5: Starten der Datensicherung  
Sie können nun mit dem Sichern von Daten auf dem Sicherungs Server beginnen.  
  
Verwenden Sie zum Sichern von Daten einen Abfrage Client, um eine Verbindung mit SQL Server PDW herzustellen, und übermitteln Sie dann die Befehle Backup Database oder RESTORE DATABASE. Verwenden Sie die Disk =-Klausel, um den Sicherungs Server und den Sicherungs Speicherort anzugeben.  
  
> [!IMPORTANT]  
> Denken Sie daran, die InfiniBand-IP-Adresse des Sicherungs Servers zu verwenden. Andernfalls werden die Daten über Ethernet anstelle von InfiniBand kopiert.  
  
Beispiel:  
  
```sql  
BACKUP DATABASE Invoices TO DISK = '\\10.172.14.255\backups\yearly\Invoices2013Full';  
  
RESTORE DATABASE Invoices2013Full  
FROM DISK = '\\10.172.14.255\backups\yearly\Invoices2013Full'  
```  
  
Weitere Informationen finden Sie unter 
  
-   [BACKUP DATABASE](../t-sql/statements/backup-database-parallel-data-warehouse.md)   
  
-   [RESTORE DATABASE](../t-sql/statements/restore-database-parallel-data-warehouse.md)  
  
## <a name="security-notices"></a><a name="Security"></a>Sicherheitshinweise  
Der Sicherungs Server ist nicht mit der privaten Domäne für das Gerät verknüpft. Sie befindet sich in Ihrem eigenen Netzwerk, und es besteht keine Vertrauensstellung zwischen Ihrer eigenen Domäne und privaten Appliance-Domäne.  
  
Da PDW-Sicherungen nicht auf dem Gerät gespeichert sind, ist das IT-Team für die Verwaltung aller Aspekte der Sicherungs Sicherheit verantwortlich. Dies umfasst z. b. die Verwaltung der Sicherheit der Sicherungsdaten, die Sicherheit des Servers, der zum Speichern der Sicherungen verwendet wird, und die Sicherheit der Netzwerkinfrastruktur, die den Sicherungs Server mit dem APS-Gerät verbindet.  
  
### <a name="manage-network-credentials"></a>Verwalten von Netzwerk Anmelde Informationen  
  
Der Netzwerkzugriff auf das Sicherungsverzeichnis basiert auf der Windows-Standarddateifreigabesicherheit. Vor dem Ausführen einer Sicherung müssen Sie ein Windows-Konto erstellen oder festlegen, das zum Authentifizieren von PDW im Sicherungs Verzeichnis verwendet wird. Dieses Windows-Konto benötigt die Berechtigung, auf das Sicherungsverzeichnis zuzugreifen, es zu erstellen und auf es zu schreiben.  
  
> [!IMPORTANT]  
> Um Sicherheitsrisiken in Verbindung mit Ihren Daten zu reduzieren, empfehlen wir, dass Sie ein Windows-Konto ausschließlich zum Ausführen der Sicherungs- und Wiederherstellungsvorgänge festlegen. Definieren Sie das Konto so, dass es nur Berechtigungen für den Sicherungsspeicherort besitzt.  
  
Verwenden Sie die gespeicherte Prozedur [sp_pdw_add_network_credentials](../relational-databases/system-stored-procedures/sp-pdw-add-network-credentials-sql-data-warehouse.md) , um den Benutzernamen und das Kennwort in PDW zu speichern. PDW verwendet Windows Credential Manager zum Speichern und Verschlüsseln von Benutzernamen und Kenn Wörtern auf dem Steuerungs Knoten und den Computeknoten. Die Anmeldeinformationen werden nicht mit dem Befehl BACKUP DATABASE gesichert.  
  
Um Netzwerk Anmelde Informationen aus PDW zu entfernen, verwenden Sie die gespeicherte Prozedur [sp_pdw_remove_network_credentials](../relational-databases/system-stored-procedures/sp-pdw-remove-network-credentials-sql-data-warehouse.md) .  
  
Um alle in SQL Server PDW gespeicherten Netzwerk Anmelde Informationen aufzulisten, verwenden Sie die dynamische Verwaltungs Sicht [sys. dm_pdw_network_credentials](../relational-databases/system-dynamic-management-views/sys-dm-pdw-network-credentials-transact-sql.md) .  
  
### <a name="secure-communications"></a>Sichere Kommunikation  
  
Vorgänge auf dem Lade Server können einen UNC-Pfad zum Abrufen von Daten von außerhalb des vertrauenswürdigen internen Netzwerks verwenden. Ein Angreifer im Netzwerk oder mit der Möglichkeit, die Namensauflösung zu beeinflussen, kann Daten abfangen oder ändern, die an das PDW gesendet werden. Dies stellt ein Risiko zur Offenlegung von Manipulationen und Informationen dar. So verringern Sie das Risiko von Manipulationen:

- Erfordert die Signierung der Verbindung. 
- Legen Sie auf dem Server, der den Server lädt, die folgende Gruppenrichtlinien Option unter Sicherheitseinstellungen\Lokale Richtlinien\Sicherheitsoptionen: Microsoft-Netzwerkclient: Kommunikation digital signieren (immer): aktiviert fest.  
  
## <a name="see-also"></a>Weitere Informationen  
[Sichern und Wiederherstellen](backup-and-restore-overview.md)  
  
