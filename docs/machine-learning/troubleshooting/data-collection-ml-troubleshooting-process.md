---
title: Sammeln von Daten zum Beheben von SQL Machine Learning-Problemen
description: Hier erfahren Sie, wie Sie die Daten sammeln, die Sie benötigen, wenn Sie Probleme selbst oder mithilfe des Microsoft-Kundensupports lösen möchten.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 07/01/2020
ms.topic: troubleshooting
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15'
ms.openlocfilehash: 3bb4aa40995db27909162f791ddfbdb3701bb0fb
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97470651"
---
# <a name="collect-data-to-troubleshoot-sql-machine-learning"></a>Sammeln von Daten zum Beheben von SQL Machine Learning-Problemen

[!INCLUDE [SQL Server 2016 and later](../../includes/applies-to-version/sqlserver2016.md)]

In diesem Artikel wird beschrieben, wie Sie die Daten sammeln, die Sie benötigen, wenn Sie versuchen, Probleme in SQL Machine Learning zu beheben. Diese Daten können nützlich sein, unabhängig davon, ob Sie Probleme selbst oder mithilfe des Microsoft-Kundensupports beheben.

## <a name="sql-server-version-and-edition"></a>SQL Server-Version und -Edition

SQL Server 2016 R Services ist das erste Release von SQL Server mit integrierter R-Unterstützung. SQL Server 2016 Service Pack 1 (SP1) umfasst mehrere wichtige Verbesserungen, einschließlich der Möglichkeit zum Ausführen externer Skripts. Wenn Sie SQL Server 2016 verwenden, sollten Sie die Installation von SP1 oder höher erwägen.

SQL Server 2017 und höher bietet die Integration der Python-Sprache. Die Integration des Python-Funktionen ist in früheren Versionen nicht verfügbar.

