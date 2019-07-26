---
title: Problembehandlung bei der Datensammlung für Machine Learning
ms.prod: sql
ms.technology: machine-learning
ms.date: 02/28/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: 3dbca20d974570d04d65fba30110049efad4e90d
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2019
ms.locfileid: "68470435"
---
# <a name="troubleshoot-data-collection-for-machine-learning"></a>Problembehandlung bei der Datensammlung für Machine Learning

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In diesem Artikel werden die Daten Sammlungs Methoden beschrieben, die Sie verwenden sollten, wenn Sie versuchen, Probleme selbst oder mithilfe des Microsoft-Kunden Supports zu beheben.

**Gilt für:** SQL Server 2016 R Services, SQL Server 2017 Machine Learning Services (R und python)

## <a name="sql-server-version-and-edition"></a>SQL Server Version und Edition

SQL Server 2016 r Services ist die erste Version von SQL Server, die integrierte R-Unterstützung umfasst. SQL Server 2016 Service Pack 1 (SP1) umfasst mehrere wichtige Verbesserungen, einschließlich der Möglichkeit zum Ausführen externer Skripts. Wenn Sie ein SQL Server 2016-Kunde sind, sollten Sie die Installation von SP1 oder höher in Erwägung gezogen.

SQL Server 2017 hinzugefügte Integration der Python-Sprache. Die Integration von Python-Funktionen in früheren Versionen ist nicht möglich.

