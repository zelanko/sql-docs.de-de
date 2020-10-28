---
title: Installieren der Azure Data CLI (azdata) mit pip
titleSuffix: ''
description: Hier erfahren Sie, wie Sie das Tool „azdata“ mit pip installieren.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 09/30/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 4aa52ebe56cbe4af3d2983a9ed800ebbc1538971
ms.sourcegitcommit: ae474d21db4f724523e419622ce79f611e956a22
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/20/2020
ms.locfileid: "92257453"
---
# <a name="install-azure-data-cli-azdata-with-pip"></a>Installieren von [!INCLUDE [azure-data-cli-azdata](../../includes/azure-data-cli-azdata.md)] mit `pip`

[!INCLUDE[azdata](../../includes/applies-to-version/azdata.md)]

In diesem Artikel wird beschrieben, wie Sie das [!INCLUDE [azure-data-cli-azdata](../../includes/azure-data-cli-azdata.md)]-Tool mithilfe von `pip` unter Windows, Linux oder macOS/OS X installieren.

> [!TIP]
> Zur Vereinfachung können Sie zum Installieren von `azdata` einen [Paket-Manager](./deploy-install-azdata.md) für Windows, Linux (Ubuntu-, Debian-, RHEL-, CentOS-, openSUSE- und SLE-Distributionen) und macOS verwenden.

## <a name="prerequisites"></a><a id="prerequisites"></a> Voraussetzungen

`azdata` ist ein in Python geschriebenes Befehlszeilen-Hilfsprogramm, mit dem Clusteradministratoren über REST-APIs Bootstraps durchführen und Datenressourcen verwalten können. Die mindestens erforderliche Python-Version ist v3.5. `pip` ist zum Herunterladen und Installieren des `azdata`-Tools erforderlich. Die nachstehenden Anweisungen enthalten Beispiele für Windows, Linux (Ubuntu) und macOS/OS X. Informationen zum Installieren von Python auf anderen Plattformen finden Sie in der [Python-Dokumentation](https://wiki.python.org/moin/BeginnersGuide/Download). Installieren und aktualisieren Sie außerdem die aktuelle Version des Python-Pakets `requests`:

```bash
pip3 install -U requests
```

## <a name="windows-azdata-installation"></a><a id="windows"></a> Installation von `azdata` unter Windows

1. Laden Sie das erforderliche Python-Paket aus [https://www.python.org/downloads/](https://www.python.org/downloads/) auf einen Windows-Client herunter. Bei Python 3.5.3 und höher wird bei der Installation von Python auch pip3 installiert.

   > [!TIP]
   > Wenn Sie Python 3 installieren, wählen Sie aus, dass Python `PATH` hinzugefügt wird. Wenn nicht, können Sie später ermitteln, wo sich pip3 befindet, und pip3 manuell `PATH` hinzufügen.

1. Öffnen Sie eine neue Windows PowerShell-Sitzung, um den aktuellen Pfad mit Python zu verwenden.

1. Ab SQL Server 2019 CU5 verfügt azdata über eine vom Server unabhängige Semantik. Wenn bereits vorherige Releases von `azdata` installiert sind, müssen Sie diese vor dem Installieren der aktuellen Version erst deinstallieren.

   Führen Sie beispielsweise für 2019-cu4 den folgenden Befehl aus:

   ```powershell
   pip3 uninstall -r https://azdatacli.blob.core.windows.net/python/azdata/2019-cu4/requirements.txt
   ```

  > [!NOTE]
  > Ersetzen Sie in den vorstehenden Beispielen `2019-cu6` durch Version und CU Ihrer installierten Version von `azdata`. 

1. Installieren von `azdata`.

   ```powershell
   pip3 install -r https://aka.ms/azdata
   ```

## <a name="linux-azdata-installation"></a><a id="linux"></a> Installation von `azdata` unter Linux

Unter Linux müssen Sie Python 3.5 installieren und dann pip aktualisieren. Das folgende Beispiel zeigt die Befehle, die für Ubuntu funktionieren. Informationen zu anderen Linux-Plattformen finden Sie in der [Python-Dokumentation](https://wiki.python.org/moin/BeginnersGuide/Download).

1. Installieren Sie die erforderlichen Python-Pakete:

   ```bash
   sudo apt-get update && \
   sudo apt-get install -y python3 && \
   sudo apt-get install -y python3-pip && \
   sudo apt-get install -y libkrb5-dev && \
   sudo apt-get install -y libsqlite3-dev && \
   sudo apt-get install -y unixodbc-dev
   ```

1. Führen Sie ein Upgrade für pip3 durch.

   ```bash
   sudo -H pip3 install --upgrade pip
   ```

1. Ab SQL Server 2019 CU5 verfügt azdata über eine vom Server unabhängige Semantik. Wenn bereits vorherige Releases von `azdata` installiert sind, müssen Sie diese vor dem Installieren der aktuellen Version erst deinstallieren.

   Führen Sie für `2019-cu6` beispielsweise den folgenden Befehl aus:

   ```bash
   pip3 uninstall -r https://azdatacli.blob.core.windows.net/python/azdata/2019-cu6/requirements.txt
   ```

  > [!NOTE]
  > Ersetzen Sie in den vorstehenden Beispielen `2019-cu6` durch Version und CU Ihrer installierten Version von `azdata`.

1. Installieren von `azdata`.

   ```bash
   pip3 install -r https://aka.ms/azdata --user
   ```

   > [!NOTE]
   > Mit der Befehlszeilenoption `--user` wird `azdata` im Python-Benutzerinstallationsverzeichnis installiert. Dies ist unter Linux in der Regel `~/.local/bin`. Fügen Sie entweder dieses Verzeichnis dem Pfad hinzu, oder navigieren Sie zum Benutzerinstallationsverzeichnis, und führen Sie `./azdata` dort aus.

## <a name="install-azdata-on-macos-or-os-x"></a><a id="macOSX"></a> Installation von `azdata` unter macOS oder OS X

Befolgen Sie diese Schritte, um `azdata` unter macOS oder OS X zu installieren. Führen Sie für jeden Schritt das Beispiel im Terminal aus.

1. Installieren Sie auf einem macOS-Client [Homebrew](https://brew.sh), sofern Sie das noch nicht getan haben:

   ```bash
   /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
   ```

1. Installieren Sie mindestens Version 3.0 von Python und pip.

   ```bash
   brew install python3
   ```

1. Installieren von Abhängigkeiten:

   ```bash
   pip3 install -U requests
   brew install freetds
   ```

1. Ab SQL Server 2019 CU5 verfügt azdata über eine vom Server unabhängige Semantik. Wenn bereits vorherige Releases von `azdata` installiert sind, müssen Sie diese vor dem Installieren der aktuellen Version erst deinstallieren. Mit dem folgenden Befehl wird beispielsweise die RC1-Version von `azdata` entfernt:

   ```bash
   pip3 uninstall -r https://azdatacli.blob.core.windows.net/python/azdata/2019-rc1/requirements.txt
   ```

1. Installieren Sie die Azure Data CLI.

   ```bash
   pip3 install -r https://aka.ms/azdata
   ```

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu Big Data-Clustern finden Sie unter [Was sind [!INCLUDE[big-data-clusters-2019](../../includes/ssbigdataclusters-ver15.md)]?](../../big-data-cluster/big-data-cluster-overview.md).

Verwenden von azdata mit [Azure Arc-fähigen Datendiensten](/azure/azure-arc/data/)
