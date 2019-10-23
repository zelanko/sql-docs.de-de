---
title: Installieren von SQL Server Machine Learning Services (Python, R) unter Linux
description: 'Erfahren Sie, wie SQL Server Machine Learning Services (Python und R) unter Linux installiert wird: Red Hat, Ubuntu und SUSE.'
author: dphansen
ms.author: davidph
ms.reviewer: vanto
manager: cgronlun
ms.date: 09/23/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: machine-learning
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: b3d2fb6c05a078e222a68e8de8998d4edff3c1a8
ms.sourcegitcommit: 2f56848ec422845ee81fb84ed321a716c677aa0e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/25/2019
ms.locfileid: "71271974"
---
# <a name="install-sql-server-machine-learning-services-python-and-r-on-linux"></a>Installieren von SQL Server Machine Learning Services (Python und R) unter Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

In diesem Artikel wird erläutert, wie [SQL Server Machine Learning Services](../advanced-analytics/index.yml) unter Linux installiert wird. Sie können Machine Learning Services verwenden, um Python- und R-Skripts in einer Datenbank auszuführen.

Die folgenden Linux-Distributionen werden unterstützt:

- Red Hat Enterprise Linux (RHEL)
- SUSE Linux Enterprise Server (SLES)
- Ubuntu

Machine Learning Services sind ein Feature-Add-On für die Datenbank-Engine. Obwohl Sie die [Datenbank-Engine und Machine Learning Services gleichzeitig installieren](#install-all) können, empfiehlt es sich, zuerst die SQL Server-Datenbank-Engine zu installieren und zu konfigurieren, damit Sie eventuelle Probleme beheben können, bevor Sie weitere Komponenten hinzufügen. 

Die Pakete von Python- und R-Erweiterungen werden unter Linux in den Quellrepositorys für SQL Server gespeichert. Wenn Sie für die Datenbank-Engine-Installation bereits Quellrepositorys konfiguriert haben, können Sie die **mssql-mlservices**-Befehle für die Paketinstallation mithilfe derselben Repositoryregistrierung ausführen.

Machine Learning Services auch auf Linux-Containern unterstützt. Wir stellen keine vorgefertigten Container mit Machine Learning Services bereit. Sie können jedoch [mithilfe einer in GitHub verfügbaren Vorlage](https://github.com/Microsoft/mssql-docker/tree/master/linux/preview/examples/mssql-mlservices) einen Container aus den SQL Server-Containern erstellen.

## <a name="uninstall-previous-ctp"></a>Deinstallieren von früheren CTP-Versionen

Die Paketliste wurde in den letzten CTP-Versionen geändert, sodass sie nun weniger Pakete enthält. Es wird empfohlen, CTP 2.x zu deinstallieren, um alle früheren Pakete vor der Installation von CTP 3.2 zu entfernen. Die Installation mehrerer Versionen gleichzeitig wird nicht unterstützt.

### <a name="1-confirm-package-installation"></a>1. Bestätigen der Paketinstallation

Sie sollten in einem ersten Schritt überprüfen, ob eine frühere Version installiert ist. Die folgenden Dateien sind Zeichen dafür, dass bereits eine Installation durchgeführt wurde: „checkinstallextensibility.sh“, „exthost“ und „launchpad“.

```bash
ls /opt/microsoft/mssql/bin
```

### <a name="2-uninstall-previous-ctp-2x-packages"></a>2. Deinstallieren von CTP 2.x-Paketen

Führen Sie die Deinstallation auf der niedrigsten Paketebene durch. Alle Upstreampakete, die von einem Paket auf niedrigerer Ebene abhängig sind, werden automatisch deinstalliert.

  + Entfernen Sie **microsoft-r-open*** für die R-Integration.
  + Entfernen Sie **mssql-mlservices-python** für die Python-Integration.

Befehle zum Entfernen von Paketen können Sie der folgenden Tabelle entnehmen.

| Platform  | Befehl(e) zum Entfernen eines Pakets | 
|-----------|----------------------------|
| Red Hat   | `sudo yum remove microsoft-r-open-mro-3.4.4`<br/>`sudo yum remove msssql-mlservices-python` |
| SUSE  | `sudo zypper remove microsoft-r-open-mro-3.4.4`<br/>`sudo zypper remove msssql-mlservices-python` |
| Ubuntu    | `sudo apt-get remove microsoft-r-open-mro-3.4.4`<br/>`sudo apt-get remove msssql-mlservices-python`|

> [!Note]
> Microsoft R Open 3.4.4 besteht abhängig von der CTP-Version, die Sie zuvor installiert haben, aus zwei oder drei Paketen. (Das foreachiterators-Paket wurde in CTP 2.2 in das MRO-Hauptpaket integriert.) Wenn Pakete nach dem Entfernen von microsoft-r-open-mro-3.4.4 beibehalten werden, sollten Sie diese einzeln entfernen.
> ```
> microsoft-r-open-foreachiterators-3.4.4
> microsoft-r-open-mkl-3.4.4
> microsoft-r-open-mro-3.4.4
> ```

### <a name="3-proceed-with-ctp-32-install"></a>3. Fortsetzen der Installation von CTP 3.2

Führen Sie die Installation gemäß den in diesem Artikel beschriebenen Anweisungen für Ihr Betriebssystem auf der höchsten Paketebene durch.

Für sämtliche betriebssystemspezifischen Installationsanweisungen ist die *höchste Paketebene* entweder **Beispiel 1: vollständige Installation** für alle Pakete oder **Beispiel 2: minimale Installation** für die geringste Anzahl von Paketen, die für eine verwendbare Installation erforderlich sind.

1. Beginnen Sie bei der Integration von R mit [Microsoft R Open](#mro), da diese Komponente eine erforderliche Voraussetzung ist. Die R-Integration kann andernfalls nicht installiert werden.

2. Führen Sie Installationsbefehle mithilfe des Paket-Managers und der Syntax für Ihr Betriebssystem aus: 

   + [Red Hat](#RHEL)
   + [Ubuntu](#ubuntu)
   + [SUSE](#suse)

## <a name="prerequisites"></a>Voraussetzungen

+ Die Linux-Version muss [von SQL Server unterstützt](sql-server-linux-release-notes-2019.md#supported-platforms) werden, muss aber nicht die Docker-Engine enthalten. Folgende Versionen werden unterstützt:

   + [Red Hat Enterprise Linux (RHEL)](quickstart-install-connect-red-hat.md)

   + [SUSE Enterprise Linux Server](quickstart-install-connect-suse.md)

   + [Ubuntu](quickstart-install-connect-ubuntu.md)

+ (nur R) [Microsoft R Open](#mro) stellt die grundlegende R-Verteilung für das R-Feature in SQL Server bereit.

+ Sie sollten über ein Tool zum Ausführen von T-SQL-Befehlen verfügen. Sie benötigen einen Abfrage-Editor für die Konfiguration und Validierung nach der Installation. Die Verwendung von [Azure Data Studio](https://docs.microsoft.com/sql/azure-data-studio/download?view=sql-server-2017#get-azure-data-studio-for-linux) wird empfohlen. Dabei handelt es sich um einen kostenlosen Download, der unter Linux ausgeführt wird.

<a name="mro"></a>

### <a name="microsoft-r-open-mro-installation"></a>Installation von Microsoft R Open (MRO)

Die grundlegende R-Verteilung von Microsoft ist eine Voraussetzung für die Verwendung von RevoScaleR, MicrosoftML und andere R-Pakete, die mit Machine Learning Services installiert werden.

Die erforderliche Version ist MRO 3.5.2.

Wählen Sie für die Installation von MRO einen der beiden folgenden Ansätze aus:

+ Laden Sie den MRO-Tarball von MRAN herunter, entpacken Sie diesen, und führen Sie das Skript „install.sh“ aus. Wenn Sie diesen Ansatz wählen, finden Sie auf [MRAN](https://mran.microsoft.com/releases/3.5.2) Anweisungen zur Installation.

+ Alternativ können Sie das Repository **packages.microsoft.com** wie unten beschrieben registrieren, um die beiden Pakete zu installieren, die die MRO-Verteilung umfassen: microsoft-r-open-mro und microsoft-r-open-mkl. 

Mit den folgenden Befehlen wird das Repository registriert, das MRO bereitstellt. Nach der Registrierung enthalten die Befehle zum Installieren anderer R-Pakete (z. B. mssql-mlservices-mml-r) automatisch MRO als Paketabhängigkeit.

#### <a name="mro-on-ubuntu"></a>Microsoft R Open unter Ubuntu

```bash
# Install as root
sudo su

# Optionally, if your system does not have the https apt transport option
apt-get install apt-transport-https

# Set the location of the package repo the "prod" directory containing the distribution.
# This example specifies 16.04. Replace with 14.04 if you want that version
wget https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb

# Register the repo
dpkg -i packages-microsoft-prod.deb

# Update packages on your system (required), including MRO installation
sudo apt-get update
```

#### <a name="mro-on-red-hat"></a>MRO unter Red Hat

```bash
# Import the Microsoft repository key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc


# Set the location of the package repo at the "prod" directory
# The following command is for version 7.x
# For 6.x, replace 7 with 6 to get that version
rpm -Uvh https://packages.microsoft.com/config/rhel/7/packages-microsoft-prod.rpm

# Update packages on your system (optional)
yum update
```

#### <a name="mro-on-suse"></a>Microsoft R Open unter SUSE

```bash
# Install as root
sudo su

# Set the location of the package repo at the "prod" directory containing the distribution
# This example is for SLES12, the only supported version of SUSE in Machine Learning Server
zypper ar -f https://packages.microsoft.com/sles/12/prod packages-microsoft-com

# Update packages on your system (optional)
zypper update
```

## <a name="package-list"></a>Paketliste

Auf einem mit dem Internet verbundenen Gerät werden Pakete unabhängig von der Datenbank-Engine mithilfe des Paketinstallationsprogramms für das betreffende Betriebssystem heruntergeladen und installiert. In der folgenden Tabelle werden alle verfügbaren Pakete beschrieben. Für R und Python geben Sie jedoch Pakete an, die entweder die vollständigen Installation oder die minimale Installation durchführen.

| Paketname | Gilt für | und Beschreibung |
|--------------|----------|-------------|
|mssql-server-extensibility  | All | Erweiterungsframework, das zum Ausführen von R- und Python-Code verwendet wird. |
| microsoft-openmpi  | Python, R | Die Schnittstelle zur Nachrichtenübergabe, die von den Revo*-Bibliotheken zur Parallelisierung unter Linux verwendet wird. |
| mssql-mlservices-python | Python | Open-Source-Verteilung von Anaconda und Python. |
|mssql-mlservices-mlm-py  | Python | *Vollständige Installation:* Stellt vortrainierte revoscalepy- bzw. microsoftml-Modelle für Imagefeatures und Stimmungsanalyse für Texte bereit.| 
|mssql-mlservices-packages-py  | Python | *Minimale Installation:* Stellt revoscalepy und microsoftml bereit. <br/>Schließt vortrainierte Modelle aus. | 
| [microsoft-r-open*](#mro) | R | Open-Source-Verteilung von R, die aus drei Paketen besteht. |
|mssql-mlservices-mlm-r  | R | *Vollständige Installation:* Stellt vortrainierte RevoScaleR-, MicrosoftML-, sqlRUtils- bzw. olapR-Modelle für Imagefeatures und Stimmungsanalyse für Texte bereit.| 
|mssql-mlservices-packages-r  | R | *Minimale Installation:* Stellt RevoScaleR, sqlRUtils, MicrosoftML und olapR bereit. <br/>Schließt vortrainierte Modelle aus. | 
|mssql-mlservices-mml-py  | nur CTP 2.0–2.1 | In CTP 2.2 aufgrund der Python-Paketkonsolidierung in mssql-mslservices-python veraltet. Stellt revoscalepy bereit. Schließt vortrainierte Modelle und microsoftml aus.| 
|mssql-mlservices-mml-r  | nur CTP 2.0–2.1 | In CTP 2.2 aufgrund der R-Paketkonsolidierung in mssql-mslservices-python veraltet. Stellt RevoScaleR, sqlRUtils, und olapR bereit. Schließt vortrainierte Modelle und MicrosoftML aus.  |

<a name="RHEL"></a>

## <a name="redhat-commands"></a>Red Hat-Befehle

Sie können die Sprachunterstützung in einer beliebigen Kombination installieren (einzelne oder mehrere Sprachen). Für R und Python gibt es zwei Pakete, aus denen Sie auswählen können. Eines bietet alle verfügbaren Features, und ist als *vollständige Installation* gekennzeichnet. Das andere schließt vortrainierte Machine Learning-Modelle aus und wird als *minimale Installation* bezeichnet.

> [!Tip]
> Führen Sie nach Möglichkeit `yum clean all` aus, um vor der Installation Pakete auf dem System zu aktualisieren.

### <a name="example-1----full-installation"></a>Beispiel 1: vollständige Installation 

Umfasst Open-Source-R und -Python, Erweiterbarkeitsframeworks, microsoft-openmpi, Erweiterungen (R, Python) mit Machine-Learning-Bibliotheken und vortrainierten Modellen für R und Python. 

```bash
# Install as root or sudo
# Add everything (all R, Python)
# Be sure to include -9.4.7* in mlsservices package names
sudo yum install mssql-mlservices-mlm-py-9.4.7*
sudo yum install mssql-mlservices-mlm-r-9.4.7* 
```

### <a name="example-2---minimum-installation"></a>Beispiel 2: minimale Installation 

Umfasst Open-Source-R und -Python, Erweiterbarkeitsframeworks, microsoft-openmpi, Revo*-Kernbibliotheken und Machine-Learning-Bibliotheken für R und Python. Schließt vortrainierte Modelle aus.

```bash
# Install as root or sudo
# Minimum install of R, Python extensions
# Be sure to include -9.4.6* in mlsservices package names
sudo yum install mssql-mlservices-packages-py-9.4.7*
sudo yum install mssql-mlservices-packages-r-9.4.7*
```

<a name="ubuntu"></a>

## <a name="ubuntu-commands"></a>Ubuntu-Befehle

Sie können die Sprachunterstützung in einer beliebigen Kombination installieren (einzelne oder mehrere Sprachen). Für R und Python gibt es zwei Pakete, aus denen Sie auswählen können. Eines bietet alle verfügbaren Features, und ist als *vollständige Installation* gekennzeichnet. Das andere schließt vortrainierte Machine Learning-Modelle aus und wird als *minimale Installation* bezeichnet.

> [!Tip]
> Führen Sie nach Möglichkeit `apt-get update` aus, um vor der Installation Pakete auf dem System zu aktualisieren. Außerdem verfügen einige Docker-Images von Ubuntu möglicherweise nicht über die HTTPS-Transportoption „apt“. Verwenden Sie `apt-get install apt-transport-https`, um diese zu installieren.

### <a name="example-1----full-installation"></a>Beispiel 1: vollständige Installation 

Umfasst Open-Source-R und -Python, Erweiterbarkeitsframeworks, microsoft-openmpi, Erweiterungen (R, Python) mit Machine-Learning-Bibliotheken und vortrainierten Modellen für R und Python. 

```bash
# Install as root or sudo
# Add everything (all R, Python)
# There is no asterisk in this full install
sudo apt-get install mssql-mlservices-mlm-py 
sudo apt-get install mssql-mlservices-mlm-r 
```

### <a name="example-2---minimum-installation"></a>Beispiel 2: minimale Installation 

Umfasst Open-Source-R und -Python, Erweiterbarkeitsframeworks, microsoft-openmpi, Revo*-Kernbibliotheken und Machine-Learning-Bibliotheken für R und Python. Schließt vortrainierte Modelle aus. 

```bash
# Install as root or sudo
# Minimum install of R, Python
# No aasterisk
sudo apt-get install mssql-mlservices-packages-py
sudo apt-get install mssql-mlservices-packages-r
```

<a name="suse"></a>

## <a name="suse-commands"></a>SUSE-Befehle

Sie können die Sprachunterstützung in einer beliebigen Kombination installieren (einzelne oder mehrere Sprachen). Für R und Python gibt es zwei Pakete, aus denen Sie auswählen können. Eines bietet alle verfügbaren Features, und ist als *vollständige Installation* gekennzeichnet. Das andere schließt vortrainierte Machine Learning-Modelle aus und wird als *minimale Installation* bezeichnet.

### <a name="example-1----full-installation"></a>Beispiel 1: vollständige Installation 

Umfasst Open-Source-R und -Python, Erweiterbarkeitsframeworks, microsoft-openmpi, Erweiterungen (R, Python) mit Machine-Learning-Bibliotheken und vortrainierten Modellen für R und Python. 

```bash
# Install as root or sudo
# Add everything (all R, Python)
# Be sure to include -9.4.7* in mlsservices package names
sudo zypper install mssql-mlservices-mlm-py-9.4.7*
sudo zypper install mssql-mlservices-mlm-r-9.4.7* 
```

### <a name="example-2---minimum-installation"></a>Beispiel 2: minimale Installation 

Umfasst Open-Source-R und -Python, Erweiterbarkeitsframeworks, microsoft-openmpi, Revo*-Kernbibliotheken und Machine-Learning-Bibliotheken für R und Python. Schließt vortrainierte Modelle aus. 

```bash
# Install as root or sudo
# Minimum install of R, Python extensions
# Be sure to include -9.4.6* in mlsservices package names
sudo zypper install mssql-mlservices-packages-py-9.4.7*
sudo zypper install mssql-mlservices-packages-r-9.4.7*
```

## <a name="post-install-config-required"></a>Konfiguration nach der Installation (erforderlich)

Die zusätzliche Konfiguration erfolgt in erster Linie über das [Tool mssql-conf](sql-server-linux-configure-mssql-conf.md).


1. Fügen Sie das MSSQL-Benutzerkonto hinzu, um den SQL Server-Dienst auszuführen. Dies ist erforderlich, wenn Sie das Setup vorher noch nicht ausgeführt haben.

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

2. Akzeptieren Sie die Lizenzvereinbarungen für Open-Source-R und -Python. Hierfür gibt es mehrere Möglichkeiten. Wenn Sie zuvor die SQL Server-Lizenzvereinbarung akzeptiert haben und nun R- oder Python-Erweiterungen hinzufügen, stimmen Sie den Bedingungen mit folgendem Befehl zu:

   ```bash
   # Run as SUDO or root
   # Use set + EULA 
   sudo /opt/mssql/bin/mssql-conf set EULA accepteulaml Y
   ```

   Wenn Sie die SQL Server-Lizenzvereinbarung für die Datenbank-Engine noch nicht akzeptiert haben, erkennt das Setup die mssql-mlservices-Pakete und fordert Sie zum Akzeptieren der Lizenzbedingungen (EULA) auf, wenn `mssql-conf setup` ausgeführt wird. Weitere Informationen zu den EULA-Parametern finden Sie unter [Konfigurieren von SQL Server mit dem Tool mssql-conf](sql-server-linux-configure-mssql-conf.md#mlservices-eula).

3. Aktivieren Sie den Zugriff auf ausgehenden Netzwerkdatenverkehr. Der Zugriff auf ausgehenden Netzwerkdatenverkehr ist standardmäßig deaktiviert. Sie können mithilfe des Tools mssql-conf die boolesche Eigenschaft „outboundnetworkaccess“ festlegen, um ausgehende Anforderungen zu aktivieren. Weitere Informationen finden Sie unter [Konfigurieren von SQL Server für Linux mithilfe von mssql-conf](sql-server-linux-configure-mssql-conf.md#mlservices-outbound-access).

   ```bash
   # Run as SUDO or root
   # Enable outbound requests over the network
   sudo /opt/mssql/bin/mssql-conf set extensibility outboundnetworkaccess 1
   ```

4. Wenn Sie nur das R-Feature integrieren möchten, legen Sie die Umgebungsvariable **MKL_CBWR** über die Intel Math Kernel Library-Berechnungen auf [ensure consistent output](https://software.intel.com/articles/introduction-to-the-conditional-numerical-reproducibility-cnr) (Konsistente Ausgabe sicherstellen) fest.

   + Bearbeiten oder erstellen Sie eine Datei namens **.bash_profile** im Stammverzeichnis Ihres Benutzers, und fügen Sie die Zeile `export MKL_CBWR="AUTO"` zur Datei hinzu.

   + Führen Sie diese Datei aus, indem Sie `source .bash_profile` in der Bash-Eingabeaufforderung eingeben.

5. Starten Sie anschließend das SQL Server-Launchpad und die Datenbank-Engine-Instanz neu, um die aktualisierten Werte aus der INI-Datei zu lesen. Wenn eine Erweiterbarkeitseinstellung geändert wird, werden Sie in einer Neustartmeldung darauf hingewiesen.  

   ```bash
   systemctl restart mssql-launchpadd

   systemctl restart mssql-server.service
   ```

6. Aktivieren Sie die externe Skriptausführung mithilfe von Azure Data Studio oder einem anderen Tool wie SQL Server Management Studio (nur unter Windows), das Transact-SQL ausführt. 

   ```bash
   EXEC sp_configure 'external scripts enabled', 1 
   RECONFIGURE WITH OVERRIDE 
   ```

7. Starten Sie den Launchpad-Dienst neu.

## <a name="verify-installation"></a>Überprüfen der Installation

R-Bibliotheken (z. B. MicrosoftML, RevoScaleR) finden Sie unter `/opt/mssql/mlservices/libraries/RServer`.

Python-Bibliotheken (microsoftml und revoscalepy) finden Sie unter `/opt/mssql/mlservices/libraries/PythonServer`.

Sie können die Installation überprüfen, indem Sie ein T-SQL-Skript ausführen, das eine gespeicherte Systemprozedur ausführt, die R oder Python aufruft. Für diese Aufgabe benötigen Sie ein Abfragetool. Azure Data Studio ist eine gute Wahl. Andere häufig verwendete Tools wie SQL Server Management Studio oder PowerShell können nur unter Windows verwendet werden. Wenn Sie über einen Windows-Computer mit diesen Tools verfügen, verwenden Sie diesen, um eine Verbindung mit Ihrer Linux-Installation der Datenbank-Engine herzustellen.

Führen Sie den folgenden SQL-Befehl aus, um die Ausführung von R in SQL Server testen. Wenn das Skript nicht ausgeführt wird, versuchen Sie mit `sudo systemctl restart mssql-server.service`, den Dienst neu zu starten.

```r
EXEC sp_execute_external_script   
@language =N'R', 
@script=N' 
OutputDataSet <- InputDataSet', 
@input_data_1 =N'SELECT 1 AS hello' 
WITH RESULT SETS (([hello] int not null)); 
GO 
```
 
Führen Sie den folgenden SQL-Befehl aus, um die Ausführung von Python in SQL Server testen. 
 
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

## <a name="chained-combo-install"></a>Verkettete kombinierte Installation

Sie können die Datenbank-Engine und Machine Learning Services zusammen installieren und konfigurieren, indem Sie R- oder Python-Pakete und -Parameter an einen Befehl anfügen, der die Datenbank-Engine installiert. 

1. Installieren Sie [Microsoft R Open](#mro), da diese Komponente für die Integration von R erforderlich ist. Überspringen Sie diesen Schritt, wenn Sie das R-Feature nicht installieren.

2. Geben Sie eine Befehlszeile an, die die Datenbank-Engine sowie Spracherweiterungsfeatures enthält.

  Sie können einer Datenbank-Engine-Installation ein einzelnes Feature hinzufügen, z. B. eine Python-Integration.

  ```bash
  sudo yum install -y mssql-server mssql-mlservices-packages-r-9.4.7* 
  ```

  Sie können auch beide Erweiterungen hinzufügen (R und Python).

  ```bash
  sudo yum install -y mssql-server mssql-mlservices-packages-r-9.4.7* mssql-mlservices-packages-py-9.4.7*
  ```

3. Akzeptieren Sie die Lizenzbedingungen, und schließen Sie die Konfiguration im Anschluss an die Installation ab. Verwenden Sie hierfür das Tool **mssql-conf**.

  ```bash
  sudo /opt/mssql/bin/mssql-conf setup
  ```

  Sie werden dann aufgefordert, die Lizenzbedingungen für die Datenbank-Engine zu akzeptieren, eine Edition auszuwählen und das Administratorkennwort festzulegen. Außerdem werden Sie aufgefordert, die Lizenzvereinbarung für Machine Learning Services zu akzeptieren.

4. Starten Sie den Dienst neu, wenn Sie dazu aufgefordert werden.

  ```bash
  sudo systemctl restart mssql-server.service
  ```

## <a name="unattended-installation"></a>Unbeaufsichtigte Installation

Fügen Sie die Pakete für „mssql-mlservices“ und die Lizenzbedingungen über eine [unbeaufsichtigte Installation](https://docs.microsoft.com/sql/linux/sql-server-linux-setup?view=sql-server-2017#unattended) der Datenbank-Engine hinzu.

Beachten Sie, dass das Setup oder das Tool mssql-conf Sie dazu auffordert, die Lizenzbedingungen zu akzeptieren. Wenn Sie SQL Server-Datenbank-Engine bereits konfiguriert und die Lizenzbedingungen akzeptiert haben, verwenden Sie einen der mlservices-spezifischen EULA-Parameter für die Open-Source-Verteilungen für R und Python:

```bash
sudo /opt/mssql/bin/mssql-conf setup accept-eula-ml
```

Die möglichen Permutationen für das Akzeptieren der Lizenzbedingungen sind unter [Konfigurieren von SQL Server für Linux mit dem Tool mssql-conf](sql-server-linux-configure-mssql-conf.md#mlservices-eula) dokumentiert.

## <a name="offline-installation"></a>Offlineinstallation

Befolgen Sie die Anweisungen zur [Offlineinstallation](sql-server-linux-setup.md#offline), um die Pakete zu installieren. Der nachfolgenden Liste können Sie entnehmen, auf welchen Websites Sie jeweils entsprechende Downloads finden. Laden Sie dann alle nötigen Pakete herunter.

> [!Tip]
> Einige der Paketverwaltungstools umfassen Befehle, mit denen Sie Paketabhängigkeiten ermitteln können. Verwenden Sie für yum `sudo yum deplist [package]`. Verwenden Sie für Ubuntu erst `sudo apt-get install --reinstall --download-only [package name]` und dann `dpkg -I [package name].deb`.


#### <a name="download-site"></a>Downloadsite

Sie können die Pakete von [https://packages.microsoft.com/](https://packages.microsoft.com/) herunterladen. Alle mlservices-Pakete für R und Python werden zusammen mit dem Datenbank-Engine-Paket bereitgestellt. Die Basisversion für die mlservices-Pakete ist 9.4.5 für CTP 2.0 und 9.4.6 für CTP 2.1 und höher. Beachten Sie, dass die microsoft-r-open-Pakete sich in einem [anderen Repository](#mro) befinden.

#### <a name="rhel7-paths"></a>RHEL/7-Pfade

|||
|--|----|
| mssql/mlservices-Pakete | [https://packages.microsoft.com/rhel/7/mssql-server-preview/](https://packages.microsoft.com/rhel/7/mssql-server-preview/) |
| microsoft-r-open-Pakete | [https://packages.microsoft.com/rhel/7/prod/](https://packages.microsoft.com/rhel/7/prod/) | 


#### <a name="ubuntu1604-paths"></a>Ubuntu/16.04-Pfade

|||
|--|----|
| mssql/mlservices-Pakete | [https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/) |
| microsoft-r-open-Pakete | [https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/](https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/) | 

#### <a name="sles12-paths"></a>SLES/12-Pfade

|||
|--|----|
| mssql/mlservices-Pakete | [https://packages.microsoft.com/sles/12/mssql-server-preview/](https://packages.microsoft.com/sles/12/mssql-server-preview/) |
| microsoft-r-open-Pakete | [https://packages.microsoft.com/sles/12/prod/](https://packages.microsoft.com/sles/12/prod/) | 

#### <a name="package-list"></a>Paketliste

Je nachdem, welche Erweiterungen Sie verwenden möchten, müssen Sie die für die jeweilige Sprache erforderlichen Pakete herunterladen. Genaue Dateinamen enthalten Plattforminformationen im Suffix, aber die unten aufgeführten Dateinamen sollten genau genug sein, damit Sie herausfinden können, welche Dateien Sie benötigen.

```
# Core packages 
mssql-server-15.0.1000
mssql-server-extensibility-15.0.1000

# R
microsoft-openmpi-3.0.0
microsoft-r-open-mkl-3.5.2
microsoft-r-open-mro-3.5.2
mssql-mlservices-packages-r-9.4.7.64
mssql-mlservices-mlm-r-9.4.7.64


# Python
microsoft-openmpi-3.0.0
mssql-mlservices-python-9.4.7.64
mssql-mlservices-packages-py-9.4.7.64
mssql-mlservices-mlm-py-9.4.7.64
```

## <a name="add-more-rpython-packages"></a>Hinzufügen weiterer R- und Python-Pakete 
 
Sie können andere R-und Python-Pakete installieren und in Skripts verwenden, die in SQL Server 2019 ausgeführt werden.

### <a name="r-packages"></a>R-Pakete 
 
1. Starten Sie eine R-Sitzung.

   ```r
   # sudo /opt/mssql/mlservices/bin/R/R 
   ```

2. Installieren Sie ein R-Paket namens [glue](https://mran.microsoft.com/package/glue), um die Installation des Pakets zu testen.

   ```r
   # install.packages("glue",lib="/opt/mssql/mlservices/libraries/RServer") 
   ```
   Alternativ können Sie ein R-Paket über die Befehlszeile installieren. 

   ```r
   # sudo /opt/mssql/mlservices/bin/R/R CMD INSTALL -l /opt/mssql/mlservices/libraries/RServer glue_1.1.1.tar.gz 
   ```

3. Importieren Sie das R-Paket in [sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

   ```r
   EXEC sp_execute_external_script  
   @language = N'R', 
   @script = N'library(glue)' 
   ```

### <a name="python-packages"></a>Python-Pakete 
 
1. Installieren Sie das Python-Paket [httpie](https://httpie.org/) mithilfe von pip. 

   ```python
   # sudo /opt/mssql/mlservices/bin/python/python -m pip install httpie 
   ``` 

2. Importieren Sie das Python-Paket in [sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).
 
   ```python
   EXEC sp_execute_external_script  
   @language = N'Python',  
   @script = N'import httpie' 
   ```

## <a name="limitations-in-ctp-releases"></a>Einschränkungen in CTP-Releases

Die Integration von R und Python unter Linux befindet sich derzeit noch in der Entwicklung. Die folgenden Features sind in der Vorschauversion noch nicht aktiviert.

+ Die implizite Authentifizierung ist zurzeit nicht in Machine Learning Services unter Linux verfügbar. Das bedeutet, dass Sie über R- oder Python-Skripts, die zu diesem Zeitpunkt ausgeführt werden, keine erneute Verbindung mit dem Server herstellen können, um auf Daten oder andere Ressourcen zuzugreifen. 

### <a name="resource-governance"></a>Ressourcengovernance

In Bezug auf die [Ressourcengovernance](../t-sql/statements/create-external-resource-pool-transact-sql.md) besteht zwar zwischen Linux und Windows Parität für externe Ressourcenpools, aber die Statistiken für [sys.dm_resource_governor_external_resource_pools](../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pools.md) haben derzeit unterschiedliche Einheiten unter Linux. Diese Einheiten werden in einer kommenden CTP-Version angepasst.
 
| Spaltenname   | und Beschreibung | Wert unter Linux | 
|---------------|--------------|---------------|
|peak_memory_kb | Der maximale Speicher, der für den Ressourcenpool verwendet wird. | Unter Linux wird diese Statistik dem CGroups-Speichersubsystem entnommen. Dabei lautet der Wert „memory.max_usage_in_bytes“. |
|write_io_count | Die Gesamtanzahl der E/A-Schreibvorgänge, die seit dem Zurücksetzen der Resource Governor-Statistiken ausgegeben wurden. | Unter Linux wird diese Statistik dem CGroups-Speichersubsystem „blkio“ entnommen. Dabei lautet der Wert der Zeile für die Schreibvorgänge „blkio.throttle.io_serviced“. | 
|read_io_count | Die Gesamtanzahl der E/A-Lesevorgänge, die seit dem Zurücksetzen der Resource Governor-Statistiken ausgegeben wurden. | Unter Linux wird diese Statistik dem CGroups-Speichersubsystem „blkio“ entnommen. Dabei lautet der Wert der Zeile für die Lesevorgänge „blkio.throttle.io_serviced“. | 
|total_cpu_kernel_ms | Die kumulierte CPU-Benutzerkernelzeit in Millisekunden, seitdem die Resource Governor-Statistiken zurückgesetzt wurden. | Unter Linux wird diese Statistik dem CGroups-Speichersubsystem „cpuacct“ entnommen. Dabei lautet der Wert der Zeile für den Benutzer „cpuacct.stat“. |  
|total_cpu_user_ms | Die kumulierte CPU-Benutzerzeit in Millisekunden, seitdem die Resource Governor-Statistiken zurückgesetzt wurden.| Unter Linux wird diese Statistik dem CGroups-Speichersubsystem „cpuacct“ entnommen. Dabei lautet der Systemzeilenwert „cpuacct.stat“. | 
|active_processes_count | Die Anzahl externer Prozesse, die zum Zeitpunkt der Anforderung ausgeführt werden.| Unter Linux wird diese Statistik dem CGroups-Speichersubsystem „pids“ entnommen. Dabei lautet der Wert „pids.current“. | 

## <a name="next-steps"></a>Nächste Schritte

R-Entwickler können mit einigen einfachen Beispielen loslegen und die Grundlagen der Funktionen von R unter SQL Server kennenlernen. Informationen zu den nächsten Schritten finden Sie unter den folgenden Links:

+ [Tutorial: Ausführen von R in T-SQL](../advanced-analytics/tutorials/quickstart-r-create-script.md)
+ [Tutorial: Datenbankinterne Analysen für R-Entwickler](../advanced-analytics/tutorials/sqldev-in-database-r-for-sql-developers.md)

Python-Entwickler können in den folgenden Tutorials erfahren, wie Python mit SQL Server verwendet werden kann:

+ [Tutorial: Ausführen von Python in T-SQL](../advanced-analytics/tutorials/run-python-using-t-sql.md)
+ [Tutorial: Datenbankinterne Analysen für Python-Entwickler](../advanced-analytics/tutorials/sqldev-in-database-python-for-sql-developers.md)

Praxisbeispiele für die Verwendung von Machine Learning finden Sie unter [Tutorials für Machine Learning](../advanced-analytics/tutorials/machine-learning-services-tutorials.md).
