---
title: SQL Server von Datendateien in Windows Azure | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
ms.assetid: 38ffd9c2-18a5-43d2-b674-e425addec4e4
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 36d940e71dc6a5816dc08fb79e045f46f783116e
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2019
ms.locfileid: "69028624"
---
# <a name="sql-server-data-files-in-windows-azure"></a>SQL Server-Datendateien in Windows Azure
  Die SQL Server-Datendateien in Windows Azure ermöglichen die systemeigene Unterstützung von SQL Server-Datenbankdateien, die als Windows Azure-BLOBs gespeichert sind. Mit der Funktion können Sie eine Datenbank in SQL Server erstellen, die lokal oder auf einem virtuellen Computer in Windows Azure ausgeführt wird, wobei ein dedizierter Speicherort für Ihre Daten im Windows Azure-BLOB-Speicher bereitgestellt wird. Diese Erweiterung vereinfacht insbesondere das Verschieben von Datenbanken zwischen Computern mithilfe von Trenn- und Anfügevorgängen. Darüber hinaus bietet sie einen alternativen Speicherort für Datenbank-Sicherungsdateien, da Wiederherstellungen im oder aus dem Windows Azure-Speicher ermöglicht werden. Mit erweiterten Funktionen für das Virtualisieren und Verschieben von Daten sowie für Sicherheit und Verfügbarkeit unterstützt sie verschiedene Hybridlösungen und bietet zusätzlich kostengünstige, einfache Verwaltungsfunktionen für hohe Verfügbarkeit und flexible Skalierung.  
  
 In diesem Thema werden zentrale Konzepte und Überlegungen zur Speicherung von SQL Server-Datendateien im Microsoft Azure-Speicherdienst eingeführt.  
  
 Ein praktisches Beispiel für die Verwendung dieses neuen Features finden Sie im [Tutorial: SQL Server Sie Datendateien im Windows Azure Storage](../tutorial-use-azure-blob-storage-service-with-sql-server-2016.md)-Dienst ab.  
  
 Das folgende Diagramm veranschaulicht, dass Sie mit dieser Erweiterung SQL Server-Datenbankdateien unabhängig vom Serverstandort im Windows Azure-Speicher als Windows Azure-BLOBs speichern können.  
  
 ![SQL Server Integration in Windows Azure Storage](../../database-engine/media/sql-server-dbfiles-stored-as-blobs.gif "SQL Server Integration in Windows Azure Storage")  
  
## <a name="benefits-of-using-sql-server-data-files-in-windows-azure"></a>Vorteile der Verwendung von SQL Server-Datendateien in Windows Azure  
  
-   **Vorteil – Einfache und schnelle Migration:** Diese Funktion vereinfacht den Migrationsprozess, indem jeweils eine Datenbank zwischen Computern in lokalen Umgebungen sowie zwischen lokalen und Cloudumgebungen verschoben wird, ohne dass Änderungen an der Anwendung vorgenommen werden müssen. Auf diese Weise wird eine inkrementelle Migration unterstützt, während Ihre vorhandene lokale Infrastruktur unverändert beibehalten wird. Darüber hinaus vereinfacht der Zugriff auf einen zentralen Datenspeicher die Anwendungslogik, wenn eine Anwendung in einer lokalen Umgebung an mehreren Stellen ausgeführt werden muss. Es kann vorkommen, dass Sie schnell Rechenzentren an geografisch verteilten Standorten einrichten müssen, in denen Daten aus vielen verschiedenen Quellen gesammelt werden. Mit dieser neuen Erweiterung müssen Daten nicht mehr zwischen Speicherorten verschoben werden. Stattdessen können Sie zahlreiche Datenbanken als Windows Azure-BLOBs speichern und anschließend mithilfe von Transact-SQL-Skripts Datenbanken auf den lokalen oder virtuellen Computern erstellen.  
  