Unterstützung bei der Beschaffung von Editionen und Versionen finden Sie in diesem Artikel, in dem die Buildnummern für jede der [SQL Server Versionen](https://social.technet.microsoft.com/wiki/contents/articles/783.sql-server-versions.aspx#Service_Pack_editions)aufgeführt sind.

Abhängig von der von Ihnen verwendeten Edition von SQL Server sind einige Machine Learning-Funktionen möglicherweise nicht verfügbar oder beschränkt. Die folgenden Artikel enthalten eine Liste der Machine Learning-Features in den Editionen Enterprise, Developer, Standard und Express.

* [Editionen und unterstützte Funktionen von SQL Server](https://docs.microsoft.com/sql/sql-server/editions-and-components-of-sql-server-2016)
* [R-und python-Features nach Editionen von SQL Server](r/differences-in-r-features-between-editions-of-sql-server.md)

## <a name="r-language-and-tool-versions"></a>R-Sprache und Tool Versionen

Im Allgemeinen wird die Version von Microsoft R, die installiert wird, wenn Sie die R Services-Funktion oder die Machine Learning Services-Funktion auswählen, durch die SQL Server Buildnummer bestimmt. Wenn Sie SQL Server aktualisieren oder patchen, müssen Sie auch die zugehörigen R-Komponenten aktualisieren oder patchen.

Eine Liste der Releases und Links zu Downloads für R-Komponenten finden Sie unter [Installieren von Machine Learning-Komponenten ohne Internet Zugriff](https://docs.microsoft.com/sql/advanced-analytics/r/installing-ml-components-without-internet-access). Auf Computern mit Internet Zugriff wird die erforderliche Version von R automatisch identifiziert und installiert.

Es ist möglich, die R Server Komponenten getrennt von der SQL Server Datenbank-Engine zu aktualisieren, und zwar in einem Prozess, der als Bindung bezeichnet wird. Daher kann die Version von r, die Sie beim Ausführen von r-Code in SQL Server verwenden, abhängig von der installierten Version von SQL Server und davon abhängen, ob Sie den Server auf die neueste Version von r migriert haben.

### <a name="determine-the-r-version"></a>Bestimmen der R-Version

Am einfachsten können Sie die R-Version ermitteln, indem Sie eine-Anweisung wie die folgende ausführen:

```sql
exec sp_execute_external_script
       @language = N'R'
       , @script = N'
# Transform R version properties to data.frame
OutputDataSet <- data.frame(
  property_name = c("R.version", "Revo.version"),
  property_value = c(R.Version()$version.string, Revo.version$version.string),
  stringsAsFactors = FALSE)
# Retrieve properties like R.home, libPath & default packages
OutputDataSet <- rbind(OutputDataSet, data.frame(
  property_name = c("R.home", "libPaths", "defaultPackages"),
  property_value = c(R.home(), .libPaths(), paste(getOption("defaultPackages"), collapse=", ")),
  stringsAsFactors = FALSE)
)
'
WITH RESULT SETS ((PropertyName nvarchar(100), PropertyValue nvarchar(4000)));

```

> [!TIP]
> Wenn r Services nicht funktioniert, versuchen Sie, nur den R-Skript Teil von rgui auszuführen.

Als letztes Mittel können Sie Dateien auf dem Server öffnen, um die installierte Version zu bestimmen. Suchen Sie hierzu die Datei "rlauncher. config", um den Speicherort der R-Laufzeit und des aktuellen Arbeitsverzeichnisses zu erhalten. Es wird empfohlen, eine Kopie der Datei zu erstellen und zu öffnen, damit Sie nicht versehentlich Eigenschaften ändern können.

* SQL Server 2016
  
  `C:\Program Files\Microsoft SQL Server\MSSQL13.<instance_name\MSSQL\Binn\rlauncher.config`

* SQL Server 2017
  
  `C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\MSSQL\Binn\rlauncher.config`

Um die r-Version und die revoscaler-Version zu erhalten, öffnen Sie eine r-Eingabeaufforderung, oder öffnen Sie die rgui, die der-Instanz zugeordnet ist.

* SQL Server 2016
  
  `C:\Program Files\Microsoft SQL Server\MSSQL13.<instancename>\R_SERVICES\bin\x64\RGui.exe`

* SQL Server 2017
  
  `C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\R_SERVICES\bin\x64\RGui.exe`

In der R-Konsole werden die Versionsinformationen beim Start angezeigt. Die folgende Version stellt z. b. die Standardkonfiguration für SQL Server 2017 dar:

    *Microsoft R Open 3.3.3*

    *The enhanced R distribution from Microsoft*

    *Microsoft packages Copyright (C) 2017 Microsoft*

    *Loading Microsoft R Server packages, version 9.1.0.*

## <a name="python-versions"></a>Python-Versionen

Es gibt mehrere Möglichkeiten, die Python-Version zu erhalten. Die einfachste Möglichkeit besteht darin, diese Anweisung aus Management Studio oder einem anderen SQL-Abfrage Tool auszuführen:

```sql
-- Get Python runtime properties:
exec sp_execute_external_script
       @language = N'Python'
       , @script = N'
import sys
import pkg_resources
OutputDataSet = pandas.DataFrame(
                    {"property_name": ["Python.home", "Python.version", "Revo.version", "libpaths"],
                    "property_value": [sys.executable[:-10], sys.version, pkg_resources.get_distribution("revoscalepy").version, str(sys.path)]}
)
'
with WITH RESULT SETS (SQL keywords) ((PropertyName nvarchar(100), PropertyValue nvarchar(4000)));
```

Wenn Machine Learning Services nicht ausgeführt wird, können Sie die installierte Python-Version ermitteln, indem Sie sich die Datei "pythonlauncher. config" ansehen. Es wird empfohlen, eine Kopie der Datei zu erstellen und zu öffnen, damit Sie nicht versehentlich Eigenschaften ändern können.

1. Nur für SQL Server 2017:`C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\MSSQL\Log\ExtensibilityLog\pythonlauncher.config`
2. Den Wert für **pythonhome**erhalten.
3. Den Wert des aktuellen Arbeitsverzeichnisses erhalten.

> [!NOTE]
> Wenn Sie sowohl python als auch R in SQL Server 2017 installiert haben, werden das Arbeitsverzeichnis und der Pool von workerkonten für die Programmiersprachen R und python freigegeben.

## <a name="are-multiple-instances-of-r-or-python-installed"></a>Sind mehrere Instanzen von R oder python installiert?

Überprüfen Sie, ob mehr als eine Kopie der R-Bibliotheken auf dem Computer installiert ist. Diese Duplizierung kann auftreten, wenn:

* Während des Setups wählen Sie sowohl R Services (in-Database) als auch R Server (eigenständig) aus.
* Sie installieren Microsoft R Client zusätzlich zu SQL Server.
* Ein anderer Satz von r-Bibliotheken wurde mit R Tools für Visual Studio, r Studio, Microsoft R Client oder einer anderen r-IDE installiert.
* Der Computer hostet mehrere Instanzen von SQL Server, und mehr als eine Instanz verwendet Machine Learning.

Die gleichen Bedingungen gelten für python.

Wenn Sie feststellen, dass mehrere Bibliotheken oder Laufzeiten installiert sind, stellen Sie sicher, dass Sie nur die Fehler erhalten, die mit den von der SQL Server Instanz verwendeten python-oder R-Laufzeiten verknüpft sind.

## <a name="origin-of-errors"></a>Ursprung von Fehlern

Die Fehler, die bei dem Versuch angezeigt werden, R-Code auszuführen, können aus einer der folgenden Quellen stammen:

* SQL Server Datenbank-Engine, einschließlich der gespeicherten Prozedur sp_execute_external_script
* Das SQL Server vertrauenswürdigen launchpad
* Weitere Komponenten des Erweiterbarkeits-Frameworks, einschließlich R-und python-Launcher und Satelliten Prozesse
* Anbieter, wie z. b. Microsoft Open Database Connectivity (ODBC)
* Sprache R

Wenn Sie zum ersten Mal mit dem Dienst arbeiten, kann es schwierig sein, zu erkennen, welche Nachrichten von welchen Diensten stammen. Es wird empfohlen, nicht nur den genauen Nachrichtentext, sondern den Kontext zu erfassen, in dem Sie die Meldung gesehen haben. Beachten Sie die Client Software, die Sie zum Ausführen von Machine Learning-Code verwenden:

* Verwenden Sie Management Studio? Eine externe Anwendung?
* Führen Sie R-Code in einem Remote Client oder direkt in einer gespeicherten Prozedur aus?

## <a name="sql-server-log-files"></a>Protokolldateien SQL Server

Holen Sie sich den neuesten SQL Server ErrorLog. Der gesamte Satz von Fehlerprotokollen besteht aus den Dateien aus dem folgenden Standardprotokoll Verzeichnis:

* SQL Server 2016
  
  `C:\Program Files\Microsoft SQL Server\MSSQL13.SQL2016\MSSQL\Log\ExtensibilityLog`

* SQL Server 2017
  
  `C:\Program Files\Microsoft SQL Server\MSSQL14.SQL2016\MSSQL\Log\ExtensibilityLog`

> [!NOTE]
> Der exakte Ordnername ist abhängig vom Instanznamen unterschiedlich.

## <a name="errors-returned-by-spexecuteexternalscript"></a>Von sp_execute_external_script zurückgegebene Fehler

Den vollständigen Fehlertext, der ggf. zurückgegeben wird, beim Ausführen des sp_execute_external_script-Befehls erhalten.

Um R-oder python-Probleme zu beheben, können Sie dieses Skript ausführen, das die R-oder python-Laufzeit startet und Daten hin-und herübergibt.

**Für R**

```sql
exec sp_execute_external_script @language =N'R',  
@script=N'OutputDataSet<-InputDataSet',  
@input_data_1 =N'select 1 as hello'  
with result sets (([hello] int not null));  
go
```

**Für python**

```sql
exec sp_execute_external_script @language =N'Python',  
@script=N'OutputDataSet= InputDataSet',  
@input_data_1 =N'select 1 as hello'  
with result sets (([hello] int not null));  
go
```

## <a name="errors-generated-by-the-extensibility-framework"></a>Vom Erweiterbarkeits Framework generierte Fehler

SQL Server generiert separate Protokolle für die Runtimes der externen Skriptsprache. Diese Fehler werden nicht von der Python-oder R-Sprache generiert. Sie werden aus den Erweiterbarkeits Komponenten in SQL Server generiert, einschließlich sprachspezifischer Launcher und Ihren Satelliten Prozessen.

Sie können diese Protokolle von den folgenden Standard Speicherorten erhalten:

* SQL Server 2016
  
  `C:\Program Files\Microsoft SQL Server\MSSQL13.<instance_name>\MSSQL\Log\ExtensibilityLog`

* SQL Server 2017
  
  `C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\MSSQL\Log\ExtensibilityLog`

> [!NOTE]
> Der exakte Ordnername unterscheidet sich je nach Instanzname. Abhängig von Ihrer Konfiguration kann sich der Ordner auf einem anderen Laufwerk befinden.

Beispielsweise sind die folgenden Protokollmeldungen mit dem Erweiterbarkeits Framework verknüpft:

* *Fehler bei "LogonUser" für Benutzer MSSQLSERVER01.*
  
  Dies kann darauf hindeuten, dass die workerkonten, die externe Skripts ausführen, nicht auf die Instanz zugreifen können

* *Initializephysicaluserspool ist fehlgeschlagen.*
  
  Diese Meldung kann bedeuten, dass Ihre Sicherheitseinstellungen verhindern, dass Setup den Pool von workerkonten erstellt, die für die Durchführung externer Skripts erforderlich sind.

* *Fehler bei der Initialisierung des Sicherheitskontext-Managers*

* *Fehler beim Initialisieren des satellitensitzungsmanagers*

## <a name="system-events"></a>System Ereignisse

1. Öffnen Sie Windows Ereignisanzeige, und suchen Sie im **System Ereignis** Protokoll Nachmeldungen, die das Zeichen folgen- *Launchpad*enthalten.
2. Öffnen Sie die Datei "extlauncherrorlog", und suchen Sie nach der Zeichenfolge " *errorCode*". Überprüfen Sie die Meldung, die dem ErrorCode zugeordnet ist.

Die folgenden Meldungen sind z. b. häufige Systemfehler im Zusammenhang mit dem SQL Server Erweiterbarkeits Framework:

* *Der SQL Server-Launchpad (MSSQLSERVER)-Dienst konnte aufgrund des folgenden Fehlers nicht gestartet werden:<text>*

* *Der Dienst hat nicht rechtzeitig auf die Start-oder Steuerungs Anforderung geantwortet.*

* *Beim Warten auf die Verbindung des SQL Server-Launchpad (MSSQLSERVER)-Dienstanbieter wurde ein Timeout (120000 Millisekunden) erreicht.*

## <a name="dump-files"></a>Dumpdateien

Wenn Sie mit dem Debuggen vertraut sind, können Sie die Dumpdateien verwenden, um einen Fehler in Launchpad zu analysieren.

1. Suchen Sie den Ordner, der die Setup-Bootstrap-Protokolle für SQL Server enthält. In SQL Server 2016 lautet der Standardpfad z. b. c:\Programme\Microsoft SQL server\130\setup Bootstrap\LOG.
2. Öffnen Sie den Unterordner Bootstrap-Protokoll, der spezifisch für die Erweiterbarkeit ist.
3. Wenn Sie eine Supportanfrage einreichen müssen, fügen Sie den gesamten Inhalt dieses Ordners einer ZIP-Datei hinzu. Beispiel: c:\Programme\Microsoft SQL server\130\setup bootstrap\log\log\extensibilitylog.
  
Der genaue Speicherort kann sich auf Ihrem System unterscheiden, und er kann sich auf einem anderen Laufwerk als dem Laufwerk C befinden. Stellen Sie sicher, dass Sie die Protokolle für die Instanz erhalten, auf der Machine Learning installiert ist.

## <a name="configuration-settings"></a>Konfigurationseinstellungen

In diesem Abschnitt werden zusätzliche Komponenten oder Anbieter aufgelistet, die beim Ausführen von R-oder python-Skripts als Fehlerquelle auftreten können.

### <a name="what-network-protocols-are-available"></a>Welche Netzwerkprotokolle sind verfügbar?

Machine Learning Services erfordert die folgenden Netzwerkprotokolle für die interne Kommunikation zwischen Erweiterbarkeits Komponenten und für die Kommunikation mit externen R-oder python-Clients.

* Named Pipes
* TCP/IP

Öffnen Sie SQL Server-Konfigurations-Manager, um zu bestimmen, ob ein Protokoll installiert ist, und wenn es installiert ist, um zu bestimmen, ob es aktiviert ist.

### <a name="security-configuration-and-permissions"></a>Sicherheitskonfiguration und-Berechtigungen

Für workerkonten:

1. Öffnen Sie in der Systemsteuerung die Option **Benutzer und Gruppen**, und suchen Sie die Gruppe, die zum Ausführen externer Skript Aufträge verwendet wird. Standardmäßig ist die Gruppe **sqlrusergroup**.
2. Vergewissern Sie sich, dass die Gruppe vorhanden ist und mindestens ein Workerkonto enthält.
3. Wählen Sie in SQL Server Management Studio die Instanz aus, auf der R-oder python-Aufträge ausgeführt werden sollen, wählen Sie **Sicherheit**aus, und bestimmen Sie dann, ob eine Anmeldung für sqlrusergroup vorliegt.
4. Überprüfen Sie die Berechtigungen für die Benutzergruppe.

Für einzelne Benutzerkonten:

1. Bestimmen Sie, ob die Instanz die Authentifizierung im gemischten Modus, nur SQL-Anmeldungen oder nur die Windows-Authentifizierung unterstützt. Diese Einstellung wirkt sich auf Ihre R-oder python-Code Anforderungen aus.
2. Legen Sie für jeden Benutzer, der r-Code ausführen muss, die erforderliche Berechtigungsebene für jede Datenbank fest, in der Objekte aus R geschrieben werden, auf Daten zugegriffen wird, oder dass Objekte erstellt werden.
3. Um die Skriptausführung zu aktivieren, erstellen Sie nach Bedarf Rollen, oder fügen Sie den folgenden Rollen Benutzer hinzu:

   - Alle, aber *db_owner*: Ausführen eines beliebigen externen Skripts erforderlich.
   - *db_datawriter*: Zum Schreiben von Ergebnissen aus R oder python.
   - *db_ddladmin*: Zum Erstellen neuer Objekte.
   - *db_datareader*: Zum Lesen von Daten, die von R-oder python-Code verwendet werden.
4. Beachten Sie, ob Sie bei der Installation von SQL Server 2016 Standard Start Konten geändert haben.
5. Wenn ein Benutzer neue r-Pakete installieren oder R-Pakete verwenden muss, die von anderen Benutzern installiert wurden, müssen Sie möglicherweise die Paketverwaltung auf der-Instanz aktivieren und dann zusätzliche Berechtigungen zuweisen. Weitere Informationen finden Sie unter [Aktivieren oder Deaktivieren der R-Paketverwaltung](r/r-package-how-to-enable-or-disable.md).

### <a name="what-folders-are-subject-to-locking-by-antivirus-software"></a>Welche Ordner können durch Antivirussoftware gesperrt werden?

Durch Antivirussoftware können Ordner gesperrt werden, was die Einrichtung der Machine Learning-Features und die erfolgreiche Skriptausführung verhindert. Bestimmen Sie, ob für Ordner in der SQL Server Struktur Viren Scans unterliegen.

Wenn jedoch mehrere Dienste oder Features auf einer-Instanz installiert sind, kann es schwierig sein, alle möglichen Ordner aufzuzählen, die von der-Instanz verwendet werden. Wenn z. b. neue Funktionen hinzugefügt werden, müssen die neuen Ordner identifiziert und ausgeschlossen werden.

Darüber hinaus erstellen einige Features neue Ordner dynamisch zur Laufzeit. Beispielsweise erstellen in-Memory-OLTP-Tabellen, gespeicherte Prozeduren und Funktionen zur Laufzeit neue Verzeichnisse. Diese Ordnernamen enthalten häufig GUIDs und können nicht vorhergesagt werden. Das SQL Server Trusted Launchpad erstellt neue Arbeitsverzeichnisse für R-und Python-Skript Aufträge.

Da es möglicherweise nicht möglich ist, alle vom SQL Server Prozess und ihren Features benötigten Ordner auszuschließen, wird empfohlen, dass Sie die gesamte SQL Server instanzverzeichnisstruktur ausschließen.

### <a name="is-the-firewall-open-for-sql-server-does-the-instance-support-remote-connections"></a>Ist die Firewall für SQL Server geöffnet? Unterstützt die Instanz Remote Verbindungen?

1. Informationen dazu, ob SQL Server Remote Verbindungen unterstützt, finden Sie unter [Konfigurieren von Remote Server Verbindungen](../database-engine/configure-windows/view-or-configure-remote-server-connection-options-sql-server.md).

2. Stellen Sie fest, ob für SQL Server eine Firewallregel erstellt wurde. Aus Sicherheitsgründen ist es in einer Standardinstallation möglicherweise nicht möglich, dass der Remote-R-oder Python-Client eine Verbindung mit der-Instanz herstellt. Weitere Informationen finden Sie unter [Problembehandlung beim Herstellen einer Verbindung mit SQL Server](../database-engine/configure-windows/troubleshoot-connecting-to-the-sql-server-database-engine.md).

## <a name="see-also"></a>Siehe auch

[Problembehandlung bei Machine Learning in SQL Server](machine-learning-troubleshooting-faq.md)
