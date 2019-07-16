---
title: Konfigurieren Sie SLES Cluster mit freigegebenen Datenträgern werden für SQL Server.
description: Implementieren Sie hohen Verfügbarkeit, indem freigegebene Datenträgercluster für SUSE Linux Enterprise Server (SLES) für SQL Server konfigurieren.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 03/17/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: e5ad1bdd-c054-4999-a5aa-00e74770b481
ms.openlocfilehash: 70701d5c0103da089444177db1143066d0c862cd
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68032222"
---
# <a name="configure-sles-shared-disk-cluster-for-sql-server"></a>Konfigurieren Sie SLES Cluster mit freigegebenen Datenträgern werden für SQL Server.

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Dieses Handbuch enthält Anweisungen zum Erstellen von eines Clusters mit zwei Knoten freigegebenen Datenträgern für SQL Server unter SUSE Linux Enterprise Server (SLES). Die clustering-Ebene basiert darauf, dass SUSE [hohe Verfügbarkeit-Erweiterung (HAE)](https://www.suse.com/products/highavailability) baut auf [Pacemaker](https://clusterlabs.org/). 

Weitere Informationen für die Clusterkonfiguration, Ressourcenoptionen-Agent, Management, bewährte Methoden und Empfehlungen finden Sie unter [SUSE Linux Enterprise hohe Verfügbarkeit Erweiterung 12 SP2](https://www.suse.com/documentation/sle-ha-12/index.html).

## <a name="prerequisites"></a>Vorraussetzungen

Um das folgende End-to-End-Szenario abzuschließen, benötigen Sie zwei Computer, der zwei Knoten-Cluster und einem anderen Server so konfigurieren Sie die NFS-Freigabe bereitzustellen. Unten aufgeführten Schritte beschreiben Sie, wie diese Server konfiguriert werden.

## <a name="setup-and-configure-the-operating-system-on-each-cluster-node"></a>Richten Sie ein und konfigurieren Sie das Betriebssystem auf jedem Clusterknoten

Der erste Schritt ist das Betriebssystem auf den Clusterknoten zu konfigurieren. Verwenden Sie für diese exemplarische Vorgehensweise SLES mit einem gültigen Abonnement, für die HA-Add-On.

## <a name="install-and-configure-sql-server-on-each-cluster-node"></a>Installieren und Konfigurieren von SQL Server auf jedem Clusterknoten

1. Installieren und Einrichten von SQL Server auf beiden Knoten. Ausführliche Anweisungen finden Sie unter [Installieren von SQL Server unter Linux](sql-server-linux-setup.md).
2. Festlegen Sie ein Knoten als primärer und der andere wird als sekundäre Datenbank, für die Zwecke der Konfiguration. Verwenden Sie diese Bedingungen für die folgenden dieses Handbuchs. 
3. Klicken Sie auf dem sekundären Knoten beenden, und Deaktivieren von SQL Server. Im folgenden Beispiel wird beendet und deaktiviert SQL Server:

    ```bash
    sudo systemctl stop mssql-server
    sudo systemctl disable mssql-server
    ```

    > [!NOTE]
    > Beim Setup ein Server-Hauptschlüssel für die SQL Server-Instanz generiert und an platziert `/var/opt/mssql/secrets/machine-key`. Unter Linux wird SQL Server immer ausgeführt, als ein lokales Konto Mssql aufgerufen werden. Da es sich um ein lokales Konto handelt, ist nicht die Identität über Knoten hinweg gemeinsam genutzt werden. Aus diesem Grund müssen Sie den Verschlüsselungsschlüssel aus dem primären Knoten für jeden sekundären Knoten kopieren, damit jedes lokalen Mssql-Konto, um den Server-Hauptschlüssel entschlüsseln zugreifen kann.
4. Klicken Sie auf dem Primärknoten, erstellen Sie eine SQL Server-Anmeldung für Pacemaker, und erteilen Sie die Login-Berechtigung zum Ausführen `sp_server_diagnostics`. Pacemaker verwendet dieses Konto, um zu überprüfen, welcher Knoten die SQL Server ausgeführt wird.

    ```bash
    sudo systemctl start mssql-server
    ```
    Verbinden mit der SQL Server-Masterdatenbank mit dem Konto "sa", und führen Sie Folgendes:

    ```sql
    USE [master]
    GO
    CREATE LOGIN [<loginName>] with PASSWORD= N'<loginPassword>'
    GRANT VIEW SERVER STATE TO <loginName>
    ```
5. Klicken Sie auf dem primären Knoten beenden, und Deaktivieren von SQL Server.
6. Befolgen Sie die Anweisungen [in der SUSE-Dokumentation](https://www.suse.com/documentation/sles11/book_sle_admin/data/sec_basicnet_yast.html) konfigurieren und Aktualisieren der Hosts-Datei für jeden Clusterknoten. Die Datei "Hosts" muss es sich um den IP-Adresse und den Namen der einzelnen Clusterknoten enthalten.

    So überprüfen Sie die IP-Adresse des aktuellen Knotens ausführen

    ```bash
    sudo ip addr show
    ```

    Legen Sie den Namen des Computers, auf den einzelnen Knoten. Weisen Sie jedem Knoten einen eindeutigen Namen, die 15 Zeichen lang ist oder weniger. Den Namen des Computers festlegen, indem Sie es `/etc/hostname` mit [Yast](https://www.suse.com/documentation/sles11/book_sle_admin/data/sec_basicnet_yast.html) oder [manuell](https://www.suse.com/documentation/sled11/book_sle_admin/data/sec_basicnet_manconf.html).

    Das folgende Beispiel zeigt `/etc/hosts` mit Ergänzungen für zwei Knoten, die mit dem Namen `SLES1` und `SLES2`.

    ```
    127.0.0.1   localhost
    10.128.18.128 SLES1
    10.128.16.77 SLES2
    ```

    > [!NOTE]
    > Alle Clusterknoten müssen über SSH, aufeinander zugreifen können. Tools wie „hb_report“ oder „crm_report“ (zur Problembehandlung) und Hawk's History Explorer erfordern kennwortlosen SSH-Zugriff zwischen den Knoten, andernfalls können sie nur Daten vom aktuellen Knoten sammeln. Für den Fall, dass Sie einen nicht standardmäßigen SSH-Port verwenden, verwenden Sie die Option-X ([Siehe Hauptseite](https://www.suse.com/documentation/sle_ha/book_sleha/data/sec_ha_requirements_other.html)). Wenn Ihr SSH-Port 3479 ist, rufen Sie z. B. ein "crm_report" mit:
    >
    >```bash
    >crm_report -X "-p 3479" [...]
    >```
    >Weitere Informationen finden Sie unter [Administratorhandbuch]. (https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html#sec.ha.troubleshooting.misc)

Im nächsten Abschnitt Konfigurieren freigegebenen Speicher und die Datenbankdateien auf den Speicher zu verschieben.  

## <a name="configure-shared-storage-and-move-database-files"></a>Konfigurieren von freigegebenem Speicher, und Verschieben von Datenbankdateien

Es gibt eine Vielzahl von Lösungen zum Bereitstellen von freigegebenen Speichers. In dieser exemplarischen Vorgehensweise veranschaulicht das Konfigurieren von freigegebenen Speichers mit NFS. Es wird empfohlen, bewährte Methoden befolgen und verwenden Kerberos, um NFS zu schützen: 

- [Freigeben von Dateisystemen für NFS](https://www.suse.com/documentation/sles-12/singlehtml/book_sle_admin/book_sle_admin.html#cha.nfs)

Wenn Sie nicht diese Anleitung befolgen, werden jeder, der Zugriff auf Ihr Netzwerk und die IP-Adresse eines SQL-Knotens zu spoofen kann auf die Datendateien zugreifen. Wie immer, stellen Sie sicher, dass Sie Bedrohungsmodells für Ihr System vor der Verwendung in der Produktion. 

Eine weitere Option für Storage ist die Verwendung von SMB-Dateifreigabe:

- [Samba-Abschnitt der SUSE-Dokumentation](https://www.suse.com/documentation/sles-12/singlehtml/book_sle_admin/book_sle_admin.html#cha.samba)

### <a name="configure-an-nfs-server"></a>Konfigurieren Sie einen NFS-server

Um einen NFS-Server zu konfigurieren, finden Sie in die folgenden Schritte aus, in der SUSE-Dokumentation: [Konfigurieren von NFS-Server](https://www.suse.com/documentation/sles-12/singlehtml/book_sle_admin/book_sle_admin.html#sec.nfs.configuring-nfs-server).

### <a name="configure-all-cluster-nodes-to-connect-to-the-nfs-shared-storage"></a>Konfigurieren Sie alle Knoten des Clusters für die Verbindung mit dem freigegebenen NFS-Speicher

Vor dem Konfigurieren des Clients NFS zum Einbinden der Pfad des SQL Server-Datenbank-Dateien auf freigegebenen Speicherort zu verweisen, sicher, dass Sie die Datenbankdateien an einem temporären Speicherort können sie später kopieren Sie die Freigabe speichern:

1. **Auf dem primären Knoten nur**, speichern Sie die Datenbankdateien an einem temporären Speicherort. Das folgende Skript erstellt ein neues temporäres Verzeichnis, die die Datenbankdateien in das neue Verzeichnis kopiert und entfernt die alten Datenbankdateien. Wie SQL Server als lokaler Benutzer Mssql ausgeführt wird, müssen Sie sicherstellen, dass nach dem Übertragen von Daten in der eingebundenen Freigabe, lokaler Benutzer Lese-/ Schreibzugriff auf die Freigabe verfügt. 

    ```bash
    su mssql
    mkdir /var/opt/mssql/tmp
    cp /var/opt/mssql/data/* /var/opt/mssql/tmp
    rm /var/opt/mssql/data/*
    exit
    ```

    Konfigurieren Sie die NFS-Client auf allen Clusterknoten aus:

    - [Konfigurieren von Clients](https://www.suse.com/documentation/sles-12/singlehtml/book_sle_admin/book_sle_admin.html#sec.nfs.configuring-nfs-clients)

    > [!NOTE]
    > Es wird empfohlen, befolgen Sie SUSEs-best Practices und Empfehlungen in Bezug auf hoch verfügbaren NFS-Speicher: [Hochverfügbarer NFS-Speicher mit DRBD und Pacemaker](https://www.suse.com/documentation/sle-ha-12/book_sleha_techguides/data/art_ha_quick_nfs.html).

2. Überprüfen Sie, dass SQL Server erfolgreich mit dem neuen Dateipfad gestartet wird. Hierzu auf jedem Knoten. An diesem Punkt sollte nur ein Knoten, über SQL Server zu einem Zeitpunkt ausführen. Sie können nicht beide gleichzeitig ausgeführt, da sie beide versuchen werden, auf die Datendateien gleichzeitig (um zu vermeiden, versehentlich Starten von SQL Server auf beiden Knoten eine Dateisystem-Clusterressource verwenden, um sicherzustellen, dass die Dateifreigabe nicht zweimal von den anderen Knoten bereitgestellt ist). Die folgenden Befehle Starten von SQL Server, den Status überprüfen und beenden Sie SQL Server.

    ```bash
    sudo systemctl start mssql-server
    sudo systemctl status mssql-server
    sudo systemctl stop mssql-server
    ```

An diesem Punkt sind beide Instanzen von SQL Server für die Ausführung mit den Datenbankdateien auf dem freigegebenen Speicher konfiguriert. Der nächste Schritt ist so konfigurieren Sie SQL Server für Pacemaker. 

## <a name="install-and-configure-pacemaker-on-each-cluster-node"></a>Installieren Sie und konfigurieren Sie auf jedem Clusterknoten die Pacemaker

1. **Erstellen Sie auf beiden Clusterknoten eine Datei zum Speichern von Benutzername und Kennwort für SQL Server für die Pacemaker-Anmeldung**. Der folgende Code erstellt und füllt diese Tabelle:

    ```bash
    sudo touch /var/opt/mssql/secrets/passwd
    sudo echo '<loginName>' >> /var/opt/mssql/secrets/passwd
    sudo echo '<loginPassword>' >> /var/opt/mssql/secrets/passwd
    sudo chown root:root /var/opt/mssql/secrets/passwd 
    sudo chmod 600 /var/opt/mssql/secrets/passwd
    ```
2. **Alle Clusterknoten müssen in der Lage sein, über SSH aufeinander zugreifen**. Tools wie „hb_report“ oder „crm_report“ (zur Problembehandlung) und Hawk's History Explorer erfordern kennwortlosen SSH-Zugriff zwischen den Knoten, andernfalls können sie nur Daten vom aktuellen Knoten sammeln. Falls Sie keinen nicht-standardmäßigen SSH-Port verwenden, nutzen Sie die Option „-X“ (siehe Hauptseite). Wenn Ihr SSH-Port z.B. 3479 ist, rufen Sie hb_report mit Folgendem auf:

    ```bash
    crm_report -X "-p 3479" [...]
    ```

    Weitere Informationen finden Sie unter [Systemanforderungen und Empfehlungen in der SUSE-Dokumentation ](https://www.suse.com/documentation/sle_ha/book_sleha/data/sec_ha_requirements_other.html).

3. **Installieren Sie die Erweiterung für hohe Verfügbarkeit**. Um die Erweiterung zu installieren, befolgen Sie die Schritte im folgenden SUSE-Thema:
    
    [Installation und Setup – Schnellstart](https://www.suse.com/documentation/sle-ha-12/singlehtml/install-quick/install-quick.html)

4. **Installieren Sie den FCI-Ressourcenagent für SQL Server**. Führen Sie die folgenden Befehle auf beiden Knoten aus:

    ```bash
    sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017.repo
    sudo zypper --gpg-auto-import-keys refresh
    sudo zypper install mssql-server-ha
    ```

5. **Richten Sie den ersten Knoten automatisch ein**. Im nächsten Schritt wird ein ausgeführter Cluster mit einem Noten durch Konfigurieren des ersten Knotens, SLES1, eingerichtet. Befolgen Sie den Anweisungen im SUSE-Thema [Setting Up the First Node (Einrichten des ersten Knotens)](https://www.suse.com/documentation/sle-ha-12/singlehtml/install-quick/install-quick.html#sec.ha.inst.quick.setup.1st-node).

    Abschließend überprüfen Sie den Status des Clusters mit `crm status`:
    ```bash
    crm status
    ```

    Es sollte angezeigt werden, dass ein Knoten, SLES1, konfiguriert wurde.

6. **Hinzufügen von Knoten zu einem vorhandenen Cluster**. Als Nächstes fügen Sie den SLES2-Knoten dem Cluster hinzu. Befolgen Sie den Anweisungen im SUSE-Thema [Adding the Second Node (Hinzufügen des zweiten Knotens)](https://www.suse.com/documentation/sle-ha-12/singlehtml/install-quick/install-quick.html#sec.ha.inst.quick.setup.2nd-node).
    
    Abschließend überprüfen Sie den Status des Clusters mit **crm status**. Wenn Sie einen zweiten Knoten erfolgreich hinzugefügt haben, sieht die Ausgabe ähnlich der folgenden aus:
        
    ```
    2 nodes configured
    1 resource configured
    Online: [ SLES1 SLES2 ]
    Full list of resources:
    admin_addr     (ocf::heartbeat:IPaddr2):       Started SLES1
    ```

    > [!NOTE]
    > **admin_addr** ist die virtuelle IP-Clusterressource, die während der anfänglichen Einrichtung des Clusters mit einem Knoten konfiguriert wird.

7.  **Vorgehensweisen zum Entfernen**. Wenn Sie einen Knoten aus dem Cluster entfernen möchten, verwenden Sie das Bootstrap-Skript **ha-cluster-remove**. Weitere Informationen finden Sie unter [Overview of the Bootstrap Scripts (Übersicht über die Bootstrap-Skripts)](https://www.suse.com/documentation/sle-ha-12/singlehtml/install-quick/install-quick.html#sec.ha.inst.quick.bootstrap).  

## <a name="configure-the-cluster-resources-for-sql-server"></a>Konfigurieren Sie die Clusterressourcen für SQL Server

Die folgenden Schritte erläutern die Clusterressource für SQL Server zu konfigurieren. Es gibt zwei Einstellungen, die Sie anpassen müssen.

- **SQL Server-Ressourcenname**: Ein Name für die SQL Server-Clusterressource. 
- **Timeoutwert**: Der Timeoutwert ist die Zeitspanne, die der Cluster wartet, während eine Ressource online geschaltet wird. Für SQL Server, ist dies die Zeit, die Sie erwarten, dass SQL Server ausführen, um bringen die `master` Datenbank online. 

Aktualisieren Sie die Werte aus dem folgenden Skript für Ihre Umgebung. Führen Sie auf einem Knoten zum Konfigurieren und starten den Clusterdienst.

```bash
sudo crm configure
primitive <sqlServerResourceName> ocf:mssql:fci op start timeout=<timeout_in_seconds>
colocation <constraintName> inf: <virtualIPResourceName> <sqlServerResourceName>
show
commit
exit
```

Das folgende Skript erstellt z. B. eine gruppierten SQL Server-Ressource, die mit dem Namen Mssqlha. 

```bash
sudo crm configure
primitive mssqlha ocf:mssql:fci op start timeout=60s
colocation admin_addr_mssqlha inf: admin_addr mssqlha
show
commit
exit
```

Nachdem die Konfiguration ein Commit ausgeführt wurde, wird SQL Server auf demselben Knoten wie die virtuelle IP-Adressressource gestartet. 

Weitere Informationen finden Sie unter [konfigurieren und Verwalten von Clusterressourcen (Befehlszeile)](https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html#cha.ha.manual_config). 

### <a name="verify-that-sql-server-is-started"></a>Stellen Sie sicher, dass SQL Server gestartet wurde. 

Um sicherzustellen, dass SQL Server gestartet wird, führen Sie die **Crm Status** Befehl:

```bash
crm status
```

In den folgenden Beispielen werden die Ergebnisse auf, wenn Pacemaker als geclusterte Ressource wurde erfolgreich gestartet wurde. 
```
2 nodes configured
2 resources configured

Online: [ SLES1 SLES2 ]

Full list of resources:

 admin_addr     (ocf::heartbeat:IPaddr2):       Started SLES1
 mssqlha        (ocf::mssql:fci):       Started SLES1
```

## <a name="managing-cluster-resources"></a>Verwalten von Clusterressourcen

Um Ihre Clusterressourcen zu verwalten, finden Sie in der folgende SUSE-Thema: [Verwalten von Clusterressourcen](https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html#sec.ha.config.crm )

### <a name="manual-failover"></a>Manuelles Failover

Obwohl Ressourcen konfiguriert werden, um automatisch ein Failover (oder migrieren), auf andere Knoten des Clusters bei einem Ausfall von Hardware oder Software, können Sie auch manuell eine Ressource auf einen anderen Knoten im Cluster mithilfe der Pacemaker-GUI oder der Befehlszeile verschieben . 

Verwenden Sie den Migrationsbefehl für diese Aufgabe. Beispielsweise zum Migrieren der SQL-Ressource auf einem Cluster Knotennamen SLES2 ausführen: 

```bash
crm resource
migrate mssqlha SLES2
```

## <a name="additional-resources"></a>Zusätzliche Ressourcen

[Erweiterung für SUSE Linux Enterprise hohe Verfügbarkeit – Administratorhandbuch](https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html) 
