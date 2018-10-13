---
title: Installieren von SQL Server Machine Learning-Dienste (R, Python, Java) unter Linux | Microsoft-Dokumentation
description: Dieser Artikel beschreibt, wie zum Installieren von SQL Server Machine Learning Services (R, Python, Java) auf Red Hat und Ubuntu.
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.date: 10/09/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: machine-learning
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 8433f705b41782c61950cb74f76f694d61cd548d
ms.sourcegitcommit: 485e4e05d88813d2a8bb8e7296dbd721d125f940
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/11/2018
ms.locfileid: "49100451"
---
# <a name="install-sql-server-2019-machine-learning-services-r-python-java-on-linux"></a>Installieren von SQL Server 2019 Machine Learning-Diensten (R, Python, Java) unter Linux

[SQL Server Machine Learning Services](../advanced-analytics/what-is-sql-server-machine-learning.md) auf Linux-Betriebssysteme, die ab dieser Preview-Version von SQL Server-2019 ausgeführt wird. Führen Sie die Schritte in diesem Artikel, die Programmiersprache Java-Erweiterung oder das Machine learning-Erweiterungen für R und Python installieren. 

Machine learning und Programmieren von Erweiterungen sind ein Add-on für die Datenbank-Engine. Zwar Sie können [installieren Sie die Datenbank-Engine und Machine Learning-Dienste gleichzeitig](#install-all), es ist eine bewährte Methode zum Installieren und konfigurieren die SQL Server-Datenbank-Engine zuerst, damit Sie Probleme beheben können, bevor Sie weitere hinzufügen Komponenten. 

Speicherort des Pakets der R, Python und Java-Erweiterungen sind in den SQL Server Linux-Quell-Repositorys. Wenn Sie bereits konfiguriert Quellcode-Repositorys für die Datenbank-Engine installieren, können Sie die Mssql-Mlservices Paketbefehle-Installation anhand der gleichen Repository-Registrierung ausführen.

## <a name="prerequisites"></a>Erforderliche Komponenten

+ Linux-Betriebssystem muss [von SQL Server unterstützte](sql-server-linux-release-notes-2019.md#supported-platforms), lokal oder in einem Docker-Container ausgeführt.

+ Eine Instanz von SQL Server-Datenbankmodul 2019 benötigen Sie für: 

   + [Red Hat Enterprise Linux (RHEL)](quickstart-install-connect-red-hat.md)

   + [SUSE Enterprise Linux-Server](quickstart-install-connect-suse.md)

   + [Ubuntu](quickstart-install-connect-ubuntu.md)

+ Für R nur [Microsoft R Open](#mro) für Mssql-Mlsservices R-Pakete. 

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
```
#### <a name="mro-on-suse"></a>MRO unter SUSE

```bash
# Install as root
sudo su

# Set the location of the package repo at the "prod" directory containing the distribution
# This example is for SLES12, the only supported version of SUSE in Machine Learning Server
zypper ar -f https://packages.microsoft.com/sles/12/prod packages-microsoft-com

# Update packages on your system:
zypper update
```

## <a name="package-list"></a>Liste der Pakete

Pakete sind auf einem Gerät Internetverbindung heruntergeladen und installiert, unabhängig von der Datenbank-Engine, die mit dem Paketinstaller für jedes Betriebssystem. Die folgende Tabelle beschreibt alle verfügbaren Pakete für die Internetverbindung installiert werden, müssen Sie allerdings nur *eine* R- oder Python-Paket um eine bestimmte Kombination von Funktionen zu erhalten.

| Paketname | Gilt für | Description |
|--------------|----------|-------------|
|MSSQL-Server-Erweiterbarkeit  | All | Das Erweiterungsframework zum Ausführen von R, Python oder Java-Code verwendet. |
|MSSQL-Server-Erweiterbarkeit – java | Java | Java-Erweiterung für das Laden einer Java-ausführungsumgebung. Es gibt keine zusätzliche Bibliotheken oder Pakete für Java. |
| Microsoft-openmpi  | Python, R | Nachrichtenübergabe, die Schnittstelle, die von den Revo *-Bibliotheken für die Parallelisierung unter Linux verwendet. |
| [Microsoft-R-Open *](#mro) | R | Open-Source-Distribution von R, die aus drei Paketen besteht. |
| MSSQL-Mlservices-python | Python | Open-Source-Verteilung von Anaconda und Python. |
|MSSQL-Mlservices-Mlm-py  | Python | Vollständige Installation. Bietet bereits trainierter Modelle für die Image-featurebereitstellung und Text standpunktanalyse zur Revoscalepy, Microsoftml lautet.| 
|MSSQL-Mlservices-Mml-py  | Python | Partielle installieren. Stellt die Revoscalepy, Microsoftml bereit. <br/>Schließt vorab trainierte Modelle. | 
|MSSQL-Mlservices-Pakete-py  | Python | Partielle installieren. Stellt die Revoscalepy bereit. <br/>Vortrainierte Modelle und Microsoftml ausgeschlossen. | 
|MSSQL-Mlservices-Mlm-r  | R | Vollständige Installation. Stellt bereits trainierter Modelle für die Image-featurebereitstellung und Text standpunktanalyse zur RevoScaleR, MicrosoftML lautet SqlRUtils, OlapR, bereit.| 
|MSSQL-Mlservices-Mml-r  | R | Partielle installieren. Bietet RevoScaleR, MicrosoftML, SqlRUtils, OlapR. <br/>Schließt vorab trainierte Modelle.  |
|MSSQL-Mlservices-Pakete-r  | R | Partielle installieren. Stellt RevoScaleR, SqlRUtils, OlapR bereit. <br/>Vortrainierte Modelle und MicrosoftML ausgeschlossen. | 

<a name="RHEL"></a>

## <a name="rhel-commands"></a>RHEL-Befehle

Installieren Sie alle *eine* R-Paket, sowie alle *eine* Python-Paket und Java, wenn Sie diese Funktion soll. Jedes R und Python-Paket enthält eine Reihe von Features. Wählen Sie das Paket, das den Satz von bereitstellt, den Sie benötigen. Abhängige Pakete werden automatisch eingefügt.

> [!Tip]
> Führen Sie nach Möglichkeit `yum clean all` Pakete auf dem System vor der Installation zu aktualisieren.

### <a name="example-1----full-installation"></a>Beispiel 1: vollständige installation 

Enthält Open-Source-R und Python, Extensibility Framework, Microsoft-Openmpi,-Erweiterungen (R, Python, Java), mit Machine Learning-Bibliotheken und vorab trainierten Modellen für R und Python. Ersatz für R und Python, wenn Sie zwischen vollständigen und minimalen-Installation – z. B. Machine Learning-Bibliotheken jedoch ohne die vorab trainierte Modelle - möchte `mssql-mlservices-mml-r-9.4.5*` und `mssql-mlservices-mml-py-9.4.5*` stattdessen.

```bash
# Install as root or sudo
# Add everything (all R, Python, Java)
# Be sure to include -9.4.5* in mlsservices package names
sudo yum install mssql-mlservices-mlm-py-9.4.5*
sudo yum install mssql-mlservices-mlm-r-9.4.5* 
sudo yum install mssql-server-extensibility-java
```

### <a name="example-2---minimum-installation"></a>Beispiel 2: Minimalinstallation 

Enthält Open Source-R und Python, Extensibility Framework, Microsoft-Openmpi, Core Revo * Bibliotheken für R und Python, Java-Erweiterung. Schließt vorab trainierte Modelle und Machine learning-Bibliotheken für R und Python. 

```bash
# Install as root or sudo
# Minimum install of R, Python, Java extensions
# Be sure to include -9.4.5* in mlsservices package names
sudo yum install mssql-mlservices-packages-py-9.4.5*
sudo yum install mssql-mlservices-packages-r-9.4.5*
sudo yum install mssql-server-extensibility-java
```

<a name="ubuntu"></a>

## <a name="ubuntu-commands"></a>Befehle für Ubuntu

Installieren Sie alle *eine* R-Paket, sowie alle *eine* Python-Paket und Java, wenn Sie diese Funktion soll. Jedes R und Python-Paket enthält eine Reihe von Features. Wählen Sie das Paket, das den Satz von bereitstellt, den Sie benötigen. Abhängige Pakete werden automatisch eingefügt.

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

Enthält Open-Source-R und Python, Extensibility Framework, Microsoft-Openmpi,-Erweiterungen (R, Python, Java), mit Machine Learning-Bibliotheken und vorab trainierten Modellen für R und Python. Für R und Python, sollten Sie etwa zwischen vollständigen und minimalen – z. B. Machine Learning-Bibliotheken jedoch ohne die vorab trainierte Modelle - installieren ersetzen Sie Mssql-Mlservices-Mml-R "und" Mssql-Mlservices-Mml-Py stattdessen.

```bash
# Install as root or sudo
# Add everything (all R, Python, Java)
# There is no asterisk in this full install
sudo apt-get install mssql-mlservices-mlm-py 
sudo apt-get install mssql-mlservices-mlm-r 
sudo apt-get install mssql-server-extensibility-java
```

### <a name="example-2---minimum-installation"></a>Beispiel 2: Minimalinstallation 

Enthält Open Source-R und Python, Extensibility Framework, Microsoft-Openmpi, Core Revo * Bibliotheken für R und Python, Java-Erweiterung. Schließt vorab trainierte Modelle und Machine learning-Bibliotheken für R und Python. 

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

Installieren Sie alle *eine* R-Paket, sowie alle *eine* Python-Paket und Java, wenn Sie diese Funktion soll. Jedes R und Python-Paket enthält eine Reihe von Features. Wählen Sie das Paket, das den Satz von bereitstellt, den Sie benötigen. Abhängige Pakete werden automatisch eingefügt. 

### <a name="example-1----full-installation"></a>Beispiel 1: vollständige installation 

Enthält Open-Source-R und Python, Extensibility Framework, Microsoft-Openmpi,-Erweiterungen (R, Python, Java), mit Machine Learning-Bibliotheken und vorab trainierten Modellen für R und Python. Ersatz für R und Python, wenn Sie zwischen vollständigen und minimalen-Installation – z. B. Machine Learning-Bibliotheken jedoch ohne die vorab trainierte Modelle - möchte `mssql-mlservices-mml-r-9.4.5*` und `mssql-mlservices-mml-py-9.4.5*` stattdessen.

```bash
# Install as root or sudo
# Add everything (all R, Python, Java)
# Be sure to include -9.4.5* in mlsservices package names
sudo zypper install mssql-mlservices-mlm-py-9.4.5*
sudo zypper install mssql-mlservices-mlm-r-9.4.5* 
sudo zypper install mssql-server-extensibility-java
```

### <a name="example-2---minimum-installation"></a>Beispiel 2: Minimalinstallation 

Enthält Open Source-R und Python, Extensibility Framework, Microsoft-Openmpi, Core Revo * Bibliotheken für R und Python, Java-Erweiterung. Schließt vorab trainierte Modelle und Machine learning-Bibliotheken für R und Python. 

```bash
# Install as root or sudo
# Minimum install of R, Python, Java extensions
# Be sure to include -9.4.5* in mlsservices package names
sudo zypper install mssql-mlservices-packages-py-9.4.5*
sudo zypper install mssql-mlservices-packages-r-9.4.5*
sudo zypper install mssql-server-extensibility-java
```

## <a name="post-install-config-required"></a>Nach der Installation Config (erforderlich)

Zusätzliche Konfiguration ist in erster Linie durch die [Mssql-Conf-Tool](sql-server-linux-configure-mssql-conf.md).


1. Fügen Sie das Mssql-Benutzerkonto verwendet, um den SQL Server Launchpad-Dienst auszuführen.

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

3. Starten der SQL Server Launchpad-Dienst und die Datenbank-Engine-Instanz neu.

  ```bash
  systemctl restart mssql-launchpadd

  systemctl restart mssql-server.service
  ```

4. Aktivieren Sie die Ausführung des externen Skripts in SQL Server Management Studio oder ein anderes Tool, das Transact-SQL ausgeführt wird. 

  ```bash
  EXEC sp_configure 'external scripts enabled', 1 
  RECONFIGURE WITH OVERRIDE 
  ```

## <a name="verify-installation"></a>Überprüfen der Installation

R-Bibliotheken (MicrosoftML, RevoScaleR usw.) finden Sie unter `/opt/mssql/mlservices/libraries/RServer`.

Python-Bibliotheken (Microsoftml "und" Revoscalepy) finden Sie unter `/opt/mssql/mlservices/libraries/PythonServer`.

Verwenden ein SQL Server-Abfragetool, führen Sie den folgenden SQL-Befehl, um die Ausführung von R in SQL Server zu testen. Wenn das Skript nicht ausgeführt wird, versuchen Sie, einen Neustart des Diensts, `sudo systemctl restart mssql-server`.

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

## <a name="chained-installation"></a>Verkettete installation

Sie können installieren und konfigurieren die Datenbank-Engine und Machine Learning-Dienste in einer Prozedur, durch Anfügen von R, Python oder Java-Pakete und Parameter für einen Befehl, der die Datenbank-Engine installiert. 

Im folgende Beispiel wird eine "Template"-Darstellung der wie eine kombinierte Paketinstallation mithilfe des Yum-Paket-Managers aussieht. Es wird die Datenbank-Engine installiert und fügt die Erweiterung der Java-Sprache, die dem Extensibility Framework-Paket als Abhängigkeit abruft.

```bash
sudo yum install -y mssql-server mssql-server-extensibility-java 
```

Ein Beispiel für erweiterte mit allen Erweiterungen (Java, R, Python) sieht folgendermaßen aus:

```bash
sudo yum install -y mssql-server mssql-server-extensibility-java mssql-mlservices-packages-r-9.4.5* mssql-mlservices-packages-py-9.4.5*
```

Mit Ausnahme der R-Voraussetzungen werden alle in diesem Beispiel verwendeten Pakete im selben Pfad gefunden. Hinzufügen von R erfordert, dass Sie [registrieren das Microsoft-R-Open-paketrepository](#mro) als ein zusätzlicher Schritt MRO zu erhalten. MRO ist eine Voraussetzung für die R-Erweiterungen. Auf einem Computer mit dem Internet verbunden ist ist MRO abgerufen und installiert automatisch als Teil der R-Erweiterung, vorausgesetzt, dass Sie beide Repositorys konfiguriert.

Nach der Installation, denken Sie daran, die Mssql-Conf-Tool verwenden, konfigurieren Sie die gesamte Installation, und akzeptieren die Lizenzbedingungen. Vom nicht akzeptierten EULAs für Open Source-R und Python-Komponenten werden automatisch erkannt, und Sie werden aufgefordert, die sie zusammen mit den Endbenutzer-Lizenzvertrag für SQL Server zu akzeptieren.

```bash
sudo /opt/mssql/bin/mssql-conf setup MSSQL_PID=Developer 
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

Sie können Pakete aus [ https://packages.microsoft.com/ ](https://packages.microsoft.com/). Alle Pakete für R, Python und Java Mlservices sind zusammen angeordnet, mit der Datenbank-Engine-Paket. Basisversion für die Pakete Mlservices ist 9.4.5. handelt. Die Micrososoft-R-Open-Pakete sind in einem anderen Ordner.

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
| MSSQL/Mlservices Pakete | [ https://packages.microsoft.com/sles/12/mssql-server-preview/](https://packages.microsoft.com/sles/12/mssql-server-preview/) |
| Microsoft-R-Open-Pakete | [https://packages.microsoft.com/sles/12/prod/](https://packages.microsoft.com/sles/12/prod/) | 

#### <a name="package-list"></a>Liste der Pakete

Je nachdem welche Erweiterungen möchten Sie verwenden, laden die Pakete, die für eine bestimmte Sprache erforderlich. Genaue Dateinamen enthalten Informationen zur sollten, aber die folgenden Dateinamen nahe genug ist, für Sie bestimmen, welche Dateien abrufen.

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
mssql-mlservices-packages-r-9.4.5
mssql-mlservices-mlm-r-9.4.5
mssql-mlservices-mml-r-9.4.5

# Python
microsoft-openmpi-3.0.0
mssql-mlservices-python-9.4.5
mssql-mlservices-packages-py-9.4.5
mssql-mlservices-mlm-py-9.4.5
mssql-mlservices-mml-py-9.4.5 
```

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

## <a name="limitations-in-ctp-20"></a>Einschränkungen in CTP 2.0

Die folgenden Einschränkungen gelten in dieser CTP-Version.

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

+ [Tutorial: Ausführen von R in T-SQL](../advanced-analytics/tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)
+ [Tutorial: Datenbankinterne Analysen für R-Entwickler](../advanced-analytics/tutorials/sqldev-in-database-r-for-sql-developers.md)

Python-Entwickler erfahren, wie Python mit SQL Server verwenden, indem Sie die folgenden in diesen Tutorials:

+ [Tutorial: Ausführen von Python in T-SQL](../advanced-analytics/tutorials/run-python-using-t-sql.md)
+ [Tutorial: Datenbankinterne Analysen für Python-Entwickler](../advanced-analytics/tutorials/sqldev-in-database-python-for-sql-developers.md)

Beispiele für Machine Learning, die auf realen Szenarien basieren, finden Sie unter [Machine learning-Tutorials](../advanced-analytics/tutorials/machine-learning-services-tutorials.md).