-   **Vorteil – Kostengünstig und unbegrenzter Speicher:** Diese Funktion ermöglicht es Ihnen, unbegrenzten Offsite-Speicher in Windows Azure zu nutzen, während gleichzeitig lokale computeressourcen genutzt werden. Wenn Sie Windows Azure als Datenspeicher verwenden, können Sie sich problemlos auf die Anwendungslogik konzentrieren, ohne sich um die aufwändige Hardwareverwaltung kümmern zu müssen. Wenn ein lokaler Serverknoten ausfällt, können Sie einen neuen Knoten einrichten, ohne Daten zu verschieben.  
  
-   **Vorteil – Hochverfügbarkeit und Notfallwiederherstellung:** Wenn Sie SQL Server Datendateien in Windows Azure verwenden, können Sie die Lösungen für Hochverfügbarkeit und Notfall Wiederherstellung vereinfachen. Beispiel: Wenn ein virtueller Computer in Windows Azure oder eine SQL Server-Instanz abstürzt, können Sie die Datenbanken auf einem neuen Computer neu erstellen, indem Sie einfach wieder Verknüpfungen zu Windows Azure-BLOBs herstellen.  
  
-   **Vorteil – Sicherheit:** Durch diese neue Erweiterung können Serverinstanzen von Speicherinstanzen getrennt behandelt werden. Beispielsweise können Sie über eine vollständig verschlüsselte Datenbank verfügen, deren Entschlüsselung ausschließlich auf einer Serverinstanz und nicht auf einer Speicherinstanz stattfindet. Dies bedeutet, dass Sie mit der neuen Erweiterung alle Daten in einer öffentlichen Cloud unter Verwendung von TDE-Zertifikaten (Transparent Data Encryption, transparente Datenverschlüsselung) verschlüsseln können, die physisch von den Daten getrennt sind. Die TDE-Schlüssel können in der Masterdatenbank gespeichert werden, die auf einem physisch sicheren lokalen Computer an Ihrem Standort gespeichert und gesichert wird. Mithilfe dieser lokalen Schlüssel können Sie die Daten verschlüsseln, die sich im Windows Azure-Speicher befinden. Falls Ihre Anmeldeinformationen für das Cloudspeicherkonto ausgespäht werden, sind die Daten trotzdem sicher, da die TDE-Zertifikate immer lokal gespeichert werden.  
  
## <a name="concepts-and-requirements"></a>Konzepte und Anforderungen  
  
