---
title: Installieren von SQL Server Machine Learning-Dienste (R, Python, Java) unter Linux | Microsoft-Dokumentation
description: Erfahren Sie, wie zum Installieren von SQL Server Machine Learning Services (R, Python, Java) auf Red Hat und Ubuntu.
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.date: 03/27/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: machine-learning
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: f1ca66c5e376704737a092f21fd25401d20bbdbb
ms.sourcegitcommit: 2db83830514d23691b914466a314dfeb49094b3c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58493872"
---
# <a name="install-sql-server-2019-machine-learning-services-r-python-java-on-linux"></a>Installieren von SQL Server 2019 Machine Learning-Diensten (R, Python, Java) unter Linux

[SQL Server Machine Learning Services](../advanced-analytics/what-is-sql-server-machine-learning.md) auf Linux-Betriebssysteme, die ab dieser Preview-Version von SQL Server-2019 ausgeführt wird. Führen Sie die Schritte in diesem Artikel, die Programmiersprache Java-Erweiterung oder das Machine learning-Erweiterungen für R und Python installieren. 

Machine learning und Programmieren von Erweiterungen sind ein Add-on für die Datenbank-Engine. Zwar Sie können [installieren Sie die Datenbank-Engine und Machine Learning-Dienste gleichzeitig](#install-all), es ist eine bewährte Methode zum Installieren und konfigurieren die SQL Server-Datenbank-Engine zuerst, damit Sie Probleme beheben können, bevor Sie weitere hinzufügen Komponenten. 

Speicherort des Pakets für die R, Python und Java-Erweiterungen sind in den SQL Server Linux-Quell-Repositorys. Wenn Sie bereits über Quellcode-Repositorys für die Datenbank-Engine-Installation konfiguriert, können Sie Ausführen den **Mssql-Mlservices** Paket Befehle zur Installation über die gleichen Repository-Registrierung.

Machine Learning-Dienste wird auch auf Linux-Container unterstützt. Mit Machine Learning-Diensten keine vordefinierten Container bereitgestellt, aber erstellen Sie einen aus der SQL Server-Containern unter Verwendung von [eine Beispielvorlage auf GitHub verfügbar](https://github.com/Microsoft/mssql-docker/tree/master/linux/preview/examples/mssql-mlservices).

## <a name="uninstall-previous-ctp"></a>Deinstallieren der vorherigen CTP-Version

Die Liste der Pakete hat sich über die letzten CTP-Version Versionen, was zu weniger Pakete geändert werden. Es wird empfohlen, deinstallieren CTP 2.x So entfernen Sie alle früheren Pakete vor der Installation der CTP-Version 2.4. Seite-an-Seite Installation mehrerer Versionen wird nicht unterstützt.

### <a name="1-confirm-package-installation"></a>1. Paketinstallation bestätigen

Sie möchten möglicherweise prüfen, ob das Vorhandensein einer früheren Installation als ersten Schritt. Die folgenden Dateien angeben eine vorhandene Installation: checkinstallextensibility.sh, Exthost, Launchpad.

```bash
ls /opt/microsoft/mssql/bin
```

### <a name="2-uninstall-previous-ctp-2x-packages"></a>2. Deinstallieren der vorherigen CTP-Version 2.x-Pakete

Deinstallieren Sie auf der untersten Paketebene. Alle abhängigen für ein Paket auf niedrigerer Ebene upstreampaket wird automatisch deinstalliert.

  + Entfernen Sie für die R-Integration **Microsoft-R-öffnen***
  + Entfernen Sie die Integration von Python **Mssql-Mlservices-Python**
  + Entfernen Sie für die Java-Integration **Mssql-Server-Erweiterbarkeit – Java**

Befehle zum Löschen von Paketen, die in der folgenden Tabelle angezeigt werden.

| Platform  | Paket entfernen Befehle | 
|-----------|----------------------------|
| RHEL  | `sudo yum remove microsoft-r-open-mro-3.4.4`<br/>`sudo yum remove msssql-mlservices-python`<br/>`sudo yum remove msssql-server-extensibility-java` |
| SLES  | `sudo zypper remove microsoft-r-open-mro-3.4.4`<br/>`sudo zypper remove msssql-mlservices-python`<br/>`sudo zypper remove msssql-server-extensibility-java` |
| Ubuntu    | `sudo apt-get remove microsoft-r-open-mro-3.4.4`<br/>`sudo apt-get remove msssql-mlservices-python`<br/>`sudo apt-get remove msssql-server-extensibility-java`|

> [!Note]
> Microsoft R Open besteht aus drei Paketen. Wenn irgendeines dieser Pakete bleiben nach dem Entfernen der Microsoft-R-öffnen-Mro-3.4.4, sollten Sie diese einzeln zu entfernen.
> ```
> microsoft-r-open-foreachiterators-3.4.4
> microsoft-r-open-mkl-3.4.4
> microsoft-r-open-mro-3.4.4
> ```

### <a name="3-proceed-with-ctp-24-install"></a>3. CTP 2.4-Installation nicht fortsetzen

Auf der höchsten Paketebene, die mithilfe der Anweisungen in diesem Artikel für Ihr Betriebssystem installieren.

Für jeden Satz betriebssystemspezifischen Anweisungen zur Installation *höchsten Paketebene* ist entweder **Beispiel 1 – vollständige Installation** für den vollständigen Satz von Paketen oder **Beispiel 2: minimale Installation**  für die geringste Anzahl von Paketen, die für die kleinstmögliche Installation erforderlich.

1. Beginnen Sie für die R-Integration mit [MRO](#mro) , da es sich um eine erforderliche Komponente ist. R-Integration wird nicht ohne ihn installiert.

2. Führen Sie Befehle zur Installation über die Paket-Manager und die Syntax für das Betriebssystem an: 

   + [RedHat](#RHEL)
   + [Ubuntu](#ubuntu)
   + [SUSE](#suse)

## <a name="prerequisites"></a>Erforderliche Komponenten

+ Die Linux-Version muss [von SQL Server unterstützte](sql-server-linux-release-notes-2019.md#supported-platforms), aber nicht die Docker-Engine enthalten ist. Versionen werden unterstützt:

   + [Red Hat Enterprise Linux (RHEL)](quickstart-install-connect-red-hat.md)

   + [SUSE Enterprise Linux Server](quickstart-install-connect-suse.md)

   + [Ubuntu](quickstart-install-connect-ubuntu.md)

+ (Nur R) [Microsoft R Open](#mro) bietet der basisverteilung von R für die R-Funktion in SQL Server

+ Sie sollten ein Tool zum Ausführen von T-SQL-Befehlen haben. Ein Abfrage-Editor ist für die Konfiguration nach der Installation und Überprüfung erforderlich. Es wird empfohlen [Studio für Azure Data](https://docs.microsoft.com/sql/azure-data-studio/download?view=sql-server-2017#get-azure-data-studio-for-linux), kostenloser Download, die unter Linux ausgeführt wird.

<a name="mro"></a>

### <a name="microsoft-r-open-mro-installation"></a>Installation von Microsoft R Open (MRO)

Microsofts basisverteilung von R ist eine Voraussetzung für die Verwendung von RevoScaleR, MicrosoftML und anderen R-Paketen, die mit Machine Learning-Dienste installiert.

Die erforderliche Version handelt es sich um MRO 3.4.4.

Wählen Sie aus der beiden folgenden Methoden, um MRO zu installieren:

+ Herunterladen Sie der MRO-Tarball aus MRAN, entpacken Sie es und führen Sie das Skript "Install.sh" angezeigt. Führen Sie die [Installationsleitfäden auf MRAN](https://mran.microsoft.com/releases/3.4.4) ggf. diesen Ansatz.

+ Alternativ registrieren, die **packages.microsoft.com** Repository wie unten beschrieben werden, zum Installieren der drei Pakete, umfasst die Verteilung der MRO: Microsoft-R-öffnen-Mro, Microsoft-R-öffnen-Mkl und Microsoft-R-öffnen-Foreachiterators. 

Die folgenden Befehle registrieren Sie das Repository MRO bereitstellen. Nach der Registrierung werden die Befehle zum Installieren von anderen R-Paketen, z. B. Mssql-Mlservices-Mml-R, automatisch MRO als eine paketabhängigkeit enthalten.

#### <a name="mro-on-ubuntu"></a>MRO unter Ubuntu

```bash
# Install as root
sudo su

# Optionally, if your system does not have the https apt transport option
apt-get install apt-transport-https

# Add the **azure-cli** repo to your apt sources list
AZ_REPO=$(lsb_release -cs)

echo "deb [arch=amd64] https://packages.microsoft.com/repos/azure-cli/ $AZ_REPO main" | sudo tee /etc/apt/sources.list.d/azure-cli.list

# Set the location of the package repo the "prod" directory containing the distribution.
# This example specifies 16.04. Replace with 14.04 if you want that version
wget https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb

# Register the repo
dpkg -i packages-microsoft-prod.deb

# Update packages on your system (required), including MRO installation
sudo apt-get update
```

#### <a name="mro-on-rhel"></a>MRO unter RHEL

```bash
# Import the Microsoft repository key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Create local `azure-cli` repository
sudo sh -c 'echo -e "[azure-cli]\nname=Azure CLI\nbaseurl=https://packages.microsoft.com/yumrepos/azure-cli\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/azure-cli.repo'

# Set the location of the package repo at the "prod" directory
# The following command is for version 7.x
# For 6.x, replace 7 with 6 to get that version
rpm -Uvh https://packages.microsoft.com/config/rhel/7/packages-microsoft-prod.rpm

# Update packages on your system (optional)
yum update
```
#### <a name="mro-on-suse"></a>MRO unter SUSE

```bash
# Install as root
sudo su

# Set the location of the package repo at the "prod" directory containing the distribution
# This example is for SLES12, the only supported version of SUSE in Machine Learning Server
zypper ar -f https://packages.microsoft.com/sles/12/prod packages-microsoft-com

# Update packages on your system (optional)
zypper update
```

## <a name="package-list"></a>Liste der Pakete

Pakete sind auf einem Gerät Internetverbindung heruntergeladen und installiert, unabhängig von der Datenbank-Engine, die mit dem Paketinstaller für jedes Betriebssystem. Die folgende Tabelle beschreibt alle verfügbaren Pakete, aber für R und Python, geben Sie Pakete, die entweder die vollständige Funktion-Installation oder die minimale funktionsinstallation bereitstellen.

| Paketname | Applies-to | Description |
|--------------|----------|-------------|
|mssql-server-extensibility  | All | Das Erweiterungsframework zum Ausführen von R, Python oder Java-Code verwendet. |
|mssql-server-extensibility-java | Java | Java-Erweiterung für das Laden einer Java-ausführungsumgebung. Es gibt keine zusätzliche Bibliotheken oder Pakete für Java. |
| microsoft-openmpi  | Python, R | Nachrichtenübergabe, die Schnittstelle, die von den Revo *-Bibliotheken für die Parallelisierung unter Linux verwendet. |
| mssql-mlservices-python | Python | Open-Source-Verteilung von Anaconda und Python. |
|mssql-mlservices-mlm-py  | Python | *Vollständige Installation*. Bietet bereits trainierter Modelle für die Image-featurebereitstellung und Text standpunktanalyse zur Revoscalepy, Microsoftml lautet.| 
|mssql-mlservices-packages-py  | Python | *Minimalinstallation*. Stellt die Revoscalepy und Microsoftml bereit. <br/>Schließt vorab trainierte Modelle. | 
| [microsoft-r-open*](#mro) | R | Open-Source-Distribution von R, die aus drei Paketen besteht. |
|mssql-mlservices-mlm-r  | R | *Vollständige Installation*. Stellt bereits trainierter Modelle für die Image-featurebereitstellung und Text standpunktanalyse zur RevoScaleR, MicrosoftML lautet SqlRUtils, OlapR, bereit.| 
|mssql-mlservices-packages-r  | R | *Minimalinstallation*. Provides RevoScaleR, sqlRUtils, MicrosoftML, olapR. <br/>Schließt vorab trainierte Modelle. | 
|mssql-mlservices-mml-py  | Nur CTP 2.0-2.1 | Veraltet in CTP 2.2 aufgrund der Konsolidierung von Python-Paket in den Mssql-Mslservices-Python. Stellt die Revoscalepy bereit. Vortrainierte Modelle und Microsoftml ausgeschlossen.| 
|mssql-mlservices-mml-r  | Nur CTP 2.0-2.1 | Veraltet in CTP 2.2 aufgrund der Konsolidierung von R-Paket in den Mssql-Mslservices-Python. Provides RevoScaleR, sqlRUtils, olapR. Vortrainierte Modelle und MicrosoftML ausgeschlossen.  |

<a name="RHEL"></a>

## <a name="rhel-commands"></a>RHEL-Befehle

Sie können die sprachunterstützung installieren in beliebige Kombination aus (einzelne oder mehrere Sprachen) erforderlich. Für R und Python gibt es zwei Pakete zur Auswahl. Eine enthält alle verfügbare Funktionen, gekennzeichnet durch die *vollständige Installation*. Die alternative Auswahl schließt vorab trainierten Machine learning-Modelle und gilt als die *Minimalinstallation*.

> [!Tip]
> Führen Sie nach Möglichkeit `yum clean all` Pakete auf dem System vor der Installation zu aktualisieren.

### <a name="example-1----full-installation"></a>Beispiel 1: vollständige installation 

Enthält Open-Source-R und Python, Extensibility Framework, Microsoft-Openmpi,-Erweiterungen (R, Python, Java), mit Machine Learning-Bibliotheken und vorab trainierten Modellen für R und Python. 

```bash
# Install as root or sudo
# Add everything (all R, Python, Java)
# Be sure to include -9.4.6* in mlsservices package names
sudo yum install mssql-mlservices-mlm-py-9.4.6*
sudo yum install mssql-mlservices-mlm-r-9.4.6* 
sudo yum install mssql-server-extensibility-java
```

### <a name="example-2---minimum-installation"></a>Beispiel 2: Minimalinstallation 

Enthält Open Source-R und Python Extensibility Framework, Microsoft-Openmpi "," Core-Bibliotheken Revo * "und" Machine Learning-Bibliotheken für R und Python und die Java-Erweiterung ein. Schließt das vorab trainierte Modelle.

```bash
# Install as root or sudo
# Minimum install of R, Python, Java extensions
# Be sure to include -9.4.6* in mlsservices package names
sudo yum install mssql-mlservices-packages-py-9.4.6*
sudo yum install mssql-mlservices-packages-r-9.4.6*
sudo yum install mssql-server-extensibility-java
```

<a name="ubuntu"></a>

## <a name="ubuntu-commands"></a>Befehle für Ubuntu

Sie können die sprachunterstützung installieren in beliebige Kombination aus (einzelne oder mehrere Sprachen) erforderlich. Für R und Python gibt es zwei Pakete zur Auswahl. Eine enthält alle verfügbare Funktionen, gekennzeichnet durch die *vollständige Installation*. Die alternative Auswahl schließt vorab trainierten Machine learning-Modelle und gilt als die *Minimalinstallation*.

> [!Tip]
> Führen Sie nach Möglichkeit `apt-get update` Pakete auf dem System vor der Installation zu aktualisieren. Darüber hinaus möglicherweise einige Docker-Images von Ubuntu nicht die Option "apt-Transport-Https". Verwenden sie zur Installation `apt-get install apt-transport-https`.

<!---
### Prerequisite for 18.04

Running mssql-mlservices R libraries on Ubuntu 18.04 requires **libpng12** from the Linux Kernel archives. This package is no longer included in the standard distribution and must be installed manually. To get this library, run the following commands:

```bash
wget https://mirrors.kernel.org/ubuntu/pool/main/libp/libpng/libpng12-0_1.2.54-1ubuntu1_amd64.deb
dpkg -i libpng12-0_1.2.54-1ubuntu1_amd64.deb
```--->

### <a name="example-1----full-installation"></a>Beispiel 1: vollständige installation 

Enthält Open-Source-R und Python, Extensibility Framework, Microsoft-Openmpi,-Erweiterungen (R, Python, Java), mit Machine Learning-Bibliotheken und vorab trainierten Modellen für R und Python. 

```bash
# Install as root or sudo
# Add everything (all R, Python, Java)
# There is no asterisk in this full install
sudo apt-get install mssql-mlservices-mlm-py 
sudo apt-get install mssql-mlservices-mlm-r 
sudo apt-get install mssql-server-extensibility-java
```

### <a name="example-2---minimum-installation"></a>Beispiel 2: Minimalinstallation 

Enthält Open Source-R und Python Extensibility Framework, Microsoft-Openmpi "," Core-Bibliotheken Revo * "und" Machine Learning-Bibliotheken für R und Python und die Java-Erweiterung ein. Schließt das vorab trainierte Modelle. 

```bash
# Install as root or sudo
# Minimum install of R, Python, Java
# No aasterisk
sudo apt-get install mssql-mlservices-packages-py
sudo apt-get install mssql-mlservices-packages-r
sudo apt-get install mssql-server-extensibility-java
```

<a name="suse"></a>

## <a name="suse-commands"></a>SUSE-Befehle

Sie können die sprachunterstützung installieren in beliebige Kombination aus (einzelne oder mehrere Sprachen) erforderlich. Für R und Python gibt es zwei Pakete zur Auswahl. Eine enthält alle verfügbare Funktionen, gekennzeichnet durch die *vollständige Installation*. Die alternative Auswahl schließt vorab trainierten Machine learning-Modelle und gilt als die *Minimalinstallation*.

### <a name="example-1----full-installation"></a>Beispiel 1: vollständige installation 

Enthält Open-Source-R und Python, Extensibility Framework, Microsoft-Openmpi,-Erweiterungen (R, Python, Java), mit Machine Learning-Bibliotheken und vorab trainierten Modellen für R und Python. 

```bash
# Install as root or sudo
# Add everything (all R, Python, Java)
# Be sure to include -9.4.6* in mlsservices package names
sudo zypper install mssql-mlservices-mlm-py-9.4.6*
sudo zypper install mssql-mlservices-mlm-r-9.4.6* 
sudo zypper install mssql-server-extensibility-java
```

### <a name="example-2---minimum-installation"></a>Beispiel 2: Minimalinstallation 

Enthält Open Source-R und Python Extensibility Framework, Microsoft-Openmpi "," Core-Bibliotheken Revo * "und" Machine Learning-Bibliotheken für R und Python und die Java-Erweiterung ein. Schließt das vorab trainierte Modelle. 

```bash
# Install as root or sudo
# Minimum install of R, Python, Java extensions
# Be sure to include -9.4.6* in mlsservices package names
sudo zypper install mssql-mlservices-packages-py-9.4.6*
sudo zypper install mssql-mlservices-packages-r-9.4.6*
sudo zypper install mssql-server-extensibility-java
```

## <a name="post-install-config-required"></a>Nach der Installation Config (erforderlich)

Zusätzliche Konfiguration ist in erster Linie durch die [Mssql-Conf-Tool](sql-server-linux-configure-mssql-conf.md).


1. Fügen Sie der Mssql-Benutzerkonto zum Ausführen von SQL Server-Dienst hinzu. Dies ist erforderlich, wenn Sie das Setup nicht zuvor ausgeführt haben.

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

2. Akzeptieren Sie die Lizenzbedingungen für Open-Source-R und Python. Es gibt mehrere Möglichkeiten zur Verfügung. Wenn Sie zuvor, SQL Server-Lizenzierung akzeptiert und nun die R- oder Python-Erweiterungen hinzufügen, ist der folgende Befehl Ihre Zustimmung zu seinen Bedingungen:

   ```bash
   # Run as SUDO or root
   # Use set + EULA 
   sudo /opt/mssql/bin/mssql-conf set EULA accepteulaml Y
   ```

   Eine alternative Workflows ist, dass wenn Sie die SQL Server-Datenbank-Engine, die lizenzveREINBARUNG noch nicht akzeptiert haben, Setup die Mssql-Mlservices-Pakete und die Aufforderung zur Zustimmung zu EULAS erkennt beim `mssql-conf setup` ausgeführt wird. Weitere Informationen zu Endbenutzer-Lizenzvertrag-Parameter, finden Sie unter [SQL-Server konfigurieren, mit der Mssql-Conf-Tool](sql-server-linux-configure-mssql-conf.md#mlservices-eula).

3. Aktivieren Sie ausgehender Netzwerkzugriff. Ausgehender Netzwerkzugriff ist standardmäßig deaktiviert. Um ausgehende Anforderungen zu aktivieren, legen Sie die "Outboundnetworkaccess" boolesche Eigenschaft, die mit dem Mssql-Conf-Tool. Weitere Informationen finden Sie unter [Konfigurieren von SQL Server unter Linux mit Mssql-Conf](sql-server-linux-configure-mssql-conf.md#mlservices-outbound-access).

   ```bash
   # Run as SUDO or root
   # Enable outbound requests over the network
   sudo /opt/mssql/bin/mssql-conf set extensibility outboundnetworkaccess 1
   ```

4. Für R feature Integration nur, legen die **MKL_CBWR** -Umgebungsvariable so fest, [sicherstellen von konsistenten Ausgabe](https://software.intel.com/articles/introduction-to-the-conditional-numerical-reproducibility-cnr) von Intel Math Kernel Library (MKL) Berechnungen.

   + Bearbeiten oder erstellen Sie eine Datei namens **bash_profile** durch Hinzufügen der Zeile, in Ihrem Basisverzeichnis des Benutzers, `export MKL_CBWR="AUTO"` in die Datei.

   + Führen Sie die Datei durch Eingabe `source .bash_profile` in einer Bash-Eingabeaufforderung.

5. Neustart der SQL Server Launchpad-Dienst und der Datenbank-Engine-Instanz, um die aktualisierten Werte aus der INI-Datei zu lesen. Eine Neustart-Nachricht daran erinnert Sie jedes Mal, wenn eine Erweiterbarkeit Einstellung geändert wird.  

   ```bash
   systemctl restart mssql-launchpadd

   systemctl restart mssql-server.service
   ```

6. Aktivieren Sie die Ausführung des externen Skripts mithilfe von Azure Data Studio oder einem anderen Tool wie SQL Server Management Studio (nur Windows), die Transact-SQL ausgeführt wird. 

   ```bash
   EXEC sp_configure 'external scripts enabled', 1 
   RECONFIGURE WITH OVERRIDE 
   ```

7. Starten Sie den Launchpad-Dienst neu.

## <a name="verify-installation"></a>Überprüfen der Installation

R-Bibliotheken (MicrosoftML, RevoScaleR usw.) finden Sie unter `/opt/mssql/mlservices/libraries/RServer`.

Python-Bibliotheken (Microsoftml "und" Revoscalepy) finden Sie unter `/opt/mssql/mlservices/libraries/PythonServer`.

Integration der Java-Funktion enthält keine Bibliotheken, Sie können jedoch ausführen `grep -r JAVA_HOME /etc` , bestätigen die JAVA_HOME-Umgebungsvariable erstellen.

Führen Sie zum Überprüfen der Installation eines T-SQL-Skripts, das eine gespeicherte Prozedur aufrufen, R oder Python ausgeführt wird. Für diese Aufgabe benötigen Sie ein Abfragetool. Azure Data Studio ist eine gute Wahl. Andere häufig verwendete Tools wie SQL Server Management Studio oder PowerShell sind nur für Windows. Wenn Sie einen Windows-Computer mit diesen Tools verfügen, verwenden Sie es für die Verbindung zu Ihrer Linux-Installation der Datenbank-Engine.

Führen Sie den folgenden SQL-Befehl, um die Ausführung von R in SQL Server zu testen. Wenn das Skript nicht ausgeführt wird, versuchen Sie, einen Neustart des Diensts, `sudo systemctl restart mssql-server.service`.

```r
EXEC sp_execute_external_script   
@language =N'R', 
@script=N' 
OutputDataSet <- InputDataSet', 
@input_data_1 =N'SELECT 1 AS hello' 
WITH RESULT SETS (([hello] int not null)); 
GO 
```
 
Führen Sie den folgenden SQL-Befehl, um die Ausführung von Python in SQL Server zu testen. 
 
```python
EXEC sp_execute_external_script  
@language =N'Python', 
@script=N' 
OutputDataSet = InputDataSet; 
', 
@input_data_1 =N'SELECT 1 AS hello' 
WITH RESULT SETS (([hello] int not null)); 
GO 
```

<a name="install-all"></a>

## <a name="chained-combo-install"></a>Installieren von verketteten "Kombinationsfeld"

Sie können installieren und konfigurieren die Datenbank-Engine und Machine Learning-Dienste in einer Prozedur, durch Anfügen von R, Python oder Java-Pakete und Parameter für einen Befehl, der die Datenbank-Engine installiert. 

1. Installieren Sie für die Integration von R, [Microsoft R Open](#mro) als erforderliche Komponente. Überspringen Sie diesen Schritt, wenn Sie nicht die R-Funktion installieren.

2. Geben Sie eine Befehlszeile, die den Datenbank-Engine sowie die Sprachfeatures für die Erweiterung enthält.

  Sie können eine einzelne Funktion, z. B. Java-Integration mit einer Datenbank-Engine installiert hinzufügen.

  ```bash
  sudo yum install -y mssql-server mssql-server-extensibility-java 
  ```

  Oder fügen Sie alle Erweiterungen (Java, R, Python).

  ```bash
  sudo yum install -y mssql-server mssql-server-extensibility-java mssql-mlservices-packages-r-9.4.6* mssql-mlservices-packages-py-9.4.6*
  ```

3. Zustimmen Sie Lizenzverträgen, und schließen Sie die Konfiguration nach der Installation. Verwenden der **Mssql-Conf** Tool für diese Aufgabe.

  ```bash
  sudo /opt/mssql/bin/mssql-conf setup
  ```

  Sie werden zum Akzeptieren des Lizenzvertrags für die Datenbank-Engine, wählen Sie eine Edition und Festlegen des Administratorkennworts aufgefordert werden. Sie werden außerdem aufgefordert, zum Akzeptieren des Lizenzvertrags für Machine Learning-Dienste.

4. Starten Sie den Dienst neu, wenn Sie dazu aufgefordert werden.

  ```bash
  sudo systemctl restart mssql-server.service
  ```

## <a name="unattended-installation"></a>Für die unbeaufsichtigte installation

Mithilfe der [unbeaufsichtigte Installation](https://docs.microsoft.com/sql/linux/sql-server-linux-setup?view=sql-server-2017#unattended) fügen Sie die Pakete für die Mssql-Mlservices und in den Lizenzbedingungen für die Datenbank-Engine.

Denken Sie daran, dass Setup- oder das Mssql-Conf-Tool für den Lizenzvertrag zu akzeptieren auffordert. Wenn Sie bereits SQL Server-Datenbank-Engine konfiguriert und der Endbenutzer-Lizenzvertrag akzeptiert, verwenden Sie eine der Endbenutzer-Lizenzvertrag Mlservices-spezifische Parameter für die Open-Source-R und Python-Distributionen:

```bash
sudo /opt/mssql/bin/mssql-conf setup accept-eula-ml
```

In allen möglichen Permutationen der Zustimmung zu EULAS dokumentiert sind [Konfigurieren von SQL Server unter Linux mit der Mssql-Conf-Tool](sql-server-linux-configure-mssql-conf.md#mlservices-eula).

## <a name="offline-installation"></a>Offlineinstallation

Führen Sie die [Offline-Installation](sql-server-linux-setup.md#offline) Anweisungen für die Schritte zum Installieren der Pakete. Suchen Sie Ihre Download-Seite, und dann herunterladen Sie bestimmte Pakete, die mithilfe der folgenden Liste der Pakete.

> [!Tip]
> Einige der Paket-Tools bieten, dass Befehle, die Ihnen helfen können paketabhängigkeiten bestimmen. Verwenden Sie für Yum, `sudo yum deplist [package]`. Für Ubuntu verwenden `sudo apt-get install --reinstall --download-only [package name]` gefolgt von `dpkg -I [package name].deb`.


#### <a name="download-site"></a>Downloadsite

Sie können Pakete aus [ https://packages.microsoft.com/ ](https://packages.microsoft.com/). Alle Pakete für R, Python und Java Mlservices sind zusammen angeordnet, mit der Datenbank-Engine-Paket. Basisversion für die Pakete Mlservices ist 9.4.5. handelt (für CTP 2.0) 9.4.6 (für CTP 2.1 und höher). Beachten Sie, die in der Microsoft-R-Open-Pakete sind eine [anderen Repository](#mro).

#### <a name="rhel7-paths"></a>RHEL/7-Pfade

|||
|--|----|
| MSSQL/Mlservices Pakete | [https://packages.microsoft.com/rhel/7/mssql-server-preview/](https://packages.microsoft.com/rhel/7/mssql-server-preview/) |
| Microsoft-R-Open-Pakete | [https://packages.microsoft.com/rhel/7/prod/](https://packages.microsoft.com/rhel/7/prod/) | 


#### <a name="ubuntu1604-paths"></a>Ubuntu 16.04/Pfade

|||
|--|----|
| MSSQL/Mlservices Pakete | [https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/) |
| Microsoft-R-Open-Pakete | [https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/](https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/) | 

#### <a name="sles12-paths"></a>SLES 12/Pfade

|||
|--|----|
| MSSQL/Mlservices Pakete | [https://packages.microsoft.com/sles/12/mssql-server-preview/](https://packages.microsoft.com/sles/12/mssql-server-preview/) |
| Microsoft-R-Open-Pakete | [https://packages.microsoft.com/sles/12/prod/](https://packages.microsoft.com/sles/12/prod/) | 

#### <a name="package-list"></a>Liste der Pakete

Je nachdem welche Erweiterungen möchten Sie verwenden, laden die Pakete, die für eine bestimmte Sprache erforderlich. Genauen Dateinamen Plattforminformationen in das Suffix einschließen sollten, aber die folgenden Dateinamen nahe genug, um zu bestimmen, welche Dateien erhalten Sie.

```
# Core packages 
mssql-server-15.0.1000
mssql-server-extensibility-15.0.1000

# Java
mssql-server-extensibility-java-15.0.1000

# R
microsoft-openmpi-3.0.0
microsoft-r-open-foreachiterators-3.4.4
microsoft-r-open-mkl-3.4.4
microsoft-r-open-mro-3.4.4
mssql-mlservices-packages-r-9.4.6.523
mssql-mlservices-mlm-r-9.4.6.523
mssql-mlservices-mml-r-9.4.6.523

# Python
microsoft-openmpi-3.0.0
mssql-mlservices-python-9.4.6.523
mssql-mlservices-packages-py-9.4.6.523
mssql-mlservices-mlm-py-9.4.6.523
mssql-mlservices-mml-py-9.4.6.523
```

#### <a name="package-list-for-original-ctp-20-and-21"></a>Liste der Pakete für die ursprünglichen CTP 2.0 und 2.1

CTP 2.2 entfernt **Mssql-Mlservices-Mlm-Py** und **Mssql-Mlservices-Mlm-R** aufgrund der Konsolidierung von Paket in **Mssql-Mlservices-Pakete-Py** und **Mssql-Mlservices-Pakete-R**bzw.

Wenn Sie speziell die ursprünglichen CTP-Version 2.0 oder 2.1 Pakete benötigen, laden Sie die folgenden Pakete herunter:

* Laden Sie für die CTP-Version 2.0 Paketversionen 9.4.5. handelt

* Laden Sie für die CTP-Version 2.1 Paketversionen 9.4.6.237


## <a name="add-more-rpython-packages"></a>Weitere R/Python-Pakete hinzufügen 
 
Sie können andere R- und Python-Pakete installieren und verwenden diese im Skript, das für SQL Server-2019 ausgeführt wird.

### <a name="r-packages"></a>R-Pakete 
 
1. Starten einer R-Sitzungs.

   ```r
   # sudo /opt/mssql/mlservices/bin/R/R 
   ```

2. Installieren Sie ein R-Paket namens ["Klebstoff"](https://mran.microsoft.com/package/glue) Paketinstallation testen.

   ```r
   # install.packages("glue",lib="/opt/mssql/mlservices/libraries/RServer") 
   ```
   Alternativ können Sie ein R-Paket über die Befehlszeile installieren. 

   ```r
   # sudo /opt/mssql/mlservices/bin/R/R CMD INSTALL -l /opt/mssql/mlservices/libraries/RServer glue_1.1.1.tar.gz 
   ```

3. Importieren Sie das R-Paket in [Sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

   ```r
   EXEC sp_execute_external_script  
   @language = N'R', 
   @script = N'library(glue)' 
   ```

### <a name="python-packages"></a>Python-Pakete 
 
1. Installieren Sie ein Python-Paket namens [Httpie](https://httpie.org/) mithilfe von Pip. 

   ```python
   # sudo /opt/mssql/mlservices/bin/python/python -m pip install httpie 
   ``` 

2. Importieren Sie das Python-Paket in [Sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).
 
   ```python
   EXEC sp_execute_external_script  
   @language = N'Python',  
   @script = N'import httpie' 
   ```

## <a name="limitations-in-ctp-releases"></a>Einschränkungen in der CTP-Versionen

Integration von R, Python und Java unter Linux ist immer noch in der aktiven Entwicklung. Die folgenden Features sind in der Vorschauversion noch nicht aktiviert.

+ Implizite Authentifizierung ist zu diesem Zeitpunkt an, was bedeutet, dass Sie über ein in Ausführung befindlichen R- oder Python-Skript den Zugriff auf Daten oder andere Ressourcen an den Server verbinden können derzeit nicht verfügbar in Machine Learning-Dienste unter Linux. 

+ [CREATE EXTERNAL LIBRARY](../t-sql/statements/create-external-library-transact-sql.md) (zum Speichern der R-Pakete in der Datenbank) ist derzeit nicht verfügbar für Linux und Python nicht unterstützt.  

### <a name="resource-governance"></a>Ressourcenkontrolle

Es gibt Parität zwischen Linux und Windows für [Ressourcenkontrolle](../t-sql/statements/create-external-resource-pool-transact-sql.md) für externe Ressourcenpools, aber die Statistiken für [sys.dm_resource_governor_external_resource_pools](../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pools.md) derzeit andere Einheiten unter Linux. Einheiten werden in einer zukünftigen CTP-Version ausgerichtet.
 
| Spaltenname   | Description | Der Wert unter Linux | 
|---------------|--------------|---------------|
|peak_memory_kb | Die Höchstmenge an Arbeitsspeicher, die für den Ressourcenpool verwendet werden soll. | Unter Linux ist diese Statistik des Arbeitsspeichersubsystems CGroups, stammen, in denen der Wert memory.max_usage_in_bytes |
|write_io_count | Die Gesamtanzahl Schreibvorgänge seit dem Zurücksetzen der ressourcenkontrollenstatistiken wurden ausgegeben. | Unter Linux ist diese Statistik über das Subsystem für CGroups Blkio, stammt, in denen der Wert in der Zeile schreiben blkio.throttle.io_serviced | 
|read_io_count | Die Gesamtanzahl Lesevorgänge seit dem Zurücksetzen der ressourcenkontrollenstatistiken wurden ausgegeben. | Unter Linux ist diese Statistik über das Subsystem für CGroups Blkio, stammt, in dem Wert der Zeile lesen blkio.throttle.io_serviced | 
|total_cpu_kernel_ms | Die kumulierte CPU-Benutzer Kernelzeit in Millisekunden seit dem Zurücksetzen der ressourcenkontrollenstatistiken wurden. | Unter Linux ist diese Statistik über das Subsystem für CGroups Cpuacct, stammt, in denen der Wert für die Benutzerzeile cpuacct.stat |  
|total_cpu_user_ms | Die kumulierte CPU-Benutzerzeit in Millisekunden seit dem Zurücksetzen der ressourcenkontrollenstatistiken wurden.| Unter Linux ist diese Statistik über das Subsystem für CGroups Cpuacct, stammt, in denen der Wert auf den Wert der System-Zeile cpuacct.stat | 
|active_processes_count | Die Anzahl von externen Prozessen, die zum Zeitpunkt der Anforderung ausgeführt wird.| Unter Linux ist diese Statistik über das Subsystem für GGroups Pids, stammt, in denen der Wert pids.current | 

## <a name="next-steps"></a>Nächste Schritte

R-Entwickler können mit einigen einfachen Beispielen beginnen, und die Grundlagen der Funktionsweise von R mit SQL Server. Der nächste Schritt ist finden Sie in den folgenden Links:

+ [Tutorial: Run R in T-SQL](../advanced-analytics/tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)
+ [Tutorial: Datenbankinterne Analysen für R-Entwickler](../advanced-analytics/tutorials/sqldev-in-database-r-for-sql-developers.md)

Python-Entwickler erfahren, wie Python mit SQL Server verwenden, indem Sie die folgenden in diesen Tutorials:

+ [Tutorial: Ausführen von Python in T-SQL](../advanced-analytics/tutorials/run-python-using-t-sql.md)
+ [Tutorial: Datenbankinterne Analysen für Python-Entwickler](../advanced-analytics/tutorials/sqldev-in-database-python-for-sql-developers.md)

Beispiele für Machine Learning, die auf realen Szenarien basieren, finden Sie unter [Machine learning-Tutorials](../advanced-analytics/tutorials/machine-learning-services-tutorials.md).