Unterstützung zur Beschaffung von Editionen und Versionen finden Sie in diesem Artikel, in dem die Buildnummern für alle [SQL Server-Versionen](https://social.technet.microsoft.com/wiki/contents/articles/783.sql-server-versions.aspx#Service_Pack_editions) aufgelistet sind.

Je nach der von Ihnen verwendeten Edition von SQL Server sind einige Machine Learning-Funktionen möglicherweise nicht verfügbar oder eingeschränkt. 

## <a name="r-language-and-tool-versions"></a>R-Sprache und -Toolversionen

Welche Version von Microsoft R installiert wird, wenn Sie das R Services- oder Machine Learning Services-Feature auswählen, wird im Allgemeinen durch die SQL Server-Buildnummer bestimmt. Wenn Sie SQL Server aktualisieren oder patchen, müssen Sie auch die zugehörigen R-Komponenten aktualisieren oder patchen.

Eine Liste der Releases und Links zu R-Komponentendownloads finden Sie unter [Installieren von Machine Learning in R und Python auf SQL Server-Computern ohne Internetzugang](../install/sql-ml-component-install-without-internet-access.md). Auf Computern mit Internetzugriff wird die erforderliche Version von R automatisch identifiziert und installiert.

Es ist möglich, die R Server-Komponenten in einem als Bindung bezeichneten Prozess getrennt von der SQL Server-Datenbank-Engine zu aktualisieren. Daher kann die Version von R, die Sie beim Ausführen von R-Code in SQL Server verwenden, abhängig von der installierten Version von SQL Server und davon, ob Sie den Server auf die neueste Version von R migriert haben, unterschiedlich sein.

### <a name="determine-the-r-version"></a>Bestimmen der R-Version

Am einfachsten können Sie die R-Version ermitteln, indem Sie mit einer Anweisung wie der folgenden die Runtimeeigenschaften abrufen:

```sql
EXECUTE sp_execute_external_script
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
> Wenn R Services nicht funktioniert, versuchen Sie, nur den R-Skriptteil von RGui auszuführen.

Als letztes Mittel können Sie Dateien auf dem Server öffnen, um die installierte Version zu bestimmen. Suchen Sie hierzu die Datei „rlauncher.config“, um den Speicherort der R-Runtime und das aktuelle Arbeitsverzeichnis abzurufen. Sie sollten eine Kopie der Datei erstellen und öffnen, damit Sie nicht versehentlich Eigenschaften ändern.

* SQL Server 2016
  
  `C:\Program Files\Microsoft SQL Server\MSSQL13.<instance_name\MSSQL\Binn\rlauncher.config`

* SQL Server 2017
  
  `C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\MSSQL\Binn\rlauncher.config`

Um die R-Version und die RevoScaleR-Versionen zu erhalten, öffnen Sie eine R-Eingabeaufforderung, oder öffnen Sie die RGui, die der Instanz zugeordnet ist.

* SQL Server 2016
  
  `C:\Program Files\Microsoft SQL Server\MSSQL13.<instancename>\R_SERVICES\bin\x64\RGui.exe`

* SQL Server 2017
  
  `C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\R_SERVICES\bin\x64\RGui.exe`

In der R-Konsole werden die Versionsinformationen beim Start angezeigt. Die folgende Version stellt z. B. die Standardkonfiguration für SQL Server 2017 dar:

```console
*Microsoft R Open 3.3.3*

*The enhanced R distribution from Microsoft*

*Microsoft packages Copyright (C) 2017 Microsoft*

*Loading Microsoft R Server packages, version 9.1.0.*
```

## <a name="python-versions"></a>Python-Versionen

Es gibt mehrere Möglichkeiten, die Python-Version zu erhalten. Die einfachste Möglichkeit besteht darin, diese Anweisung von Management Studio oder einem anderen SQL-Abfragetool aus auszuführen:

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

Wenn Machine Learning Services nicht ausgeführt wird, können Sie die installierte Python-Version ermitteln, indem Sie sich die Datei „pythonlauncher. config“ ansehen. Sie sollten eine Kopie der Datei erstellen und öffnen, damit Sie nicht versehentlich Eigenschaften ändern.

1. Nur für SQL Server 2017: `C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\MSSQL\Log\ExtensibilityLog\pythonlauncher.config`
2. Rufen Sie den Wert für **PYTHONHOME** ab.
3. Rufen Sie den Wert des aktuellen Arbeitsverzeichnisses ab.

> [!NOTE]
> Wenn Sie sowohl Python als auch R auf SQL Server 2017 installiert haben, werden das Arbeitsverzeichnis und der Pool von Workerkonten für die Programmiersprachen R und Python freigegeben.

## <a name="are-multiple-instances-of-r-or-python-installed"></a>Sind mehrere Instanzen von R oder Python installiert?

Überprüfen Sie, ob mehrere Kopien der R-Bibliotheken auf dem Computer installiert sind. Diese Duplizierung kann unter folgenden Umständen auftreten:

* Während des Setups wählen Sie gleichzeitig „R Services (datenbankintern)“ und „R Server (Standalone)“ aus.
* Sie installieren Microsoft R Client zusätzlich zu SQL Server.
* Ein anderer Satz von R-Bibliotheken wurde mit R Tools für Visual Studio, R Studio, Microsoft R Client oder einer anderen R-IDE installiert.
* Der Computer hostet mehrere Instanzen von SQL Server, und mehrere Instanzen verwenden maschinelles Lernen.

Die gleichen Bedingungen gelten für Python.

Wenn Sie feststellen, dass mehrere Bibliotheken oder Runtimes installiert sind, stellen Sie sicher, dass Sie nur die Fehlermeldungen erhalten, die sich auf die von der SQL Server-Instanz verwendeten Python- oder R-Runtimes beziehen.

## <a name="origin-of-errors"></a>Ursprung von Fehlern

Die Fehler, die angezeigt werden, wenn Sie versuchen, R-Code auszuführen, können aus einer der folgenden Quellen stammen:

* SQL Server-Datenbank-Engine einschließlich der gespeicherten Prozedur „sp_execute_external_script“
* Das SQL Server Trusted Launchpad
* Weitere Komponenten des Erweiterbarkeitsframeworks, einschließlich R- und Python-Startprogrammen und Satellitenprozessen
* Anbieter wie Microsoft Open Database Connectivity (ODBC)
* R-Sprache

Wenn Sie zum ersten Mal mit dem Dienst arbeiten, kann es schwierig sein, zu erkennen, welche Nachrichten von welchen Diensten stammen. Sie sollten nicht nur den genauen Nachrichtentext, sondern den Kontext erfassen, in dem Sie die Meldung gesehen haben. Beachten Sie die Clientsoftware, die Sie zum Ausführen von Code für maschinelles Lernen verwenden:

* Verwenden Sie Management Studio? Eine externe Anwendung?
* Führen Sie R-Code in einem Remoteclient oder direkt in einer gespeicherten Prozedur aus?

## <a name="sql-server-log-files"></a>SQL Server-Protokolldateien

Rufen Sie das aktuelle SQL Server-ERRORLOG ab. Der gesamte Satz von Fehlerprotokollen besteht aus den Dateien aus dem folgenden Standardprotokollverzeichnis:

* SQL Server 2016
  
  `C:\Program Files\Microsoft SQL Server\MSSQL13.SQL2016\MSSQL\Log\ExtensibilityLog`

* SQL Server 2017
  
  `C:\Program Files\Microsoft SQL Server\MSSQL14.SQL2016\MSSQL\Log\ExtensibilityLog`

> [!NOTE]
> Der exakte Ordnername variiert abhängig vom Instanznamen.

## <a name="errors-returned-by-sp_execute_external_script"></a>Von „sp_execute_external_script“ zurückgegebene Fehler

Rufen Sie den vollständigen Text der ggf. zurückgegebenen Fehlermeldungen ab, wenn Sie sp_execute_external_script-Befehl ausführen.

Um R- oder Python-Probleme zu entfernen, können Sie dieses Skript ausführen, das die R- oder Python-Runtime startet und Daten in beide Richtungen übergibt.

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

## <a name="errors-generated-by-the-extensibility-framework"></a>Vom Erweiterbarkeitsframework generierte Fehlermeldungen

SQL Server generiert separate Protokolle für die Runtimes der externen Skriptsprache. Diese Fehler werden nicht von der Python- oder R-Sprache generiert. Sie werden aus den Erweiterbarkeitskomponenten in SQL Server generiert, einschließlich sprachspezifischer Startprogramme und ihrer Satellitenprozesse.

Sie können diese Protokolle von den folgenden Standardspeicherorten abrufen:

* SQL Server 2016
  
  `C:\Program Files\Microsoft SQL Server\MSSQL13.<instance_name>\MSSQL\Log\ExtensibilityLog`

* SQL Server 2017
  
  `C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\MSSQL\Log\ExtensibilityLog`

> [!NOTE]
> Der exakte Ordnername variiert abhängig vom Instanznamen. Abhängig von Ihrer Konfiguration könnte sich der Ordner auf einem anderen Laufwerk befinden.

Beispielsweise sind die folgenden Protokollmeldungen mit dem Erweiterbarkeitsframework verknüpft:

* *LogonUser Failed for user MSSQLSERVER01* (Fehler bei „LogonUser“ für Benutzer MSSQLSERVER01)
  
  Dies könnte darauf hindeuten, dass die Workerkonten, die externe Skripts ausführen, nicht auf die Instanz zugreifen können.

* *InitializePhysicalUsersPool Failed* (Fehler bei InitializePhysicalUsersPool)
  
  Diese Meldung könnte bedeuten, dass Ihre Sicherheitseinstellungen das Setup am Erstellen des Pools von Workerkonten hindern, die für die Ausführung externer Skripts erforderlich sind.

* *Security Context Manager initialization failed* (Fehler bei der Initialisierung des Sicherheitskontext-Managers)

* *Satellite Session Manager initialization failed* (Fehler bei der Initialisierung des Satellitensitzungs-Managers)

## <a name="system-events"></a>Systemereignisse

1. Öffnen Sie die Windows-Ereignisanzeige, und suchen Sie im **Systemereignis**-Protokoll nach Meldungen, die die Zeichenfolge *Launchpad* enthalten.
2. Öffnen Sie die ExtLaunchErrorlog-Datei, und suchen Sie nach der Zeichenfolge *ErrorCode*. Überprüfen Sie die Meldung, die dem ErrorCode zugeordnet ist.

Die folgenden Meldungen beziehen sich z. B. auf häufige Systemfehler im Zusammenhang mit dem SQL Server-Erweiterbarkeitsframework:

* *Der Dienst SQL Server-Launchpad (MSSQLSERVER) wurde aufgrund folgenden Fehlers nicht gestartet:  <text>*

* *Der Dienst antwortete nicht rechtzeitig auf die Start- oder Steuerungsanforderung.*

* *Das Zeitlimit (120.000 ms) wurde beim Verbindungsversuch mit dem Dienst SQL Server-Launchpad (MSSQLSERVER) erreicht.*

## <a name="dump-files"></a>Dumpdateien

Wenn Sie mit dem Debuggen vertraut sind, können Sie die Dumpdateien verwenden, um einen Fehler in Launchpad zu analysieren.

1. Suchen Sie den Ordner, der die Setup-Bootstrapprotokolle für SQL Server enthält. In SQL Server 2016 war der Standardpfad z. B. „C:\Programme\Microsoft SQL Server\130\Setup Bootstrap\Logs“.
2. Öffnen Sie den für die Erweiterbarkeit spezifischen Bootstrapprotokoll-Unterordner.
3. Wenn Sie eine Supportanfrage einreichen müssen, fügen Sie den gesamten Inhalt dieses Ordners einer ZIP-Datei hinzu. Beispiel: „C:\Programme\Microsoft SQL Server\130\Setup Bootstrap\Log\LOG\ExtensibilityLog“.
  
Der genaue Speicherort könnte auf Ihrem System anders sein und sich auf einem anderen Laufwerk als C befinden. Stellen Sie sicher, dass Sie die Protokolle für die Instanz erhalten, auf der maschinelles Lernen installiert ist.

## <a name="configuration-settings"></a>Konfigurationseinstellungen

In diesem Abschnitt werden zusätzliche Komponenten oder Anbieter aufgelistet, die beim Ausführen von R- oder Python-Skripts als Fehlerquelle infrage kommen.

### <a name="what-network-protocols-are-available"></a>Welche Netzwerkprotokolle sind verfügbar?

Machine Learning Services benötigt die folgenden Netzwerkprotokolle für die interne Kommunikation zwischen Erweiterbarkeitskomponenten und für die Kommunikation mit externen R- oder Python-Clients.

* Named Pipes
* TCP/IP

Öffnen Sie den SQL Server-Konfigurations-Manager, um zu bestimmen, ob ein Protokoll installiert ist, und wenn es installiert ist, ob es aktiviert ist.

### <a name="security-configuration-and-permissions"></a>Sicherheitskonfiguration und Berechtigungen

Für Workerkonten:

1. Öffnen Sie in der Systemsteuerung **Benutzer und Gruppen**, und suchen Sie die Gruppe, die zum Ausführen externer Skriptaufträge verwendet wird. Standardmäßig ist dies die Gruppe **SQLRUserGroup**.
2. Vergewissern Sie sich, dass die Gruppe vorhanden ist und mindestens ein Workerkonto enthält.
3. Wählen Sie in SQL Server Management Studio die Instanz aus, auf der R- oder Python-Aufträge ausgeführt werden, wählen Sie **Sicherheit** aus, und bestimmen Sie dann, ob eine Anmeldung für SQLRUserGroup vorliegt.
4. Überprüfen Sie die Berechtigungen für die Benutzergruppe.

Für einzelne Benutzerkonten:

1. Bestimmen Sie, ob die Instanz die Authentifizierung im gemischten Modus, nur SQL-Anmeldungen oder nur die Windows-Authentifizierung unterstützt. Diese Einstellung wirkt sich auf Ihre R- oder Python-Codeanforderungen aus.
2. Legen Sie für jeden Benutzer, der R-Code ausführen muss, die erforderliche Berechtigungsebene für jede Datenbank fest, in die Objekte aus R geschrieben werden, in der auf Daten zugegriffen wird oder aus der Objekte erstellt werden.
3. Um die Skriptausführung zu aktivieren, erstellen Sie nach Bedarf Rollen, oder fügen Sie den folgenden Rollen Benutzer hinzu:

   - Alle außer *db_owner*: Erfordern „EXECUTE ANY EXTERNAL SCRIPT“.
   - *db_datawriter:* Zum Schreiben von Ergebnissen aus R oder Python.
   - *db_ddladmin:* Zum Erstellen neuer Objekte.
   - *db_datareader:* Zum Lesen von Daten, die von R- oder Python-Code verwendet werden.
4. Beachten Sie, ob Sie bei der Installation von SQL Server 2016 Standardstartkonten geändert haben.
5. Wenn ein Benutzer neue R-Pakete installieren oder R-Pakete verwenden muss, die von anderen Benutzern installiert wurden, müssen Sie möglicherweise die Paketverwaltung auf der Instanz aktivieren und dann zusätzliche Berechtigungen zuweisen. 

### <a name="what-folders-are-subject-to-locking-by-antivirus-software"></a>Welche Ordner können durch Antivirussoftware gesperrt werden?

Durch Antivirussoftware können Ordner gesperrt werden, was die Einrichtung der Features für maschinelles Lernen und die erfolgreiche Skriptausführung verhindert. Ermitteln Sie, ob für Ordner in der SQL Server-Struktur Virenscans durchgeführt werden.

Wenn jedoch mehrere Dienste oder Features auf einer Instanz installiert sind, kann es schwierig sein, alle möglichen Ordner aufzuzählen, die von der Instanz verwendet werden. Wenn z. B. neue Features hinzugefügt werden, müssen die neuen Ordner identifiziert und ausgeschlossen werden.

Darüber hinaus erstellen einige Features zur Runtime dynamisch neue Ordner. Beispielsweise erstellen In-Memory-OLTP-Tabellen, gespeicherte Prozeduren und Funktionen zur Runtime neue Verzeichnisse. Diese Ordnernamen enthalten häufig GUIDs und können nicht vorhergesagt werden. Das SQL Server Trusted Launchpad erstellt neue Arbeitsverzeichnisse für R- und Python-Skriptaufträge.

Da es vielleicht nicht möglich ist, alle vom SQL Server-Prozess und seinen Features benötigten Ordner auszuschließen, sollten Sie die gesamte Instanzverzeichnisstruktur von SQL Server ausschließen.

### <a name="is-the-firewall-open-for-sql-server-does-the-instance-support-remote-connections"></a>Ist die Firewall für SQL Server geöffnet? Unterstützt die Instanz Remoteverbindungen?

1. Um zu bestimmen, ob SQL Server Remoteverbindungen unterstützt, lesen Sie [Anzeigen oder Konfigurieren von Verbindungsoptionen für Remoteserver (SQL Server)](../../database-engine/configure-windows/view-or-configure-remote-server-connection-options-sql-server.md).

2. Stellen Sie fest, ob für SQL Server eine Firewallregel erstellt wurde. Aus Sicherheitsgründen ist in einer Standardinstallation möglicherweise nicht möglich, dass der Remote-R- oder Remote-Python-Client eine Verbindung mit der Instanz herstellt. Weitere Informationen finden Sie unter [Beheben von Verbindungsfehlern mit der SQL Server-Datenbank-Engine](../../database-engine/configure-windows/troubleshoot-connecting-to-the-sql-server-database-engine.md).

## <a name="see-also"></a>Weitere Informationen

[Problembehandlung bei Machine Learning in SQL Server](machine-learning-troubleshooting-overview.md)