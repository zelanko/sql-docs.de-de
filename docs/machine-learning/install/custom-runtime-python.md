---
title: Installieren einer benutzerdefinierten Python-Laufzeit
description: Erfahren Sie, wie Sie eine benutzerdefinierte Python-Laufzeit für SQL Server installieren.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 09/20/2020
ms.topic: how-to
author: cawrites
ms.author: chadam
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: d02217eaae3cf402a1ccb6e08780f4e9406d446f
ms.sourcegitcommit: afb02c275b7c79fbd90fac4bfcfd92b00a399019
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2020
ms.locfileid: "91956316"
---
# <a name="install-a-python-custom-runtime-for-sql-server"></a>Installieren einer benutzerdefinierten Python-Laufzeit für SQL Server
[!INCLUDE [SQL Server 2019 and later](../../includes/applies-to-version/sqlserver2019.md)]

In diesem Artikel wird beschrieben, wie Sie eine benutzerdefinierte Laufzeit zum Ausführen von Python-Skripts mit SQL Server installieren. Die benutzerdefinierte Runtime verwendet Technologie zur Sprachenerweiterung, die auf einem Erweiterbarkeitsframework für die Ausführung von externem Code aufbaut. Die benutzerdefinierte Laufzeit für Python kann in folgenden Szenarien verwendet werden:

+ In einer Installation von SQL Server mit dem Erweiterbarkeitsframework.

+ In einer Installation von Machine Learning Services mit SQL Server 2019. Die Spracherweiterung kann mit [SQL Server Machine Learning Services](../sql-server-machine-learning-services.md) verwendet werden, nachdem einige zusätzliche Konfigurationsschritte abgeschlossen wurden.

::: moniker range=">=sql-server-ver15||=sqlallproducts-allversions"

> [!NOTE]
> In diesem Artikel wird beschrieben, wie Sie eine benutzerdefinierte Laufzeit für Python unter Windows installieren. Informationen zur Installation unter Linux finden Sie unter [Installieren einer benutzerdefinierten Python-Laufzeit für SQL Server unter Linux](custom-runtime-python.md?view=sql-server-linux-ver15&preserve-view=true).



## <a name="pre-install-checklist"></a>Prüfliste vor der Installation

Vor der Installation einer benutzerdefinierten Python-Laufzeit müssen Sie Folgendes installieren:

+ [SQL Server 2019 für Windows CU3 oder höher](../../database-engine/install-windows/install-sql-server.md).

  > [!NOTE]
  > Die benutzerdefinierte Python-Laufzeit erfordert das kumulative Update (CU) 3 oder höher für SQL Server 2019.

+ [SQL Server-Spracherweiterungen unter Windows mit dem Erweiterbarkeitsframework](../../language-extensions/install/install-sql-server-language-extensions-on-windows.md).

