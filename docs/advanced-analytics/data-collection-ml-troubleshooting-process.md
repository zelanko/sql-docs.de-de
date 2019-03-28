---
title: Problembehandlung bei der Datensammlung wird für Machine Learning – SQL Server Machine Learning Services
ms.prod: sql
ms.technology: machine-learning
ms.date: 02/28/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: fe383652a63b0972097fc739cf33bd3fcbe2e7e6
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58513227"
---
# <a name="troubleshoot-data-collection-for-machine-learning"></a>Problembehandlung bei der Datensammlung für Machine learning

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dieser Artikel beschreibt die Datensammlungsmethoden zu verwendende beim Beheben von Problemen in Ihren eigenen oder mit Hilfe der Microsoft-Kunden zu unterstützen.

**Gilt für:** SQL Server 2016 R Services, SQL Server 2017-Machine Learning-Dienste (R und Python)

## <a name="sql-server-version-and-edition"></a>SQL Server-Version und edition

SQL Server 2016 R Services ist die erste Version von SQL Server integrierte Unterstützung von R enthalten. SQL Server 2016 Service Pack 1 (SP1) enthält mehrere wesentliche Verbesserungen, einschließlich der Möglichkeit, um externe Skripts auszuführen. Wenn Sie eine SQL Server 2016-Kunde sind, sollten Sie erwägen, die Installation von SP1 oder höher.

SQL Server 2017 hinzugefügt, die Integration von Python-Sprache. Integration von Python-Funktion kann nicht in früheren Versionen nicht abgerufen werden.

