---
title: Abrufen und die Konfiguration eines Sicherungsservers - Parallel Data Warehouse | Microsoft-Dokumentation
description: Dieser Artikel beschreibt, wie Sie ein Windows-System nicht zur Appliance gehört als Sicherungsserver für die Verwendung mit der Funktionen zum Sichern und Wiederherstellen in Analytics Platform System (APS) und Parallel Data Warehouse (PDW) zu konfigurieren.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: cba345eb7a5aec9ef857819a1f0499266649f6e4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63040826"
---
# <a name="acquire-and-configure-a-backup-server-for-parallel-data-warehouse"></a>Erwerben Sie und konfigurieren Sie einen backup-Server Parallel Data Warehouse
Dieser Artikel beschreibt, wie Sie ein Windows-System nicht zur Appliance gehört als Sicherungsserver für die Verwendung mit der Funktionen zum Sichern und Wiederherstellen in Analytics Platform System (APS) und Parallel Data Warehouse (PDW) zu konfigurieren.  
  
  
## <a name="Basics"></a>Grundlagen für Sicherungsserver  
Der Sicherungsserver:  
  
-   Bereitgestellt und von Ihren eigenen IT-Team verwaltet wird.  
  
-   PDW-spezifische Software oder Tools ist nicht erforderlich. PDW wird Software auf den backup-Server nicht installiert.  
  
-   Befindet sich in Ihren eigenen Rack nicht zur Appliance gehört, und kann nicht in der APS-Appliance platziert werden.  
  
-   Kann mit dem Gerät InfiniBand-Netzwerk verbunden werden. Sicherungen können über InfiniBand oder Ethernet-ausgeführt werden; InfiniBand wird aus Leistungsgründen empfohlen.  
  
-   Befindet sich in der Domäne Ihren eigenen Kunden, nicht der Domäne der Anwendung. Es ist keine Vertrauensstellung zwischen Ihrem Kunden und der Appliance-Domäne.  
  
-   Hostet eine Sicherungsdatei-Freigabe, einer Windows-Dateifreigabe handelt, die das Netzwerkprotokoll für Server Message Block (SMB) auf Anwendungsebene verwendet. Die Freigabeberechtigungen für die Sicherungsdatei geben einen Windows-Domänenbenutzer (in der Regel ist dies eine dedizierte sicherungsbenutzer) die Möglichkeit, sicherungs- und Wiederherstellungsvorgänge Vorgänge für die Freigabe auszuführen. Der Benutzername und Kennwort-Anmeldeinformationen von der Windows-Domänenbenutzer sind in PDW gespeichert, sodass PDW kann sicherungs- und Wiederherstellungsvorgänge Vorgänge für die Freigabe der Sicherungsdatei auszuführen.  
  
## <a name="Step1"></a>Schritt 1: Bestimmen der Kapazitätsanforderungen  
Die Systemanforderungen für den Backup-Server hängt der eigenen arbeitsauslastung, fast vollständig. Vor dem Kauf oder einen backup-Server-Bereitstellung müssen Sie herausfinden, welche kapazitätsanforderungen. Die Backup-Server muss nicht nur für Sicherungen dedizierte werden, solange sie die Leistung und Speicher die Anforderungen Ihrer Workload behandeln soll. Sie können auch mehrere Server zum Sichern und Wiederherstellen jeder Datenbank auf einen von mehreren Servern verwenden.  
  
Verwenden der [Backup Server Worksheet zur kapazitätsplanung eines](backup-capacity-planning-worksheet.md) um zu ermitteln, welche kapazitätsanforderungen.  
  
## <a name="Step2"></a>Schritt 2: Abrufen des backup-Servers  
Nun, da Sie Ihre kapazitätsanforderungen besser verstehen, können Sie planen, die Server und Netzwerkkomponenten, die Sie erwerben oder bereitstellen müssen. Integrieren Sie die folgende Liste von Anforderungen in den purchasing-Plan, und klicken Sie dann den Server zu erwerben oder Bereitstellen eines vorhandenen Servers.  
  
### <a name="software-requirements"></a>Softwareanforderungen  
Alle Dateiserver, die die Windows File-Freigabe (SMB)-Protokoll verwendet.  
  
Es wird empfohlen, Windows Server 2012 oder darüber hinaus um:  
  
-   Rufen Sie den Leistungsvorteil von Datei-vorabzuweisung über SMB.  
  
-   Verwenden Sie für Sicherungsvorgänge (Instant Datei Initialization, IFI). Ihr IT-Team verwaltet diese Einstellung auf dem Sicherungsserver. Der PDW-Konfigurations-Manager (dwconfig.exe) nicht festgelegt oder IFI auf dem backup Server steuern. Frühere Versionen von Windows keine IFI, aber Sie können weiterhin als Sicherungsserver verwendet werden.  
  
### <a name="networking-requirements"></a>Netzwerkanforderungen  
Obwohl nicht zwingend erforderlich, ist InfiniBand den empfohlenen Verbindungstyp für Backup Server-Instanzen. Zur Vorbereitung der Appliance InfiniBand-Netzwerk mit dem Server geladen:  
  