### <a name="windows-azure-storage-concepts"></a>Konzepte des Windows Azure-Speichers  
 Bei Verwendung von SQL Server-Datendateien in Windows Azure müssen Sie ein Speicherkonto und einen Container in Windows Azure erstellen. Anschließend müssen Sie SQL Server-Anmeldeinformationen erstellen, die Informationen zur Containerrichtlinie sowie eine SAS (Shared Access Signature, Signatur für gemeinsamen Zugriff) enthalten, die für den Zugriff auf den Container erforderlich ist.  
  
 In Windows Azure stellt ein Speicherkonto die höchste Namespaceebene für den BLOB-Zugriff dar. Ein Speicherkonto kann eine unbegrenzte Anzahl von Containern enthalten, solange deren Gesamtgröße 500 TB nicht überschreitet. Aktuelle Informationen zu Speichergrößenbeschränkungen finden Sie unter [Azure-Abonnement und Dienstbeschränkungen, Kontingente und Einschränkungen](https://azure.microsoft.com/documentation/articles/azure-subscription-service-limits/). Ein Container stellt eine Gruppierung eines BLOB-Satzes bereit. Alle BLOBs müssen sich in einem Container befinden. Ein Konto kann eine unbegrenzte Anzahl von Containern enthalten. Analog dazu kann in einem Container auch eine unbegrenzte Anzahl von BLOBs gespeichert werden. Es gibt zwei Arten von BLOBs, die im Windows Azure-Speicher gespeichert werden können: Blockblobs und Seitenblobs. Für die neue Funktion werden Seitenblobs von bis zu 1 TB verwendet, die effizienter sind, wenn Bytebereiche in einer Datei häufig geändert werden. Sie können mit folgendem URL-Format auf BLOBs zugreifen: `http://storageaccount.blob.core.windows.net/<container>/<blob>`.  
  
### <a name="windows-azure-billing-considerations"></a>Überlegungen zur Abrechnung in Windows Azure  
 Die Schätzung der für die Nutzung der Windows Azure-Dienste anfallenden Kosten ist ein wichtiger Aspekt des Entscheidungs- und Planungsprozesses. Wenn Sie SQL Server-Datendateien im Windows Azure-Speicher speichern, fallen Kosten für die Speicherung und Transaktionen an. Zusätzlich erfordert die Implementierung von SQL Server-Datendateien im Windows Azure-Speicher alle 45 bis 60 Sekunden eine implizite Erneuerung der BLOB-Leasedauer. Auf diese Weise entstehen ebenfalls Transaktionskosten pro Datenbankdatei, z. B. MDF- oder LDF-Datei. Nach unserer Einschätzung würden sich die Kosten für das Erneuern der Leasedauer für zwei Datenbankdateien (MDF und LDF) gemäß dem aktuellen Preismodell auf ca. 2 US-Cent pro Monat belaufen. Die Informationen auf der [Azure-Preisseite](https://azure.microsoft.com/pricing/) sollen helfen, die monatlichen Kosten einzuschätzen, die mit der Nutzung des Microsoft Azure-Speichers und der virtuellen Computer in Microsoft Azure verbunden sind.  
  
### <a name="sql-server-concepts"></a>Konzepte von SQL Server  
 Die folgenden Voraussetzungen müssen zur Verwendung der neuen Erweiterung erfüllt sein:  
  
-   Sie erstellen eine Richtlinie für einen Container und generieren zusätzlich einen SAS-Schlüssel.  
  
-   Für jeden Container, der von einer Daten- oder Protokolldatei verwendet wird, erstellen Sie SQL Server-Anmeldeinformationen, deren Name mit dem Containerpfad übereinstimmt.  
  
-   Die Informationen zum Windows Azure-Speichercontainer, der zugehörige Richtlinienname und der SAS-Schlüssel müssen im Anmeldeinformationsspeicher von SQL Server gespeichert werden.  
  
 Im folgenden Beispiel wird vorausgesetzt, dass ein Windows Azure-Speichercontainer sowie eine Richtlinie mit Lese-, Schreib- und Auflistungsrechten erstellt wurde. Beim Erstellen einer Richtlinie für einen Container wird ein SAS-Schlüssel generiert, der gefahrlos unverschlüsselt im Arbeitsspeicher vorgehalten werden kann und von SQL Server für den Zugriff auf die BLOB-Dateien im Container benötigt wird. Ersetzen Sie in den folgenden Codeausschnitt `'your SAS key'` mit einem Eintrag, der dem folgenden ähnelt: `'sr=c&si=<MYPOLICYNAME>&sig=<THESHAREDACCESSSIGNATURE>'`. Weitere Informationen finden Sie unter [Erstellen und Verwenden einer Shared Access Signature](https://msdn.microsoft.com/library/azure/jj721951.aspx)  
  
```  
  
-- Create a credential  
CREATE CREDENTIAL [https://testdb.blob.core.windows.net/data]  
WITH IDENTITY='SHARED ACCESS SIGNATURE',  
SECRET = 'your SAS key'  
  
-- Create database with data and log files in Windows Azure container.  
CREATE DATABASE testdb   
ON  
( NAME = testdb_dat,  
    FILENAME = 'https://testdb.blob.core.windows.net/data/TestData.mdf' )  
 LOG ON  
( NAME = testdb_log,  
    FILENAME =  'https://testdb.blob.core.windows.net/data/TestLog.ldf')  
  
```  
  
 **Wichtiger Hinweis:** Wenn ein Container aktive Verweise auf Datendateien enthält, schlagen Versuche, die entsprechenden SQL Server-Anmeldeinformationen zu löschen, fehl.  
  
### <a name="security"></a>Sicherheit  
 Die folgenden Sicherheitsüberlegungen und -anforderungen sollten beim Speichern von SQL Server-Datendateien im Windows Azure-Speicher berücksichtigt werden.  
  
-   Beim Erstellen eines Containers für den Windows Azure-BLOB-Speicherdienst sollten Sie den Zugriff auf Privat festlegen. Wenn Sie den Zugriff auf "Privat" festlegen, können die Container- und BLOB-Daten nur vom Besitzer des Windows Azure-Kontos gelesen werden.  
  
-   Wenn Sie SQL Server-Datenbankdateien im Windows Azure-Speicher speichern, müssen Sie eine SAS verwenden, d. h. einen URI, der eingeschränkte Rechte für den Zugriff auf Container, BLOBs, Warteschlangen und Tabellen gewährt. Durch die Verwendung einer SAS ermöglichen Sie SQL Server unter dem Speicherkonto den Zugriff auf Ressourcen, ohne Ihren Schlüssel für das Windows Azure-Speicherkonto offen zu legen.  
  
-   Außerdem wird empfohlen, weiterhin die herkömmlichen Sicherheitsvorkehrungen für lokale Datenbanken zu treffen.  
  
### <a name="installation-prerequisites"></a>Installationsvoraussetzungen  
 Die folgenden Installationsvoraussetzungen gelten beim Speichern von SQL Server-Datendateien in Windows Azure.  
  
-   **Lokaler SQL Server:** SQL Server Version 2014 enthält diese Funktion. Informationen zum Herunterladen von SQL Server 2014 finden Sie unter [SQL Server 2014](https://www.microsoft.com/sqlserver/sql-server-2014.aspx).  
  
-   SQL Server, die auf einem virtuellen Computer in Windows Azure ausgeführt werden: Wenn Sie SQL Server auf einem virtuellen Computer in Windows Azure installieren, installieren Sie SQL Server 2014, oder aktualisieren Sie Ihre vorhandene Instanz. Sie können auch einen neuen virtuellen Computer in Windows Azure erstellen, indem Sie ein Plattformimage von SQL Server 2014 verwenden. Informationen zum Herunterladen von SQL Server 2014 finden Sie unter [SQL Server 2014](https://www.microsoft.com/sqlserver/sql-server-2014.aspx).  
  
###  <a name="bkmk_Limitations"></a> Einschränkungen  
  
-   In der aktuellen Version dieser Funktion wird das Speichern von `FileStream`-Daten im Windows Azure-Speicher nicht unterstützt. Sie können `Filestream`-Daten in einer lokalen, in den Windows Azure-Speicher integrierten Datenbank speichern, es ist jedoch nicht möglich, Filestream-Daten unter Verwendung des Windows Azure-Speichers zwischen Computern zu verschieben. Bei `FileStream`-Daten wird empfohlen, die herkömmlichen Verfahren zu verwenden, die bisher zum Verschieben von Dateien (MDF, LDF) in Verbindung mit Filestream-Daten zwischen verschiedenen Computern eingesetzt werden.  
  
-   Bei Verwendung der neuen Erweiterung kann derzeit nur eine SQL Server-Instanz (nicht mehrere) auf dieselben Datenbankdateien im Windows Azure-Speicher zugreifen. Wenn ServerA mit einer aktiven Datenbankdatei online ist und ServerB versehentlich gestartet wird und auch über eine Datenbank verfügt, die auf dieselbe Datendatei verweist, kann die Datenbank des zweiten Servers nicht gestartet werden und verursacht den Fehlercode **5120 Die physische Datei „%.\*ls“ kann nicht geöffnet werden. Betriebssystemfehler %d: „%ls“** .  
  
-   von SQL Server-Datendateien in Microsoft Azure können ausschließlich MDF-, LDF- und NDF-Dateien in Microsoft Azure Storage gespeichert werden.  
  
-   Wenn Sie die Funktion für SQL Server-Datendateien in Windows Azure nutzen, wird die Georeplikation für Ihr Speicherkonto nicht unterstützt. Wenn für ein Speicherkonto eine Georeplikation ausgeführt wird und ein Geo-Failover auftritt, kann die Datenbank beschädigt werden.  
  
-   Jedes BLOB kann eine maximale Größe von 1 TB aufweisen. Auf diese Weise wird für die Datenbankdaten- und Protokolldateien, die im Windows Azure-Speicher gespeichert werden können, eine Obergrenze festgelegt.  
  
-   Es ist nicht möglich, In-Memory OLTP-Daten bei Verwendung von SQL Server-Datendateien im Windows Azure-Speicher in einem Windows Azure-BLOB zu speichern. Das liegt daran, dass In-Memory OLTP von `FileStream` abhängig ist und das Speichern von `FileStream`-Daten im Windows Azure-Speicher von der Funktion in der derzeitigen Version nicht unterstützt wird.  
  
-   Bei Verwendung von SQL Server-Datendateien in Windows Azure führt SQL Server alle URL- oder Dateipfadvergleiche mit der in der `master`-Datenbank festgelegten Sortierung aus.  
  
-   `AlwaysOn Availability Groups` werden unterstützt, solange der primären Datenbank keine neuen Datenbankdateien hinzugefügt werden. Wenn für einen Datenbankvorgang in der primären Datenbank eine neue Datei erstellt werden muss, deaktivieren Sie zuerst AlwaysOn-Verfügbarkeitsgruppen im sekundären Knoten. Führen Sie anschließend den Datenbankvorgang in der primären Datenbank aus, und sichern Sie die Datenbank im primären Knoten. Stellen Sie anschließend die Datenbank auf dem sekundären Knoten wieder her, und aktivieren Sie die AlwaysOn-Verfügbarkeitsgruppen im sekundären Knoten. Es sollte beachtet werden, dass AlwaysOn-Failoverclusterinstanzen bei Verwendung von SQL Server-Datendateien in Windows Azure nicht unterstützt werden.  
  
-   Während des normalen Betriebs verwendet SQL Server temporäre Leasedauern, um BLOBs für den Speicher zu reservieren, wobei jede BLOB-Leasedauer alle 45 bis 60 Sekunden erneuert wird. Wenn ein Server abstürzt und eine andere SQL Server-Instanz gestartet wird, die für die Verwendung derselben BLOBs konfiguriert ist, wartet die neue Instanz bis zu 60 Sekunden, dass die vorhandene Leasedauer für das BLOB abläuft. Wenn Sie die Datenbank an eine andere Instanz anfügen möchten und nicht 60 Sekunden bis zum Ablauf der Leasedauer warten können, können Sie die BLOB-Leasedauer explizit unterbrechen, um Fehler in Anfügevorgängen zu vermeiden.  
  
## <a name="tools-and-programming-reference-support"></a>Unterstützung von Tools und Programmierreferenzen  
 In diesem Abschnitt werden die Tools und Referenzbibliotheken für die Programmierung beschrieben, die beim Speichern von SQL Server-Datendateien im Windows Azure-Speicher verwendet werden können.  
  
### <a name="powershell-support"></a>PowerShell-Unterstützung  
 In SQL Server 2014 können PowerShell-Cmdlets für die Speicherung von SQL Server-Datendateien im Windows Azure-BLOB-Speicherdienst verwendet werden. Dabei wird anstatt auf einen Dateipfad auf den URL-Pfad eines BLOB-Speichers verwiesen. Sie können mit folgendem URL-Format auf BLOBs zugreifen: `: http://storageaccount.blob.core.windows.net/<container>/<blob>`.  
  
### <a name="sql-server-object-and-performance-counters-support"></a>Unterstützung von SQL Server-Objekten und -Leistungsindikatoren  
 In SQL Server 2014 wurde ein neues SQL Server-Objekt eingeführt, das mit SQL Server-Datendateien im Windows Azure-Speicher verwendet werden kann. Das neue SQL Server-Objekt wird als [SQL Server, HTTP_STORAGE_OBJECT](../performance-monitor/sql-server-http-storage-object.md) aufgerufen und kann vom Systemmonitor verwendet werden, um Aktivitäten bei der Ausführung von SQL Server mit dem Microsoft Azure-Speicher zu überwachen.  
  
### <a name="sql-server-management-studio-support"></a>Unterstützung von SQL Server Management Studio  
 SQL Server Management Studio unterstützt die Verwendung der Funktion in mehreren Dialogfeldern. Beispielsweise können Sie den URL-Pfad des Speichercontainers, wie `https://teststorageaccnt.blob.core.windows.net/testcontainer/`, als **Pfad** in mehreren Dialogfeldern eingeben, z.B. **Neue Datenbank**, **Datenbank anfügen** und **Datenbank wiederherstellen**. Weitere Informationen finden Sie unter [Tutorial: SQL Server Sie Datendateien im Windows Azure Storage](../tutorial-use-azure-blob-storage-service-with-sql-server-2016.md)-Dienst ab.  
  
### <a name="sql-server-management-objects-support"></a>Unterstützung von SQL Server Management Objects  
 Bei Verwendung von SQL Server-Datendateien in Microsoft Azure werden alle SQL Server Management Objects (SMO) unterstützt. Wenn ein SMO-Objekt einen Dateipfad erfordert, verwenden Sie das BLOB-URL-Format anstelle eines lokalen Dateipfads, beispielsweise `https://teststorageaccnt.blob.core.windows.net/testcontainer/`. Weitere Informationen zu SQL Server Management Objects (SMO) finden Sie unter [SQL Server Management Objects &#40;SMO&#41;-Programmierungshandbuch](../server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md) in der SQL Server-Onlinedokumentation.  
  
### <a name="transact-sql-support"></a>Unterstützung von Transact-SQL  
 Durch die neue Funktion wurde folgende Änderung in der -Oberfläche eingeführt:  
  
-   Die neue **int** -Spalte **credential_id**in der **sys.master_files** -Systemsicht. Die **credential_id** -Spalte ermöglicht die Rückverweisung von Azure-Speicher-fähigen Datendateien auf sys.credentials, um die zugehörigen Anmeldeinformationen zu identifizieren. Sie können die Spalte zur Problembehandlung verwenden, beispielsweise, wenn Anmeldeinformationen nicht gelöscht werden können, weil sie von einer Datenbankdatei verwendet werden.  
  
##  <a name="bkmk_Troubleshooting"></a>Problembehandlung für SQL Server-Datendateien in Windows Azure  
 Um Fehler aufgrund von nicht unterstützten Funktionen oder Einschränkungen zu vermeiden, sollten Sie sich zunächst unter [Einschränkungen](sql-server-data-files-in-microsoft-azure.md#bkmk_Limitations)informieren.  
  
 In der folgenden Liste sind Fehler aufgeführt, die bei Verwendung von SQL Server-Datendateien mit dem Windows Azure-Speicher auftreten können.  
  
 **Authentifizierungsfehler**  
  
-   *Die %.\*ls-Anmeldeinformationen können nicht gelöscht werden, weil sie von einer aktiven Datenbankdatei verwendet werden.*    
    Lösung: Dieser Fehler wird möglicherweise angezeigt, wenn Sie versuchen, Anmelde Informationen zu löschen, die noch von einer aktiven Datenbankdatei in Windows Azure Storage verwendet werden. Um die Anmeldeinformationen zu löschen, müssen Sie zuerst das zugeordnete BLOB löschen, das diese Datenbankdatei enthält. Um ein BLOB zu löschen, das über eine aktive Leasedauer verfügt, müssen Sie zunächst die Leasedauer unterbrechen.  
  
-   *Für den Container wurde nicht ordnungsgemäß eine SAS (Shared Access Signature) erstellt.*    
     Lösung: Stellen Sie sicher, dass eine SAS ordnungsgemäß für den Container erstellt wurde. Lesen Sie die Hinweise in Lektion 2 im [Tutorial: SQL Server Sie Datendateien im Windows Azure Storage](../tutorial-use-azure-blob-storage-service-with-sql-server-2016.md)-Dienst ab.  
  
-   *SQL Server-Anmeldeinformationen wurden nicht ordnungsgemäß erstellt.*    
    Lösung: Vergewissern Sie sich, dass Sie für das Feld **Identität** die Option „Shared Access Signature“ verwendet und ordnungsgemäß einen geheimen Schlüssel erstellt haben. Lesen Sie die Hinweise in Lektion 3 im [Tutorial: SQL Server Sie Datendateien im Windows Azure Storage](../tutorial-use-azure-blob-storage-service-with-sql-server-2016.md)-Dienst ab.  
  
 **Fehler bei BLOB-Leasedauer:**  
  
-   Fehler beim Starten von SQL Server, nachdem eine andere Instanz, die dieselben BLOB-Dateien verwendet, abgestürzt ist. Lösung: Während des normalen Betriebs verwendet SQL Server temporäre Leasedauern, um BLOBs für den Speicher zu reservieren, wobei jede BLOB-Leasedauer alle 45 bis 60 Sekunden erneuert wird. Wenn ein Server abstürzt und eine andere SQL Server-Instanz gestartet wird, die für die Verwendung derselben BLOBs konfiguriert ist, wartet die neue Instanz bis zu 60 Sekunden, dass die vorhandene Leasedauer für das BLOB abläuft. Wenn Sie die Datenbank an eine andere Instanz anfügen möchten und nicht 60 Sekunden bis zum Ablauf der Leasedauer warten können, können Sie die BLOB-Leasedauer explizit unterbrechen, um Fehler in Anfügevorgängen zu vermeiden.  
  
 **Datenbankfehler**  
  
1.  *Fehler beim Erstellen einer Datenbank*   
    Lösung: Lesen Sie die Hinweise in Lektion 4 im [Tutorial: SQL Server Sie Datendateien im Windows Azure Storage](../tutorial-use-azure-blob-storage-service-with-sql-server-2016.md)-Dienst ab.  
  
2.  *Fehler beim Ausführen der ALTER-Anweisung*   
    Lösung: Stellen Sie sicher, dass die ALTER DATABASE-Anweisung ausgeführt wird, während die Datenbank online ist. Wenn Sie die Datendateien in den Windows Azure-Speicher kopieren, erstellen Sie immer ein Seitenblob und kein Blockblob. Andernfalls erzeugt ALTER DATABASE einen Fehler. Lesen Sie die Hinweise in Lektion 7 im [Tutorial: SQL Server Sie Datendateien im Windows Azure Storage](../tutorial-use-azure-blob-storage-service-with-sql-server-2016.md)-Dienst ab.  
  
3.  *Fehlercode 5120: Die physische Datei „%.\*ls“ kann nicht geöffnet werden. Betriebssystemfehler %d: „%ls“*    
    Lösung: Bei Verwendung der neuen Erweiterung kann derzeit nur eine SQL Server-Instanz (nicht mehrere) auf dieselben Datenbankdateien im Windows Azure-Speicher zugreifen. Wenn ServerA mit einer aktiven Datenbankdatei online ist und ServerB versehentlich gestartet wird und auch über eine Datenbank verfügt, die auf dieselbe Datendatei verweist, kann die Datenbank des zweiten Servers nicht gestartet werden und verursacht den Fehlercode *5120 Die physische Datei „%.\*ls“ kann nicht geöffnet werden. Betriebssystemfehler %d: „%ls“* .  
  
     Um dieses Problem zu beheben, stellen Sie zuerst fest, ob ServerA auf die Datenbankdatei im Windows Azure-Speicher zugreifen muss oder nicht. Wenn nicht, entfernen Sie einfach jegliche Verbindungen zwischen ServerA und den Datenbankdateien im Windows Azure-Speicher. Führen Sie hierzu folgende Schritte aus:  
  
    1.  Legen Sie den Dateipfad von Server A mit der ALTER DATABASE-Anweisung auf einen lokalen Ordner fest.  
  
    2.  Schalten Sie die Datenbank auf Server A offline.  
  
    3.  Kopieren Sie dann die Datenbankdateien aus Microsoft Azure Storage im lokalen Ordner auf Server a. Dadurch wird sichergestellt, dass ServerA noch lokal eine Kopie der Datenbank hat.  
  
    4.  Schalten Sie die Datenbank online.  
  
## <a name="see-also"></a>Siehe auch  
 [Tutorial: SQL Server von Datendateien im Windows Azure Storage-Dienst](../tutorial-use-azure-blob-storage-service-with-sql-server-2016.md)  
  
  