Weitere Unterstützung zu erhalten, die erste Edition und Versionen finden Sie unter in diesem Artikel, der die Buildnummern für die einzelnen aufgeführt sind die [SQL Server-Versionen](https://social.technet.microsoft.com/wiki/contents/articles/783.sql-server-versions.aspx#Service_Pack_editions).

Abhängig von der Edition von SQL Server, die Sie verwenden, können möglicherweise einige Machine learning-Funktionen nicht verfügbar oder nur eingeschränkt. Die folgenden Artikel Liste von Machine Learning-Features in Enterprise, Developer, Standard und Express-Editionen.

* [Editionen und unterstützte Funktionen von SQL Server](https://docs.microsoft.com/sql/sql-server/editions-and-components-of-sql-server-2016)
* [R und Python-Funktionen von SQL Server-Editionen](r/differences-in-r-features-between-editions-of-sql-server.md)

## <a name="r-language-and-tool-versions"></a>R-Sprache und Tool-Versionen

Im Allgemeinen wird die Version von Microsoft R, die installiert wird, wenn Sie die R-Funktion oder das Machine Learning Services-Feature auswählen, durch die SQL Server-Build-Nummer bestimmt. Wenn Sie ein upgrade oder patch für SQL Server, müssen auch ein upgrade oder patch für die R-Komponenten.

Eine Liste der Versionen und Links zu Downloads von R-Komponente, finden Sie unter [Machine Learning-Komponenten ohne Internetzugang installieren](https://docs.microsoft.com/sql/advanced-analytics/r/installing-ml-components-without-internet-access). Auf Computern mit Internetzugriff die erforderliche Version von R identifiziert und automatisch installiert.

Es ist möglich, aktualisieren Sie die R Server-Komponenten separat von SQL Server-Datenbank-Engine in einem Prozess, der als Bindung bezeichnet. Aus diesem Grund kann die Version von R, mit denen Sie beim Ausführen von R-Code in SQL Server variieren, je nach sowohl die installierte Version von SQL Server und gibt an, ob Sie auf die neueste Version von R Server migriert wurden.

### <a name="determine-the-r-version"></a>Ermitteln Sie die R-version

Die einfachste Möglichkeit zum Ermitteln der R-Version ist zum Abrufen der Common Language Runtime-Eigenschaften, durch die Ausführung einer Anweisung wie die folgende:

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
> Wenn R Services nicht funktioniert, versuchen Sie es nur in den R-Skript-Teil von RGui ausgeführt.

Als letzten Ausweg können Sie Dateien auf dem Server zum Ermitteln der installierten Version öffnen. Suchen Sie dazu die Datei "rlauncher.config" rufen Sie den Speicherort der R-Laufzeit und das aktuelle Arbeitsverzeichnis. Es wird empfohlen, und öffnen eine Kopie der Datei, sodass Sie nicht versehentlich alle Eigenschaften ändern.

* SQL Server 2016
  
  `C:\Program Files\Microsoft SQL Server\MSSQL13.<instance_name\MSSQL\Binn\rlauncher.config`

* SQL Server 2017
  
  `C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\MSSQL\Binn\rlauncher.config`

Um die R-Version und die RevoScaleR-Versionen zu erhalten, öffnen Sie eine R-Eingabeaufforderung oder öffnen Sie die RGui, das mit der Instanz zugeordnet ist.

* SQL Server 2016
  
  `C:\Program Files\Microsoft SQL Server\MSSQL13.<instancename>\R_SERVICES\bin\x64\RGui.exe`

* SQL Server 2017
  
  `C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\R_SERVICES\bin\x64\RGui.exe`

Die R-Konsole zeigt die Versionsinformationen auf Start. Beispielsweise steht die folgende Version die Standardkonfiguration für SQL Server 2017:

    *Microsoft R Open 3.3.3*

    *The enhanced R distribution from Microsoft*

    *Microsoft packages Copyright (C) 2017 Microsoft*

    *Loading Microsoft R Server packages, version 9.1.0.*

## <a name="python-versions"></a>Python-Versionen

Es gibt mehrere Möglichkeiten, die Python-Version zu erhalten. Die einfachste Möglichkeit ist die Ausführung dieser Anweisung in Management Studio oder anderen Tool zur SQL-Abfrage:

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

Wenn es sich bei Machine Learning-Dienste nicht ausgeführt wird, können Sie die installierten Python-Version bestimmen, anhand der pythonlauncher.config-Datei. Es wird empfohlen, und öffnen eine Kopie der Datei, sodass Sie nicht versehentlich alle Eigenschaften ändern.

1. Nur für SQLServer 2017: `C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\MSSQL\Log\ExtensibilityLog\pythonlauncher.config`
2. Rufen Sie den Wert für **PYTHONHOME**.
3. Ruft den Wert des aktuellen Arbeitsverzeichnisses.

> [!NOTE]
> Wenn Sie Python und R in SQL Server 2017 installiert haben, werden das Arbeitsverzeichnis und den Pool von workerkonten für die R und Python-Sprachen gemeinsam genutzt.

## <a name="are-multiple-instances-of-r-or-python-installed"></a>Mehrere Instanzen von R oder Python installiert?

Überprüfen Sie, ob mehr als eine Kopie der R-Bibliotheken auf dem Computer installiert ist. Diese Duplizierung kann auftreten, wenn:

* Während der Installation wählen Sie sowohl für R Services (Datenbankintern) als auch für R Server (eigenständig).
* Microsoft R Client zusätzlich zu SQL Server installiert.
* Ein anderen Satz von R-Bibliotheken wurde mithilfe von R-Tools für Visual Studio, Rstudio, Microsoft R Client oder eine andere R-IDE installiert.
* Der Computer hostet mehrere Instanzen von SQL Server, und mehr als eine Instanz verwendet Machine Learning.

Die gleichen Bedingungen gelten für Python.

Wenn Sie feststellen, dass mehrere Bibliotheken oder Laufzeiten installiert sind, stellen Sie sicher, dass Sie erhalten nur die Fehler im Zusammenhang mit der Python oder R-Laufzeiten, die von der SQL Server-Instanz verwendet werden.

## <a name="origin-of-errors"></a>Ursprung von Fehlern

Die Fehler, die Sie sehen, wenn Sie versuchen, die R-Code ausführen, können von jedem der folgenden Quellen stammen:

* SQL Server-Datenbankmodul, einschließlich der gespeicherten Prozedur sp_execute_external_script
* Die SQLServer Trusted Launchpad
* Andere Komponenten des Erweiterungsframeworks, einschließlich R und Python Auswahl- und satellitenprozesse
* Anbieter, z. B. Microsoft Open Database Connectivity (ODBC)
* R-Sprache

Wenn Sie mit dem Dienst zum ersten Mal arbeiten, kann es schwierig sein zu informieren, welche Meldungen von welchen Diensten stammen. Es wird empfohlen, dass Sie erfassen, nicht nur den Text genau Nachricht, sondern auch der Kontext, in dem Sie die Nachricht gesehen haben. Beachten Sie die Client-Software, die Sie zum Ausführen von Machine Learning-Code verwenden:

* Verwenden Sie Management Studio? Eine externe Anwendung?
* Führen Sie R-Code in einem Remoteclient oder direkt in einer gespeicherten Prozedur aus?

## <a name="sql-server-log-files"></a>SQL Server-Protokolldateien

Abrufen der neuesten SQL Server-Fehlerprotokoll. Der vollständige Satz von Fehlerprotokollen besteht aus den Dateien aus dem folgenden Standardverzeichnis für Protokolldateien:

* SQL Server 2016
  
  `C:\Program Files\Microsoft SQL Server\MSSQL13.SQL2016\MSSQL\Log\ExtensibilityLog`

* SQL Server 2017
  
  `C:\Program Files\Microsoft SQL Server\MSSQL14.SQL2016\MSSQL\Log\ExtensibilityLog`

> [!NOTE]
> Der genauen Ordnernamen unterscheidet sich je nach den Namen der Instanz.

## <a name="errors-returned-by-spexecuteexternalscript"></a>Fehler, die von Sp_execute_external_script zurückgegeben werden.

Erhalten Sie den gesamten Text von Fehlern, die zurückgegeben werden, ggf. ein, wenn Sie den Sp_execute_external_script-Befehl ausführen.

Um R oder Python-Probleme Zielmodell zu entfernen, können Sie dieses Skript ausführen, startet die R- oder Python-Laufzeit und übergibt Daten hin und her.

**Für R**

```sql
exec sp_execute_external_script @language =N'R',  
@script=N'OutputDataSet<-InputDataSet',  
@input_data_1 =N'select 1 as hello'  
with result sets (([hello] int not null));  
go
```

**Für Python**

```sql
exec sp_execute_external_script @language =N'Python',  
@script=N'OutputDataSet= InputDataSet',  
@input_data_1 =N'select 1 as hello'  
with result sets (([hello] int not null));  
go
```

## <a name="errors-generated-by-the-extensibility-framework"></a>Fehler, die durch das Extensibility Framework generiert werden.

SQL Server generiert separate Protokolldateien für die externen Skript Language Runtimes. Diese Fehler werden nicht von der Sprache Python oder R generiert. Sie werden über die Erweiterbarkeitskomponenten in SQL Server, einschließlich sprachspezifische-Auswahl- und ihre satellitenprozesse, die generiert werden.

Sie können diese Protokolle von den folgenden standardmäßigen Speicherorten abrufen:

* SQL Server 2016
  
  `C:\Program Files\Microsoft SQL Server\MSSQL13.<instance_name>\MSSQL\Log\ExtensibilityLog`

* SQL Server 2017
  
  `C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\MSSQL\Log\ExtensibilityLog`

> [!NOTE]
> Der genauen Ordnernamen variiert abhängig von den Namen der Instanz. Je nach Konfiguration kann der Ordner auf einem anderen Laufwerk sein.

Z. B. beziehen sich die folgenden Meldungen auf dem Extensibility Framework:

* *Fehler bei der LogonUser für Benutzer MSSQLSERVER01*
  
  Dadurch wird angegeben, dass die workerkonten, die Ausführung externer Skripts, die Zugriff auf die Instanz nicht möglich.

* *Fehler bei InitializePhysicalUsersPool*
  
  Diese Meldung kann bedeuten, die Sicherheitseinstellungen verhindern Setup von der Erstellung des Pools von workerkonten, die erforderlich sind, um externe Skripts auszuführen.

* *Fehler bei der Security-Kontext-Manager-Initialisierung*

* *Fehler bei der Initialisierung von Satelliten-Sitzungs-Manager*

## <a name="system-events"></a>Systemereignisse

1. Öffnen Sie Windows-Ereignisanzeige, und suchen die **Systemereignis** Log für Nachrichten, die die Zeichenfolge *Launchpad*.
2. Öffnen Sie die ExtLaunchErrorlog-Datei, und suchen Sie nach der Zeichenfolge *ErrorCode*. Überprüfen Sie die Meldung, die den ErrorCode zugeordnet ist.

Beispielsweise sind die folgenden Meldungen häufige Fehler, die im Zusammenhang mit dem Extensibility Framework von SQL Server:

* *Der SQL Server Launchpad (MSSQLSERVER)-Dienst wurde aufgrund des folgenden Fehlers nicht gestartet werden:  <text>*

* *Der Dienst hat nicht auf die Start- oder Anforderung rechtzeitig reagiert.*

* *Das Zeitlimit wurde (120000 in Millisekunden) erreicht, beim Warten auf des SQL Server Launchpad (MSSQLSERVER)-Diensts eine Verbindung herstellen.*

## <a name="dump-files"></a>Dumpdateien

Wenn Sie über fundierte Kenntnisse zu debuggen sind, können Sie die Dumpdateien, um einen Fehler im Launchpad zu analysieren.

1. Suchen Sie den Ordner, der die bootstrap-Setupprotokolle für SQL Server enthält. In SQL Server 2016 war zum Beispiel der Standardpfad c:\Programme\Microsoft c:\Programme\Microsoft SQL Server\130\Setup Bootstrap\Log.
2. Öffnen Sie den bootstrap protokollunterordner, der Erweiterbarkeit von spezifisch sind.
3. Wenn Sie eine Supportanfrage übermitteln möchten, fügen Sie den gesamten Inhalt dieses Ordners in einer ZIP-Datei hinzu. Beispiel: c:\Programme\Microsoft c:\Programme\Microsoft SQL Server\130\Setup Bootstrap\Log\LOG\ExtensibilityLog.
  
Der genaue Speicherort auf Ihrem System unterscheiden, und es kann sein, auf einem anderen Laufwerk als Laufwerk C:. Achten Sie darauf, dass Sie die Protokolle für die Instanz abzurufen, auf Machine Learning installiert ist.

## <a name="configuration-settings"></a>Konfigurationseinstellungen

Dieser Abschnitt enthält zusätzliche Komponenten oder Anbieter, die eine Fehlerquelle werden können, wenn Sie R oder Python-Skripts ausführen.

### <a name="what-network-protocols-are-available"></a>Welche Netzwerkprotokolle sind verfügbar?

Machine Learning-Dienste müssen die folgenden Netzwerkprotokolle aus, für die interne Kommunikation zwischen Erweiterbarkeitskomponenten und für die Kommunikation mit externen R oder Python-Clients.

* Named Pipes
* TCP/IP

Öffnen Sie SQL Server Configuration Manager, um zu bestimmen, ob ein Protokoll installiert ist und, sofern es installiert ist, um zu bestimmen, ob er aktiviert ist.

### <a name="security-configuration-and-permissions"></a>Konfiguration der Sicherheit und Berechtigungen

Für workerkonten:

1. Öffnen Sie in der Systemsteuerung **Benutzer und Gruppen**, und suchen Sie die Gruppe verwendet, um externe Skripts für Aufträge auszuführen. Standardmäßig ist die Gruppe **SQLRUserGroup**.
2. Stellen Sie sicher, dass die Gruppe vorhanden ist und mindestens ein workerkonto enthält.
3. Wählen Sie in SQL Server Management Studio, die Instanz, in dem R oder Python-Aufträge durchgeführt werden, wählen Sie **Sicherheit**, und klicken Sie dann zu bestimmen, ob eine Anmeldung für SQLRUserGroup vorhanden ist.
4. Überprüfen Sie Berechtigungen für die Benutzergruppe aus.

Für einzelne Benutzerkonten:

1. Bestimmen Sie, ob die Instanz Authentifizierung im gemischten Modus, nur die SQL-Anmeldungen oder nur die Windows-Authentifizierung unterstützt. Diese Einstellung wirkt sich auf Ihrer R oder Python-code Anforderungen.
2. Für jeden Benutzer, die R-Code ausgeführt werden muss, ermitteln Sie die erforderliche Berechtigungsstufe für jede Datenbank, in denen Objekte werden aus R geschrieben werden, Zugriff auf Daten oder Objekte erstellt werden.
3. Aktivieren Sie skriptausführung Rollen erstellen oder Hinzufügen von Benutzern zu den folgenden Rollen nach Bedarf:

   - Alle außer *Db_owner*: Erfordert EXTERNEN SKRIPTAUSFÜHRUNG.
   - *db_datawriter*: Um Ergebnisse aus R oder Python zu schreiben.
   - *db_ddladmin*: Neue Objekte zu erstellen.
   - *db_datareader*: Zum Lesen von Daten, die von R oder Python-Code verwendet wird.
4. Beachten Sie, ob Sie alle Standardkonten-Startup geändert, wenn Sie SQL Server 2016 installiert.
5. Wenn ein Benutzer muss neue R-Pakete installieren oder verwenden Sie R-Pakete, die von anderen Benutzern installiert wurden, müssen Sie zum Aktivieren der paketverwaltung in der Instanz und dann zusätzliche Berechtigungen zuzuweisen. Weitere Informationen finden Sie unter [aktivieren oder Deaktivieren der R-paketverwaltung](r/r-package-how-to-enable-or-disable.md).

### <a name="what-folders-are-subject-to-locking-by-antivirus-software"></a>Welchen Ordnern unterliegen durch Antivirensoftware Sperren?

Antivirus-Software kann Ordner sperren, was verhindert, dass sowohl das Setup von Machine learning-Funktionen und die skriptausführung erfolgreich. Bestimmen Sie, ob alle Ordner in der SQL Server-Struktur virenprüfung gelten.

Allerdings bei der Installation von mehreren Diensten oder Features auf einer Instanz kann es schwierig sein, alle möglichen Ordner aufzulisten, die von der Instanz verwendet werden. Angenommen, wenn neue Features hinzugefügt werden, müssen die neuen Ordner identifiziert und ausgeschlossen werden.

Darüber hinaus erstellen Sie einige Funktionen neue Ordner dynamisch zur Laufzeit. Beispielsweise wird mit in-Memory-OLTP-Tabellen, gespeicherten Prozeduren und Funktionen neue Verzeichnisse zur Laufzeit erstellen. Diese Ordnernamen häufig-GUIDs enthalten und können nicht vorhergesagt werden. Das Trusted Launchpad von SQL Server erstellt eine neue Arbeitsverzeichnisse für R und Python-Skript Aufträge.

Da es möglicherweise nicht möglich, alle Ordner ausschließen, die von SQL Server-Prozess und dessen Funktionen benötigt werden, empfehlen wir, dass Sie die gesamte Verzeichnisstruktur der SQL Server-Instanz ausschließen.

### <a name="is-the-firewall-open-for-sql-server-does-the-instance-support-remote-connections"></a>Ist die Firewall für SQL Server geöffnet? Unterstützt die Instanz die Remoteverbindungen?

1. Um zu bestimmen, ob SQL Server Remoteverbindungen unterstützt, finden Sie unter [konfigurieren Remoteserververbindungen](../database-engine/configure-windows/view-or-configure-remote-server-connection-options-sql-server.md).

2. Bestimmen Sie, ob eine Firewallregel für SQL Server erstellt wurde. Aus Sicherheitsgründen in einer Standardinstallation möglicherweise es nicht möglich, dass remote R oder Python-Client eine Verbindung mit der Instanz herstellen. Weitere Informationen finden Sie unter [Problembehandlung eine Verbindung mit SQL Server](../database-engine/configure-windows/troubleshoot-connecting-to-the-sql-server-database-engine.md).

## <a name="see-also"></a>Siehe auch

[Problembehandlung bei Machine Learning in SQL Server](machine-learning-troubleshooting-faq.md)