1.  Planen den Server im rack nah an das Gerät, damit Sie es an das Gerät eine Verbindung herstellen können InfiniBand wechselt. Weitere Informationen von Mellanox-Technologien zu InfiniBand, finden Sie im Whitepaper, [Einführung in die InfiniBand](https://www.mellanox.com/pdf/whitepapers/IB_Intro_WP_190.pdf).  
  
2.  Erwerben Sie einen Netzwerkadapter von Mellanox ConnectX-3 ein FDR InfiniBand Single- oder dual-Port. Es wird empfohlen, erwerben die Netzwerkkarte mit zwei Ports für die Fehlertoleranz während der Datenübertragung. Ein zwei Port-Netzwerkadapter ist für hohe Verfügbarkeit erforderlich.  
  
3.  Erwerben Sie 2 ein FDR InfiniBand-Kabel für eine Karte mit zwei Ports bzw. 1 ein FDR InfiniBand-Kabel für einen einzelnen Port-Karte. Die Kabel ein FDR InfiniBand werden den Laden von Server mit Appliance InfiniBand-Netzwerk verbunden. Die Länge der Kabel hängt von den Abstand zwischen dem Server geladen und die Einheiten InfiniBand-Switches, gemäß Ihrer Umgebung ab.  
  
## <a name="Step3"></a>Schritt 3: Verbinden Sie den Server mit InfiniBand-Netzwerke  
Verwenden Sie diese Schritte, um den Server Laden mit dem InfiniBand-Netzwerk zu verbinden. Wenn der Server nicht das InfiniBand-Netzwerk verwendet wird, überspringen Sie diesen Schritt.  
  
1.  Rack Server nah an das Gerät, damit Sie das Gerät InfiniBand-Netzwerk hergestellt werden können.  
  
2.  Installieren Sie den InfiniBand Mellanox ConnectX-3 ein FDR InfiniBand-Netzwerkadapter in den Server laden.  
  
3.  Verwenden Sie die FDR-Kabel, um dem InfiniBand-Netzwerkadapter mit einer der beiden InfiniBand Schalter in das erste Gerät Rack herstellen.  
  
4.  Installieren Sie und konfigurieren Sie den entsprechenden Windows-Treiber für das InfiniBand-Netzwerkadapter.  
  
    -   InfiniBand-Treibern für Windows werden durch die OpenFabrics Alliance, ein Branchenkonsortium von InfiniBand-Anbietern entwickelt.  Der richtige Treiber möglicherweise mit dem InfiniBand-Netzwerkadapter verteilt wurden. Wenn dies nicht der Fall ist, kann der Treiber www.openfabrics.org heruntergeladen werden.  
  
5.  Konfigurieren Sie InfiniBand und DNS-Einstellungen für die Netzwerkadapter. Konfigurationsanweisungen, finden Sie unter [InfiniBand-Netzwerkadapter konfigurieren](configure-infiniband-network-adapters.md).  
  
## <a name="Step4"></a>Schritt 4: Konfigurieren Sie die backup-Datei-Freigabe  
PDW wird den backup-Server über einen UNC-Dateifreigabe zugreifen. So richten die Dateifreigabe aus:  
  
1.  Erstellen Sie einen Ordner auf dem Sicherungsserver für das Speichern von Sicherungen.  
  
2.  Erstellen Sie eine Dateifreigabe, eine Sicherungsfreigabe fest, für den Sicherungsordner aufgerufen.  
  
3.  Festlegen Sie, oder erstellen Sie ein Windows-Domänenkonto in der Customer-Domäne, die Sie für die Durchführung von Sicherungen und Wiederherstellungen verwenden möchten. Aus Sicherheitsgründen empfiehlt es sich um ein dediziertes Konto als backup-Benutzer verwenden.  
  
4.  Fügen Sie Berechtigungen für die Sicherung freigeben, sodass nur vertrauenswürdige Konten und ein Domänenkonto Sicherung zugreifen können, lesen und Schreiben an den Speicherort.  
  
5.  Fügen Sie die Anmeldeinformationen für ein backup Domänenkonto PDW hinzu.  
  
    Zum Beispiel:  
  
    ```sql  
    EXEC sp_pdw_add_network_credentials '10.192.147.63', 'seattle\david', '********';  
    ```  
  
    Weitere Informationen finden Sie auf diese gespeicherten Prozeduren:  
  
    -   [sp_pdw_add_network_credentials](../relational-databases/system-stored-procedures/sp-pdw-add-network-credentials-sql-data-warehouse.md)  
  
    -   [sp_pdw_remove_network_credentials](../relational-databases/system-stored-procedures/sp-pdw-remove-network-credentials-sql-data-warehouse.md)  
  
## <a name="Step5"></a>Schritt 5: Starten Sie Ihre Daten sichern  
Sie können nun damit beginnen, Sichern von Daten auf Ihre backup-Server.  
  
Daten sichern, verwenden Sie einen abfrageclient eine Verbindung mit SQL Server PDW, und senden dann BACKUP DATABASE oder RESTORE DATABASE-Befehle. Verwenden Sie den Datenträger =-Klausel, um den Sicherungsspeicherort für Server und die Sicherung angeben.  
  
> [!IMPORTANT]  
> Denken Sie daran, die InfiniBand IP-Adresse des backup-Server verwenden. Andernfalls werden die Daten über Ethernet, anstelle von InfiniBand kopiert.  
  
Zum Beispiel:  
  
```sql  
BACKUP DATABASE Invoices TO DISK = '\\10.172.14.255\backups\yearly\Invoices2013Full';  
  
RESTORE DATABASE Invoices2013Full  
FROM DISK = '\\10.172.14.255\backups\yearly\Invoices2013Full'  
```  
  
Weitere Informationen finden Sie in den folgenden Themen: 
  
-   [DATENBANK SICHERN](../t-sql/statements/backup-database-parallel-data-warehouse.md)   
  
-   [RESTORE DATABASE](../t-sql/statements/restore-database-parallel-data-warehouse.md)  
  
## <a name="Security"></a>Security-Hinweise  
Der backup-Server ist nicht mit der privaten Domäne für die Anwendung verknüpft. Es ist in Ihrem eigenen Netzwerk, und es besteht keine Vertrauensstellung zwischen Ihrer eigenen Domäne und den privaten Appliance-Domäne.  
  
Da Sicherungen von PDW nicht auf dem Gerät gespeichert werden, ist Ihr IT-Team für die Verwaltung aller Aspekte der Sicherung Sicherheit zuständig. Beispielsweise schließt dies die Verwaltung der Sicherheit der Sicherungsdaten, die Sicherheit des Servers verwendet, um Sicherungen zu speichern und die Sicherheit der Netzwerkinfrastruktur, die die Sicherungsserver mit der APS-Appliance verbindet.  
  
### <a name="manage-network-credentials"></a>Verwalten von Anmeldeinformationen für das Netzwerk  
  
Der Netzwerkzugriff auf das Sicherungsverzeichnis basiert auf der Windows-Standarddateifreigabesicherheit. Bevor Sie eine Sicherung durchführen, müssen Sie erstellen oder reservieren ein Windows-Konto, das für die Authentifizierung der PDW auf das Sicherungsverzeichnis verwendet wird. Dieses Windows-Konto benötigt die Berechtigung, auf das Sicherungsverzeichnis zuzugreifen, es zu erstellen und auf es zu schreiben.  
  
> [!IMPORTANT]  
> Um Sicherheitsrisiken in Verbindung mit Ihren Daten zu reduzieren, empfehlen wir, dass Sie ein Windows-Konto ausschließlich zum Ausführen der Sicherungs- und Wiederherstellungsvorgänge festlegen. Definieren Sie das Konto so, dass es nur Berechtigungen für den Sicherungsspeicherort besitzt.  
  
Um den Benutzernamen und das Kennwort in PDW speichern möchten, verwenden Sie die [Sp_pdw_add_network_credentials](../relational-databases/system-stored-procedures/sp-pdw-add-network-credentials-sql-data-warehouse.md) gespeicherte Prozedur. PDW verwendet Windows-Anmeldeinformationsverwaltung zum Speichern und Verschlüsseln von Benutzernamen und Kennwörter auf dem steuerknoten und Compute-Knoten. Die Anmeldeinformationen werden nicht mit dem Befehl BACKUP DATABASE gesichert.  
  
Verwenden Sie zum Entfernen von Anmeldeinformationen für das Netzwerk von PDW die [Sp_pdw_remove_network_credentials](../relational-databases/system-stored-procedures/sp-pdw-remove-network-credentials-sql-data-warehouse.md) gespeicherte Prozedur.  
  
Um alle in SQL Server PDW gespeicherten Netzwerkanmeldeinformationen aufzulisten, verwenden die [Sys. dm_pdw_network_credentials](../relational-databases/system-dynamic-management-views/sys-dm-pdw-network-credentials-transact-sql.md) dynamische verwaltungssicht.  
  
### <a name="secure-communications"></a>Sichere Kommunikation  
  
Vorgänge auf dem Server laden können einen UNC-Pfad, um Daten von außerhalb des internen vertrauenswürdigen Netzwerks. Ein Angreifer im Netzwerk oder mit der Möglichkeit, die namensauflösung zu beeinflussen kann abfangen oder Datenübertragungen an den PDW geändert werden. Dies stellt ein Risiko der Offenlegung von Manipulationen und Informationen. Um das Risiko von Manipulationen zu verringern:

- Erfordern Sie eine Anmeldung für die Verbindung. 
- Legen Sie die folgende Gruppenrichtlinie-Option in Sicherheitseinstellungen\Lokale Richtlinien\sicherheitsoptionen, auf dem Server geladen:  Microsoft-Netzwerkclient: Signieren Sie Kommunikation digital (immer): aktiviert.  
  
## <a name="see-also"></a>Siehe auch  
[Sichern und Wiederherstellen](backup-and-restore-overview.md)  
  
