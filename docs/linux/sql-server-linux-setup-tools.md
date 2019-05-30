---
title: Installieren von SQL Server-Befehlszeilentools unter Linux
titleSuffix: SQL Server
description: Dieser Artikel beschreibt, wie Sie die SQL Server-Tools unter Linux zu installieren.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 05/28/2019
ms.topic: conceptual
ms.prod: sql
ms.custom: sqlfreshmay19
ms.technology: linux
ms.assetid: eff8e226-185f-46d4-a3e3-e18b7a439e63
ms.openlocfilehash: 86a452237628df8952beaa09277a79b1de507aa1
ms.sourcegitcommit: 02df4e7965b2a858030bb508eaf8daa9bc10b00b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/28/2019
ms.locfileid: "66265400"
---
# <a name="install-sqlcmd-and-bcp-the-sql-server-command-line-tools-on-linux"></a>Installieren von Sqlcmd und Bcp die SQL Server-Befehlszeilenprogramme unter Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Die folgenden Schritte installieren Sie die Befehlszeilentools, Microsoft ODBC-Treiber und deren Abhängigkeiten. Die **Mssql-Tools** Paket enthält:

- **sqlcmd**: Befehlszeilen-Abfrage-Hilfsprogramm.
- **bcp**: BULK Import / Export-Dienstprogramm.

Installieren der Tools für Ihre Plattform:

- [Red Hat Enterprise Linux](#RHEL)
- [Ubuntu](#ubuntu)
- [SUSE Linux Enterprise Server](#SLES)
- [macOS](#macos)
- [Docker](#docker)

In diesem Artikel wird beschrieben, wie die Befehlszeilentools installiert wird. Wenn Sie Beispiele zum Verwenden von Suchen **Sqlcmd** oder **Bcp**, finden Sie unter den [Links](#next-steps) am Ende dieses Themas.

## <a name="a-idrhelainstall-tools-on-rhel-7"></a><a id="RHEL"><a/>Installieren Sie auf dem virtuellen RHEL 7-tools

Verwenden Sie die folgenden Schritte aus, um das Installieren der **Mssql-Tools** unter Red Hat Enterprise Linux. 

1. Geben Sie ein Superuser-Modus.

   ```bash
   sudo su
   ```

1. Laden Sie die Konfigurationsdatei des Microsoft Red Hat-Repository herunter.

   ```bash
   curl https://packages.microsoft.com/config/rhel/7/prod.repo > /etc/yum.repos.d/msprod.repo
   ```

1. Exit-Superuser-Modus.

   ```bash
   exit
   ```

1. Wenn Sie eine frühere Version von hatten **Mssql-Tools** installiert haben, entfernen Sie alle älteren UnixODBC-Pakete.

   ```bash
   sudo yum remove mssql-tools unixODBC-utf16-devel
   ```

1. Führen Sie die folgenden Befehle zum Installieren **Mssql-Tools** mit dem UnixODBC-Developer-Paket.

   ```bash
   sudo yum install mssql-tools unixODBC-devel
   ```

   > [!Note] 
   > Aktualisieren Sie auf die neueste Version der **Mssql-Tools** führen Sie die folgenden Befehle:
   >    ```bash
   >   sudo yum check-update
   >   sudo yum update mssql-tools
   >   ```

1. **Optional**: Hinzufügen `/opt/mssql-tools/bin/` auf Ihre **Pfad** in einer Bash-Shell-Umgebungsvariablen angegeben.

   Zu **Sqlcmd/Bcp** zugegriffen werden kann, in der Bash-Shell für und-anmeldesitzungen, ändern Ihre **Pfad** in die **~/.bash_profile** -Datei mit den folgenden Befehl aus:

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   ```

   Vornehmen **Sqlcmd/Bcp-** zugegriffen werden kann, in der Bash-Shell für interaktive/Sitzungen ohne Anmeldung, ändern Sie die **Pfad** in die **~/.bashrc** -Datei mit den folgenden Befehl aus:

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

## <a id="ubuntu"></a>Installieren von Tools auf Ubuntu 16.04

Verwenden Sie die folgenden Schritte aus, um das Installieren der **Mssql-Tools** unter Ubuntu. 

1. Importieren Sie die öffentlichen Repository GPG-Schlüssel.

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

1. Registrieren Sie das Microsoft-Ubuntu-Repository.

   ```bash
   curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list | sudo tee /etc/apt/sources.list.d/msprod.list
   ```

1. Aktualisieren Sie die Liste der Datenquellen, und führen Sie den Installationsbefehl mit dem UnixODBC-Developer-Paket.

   ```bash
   sudo apt-get update 
   sudo apt-get install mssql-tools unixodbc-dev
   ```

   > [!Note] 
   > Aktualisieren Sie auf die neueste Version der **Mssql-Tools** führen Sie die folgenden Befehle:
   >    ```bash
   >   sudo apt-get update 
   >   sudo apt-get install mssql-tools 
   >   ```

1. **Optional**: Hinzufügen `/opt/mssql-tools/bin/` auf Ihre **Pfad** in einer Bash-Shell-Umgebungsvariablen angegeben.

   Zu **Sqlcmd/Bcp** zugegriffen werden kann, in der Bash-Shell für und-anmeldesitzungen, ändern Ihre **Pfad** in die **~/.bash_profile** -Datei mit den folgenden Befehl aus:

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   ```

   Vornehmen **Sqlcmd/Bcp-** zugegriffen werden kann, in der Bash-Shell für interaktive/Sitzungen ohne Anmeldung, ändern Sie die **Pfad** in die **~/.bashrc** -Datei mit den folgenden Befehl aus:

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

## <a id="SLES"></a>Installieren von Tools unter SLES 12

Verwenden Sie die folgenden Schritte aus, um das Installieren der **Mssql-Tools** unter SUSE Linux Enterprise Server. 

1. Die Microsoft SQL Server-Repository Zypper hinzufügen.

   ```bash
   sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/prod.repo 
   sudo zypper --gpg-auto-import-keys refresh
   ```

1. Installieren Sie **Mssql-Tools** mit dem UnixODBC-Developer-Paket.

   ```bash
   sudo zypper install mssql-tools unixODBC-devel
   ```

   > [!Note] 
   > Aktualisieren Sie auf die neueste Version der **Mssql-Tools** führen Sie die folgenden Befehle:
   >    ```bash
   >   sudo zypper refresh
   >   sudo zypper update mssql-tools
   >   ```

1. **Optional**: Hinzufügen `/opt/mssql-tools/bin/` auf Ihre **Pfad** in einer Bash-Shell-Umgebungsvariablen angegeben.

   Zu **Sqlcmd/Bcp** zugegriffen werden kann, in der Bash-Shell für und-anmeldesitzungen, ändern Ihre **Pfad** in die **~/.bash_profile** -Datei mit den folgenden Befehl aus:

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   ```

   Vornehmen **Sqlcmd/Bcp-** zugegriffen werden kann, in der Bash-Shell für interaktive/Sitzungen ohne Anmeldung, ändern Sie die **Pfad** in die **~/.bashrc** -Datei mit den folgenden Befehl aus:

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

## <a id="macos"></a> Installieren von Tools unter macOS

Eine Vorschau der **Sqlcmd** und **Bcp** ist jetzt unter MacOS verfügbar. Weitere Informationen finden Sie unter den [Ankündigung](https://blogs.technet.microsoft.com/dataplatforminsider/2017/05/16/sql-server-command-line-tools-for-macos-released/).

*Installieren Sie [Homebrew](https://brew.sh) , wenn Sie noch nicht vorhanden ist:*

        /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

Zum Installieren der Tools für Mac El Capitan und Sierra, verwenden Sie die folgenden Befehle aus:

```
# brew untap microsoft/mssql-preview if you installed the preview version 
brew tap microsoft/mssql-release https://github.com/Microsoft/homebrew-mssql-release
brew update
brew install mssql-tools
#for silent install: 
#HOMEBREW_NO_ENV_FILTERING=1 ACCEPT_EULA=y brew install mssql-tools
```

## <a id="docker"></a> Docker

Die SQL Server-Befehlszeilentools sind im Docker-Image enthalten. Wenn Sie das Image mit einer interaktiven Eingabeaufforderung anfügen, können Sie die Tools lokal ausführen.

## <a name="offline-installation"></a>Offlineinstallation

[!INCLUDE[SQL Server Linux offline package installation](../includes/sql-server-linux-offline-package-install-intro.md)]

1. Zunächst suchen und kopieren Sie die **Mssql-Tools** -Paket für Ihre Linux-Distribution:

   | Linux-distribution | **MSSQL-Tools** Paketspeicherort |
   |---|---|
   | Red Hat | [https://packages.microsoft.com/rhel/7.3/prod](https://packages.microsoft.com/rhel/7.3/prod) |
   | SLES | [https://packages.microsoft.com/sles/12/prod](https://packages.microsoft.com/sles/12/prod)|
   | Ubuntu 16.04 | [https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/mssql-tools](https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/mssql-tools) |

1. Außerdem suchen und kopieren Sie die **Msodbcsql** -Paket, das eine Abhängigkeit ist. Die **Msodbcsql** Paket besteht eine Abhängigkeit auf **UnixODBC-entwickl** (Red Hat und SLES) oder **Unixodbc-Dev-** (Ubuntu). Den Speicherort der **Msodbcsql** Pakete werden in der folgenden Tabelle aufgeführt:

   | Linux-distribution | Speicherort der ODBC-Pakete |
   |---|---|
   | Red Hat | [https://packages.microsoft.com/rhel/7.3/prod](https://packages.microsoft.com/rhel/7.3/prod) |
   | SLES | [https://packages.microsoft.com/sles/12/prod](https://packages.microsoft.com/sles/12/prod)|
   | Ubuntu 16.04 | [**msodbcsql**](https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/msodbcsql)<br/>[**unixodbc-dev**](https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/u/unixodbc/) |

1. **Verschieben Sie die heruntergeladenen Pakete auf Ihren Linux-Computer**. Wenn Sie einen anderen Computer verwendet, um die Pakete herunterzuladen, ist eine Möglichkeit, verschieben Sie die Pakete auf Ihren Linux-Computer mit der **scp** Befehl.

1. **Installieren der und Pakete**: Installieren Sie die **Mssql-Tools** und **Msodbc** Pakete. Wenn Sie alle abhängigkeitsfehler erhalten, bis der nächste Schritt ignorieren.

    | Platform | Installieren der Paketbefehle |
    |-----|-----|
    | Red Hat | `sudo yum localinstall msodbcsql-<version>.rpm`<br/>`sudo yum localinstall mssql-tools-<version>.rpm` |
    | SLES | `sudo zypper install msodbcsql-<version>.rpm`<br/>`sudo zypper install mssql-tools-<version>.rpm` |
    | Ubuntu | `sudo dpkg -i msodbcsql_<version>.deb`<br/>`sudo dpkg -i mssql-tools_<version>.deb` |

1. **Beheben Sie fehlende Abhängigkeiten**: Möglicherweise müssen Sie Abhängigkeiten an diesem Punkt fehlt. Wenn dies nicht der Fall ist, können Sie diesen Schritt überspringen. In einigen Fällen müssen Sie manuell suchen und diese Abhängigkeiten zu installieren.

    Für RPM-Pakete können Sie die erforderlichen Abhängigkeiten mit den folgenden Befehlen überprüfen:

    ```bash
    rpm -qpR msodbcsql-<version>.rpm
    rpm -qpR mssql-tools-<version>.rpm
    ```

    Für Debian-Pakete, wenn Sie Zugriff auf genehmigte Repositorys, die mit diesen Abhängigkeiten, haben die einfachste Lösung ist die Verwendung der **apt-Get** Befehl:

    ```bash
    sudo apt-get -f install
    ```

    > [!NOTE]
    > Dieser Befehl schließt die Installation der SQL Server-Pakete auch.

    Wenn dies nicht für das Debian-Paket funktioniert, können Sie die erforderlichen Abhängigkeiten mit den folgenden Befehlen überprüfen:

    ```bash
    dpkg -I msodbcsql_<version>_amd64.deb | grep "Depends:"
    dpkg -I mssql-tools_<version>_amd64.deb | grep "Depends:"
    ```

## <a name="next-steps"></a>Nächste Schritte

Ein Beispiel zur Verwendung für **Sqlcmd** zum Verbinden mit SQL Server, und erstellen Sie eine Datenbank, finden Sie in der folgenden schnellstartanleitungen:

- [Installieren Sie unter Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Installieren Sie unter SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Installieren unter Ubuntu](quickstart-install-connect-ubuntu.md)
- [Führen unter Docker aus](quickstart-install-connect-ubuntu.md)

Ein Beispiel zur Verwendung für **Bcp** um per Massenvorgang zu importieren und Exportieren von Daten, finden Sie unter [Massenkopieren von Daten in SQL Server unter Linux](sql-server-linux-migrate-bcp.md).
