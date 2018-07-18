---
title: Konfigurieren von SQL Server-Einstellungen unter Linux | Microsoft-Dokumentation
description: Dieser Artikel beschreibt, wie Sie die Mssql-Conf-Tool zu verwenden, um die Einstellungen für SQL Server 2017 unter Linux konfigurieren.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 06/22/2018
ms.topic: article
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: 06798dff-65c7-43e0-9ab3-ffb23374b322
ms.openlocfilehash: 3a919f19b0b1aaef4702ac9d6e456cb9c5cf1357
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/12/2018
ms.locfileid: "38982472"
---
# <a name="configure-sql-server-on-linux-with-the-mssql-conf-tool"></a>Konfigurieren von SQL Server unter Linux mit dem Mssql-Conf-tool

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

**MSSQL-Conf** ein Konfigurationsskript, das mit SQL Server 2017 für Red Hat Enterprise Linux, SUSE Linux Enterprise Server und Ubuntu installiert ist. Sie können dieses Dienstprogramm verwenden, die folgenden Parameter fest:

|||
|---|---|
| [Agent](#agent) | SQL Server-Agent aktivieren |
| [Sortierung](#collation) | Legen Sie eine neue Sortierung für SQL Server unter Linux. |
| [Feedback von Kunden](#customerfeedback) | Wählen Sie, und zwar unabhängig davon, ob SQL Server Feedback an Microsoft sendet. |
| [Datenbank-E-Mail-Profil](#dbmail) | Legen Sie das Standard-Datenbank-Mailprofil für SQL Server unter Linux |
| [Standarddatenverzeichnis](#datadir) | Ändern Sie das Standardverzeichnis für die neue SQL Server-Datenbank-Datendateien (MDF). |
| [Standardprotokollverzeichnis](#datadir) | Ändert das Standardverzeichnis für die neue SQL Server-Datenbank-Protokolldatei (.ldf)-Dateien. |
| [Standardverzeichnis für master-Datenbank-Datei](#masterdatabasedir) | Ändert das Standardverzeichnis für die master-Datenbank-Dateien auf vorhandenen SQL-Installation.|
| [Standarddateiname für die master-Datenbank](#masterdatabasename) | Ändert den Namen der master-Datenbank-Dateien. |
| [Standardverzeichnis für die Sicherung](#dumpdir) | Ändern Sie das Standardverzeichnis für neue Speicherabbilder und andere Dateien bei der Problembehandlung. |
| [Fehler-Standardprotokollverzeichnis](#errorlogdir) | Ändert das Standardverzeichnis für die neue SQL Server-Fehlerprotokoll, Standard-Profiler-Ablaufverfolgung, System Health-Sitzung XE und Hekaton Sitzung XE-Dateien. |
| [Standardsicherungsverzeichnis](#backupdir) | Ändern Sie das Standardverzeichnis für neue Sicherungsdateien. |
| [Abbildtyp](#coredump) | Wählen Sie den Typ der Dump Speicherabbilddatei sammeln. |
| [High Availability (Hohe Verfügbarkeit)](#hadr) | Aktivieren Sie Verfügbarkeitsgruppen. |
| [Verzeichnis der lokalen Überwachung](#localaudit) | Legen Sie einen ein Verzeichnis an die lokale Überwachungsdateien hinzufügen. |
| [Gebietsschema](#lcid) | Legen Sie das Gebietsschema für SQL Server verwenden. |
| [Das Arbeitsspeicherlimit](#memorylimit) | Legen Sie das Arbeitsspeicherlimit für SQL Server. |
| [TCP-port](#tcpport) | Ändern Sie den Port, der von SQL Server, in dem für Verbindungen überwacht. |
| [TLS](#tls) | Konfigurieren Sie die Sicherheit auf Transportebene. |
| [Ablaufverfolgungsflags](#traceflags) | Legen Sie die Ablaufverfolgungsflags, die der Dienst verwenden soll. |

> [!TIP]
> Einige dieser Einstellungen können auch mit Umgebungsvariablen konfiguriert werden. Weitere Informationen finden Sie unter [Konfigurieren von SQL Server-Einstellungen mit Umgebungsvariablen](sql-server-linux-configure-environment-variables.md).

## <a name="usage-tips"></a>Tipps zur Verwendung

* Stellen Sie für AlwaysOn-Verfügbarkeitsgruppen und freigegebenen datenträgerclustern immer die gleichen Änderungen an der Konfiguration auf jedem Knoten ein.

* Für den freigegebenen Datenträger-Clusterszenario: versuchen Sie nicht neu starten die **Mssql-Server** Dienst, um Änderungen zu übernehmen. SQL Server wird als Anwendung ausgeführt. Stattdessen sollte die Ressource offline und anschließend wieder online geschaltet.

* Diese Beispiele führen Sie die Mssql-Conf, indem Sie den vollständigen Pfad angeben: **/opt/mssql/bin/mssql-conf**. Wenn Sie stattdessen auf diesen Pfad navigieren möchten, führen Sie die Mssql-Conf im Kontext des aktuellen Verzeichnisses: **. / Mssql-Conf**.

## <a id="agent"></a> SQL Server-Agent aktivieren

Die **sqlagent.enabled** festgelegt werden, dass [SQL Server-Agent](sql-server-linux-run-sql-server-agent-job.md). Standardmäßig ist SQL Server-Agent deaktiviert. Wenn **sqlagent.enabled** ist nicht vorhanden ist, in der Datei mssql.conf Einstellungen, und klicken Sie dann SQL Server wird intern davon ausgegangen, dass SQL Server-Agent deaktiviert ist.

Verwenden Sie die folgenden Schritte aus, um diese Einstellungen zu ändern:

1. Aktivieren Sie SQL Server-Agent:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set sqlagent.enabled true 
   ```

1. Starten Sie SQL Server-Dienst neu:

   ```bash
   sudo systemctl restart mssql-server
   ```

## <a id="collation"></a> Ändern Sie die SQL Server-Sortierung

Die **Set-Collation** Option ändert den Sortierungswert auf eine der unterstützten Sortierungen.

1. Erste [Sichern einer beliebigen Benutzerdatenbank](sql-server-linux-backup-and-restore-database.md) auf dem Server.

1. Verwenden Sie dann die [Sp_detach_db](../relational-databases/system-stored-procedures/sp-detach-db-transact-sql.md) gespeicherte Prozedur, um die Benutzerdatenbanken zu trennen.

1. Führen Sie die **Set-Collation** aus, und befolgen Sie die Anweisungen:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set-collation
   ```

1. Das Hilfsprogramm für die Mssql-Conf versucht, auf den Wert der angegebenen Sortierung ändern und den Dienst neu. Wenn Fehler vorliegen, setzt es die Sortierung auf den vorherigen Wert zurück.

1. Wiederherstellen von Sicherungen Ihrer Benutzer-Datenbank.

Führen Sie eine Liste der unterstützten Sortierungen, die [fn_helpcollations](../relational-databases/system-functions/sys-fn-helpcollations-transact-sql.md) Funktion: `SELECT Name from sys.fn_helpcollations()`.

## <a id="customerfeedback"></a> Konfigurieren Sie Feedback von Kunden

Die **telemetry.customerfeedback** Änderungen festlegen, ob SQL Server Feedback an Microsoft oder nicht sendet. Standardmäßig ist dieser Wert auf festgelegt **"true"** für alle Editionen. Um den Wert zu ändern, führen Sie die folgenden Befehle aus:

> [!IMPORTANT]
> Sie können nicht die Feedback von Kunden für kostenlose Editionen von SQL Server "," Express "und" Developer deaktivieren.

1. Führen Sie das Mssql-Conf-Skript als Root-Benutzer mit der **festgelegt** Befehl **telemetry.customerfeedback**. Das folgende Beispiel deaktiviert die Feedback von Kunden dazu **"false"**.

   ```bash
   sudo /opt/mssql/bin/mssql-conf set telemetry.customerfeedback false
   ```

1. Starten Sie SQL Server-Dienst neu:

   ```bash
   sudo systemctl restart mssql-server
   ```

Weitere Informationen finden Sie unter [Kundenfeedback zu SQL Server unter Linux](sql-server-linux-customer-feedback.md) und [Datenschutzbestimmungen für SQL Server](http://go.microsoft.com/fwlink/?LinkID=868444).

## <a id="datadir"></a> Speicherort des Standardverzeichnisses Daten- oder Protokolldatei zu ändern

Die **filelocation.defaultdatadir** und **filelocation.defaultlogdir** Einstellungen ändern, die Position, in dem die neuen Datenbank und-Protokolldateien erstellt werden. Standardmäßig ist dieser Speicherort /var/opt/mssql/data. Um diese Einstellungen zu ändern, verwenden Sie die folgenden Schritte aus:

1. Erstellen Sie das Zielverzeichnis für die neue Datenbank die Daten-und Protokolldateien. Das folgende Beispiel erstellt ein neues **/Tmp/Daten** Verzeichnis:

   ```bash
   sudo mkdir /tmp/data
   ```

1. Ändern Sie den Besitzer und die Gruppe des Verzeichnisses, das die **Mssql** Benutzer:

   ```bash
   sudo chown mssql /tmp/data
   sudo chgrp mssql /tmp/data
   ```

1. Verwenden der Mssql-Conf so ändern Sie das Standardverzeichnis für die Daten mit der **festgelegt** Befehl:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set filelocation.defaultdatadir /tmp/data
   ```

1. Starten Sie SQL Server-Dienst neu:

   ```bash
   sudo systemctl restart mssql-server
   ```

1. Alle Datenbankdateien für die neuen erstellten Datenbanken werden jetzt in den neuen Speicherort gespeichert werden. Wenn Sie den Speicherort der Protokolldateien (LDF) der neuen Datenbanken ändern möchten, können Sie den folgenden "Set"-Befehl verwenden:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set filelocation.defaultlogdir /tmp/log
   ```

1. Dieser Befehl setzt auch voraus, dass ein/Tmp/Log-Verzeichnis vorhanden ist und sie die Benutzer und Gruppen ist, die **Mssql**.


## <a id="masterdatabasedir"></a> Ändern Sie das Standard-master-Datenbank-Dateiverzeichnis

Die **filelocation.masterdatafile** und **filelocation.masterlogfile** Einstellung ändert sich den Speicherort, in dem Dateien der Masterdatenbank die SQL Server-Engine sucht. Standardmäßig ist dieser Speicherort /var/opt/mssql/data. 

Um diese Einstellungen zu ändern, verwenden Sie die folgenden Schritte aus:

1. Erstellen Sie das Zielverzeichnis für neue Fehlerprotokolldateien. Das folgende Beispiel erstellt ein neues **/Tmp/Masterdatabasedir** Verzeichnis:

   ```bash
   sudo mkdir /tmp/masterdatabasedir
   ```

1. Ändern Sie den Besitzer und die Gruppe des Verzeichnisses, das die **Mssql** Benutzer:

   ```bash
   sudo chown mssql /tmp/masterdatabasedir
   sudo chgrp mssql /tmp/masterdatabasedir
   ```

1. Verwenden der Mssql-Conf so ändern Sie das Standardverzeichnis für die master-Datenbank für die master Daten- und Protokolldateien mit den **festgelegt** Befehl:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set filelocation.masterdatafile /tmp/masterdatabasedir/master.mdf
   sudo /opt/mssql/bin/mssql-conf set filelocation.masterlogfile /tmp/masterdatabasedir/mastlog.ldf
   ```

1. Beenden Sie den SQL Server-Dienst:

   ```bash
   sudo systemctl stop mssql-server
   ```

1. Verschieben Sie die master.mdf und masterlog.ldf: 

   ```bash
   sudo mv /var/opt/mssql/data/master.mdf /tmp/masterdatabasedir/master.mdf 
   sudo mv /var/opt/mssql/data/mastlog.ldf /tmp/masterdatabasedir/mastlog.ldf
   ```

1. Starten Sie den SQL Server-Dienst:

   ```bash
   sudo systemctl start mssql-server
   ```
   
> [!NOTE]
> Wenn SQL Server im angegebenen Verzeichnis die Dateien master.mdf und mastlog.ldf finden kann, eine auf Vorlagen basierenden Kopie der Datenbanken wird automatisch im angegebenen Verzeichnis erstellt werden, und SQL Server wird erfolgreich gestartet. Metadaten wie z. B. Benutzerdatenbanken, Server-Anmeldungen, Server-Zertifikate, Verschlüsselungsschlüssel, SQL Agent-Aufträge oder alte SA-Anmeldekennwort wird jedoch nicht in der neuen master-Datenbank aktualisiert werden. Sie müssen zum Beenden von SQL Server und Ihrer alten master.mdf und mastlog.ldf an den neuen angegebenen Speicherort zu verschieben, und Starten von SQL Server, um den Vorgang fortzusetzen, verwenden die vorhandene Metadaten. 


## <a id="masterdatabasename"></a> Ändern Sie den Namen der master-Datenbank.

Die **filelocation.masterdatafile** und **filelocation.masterlogfile** Einstellung ändert sich den Speicherort, in dem Dateien der Masterdatenbank die SQL Server-Engine sucht. Standardmäßig ist dieser Speicherort /var/opt/mssql/data. Um diese Einstellungen zu ändern, verwenden Sie die folgenden Schritte aus:

1. Beenden Sie den SQL Server-Dienst:

   ```bash
   sudo systemctl stop mssql-server
   ```

1. Verwenden der Mssql-Conf so ändern Sie die erwartete master-Datenbank-Namen für die master Daten- und Protokolldateien mit den **festgelegt** Befehl:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set filelocation.masterdatafile /var/opt/mssql/data/masternew.mdf
   sudo /opt/mssql/bin/mssql-conf set filelocation.mastlogfile /var/opt/mssql/data /mastlognew.ldf
   ```

1. Ändern Sie den Namen der der master-Datenbank Daten und Protokolldateien 

   ```bash
   sudo mv /var/opt/mssql/data/master.mdf /var/opt/mssql/data/masternew.mdf
   sudo mv /var/opt/mssql/data/mastlog.ldf /var/opt/mssql/data/mastlognew.ldf
   ```

1. Starten Sie den SQL Server-Dienst:

   ```bash
   sudo systemctl start mssql-server
   ```



## <a id="dumpdir"></a> Ändern Sie den Speicherort des Standardverzeichnisses dump

Die **filelocation.defaultdumpdir** am Standardspeicherort, in dem der Arbeitsspeicher und die SQL-Dumps generiert werden, wenn ein Absturz ist, die Einstellung ändert sich. Standardmäßig werden diese Dateien im /var/opt/mssql/log generiert.

Um den neuen Speicherort einzurichten, verwenden Sie die folgenden Befehle aus:

1. Erstellen Sie das Zielverzeichnis für neue debugdumpdateien. Das folgende Beispiel erstellt ein neues **/Tmp/Dump** Verzeichnis:

   ```bash
   sudo mkdir /tmp/dump
   ```

1. Ändern Sie den Besitzer und die Gruppe des Verzeichnisses, das die **Mssql** Benutzer:

   ```bash
   sudo chown mssql /tmp/dump
   sudo chgrp mssql /tmp/dump
   ```

1. Verwenden der Mssql-Conf so ändern Sie das Standardverzeichnis für die Daten mit der **festgelegt** Befehl:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set filelocation.defaultdumpdir /tmp/dump
   ```

1. Starten Sie SQL Server-Dienst neu:

   ```bash
   sudo systemctl restart mssql-server
   ```

## <a id="errorlogdir"></a> Ändern Sie den Fehler Directory Standardspeicherort der Protokolldatei

Die **filelocation.errorlogfile** Einstellung ändert sich die Position, in dem das neue Fehlerprotokoll, Standard-Profiler-Ablaufverfolgung, systemintegritätssitzung XE und Hekaton-Sitzungsdateien XE erstellt werden. Standardmäßig ist dieser Speicherort /var/opt/mssql/log. Das Verzeichnis, in dem SQL-Fehlerprotokoll-Datei festgelegt ist, wird das Standardprotokollverzeichnis für andere Protokolle.

So ändern Sie diese Einstellungen:

1. Erstellen Sie das Zielverzeichnis für neue Fehlerprotokolldateien. Das folgende Beispiel erstellt ein neues **/Tmp/Protokolle** Verzeichnis:

   ```bash
   sudo mkdir /tmp/logs
   ```

1. Ändern Sie den Besitzer und die Gruppe des Verzeichnisses, das die **Mssql** Benutzer:

   ```bash
   sudo chown mssql /tmp/logs
   sudo chgrp mssql /tmp/logs
   ```

1. Verwenden der Mssql-Conf so ändern Sie den standardmäßigen Errorlog-Dateinamen mit der **festgelegt** Befehl:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set filelocation.errorlogfile /tmp/logs/errorlog
   ```

1. Starten Sie SQL Server-Dienst neu:

   ```bash
   sudo systemctl restart mssql-server
   ```


## <a id="backupdir"></a> Ändern des Standardspeicherorts für das Sicherungsverzeichnis

Die **filelocation.defaultbackupdir** Einstellung ändert sich den Standardspeicherort, an dem die Sicherungsdateien generiert werden. Standardmäßig werden diese Dateien im /var/opt/mssql/data generiert.

Um den neuen Speicherort einzurichten, verwenden Sie die folgenden Befehle aus:

1. Erstellen Sie das Zielverzeichnis für neue Sicherungsdateien. Das folgende Beispiel erstellt ein neues **/Tmp/Backup** Verzeichnis:

   ```bash
   sudo mkdir /tmp/backup
   ```

1. Ändern Sie den Besitzer und die Gruppe des Verzeichnisses, das die **Mssql** Benutzer:

   ```bash
   sudo chown mssql /tmp/backup
   sudo chgrp mssql /tmp/backup
   ```

1. Verwenden Sie Mssql-Conf, um das Standardsicherungsverzeichnis mit dem Befehl "Set" zu ändern:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set filelocation.defaultbackupdir /tmp/backup
   ```

1. Starten Sie SQL Server-Dienst neu:

   ```bash
   sudo systemctl restart mssql-server
   ```

## <a id="coredump"></a> Geben Sie kernspeicherabbilds-Einstellungen

Wenn in einer der SQL Server-Prozesse eine Ausnahme auftritt, erstellt SQL Server ein Speicherabbild.

Es gibt zwei Optionen für das Steuern des Typs des Arbeitsspeichers, dass SQL Server erfasst Speicherabbilder: **coredump.coredumptype** und **coredump.captureminiandfull**. Diese beziehen sich auf die beiden Phasen des kernspeicherabbilds erfassen. 

Die erste Phase Aufzeichnung wird gesteuert, indem die **coredump.coredumptype** Einstellung, die den Typ der Dumpdatei, während eine Ausnahme generiert bestimmt. Die zweite Phase aktiviert ist, wenn die **coredump.captureminiandfull** festlegen. Wenn **coredump.captureminiandfull** ist auf true festgelegt, das Abbild vom angegebenen Datei **coredump.coredumptype** wird generiert, und ein zweites Miniabbild wird ebenfalls generiert. Festlegen von **coredump.captureminiandfull** auf "false" verhindert die zweite Erfassung versuchen.

1. Entscheiden Sie, ob sowohl vollständige als auch Mini-Dumpdateien mit Erfassen der **coredump.captureminiandfull** festlegen.

    ```bash
    sudo /opt/mssql/bin/mssql-conf set coredump.captureminiandfull <true or false>
    ```

    Standardwert: **"false"**

1. Geben Sie die Dumpdatei mit der **coredump.coredumptype** festlegen.

    ```bash
    sudo /opt/mssql/bin/mssql-conf set coredump.coredumptype <dump_type>
    ```

    Standardwert: **Miniplus**

    Die folgende Tabelle enthält die möglichen **coredump.coredumptype** Werte.

    | Typ | Description |
    |-----|-----|
    | **Mini** | Mini ist der kleinste Dump-Dateityp. Es verwendet die Linux-System-Informationen, um zu bestimmen, Threads und Module im Prozess. Das Speicherabbild enthält nur die Host-Umgebung Threadstapel und Module. Es enthält keine Speicherverweise indirekte oder globale Variablen. |
    | **miniplus** | MiniPlus Mini ähnelt, aber sie zusätzlichen Arbeitsspeicher enthält. Es versteht die Interna der SQLPAL und der hostumgebung, die der Dump werden die folgenden Arbeitsspeicherbereiche hinzugefügt:</br></br> -Verschiedene globale Variablen</br> – Alle Arbeitsspeicher über 64TB</br> -Alle Regionen finden Sie im Namen **/proc/$ pid/Zuordnungen**</br> -Indirekte Arbeitsspeicher von Threads und Stapel</br> -Thread Informationen</br> -Verknüpft ist, die Teb und des Peb</br> -Module-Informationen</br> -VMM und VAD-Struktur |
    | **filtered** | Gefilterte verwendet ein Subtraktion basierende entwerfen, in dem gesamten Speicher im Prozess enthalten ist, es sei denn, Sie ausdrücklich ausgeschlossen. Der Entwurf versteht die Interna der SQLPAL und der hostumgebung, die bestimmten Regionen aus der Sicherung ausschließen.
    | **full** | Vollständige befindet sich vollständig prozessdump, die alle Bereiche im **/proc/$ pid/Zuordnungen**. Dies wird nicht durch gesteuert **coredump.captureminiandfull** festlegen. |

## <a id="dbmail"></a> Legen Sie das Standard-Datenbank-Mailprofil für SQL Server unter Linux

Die **sqlpagent.databasemailprofile** können Sie das Standardprofil für die Datenbank-Mail für Warnungen über e-Mail festlegen.

```bash
sudo /opt/mssq/bin/mssql-conf set sqlagent.databasemailprofile <profile_name>
```
## <a id="hadr"></a> Hohe Verfügbarkeit

Die **hadr.hadrenabled** Option Verfügbarkeitsgruppen auf Ihrer SQL Server-Instanz aktiviert. Der folgende Befehl aktiviert die Verfügbarkeitsgruppen durch Festlegen von **hadr.hadrenabled** auf 1. Sie müssen SQL Server für die Einstellung wirksam wird neu starten.

```bash
sudo /opt/mssql/bin/mssql-conf set hadr.hadrenabled  1
sudo systemctl restart mssql-server
```

Informationen, wie dies mit Verfügbarkeitsgruppen verwendet wird, finden Sie unter den folgenden zwei Themen.

- [Konfigurieren Sie Always On-Verfügbarkeitsgruppe für SQLServer unter Linux](sql-server-linux-availability-group-configure-ha.md)
- [Konfigurieren von schreibgeschützten Verfügbarkeitsgruppen für SQL Server unter Linux](sql-server-linux-availability-group-configure-rs.md)

## <a id="localaudit"></a> Die lokale Überwachung Directory Satz

Die **telemetry.userrequestedlocalauditdirectory** Einstellung wird die lokale Überwachung aktiviert, und können Sie das Verzeichnis, in dem Protokolle der lokalen Überwachung erstellt werden.

1. Erstellen Sie ein Zielverzeichnis für neue Protokolle der lokalen Überwachung. Das folgende Beispiel erstellt ein neues **/Tmp/Audit** Verzeichnis:

   ```bash
   sudo mkdir /tmp/audit
   ```

1. Ändern Sie den Besitzer und die Gruppe des Verzeichnisses, das die **Mssql** Benutzer:

   ```bash
   sudo chown mssql /tmp/audit
   sudo chgrp mssql /tmp/audit
   ```

1. Führen Sie das Mssql-Conf-Skript als Root-Benutzer mit der **festgelegt** Befehl **telemetry.userrequestedlocalauditdirectory**:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set telemetry.userrequestedlocalauditdirectory /tmp/audit
   ```

1. Starten Sie SQL Server-Dienst neu:

   ```bash
   sudo systemctl restart mssql-server
   ```

Weitere Informationen finden Sie unter [Kundenfeedback zu SQL Server unter Linux](sql-server-linux-customer-feedback.md).

## <a id="lcid"></a> Ändern Sie das SQL Server-Gebietsschema

Die **language.lcid** Einstellung ändert sich das SQL Server-Gebietsschema auf alle unterstützten Sprachen-ID (LCID). 

1. Im folgende Beispiel ändert das Gebietsschema auf Französisch (1036):

   ```bash
   sudo /opt/mssql/bin/mssql-conf set language.lcid 1036
   ```

1. Starten Sie SQL Server-Diensts zum Übernehmen der Änderungen neu:

   ```bash
   sudo systemctl restart mssql-server
   ```

## <a id="memorylimit"></a> Legen Sie das Arbeitsspeicherlimit

Die **memory.memorylimitmb** das Festlegen der Steuerelemente des Menge verfügbaren physischen Speichers (in MB) in SQL Server. Der Standardwert ist 80 % des physischen Arbeitsspeichers.

1. Führen Sie das Mssql-Conf-Skript als Root-Benutzer mit der **festgelegt** Befehl **memory.memorylimitmb**. Im folgende Beispiel ändert den verfügbaren Arbeitsspeicher mit SQL Server zum 3,25 GB (3328 MB).

   ```bash
   sudo /opt/mssql/bin/mssql-conf set memory.memorylimitmb 3328
   ```

1. Starten Sie SQL Server-Diensts zum Übernehmen der Änderungen neu:

   ```bash
   sudo systemctl restart mssql-server
   ```

## <a id="tcpport"></a> Ändern Sie den TCP-port

Die **network.tcpport** Einstellung ändert sich des TCP-Ports, in dem von SQL Server für Verbindungen überwacht. Standardmäßig wird dieser Port auf 1433 festgelegt. Um den Port zu ändern, führen Sie die folgenden Befehle aus:

1. Führen Sie das Mssql-Conf-Skript als Root-Benutzer mit dem Befehl "set" für "network.tcpport":

   ```bash
   sudo /opt/mssql/bin/mssql-conf set network.tcpport <new_tcp_port>
   ```

1. Starten Sie SQL Server-Dienst neu:

   ```bash
   sudo systemctl restart mssql-server
   ```

1. Wenn jetzt eine Verbindung mit SQL Server herstellen, müssen Sie den benutzerdefinierten Port durch ein Komma (,) nach den Hostnamen oder IP-Adresse angeben. Zur Verbindung mit SQLCMD würden Sie beispielsweise den folgenden Befehl verwenden:

   ```bash
   sqlcmd -S localhost,<new_tcp_port> -U test -P test
   ```

## <a id="tls"></a> Geben Sie die TLS-Einstellungen

Die folgenden Optionen konfigurieren TLS für eine Instanz von SQL Server unter Linux ausgeführt wird.

|Option |Description |
|--- |--- |
|**network.forceencryption** |Wenn der Wert 1 ist, klicken Sie dann [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] erzwingt, dass alle Verbindungen verschlüsselt werden. Standardmäßig ist diese Option 0. |
|**network.tlscert** |Der absolute Pfad zu dem Zertifikat-Datei, die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] für TLS verwendet. Beispiel: `/etc/ssl/certs/mssql.pem` die Zertifikatdatei muss den Mssql-Konto zugänglich sein. Microsoft empfiehlt die Beschränkung des Zugriffs auf die Datei mit `chown mssql:mssql <file>; chmod 400 <file>`. |
|**network.tlskey** |Der absolute Pfad zum privaten Schlüssel der Datei, die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] für TLS verwendet. Beispiel: `/etc/ssl/private/mssql.key` die Zertifikatdatei muss den Mssql-Konto zugänglich sein. Microsoft empfiehlt die Beschränkung des Zugriffs auf die Datei mit `chown mssql:mssql <file>; chmod 400 <file>`. |
|**network.tlsprotocols** |Eine durch Trennzeichen getrennte Liste der TLS-Protokolle von SQL Server zulässig sind. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] immer versucht, die höchste zulässige Protokoll ausgehandelt. Wenn ein Client keine zulässigen Protokolle und unterstützt [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] den Verbindungsversuch abgelehnt.  Für die Kompatibilität sind alle unterstützten Protokolle (1.2, 1.1, 1.0) standardmäßig zulässig.  Wenn Ihre Clients TLS 1.2 unterstützen, empfiehlt Microsoft, sodass nur TLS 1.2. |
|**Network.tlsciphers** |Gibt an, welche Verschlüsselungen zulässig sind [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] für TLS. Diese Zeichenfolge muss formatiert werden, pro [Format für die OpenSSL-Verschlüsselungsverfahren](https://www.openssl.org/docs/man1.0.2/apps/ciphers.html). Im Allgemeinen sollten Sie nicht diese Option ändern müssen. <br /> Standardmäßig sind die folgenden Chiffren zulässig: <br /> `ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-AES128-SHA256:ECDHE-ECDSA-AES256-SHA384:ECDHE-RSA-AES128-SHA256:ECDHE-RSA-AES256-SHA384:ECDHE-ECDSA-AES256-SHA:ECDHE-ECDSA-AES128-SHA:ECDHE-RSA-AES256-SHA:ECDHE-RSA-AES128-SHA:AES256-GCM-SHA384:AES128-GCM-SHA256:AES256-SHA256:AES128-SHA256:AES256-SHA:AES128-SHA` |
| **network.kerberoskeytabfile** |Pfad zu die Kerberos-schlüsseltabellendatei |

Ein Beispiel für die TLS-Einstellungen verwenden, finden Sie unter [Verschlüsseln von Verbindungen zu SQL Server unter Linux](sql-server-linux-encrypted-connections.md).

## <a id="traceflags"></a> Aktivieren/Deaktivieren von Ablaufverfolgungsflags

Dies **Ablaufverfolgungsflag** Option aktiviert oder deaktiviert die Ablaufverfolgungsflags für den Start des SQL Server-Diensts. Zum Aktivieren/Deaktivieren des ein Ablaufverfolgungsflag, verwenden Sie die folgenden Befehle aus:

1. Aktivieren Sie ein Ablaufverfolgungsflag mit dem folgenden Befehl ein. Z. B. für das Ablaufverfolgungsflag 1234:

   ```bash
   sudo /opt/mssql/bin/mssql-conf traceflag 1234 on
   ```

1. Sie können mehrere Ablaufverfolgungsflags aktivieren, indem Sie diese separat angeben:

   ```bash
   sudo /opt/mssql/bin/mssql-conf traceflag 2345 3456 on
   ```

1. Auf ähnliche Weise, können Sie eine oder mehrere aktivierte Ablaufverfolgungsflags deaktivieren, indem sie angeben und das Hinzufügen der **aus** Parameter:

   ```bash
   sudo /opt/mssql/bin/mssql-conf traceflag 1234 2345 3456 off
   ```

1. Starten Sie SQL Server-Diensts zum Übernehmen der Änderungen neu:

   ```bash
   sudo systemctl restart mssql-server
   ```

## <a name="remove-a-setting"></a>Entfernen einer Einstellung

Wieder entfernen eine Einstellung vorgenommen, mit `mssql-conf set`, rufen Sie **Mssql-Conf** mit der `unset` Option und den Namen der Einstellung. Dies löscht die Einstellung, die sie tatsächlich auf den Standardwert zurückgegeben.

1. Das folgende Beispiel löscht den **network.tcpport** Option.

   ```bash
   sudo /opt/mssql/bin/mssql-conf unset network.tcpport
   ```

1. Starten Sie SQL Server-Dienst neu.

   ```bash
   sudo systemctl restart mssql-server
   ```

## <a name="view-current-settings"></a>Anzeigen der aktuellen Einstellungen

Konfiguriert Sie, alle Einstellungen, führen Sie den folgenden Befehl aus, um den Inhalt der Ausgabe der **mssql.conf** Datei:

```bash
sudo cat /var/opt/mssql/mssql.conf
```

Beachten Sie, dass alle Einstellungen, die in dieser Datei nicht angezeigt. die Standardwerte verwenden. Der nächste Abschnitt enthält ein Beispiel für **mssql.conf** Datei.

## <a name="mssqlconf-format"></a>MSSQL.conf-format

Die folgenden **/var/opt/mssql/mssql.conf** Datei enthält ein Beispiel für jede Einstellung. Sie können dieses Format verwenden, manuell vornehmen von Änderungen an der **mssql.conf** Datei je nach Bedarf. Wenn Sie die Datei manuell ändern, müssen Sie SQL Server neu starten, bevor die Änderungen angewendet werden. Verwenden der **mssql.conf** Datei mit Docker benötigen Sie Docker [speichern Ihre Daten](sql-server-linux-configure-docker.md). Fügen Sie zunächst eine vollständige **mssql.conf** -Datei in Ihrem Hostverzeichnis ein, und führen Sie dann den Container. Es ist ein Beispiel hierfür in [Kundenfeedback](sql-server-linux-customer-feedback.md).

```ini
[EULA]
accepteula = Y

[coredump]
captureminiandfull = true
coredumptype = full

[filelocation]
defaultbackupdir = /var/opt/mssql/data/
defaultdatadir = /var/opt/mssql/data/
defaultdumpdir = /var/opt/mssql/data/
defaultlogdir = /var/opt/mssql/data/

[hadr]
hadrenabled = 0

[language]
lcid = 1033

[memory]
memorylimitmb = 4096

[network]
forceencryption = 0
ipaddress = 10.192.0.0
kerberoskeytabfile = /var/opt/mssql/secrets/mssql.keytab
tcpport = 1401
tlscert = /etc/ssl/certs/mssql.pem
tlsciphers = ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-AES128-SHA256:ECDHE-ECDSA-AES256-SHA384:ECDHE-RSA-AES128-SHA256:ECDHE-RSA-AES256-SHA384:ECDHE-ECDSA-AES256-SHA:ECDHE-ECDSA-AES128-SHA:ECDHE-RSA-AES256-SHA:ECDHE-RSA-AES128-SHA:AES256-GCM-SHA384:AES128-GCM-SHA256:AES256-SHA256:AES128-SHA256:AES256-SHA:AES128-SHA
tlskey = /etc/ssl/private/mssql.key
tlsprotocols = 1.2,1.1,1.0

[sqlagent]
databasemailprofile = default
errorlogfile = /var/opt/mssql/log/sqlagentlog.log
errorlogginglevel = 7

[telemetry]
customerfeedback = true
userrequestedlocalauditdirectory = /tmp/audit

[traceflag]
traceflag0 = 1204
traceflag1 = 2345
traceflag = 3456
```

## <a name="next-steps"></a>Nächste Schritte

Stattdessen Umgebungsvariablen verwenden, um einige dieser Änderungen an der Konfiguration vornehmen, finden Sie unter [Konfigurieren von SQL Server-Einstellungen mit Umgebungsvariablen](sql-server-linux-configure-environment-variables.md).

Andere Verwaltungstools und Szenarien finden Sie unter [Verwalten von SQL Server unter Linux](sql-server-linux-management-overview.md).