+ [Python 3.7]( https://www.python.org/downloads/release/python-379/).

## <a name="add-sql-server-language-extensions-for-windows"></a>Hinzufügen der SQL Server-Spracherweiterungen für Windows

> [!NOTE]
> Wenn Sie Machine Learning Services unter SQL Server 2019 installiert haben, ist das Erweiterbarkeitsframework bereits installiert, und Sie können diesen Schritt überspringen.

Spracherweiterungen verwenden das Erweiterbarkeitsframework zum Ausführen von externem Code. Die Codeausführung ist von den Prozessen der Kern-Engine isoliert, aber vollständig in die Ausführung von SQL Server-Abfragen integriert.

1. Starten Sie den Setup-Assistenten für SQL Server 2019.
  
1. Klicken Sie auf der Registerkarte **Installation** auf **Neue eigenständige SQL Server-Installation oder Hinzufügen von Funktionen zu einer vorhandenen Installation**.
    
    ![SQL Server 2019-Installation CU3 oder höher](../install/media/2019setup-installation-page-mlsvcs.png) 

1. Wählen Sie diese Optionen auf der Seite **Funktionsauswahl** aus:
  
    - **Datenbank-Engine-Dienste**
  
        Sie müssen eine Instanz der Datenbank-Engine installieren, um Spracherweiterungen mit SQL Server verwenden zu können. Sie können entweder eine Standardinstanz oder eine benannte Instanz verwenden.
  
    - **Machine Learning-Dienste und -Spracherweiterungen**
   
       Wählen Sie **Machine Learning-Dienste und -Spracherweiterungen** aus. Es ist nicht erforderlich, Python auszuwählen.

    ![Installationsfeatures von SQL Server 2019 CU3 oder höher](../install/media/sql-feature-selection.png) 

1. Stellen Sie auf der Seite **Installationsbereit** sicher, dass die folgenden Auswahlmöglichkeiten aktiviert sind, und klicken Sie auf **Installieren**.
  
    + -Datenbank-Engine-Dienste
    + Machine Learning-Dienste und -Spracherweiterungen

1. Wenn Sie nach Abschluss des Setups dazu aufgefordert werden, starten Sie jetzt den Computer neu. Wenn Sie den Setupvorgang abgeschlossen haben, sollten Sie unbedingt die vom Installations-Assistenten angezeigte Meldung lesen. Weitere Informationen finden Sie unter [View and Read SQL Server Setup Log Files](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md).


## <a name="install-python-37"></a>Installation von Python 3.7 

Installieren Sie [Python 3.7]( https://www.python.org/downloads/release/python-379/), und fügen Sie die Installation PATH hinzu.

![Hinzufügen von Python 3.7 zum Pfad.](../install/media/python-379.png) 


#### <a name="install-pandas"></a>Installieren von Pandas

Installieren Sie das [Pandas](https://pandas.pydata.org/)-Paket für Python über eine Eingabeaufforderung mit *erhöhten Rechten*:

```bash
python.exe -m pip install pandas
```

## <a name="update-the-system-environment-variables"></a>Aktualisieren der Systemumgebungsvariablen

Fügen Sie PYTHONHOME als Systemumgebungsvariable hinzu, oder ändern Sie diese.

+ Geben Sie im Windows-Suchfeld „environment“ ein, und wählen Sie **Systemumgebungsvariablen bearbeiten** aus.
+ Klicken Sie auf der Registerkarte **Erweitert** auf **Umgebungsvariablen**.
+ Wählen Sie unter **Systemvariablen** die Option **Neu** aus, um PYTHONHOME zu erstellen und auf den Python 3.7-Installationsspeicherort zu verweisen.
Wenn PYTHONHOME bereits vorhanden ist, wählen Sie **Bearbeiten** aus, um auf den Installationsspeicherort von Python 3.7 zu verweisen.
+ Wählen Sie **OK** aus, um die restlichen Fenster zu schließen.

![Erstellen Sie die PYTHONHOME-Systemvariable.](../install/media/sys-pythonhome.png)

## <a name="grant-access-to-the-custom-python-installation-folder"></a>Gewähren des Zugriffs auf den benutzerdefinierten Python-Installationsordner

Führen Sie die folgenden **icacls**-Befehle in einer neuen Eingabeaufforderung mit *erhöhten Rechten* aus, um PYTHONHOME für den **SQL Server-Launchpad-Dienst** und SID **S-1-15-2-1** (**ALL_APPLICATION_PACKAGES**) LESE- und AUSFÜHRUNGSZUGRIFF zu gewähren. Der Benutzername des Launchpad-Diensts ist `NT Service\MSSQLLAUNCHPAD$INSTANCENAME* where INSTANCENAME`, der Instanzname Ihrer SQL Server-Instanz. Die Befehle gewähren rekursiv Zugriff auf alle Dateien und Ordner unter dem angegebenen Verzeichnispfad.

Fügen Sie den Instanznamen an `MSSQLLAUNCHPAD` (`MSSQLLAUNCHPAD$INSTANCENAME`) an. In diesem Beispiel ist INSTANCENAME die Standardinstanz `MSSQLSERVER`.

1. Erteilen Sie Berechtigungen für **Benutzername des SQL Server-Launchpad Diensts**.

    ```cmd
    icacls "%PYTHONHOME%" /grant "NT Service\MSSQLLAUNCHPAD$MSSQLSERVER":(OI)(CI)RX /T

2. Give permissions to **SID S-1-15-2-1**.
    ```cmd
    icacls "%PYTHONHOME%" /grant *S-1-15-2-1:(OI)(CI)RX /T

>[!NOTE]
>The preceding command grants permissions to the computer **SID S-1-15-2-1**, which is equivalent to ALL APPLICATION PACKAGES on an English version of Windows. Alternatively, you can use `icacls "%R_HOME%" /grant "ALL APPLICATION PACKAGES":(OI)(CI)RX /T` on an English version of Windows.

## Restart SQL Server Launchpad service

From an *elevated* command prompt, run the following commands. Replace "MSSQLSERVER" with the name of your SQL Server instance.

```CMD
net stop MSSQLLAUNCHPAD$MSSQLSERVER
net start MSSQLLAUNCHPAD$MSSQLSERVER
```

Klicken Sie alternativ mit der rechten Maustaste auf den SQL Server-Launchpad-Dienst in der App **Dienste** des Systems, und klicken Sie auf **Neu starten**. Verwenden Sie alternativ den [SQL Server-Konfigurations-Manager](../../relational-databases/sql-server-configuration-manager.md) zum erneuten Starten des Diensts.

## <a name="download-python-language-extension"></a>Herunterladen der Python-Programmiersprachenerweiterung

Laden Sie die [ZIP-Datei herunter, die die Python-Sprachenerweiterung für Windows](https://github.com/microsoft/sql-server-language-extensions/releases) enthält. Es wird empfohlen, die Releaseversion in der Produktionsumgebung zu verwenden. Verwenden Sie die Debugversion in der Entwicklungs- oder Testumgebung, da sie ausführliche Protokollierungsinformationen zur Untersuchung eventueller Fehler liefert.

## <a name="register-external-language"></a>Registrieren einer externen Sprache

Registrieren Sie diese Python-Spracherweiterung mit [CREATE EXTERNAL LANGUAGE](../../t-sql/statements/create-external-language-transact-sql.md) für jede Datenbank, in der Sie sie verwenden möchten. Verwenden Sie [Azure Data Studio](../../azure-data-studio/download-azure-data-studio.md), um eine Verbindung mit SQL Server herzustellen und den folgenden T-SQL-Befehl auszuführen. Ändern Sie den Pfad in dieser Anweisung, um den Speicherort der heruntergeladenen ZIP-Spracherweiterungsdatei („python-lang-extension.zip“) anzugeben.

> [!NOTE]
> Python ist ein reserviertes Wort. Verwenden Sie einen anderen Namen für die externe Sprache, z. B. „myPython“.

```sql
CREATE EXTERNAL LANGUAGE [myPython]
FROM (CONTENT = N'/path/to/python-lang-extension.zip', FILE_NAME = 'pythonextension.dll');
GO
```

::: moniker-end

::: moniker range=">=sql-server-linux-ver15||=sqlallproducts-allversions"

Sie könne SQL Server unter Red Hat Enterprise Linux (RHEL), SUSE Linux Enterprise Server (SLES) und Ubuntu installieren. Weitere Informationen finden Sie [im Abschnitt „Unterstützte Plattformen“ im Leitfaden für die Installation von SQL Server unter Linux](../../linux/sql-server-linux-setup.md).

> [!NOTE]
> In diesem Artikel wird beschrieben, wie Sie eine benutzerdefinierte Laufzeit für Python unter Linux installieren. Informationen zur Installation unter Windows finden Sie unter [Installieren einer benutzerdefinierten Python-Laufzeit für SQL Server unter Windows](custom-runtime-python.md?view=sql-server-ver15&preserve-view=true).

## <a name="pre-install-checklist"></a>Prüfliste vor der Installation

Vor der Installation einer benutzerdefinierten Python-Laufzeit müssen Sie Folgendes installieren:

+ [SQL Server 2019 für Linux (kumulatives Update 3 oder höher)](../../linux/sql-server-linux-setup.md).
Wenn Sie SQL Server für Linux installieren, müssen Sie ein Microsoft-Repository konfigurieren. Weitere Informationen finden Sie unter [Konfigurieren von Repositorys](../../linux/sql-server-linux-change-repo.md).

  > [!NOTE]
  > Die benutzerdefinierte Python-Laufzeit erfordert das kumulative Update (CU) 3 oder höher für SQL Server 2019.

+ [SQL Server-Spracherweiterungen unter Linux mit dem Erweiterbarkeitsframework](../../linux/sql-server-linux-setup-language-extensions.md).

+ [Python 3.7](https://www.python.org/downloads/release/python-379/).

## <a name="add-sql-server-language-extensions-for-linux"></a>Hinzufügen der SQL Server-Spracherweiterungen für Linux

> [!NOTE]
> Wenn Sie Machine Learning Services unter SQL Server 2019 installiert haben, ist das Paket **mssql-server-extensibility** für Spracherweiterungen bereits installiert, und Sie können diesen Schritt überspringen.

Spracherweiterungen verwenden das Erweiterbarkeitsframework zum Ausführen von externem Code. Die Codeausführung ist von den Prozessen der Kern-Engine isoliert, aber vollständig in die Ausführung von SQL Server-Abfragen integriert.

Verwenden Sie die folgenden Befehle, um Spracherweiterungen abhängig von Ihrer Linux-Version zu installieren.

### <a name="ubuntu"></a>Ubuntu
> [!TIP]
> Führen Sie nach Möglichkeit `update` aus, um Pakete auf dem System vor der Installation zu aktualisieren. Ubuntu verfügt möglicherweise nicht über die Option „https apt transport“. Verwenden Sie `apt-get install apt-transport-https`, um diese zu installieren.

```bash
# Install as root or sudo
sudo apt-get install mssql-server-extensibility
```

### <a name="red-hat"></a>Red Hat
```bash
# Install as root or sudo
sudo yum install mssql-server-extensibility
```

### <a name="suse"></a>Suse
```bash
# Install as root or sudo
sudo zypper install mssql-server-extensibility
```

## <a name="install-python-37-and-pandas"></a>Installieren von Python 3.7 and Pandas

Installieren Sie Python 3.7, die libpython3.7-Bibliothek und das Pandas-Paket. 

Im Folgenden finden Sie Beispielbefehle für Ubuntu:

```bash
# Install python3.7 and the corresponding library:
sudo add-apt-repository ppa:deadsnakes/ppa
sudo apt-get update
sudo apt-get install python3.7 python3-pip libpython3.7

# Install pandas to /usr/lib:
sudo python3.7 -m pip install pandas -t /usr/lib/python3.7/dist-packages
```

## <a name="using-a-custom-installation-of-python-37"></a>Verwenden einer benutzerdefinierten Installation von Python 3.7

> [!NOTE]
> Wenn Sie Python am Standardspeicherort `/usr/lib/python3.7` installiert haben, können Sie mit dem [nächsten Abschnitt](#download-python-linux) fortfahren.

Wenn Sie Ihre eigene Version von Python 3.7 erstellt haben, verwenden Sie die folgenden Befehle, damit SQL Server die benutzerdefinierte Installation ermitteln und laden kann.

### <a name="update-the-environment-variables"></a>Aktualisieren der Umgebungsvariablen

1. Bearbeiten Sie den Dienst mssql-launchpadd, um der Datei `/etc/systemd/system/mssql-launchpadd.service.d/override.conf` die PYTHONHOME-Umgebungsvariable hinzuzufügen.

      ```bash
      sudo systemctl edit mssql-launchpadd
      ```

    + Fügen Sie den folgenden Text in die Datei `/etc/systemd/system/mssql-launchpadd.service.d/override.conf` ein, die geöffnet wird. Legen Sie den Wert von PYTHONHOME auf den benutzerdefinierten Python-Installationspfad fest.

      ```vi
      [Service]
      Environment="PYTHONHOME=/path/to/installation/of/python3.7"
      ```

    + Speichern und schließen Sie die Datei.

2. Stellen Sie sicher, dass `libpython3.7m.so.1.0` geladen werden kann.

    + Erstellen Sie eine benutzerdefinierte Datei „python.conf“ in `/etc/ld.so.conf.d`.

      ```bash
      sudo vi /etc/ld.so.conf.d/custom-python.conf
      ```

    + Fügen Sie in der Datei, die geöffnet wird, den Pfad zu **libpython3.7m.so.1.0** aus der benutzerdefinierten Python-Installation hinzu.

      ```vi
      /path/to/installation/of/python3.7/lib
      ```

    + Speichern und schließen Sie die neue Datei.

    + Führen Sie `ldconfig` aus, und vergewissern Sie sich, dass `libpython3.7m.so.1.0` geladen werden kann, indem Sie den folgenden Befehl ausführen und überprüfen, ob die abhängigen Bibliotheken gefunden werden.

      ```bash
      sudo ldconfig
      ldd /path/to/installation/of/python3.7/lib/libpython3.7m.so.1.0
      ```

### <a name="grant-access-to-the-custom-python-folder"></a>Gewähren des Zugriffs auf den benutzerdefinierten Python-Ordner

Legen Sie die `datadirectories`-Option im Erweiterbarkeitsabschnitt der Datei „/var/opt/mssql/mssql.conf“ auf die benutzerdefinierte Python-Installation fest.

```bash
sudo /opt/mssql/bin/mssql-conf set extensibility.datadirectories /path/to/installation/of/python3.7
```

### <a name="restart-the-mssql-launchpadd-service"></a>Neustarten des mssql-launchpadd-Diensts

```bash
sudo systemctl restart mssql-launchpadd
```
## <a name="download-python-language-extension"></a><a name="download-python-linux"></a> Herunterladen der Python-Programmiersprachenerweiterung

Laden Sie die [ZIP-Datei herunter, die die Python-Sprachenerweiterung für Linux](https://github.com/microsoft/sql-server-language-extensions/releases) enthält. Es wird empfohlen, die Releaseversion in der Produktionsumgebung zu verwenden. Verwenden Sie die Debugversion in der Entwicklungs- oder Testumgebung, da sie ausführliche Protokollierungsinformationen zur Untersuchung eventueller Fehler liefert.

## <a name="register-external-language"></a>Registrieren einer externen Sprache

Registrieren Sie diese Python-Spracherweiterung mit [CREATE EXTERNAL LANGUAGE](../../t-sql/statements/create-external-language-transact-sql.md) für jede Datenbank, in der Sie sie verwenden möchten. Verwenden Sie [Azure Data Studio](../../azure-data-studio/download-azure-data-studio.md), um eine Verbindung mit SQL Server herzustellen und den folgenden T-SQL-Befehl auszuführen. 
Ändern Sie den Pfad in dieser Anweisung, um den Speicherort der heruntergeladenen ZIP-Spracherweiterungsdatei („python-lang-extension.zip“) anzugeben.

> [!NOTE]
>Python ist ein reserviertes Wort. Verwenden Sie einen anderen Namen für die externe Sprache, z. B. „myPython“.

```sql
CREATE EXTERNAL LANGUAGE myPython 
FROM (CONTENT = N'/PATH/TO/python-lang-extension.zip', FILE_NAME = 'libPythonExtension.so.1.0');
GO
```

::: moniker-end

## <a name="enable-external-script-execution-in-sql-server"></a>Aktivieren der externen Skriptausführung in SQL Server

Ein externes Skript in Python kann über die gespeicherte Prozedur [sp_execute_external script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) ausgeführt werden, die für SQL Server ausgeführt wird. 

Um externe Skripts zu aktivieren, führen Sie die folgenden SQL-Befehle mit [Azure Data Studio](../../azure-data-studio/download-azure-data-studio.md) aus, während eine Verbindung mit SQL Server besteht.

```sql
sp_configure 'external scripts enabled', 1;
RECONFIGURE WITH OVERRIDE;  
```

## <a name="verify-language-extension-installation"></a>Überprüfen der Installation der Spracherweiterung

Mit diesem SQL-Skript wird die Funktionalität der installierten Spracherweiterung getestet.

```sql
EXEC sp_execute_external_script
@language =N'myPython',
@script=N'
import sys
print(sys.path)
print(sys.version)
print(sys.executable)'
```

## <a name="verify-parameters-and-datasets-of-different-data-types"></a>Überprüfen von Parametern und Datasets mit unterschiedlichen Datentypen

Dieses Skript testet verschiedene Datentypen für Eingabe-/Ausgabeparameter und Datasets.

```sql
DECLARE @sumVal int = 12;
DECLARE @charVal VARCHAR(30) = N'Hello'

EXEC sp_execute_external_script
@language =N'myPython',
@script=N'
print(sumVal)
print(charVal)
sumVal = sumVal + 300
OutputDataSet = InputDataSet'
,@input_data_1 = N'SELECT 1, CAST(1.4 as real), ''Hi'', CAST(''1'' as bit)'
,@params = N'@sumVal int OUTPUT, @charVal VARCHAR(30)'
,@sumVal = @sumVal OUTPUT
,@charVal = @charVal
WITH RESULT SETS ((intCol int, doubleCol real, charCol char(2), logicalCol bit));

PRINT @sumVal
```

## <a name="next-steps"></a>Nächste Schritte

+ [Erweiterbarkeitsframework in SQL Server](../concepts/extensibility-framework.md)
+ [Übersicht über Spracherweiterungen](../../language-extensions/language-extensions-overview.md)