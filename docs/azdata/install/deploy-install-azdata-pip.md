---
title: Installation von azdata mithilfe von pip
titleSuffix: SQL Server big data clusters
description: Erfahren Sie, wie Sie das azdata-Tool zum Installieren und Verwalten Big Data-Clustern mit pip installieren.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 01/07/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 51faf26a6414854ad3b2b1c2d205304e9b3dfb36
ms.sourcegitcommit: 883435b4c7366f06ac03579752093737b098feab
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/28/2020
ms.locfileid: "89733867"
---
# <a name="install-azdata-with-pip"></a>Installieren von `azdata` mit `pip`

[!INCLUDE[SQL Server 2019](../../includes/applies-to-version/sqlserver2019.md)]

In diesem Artikel wird beschrieben, wie Sie das `azdata`-Tool mithilfe von `pip` unter Windows oder Linux installieren.

Unter Windows und Linux (Ubuntu-Distribution) ist es einfacher, wenn Sie einen [Paket-Manager](./deploy-install-azdata-installer.md) für die Installation verwenden.

## <a name="prerequisites"></a><a id="prerequisites"></a> Voraussetzungen

`azdata` ist ein in Python geschriebenes Befehlszeilen-Hilfsprogramm, das es Clusteradministratoren ermöglicht, den Big Data-Cluster über REST-APIs zu starten und zu verwalten. Die mindestens erforderliche Python-Version ist v3.5. `pip` ist zum Herunterladen und Installieren des `azdata`-Tools erforderlich. Die nachfolgenden Anweisungen enthalten Beispiele für Windows und Ubuntu. Informationen zum Installieren von Python auf anderen Plattformen finden Sie in der [Python-Dokumentation](https://wiki.python.org/moin/BeginnersGuide/Download).
Installieren und aktualisieren Sie außerdem die aktuelle Version des Python-Pakets `requests`:

```bash
pip3 install -U requests
```

> [!IMPORTANT]
> Wenn Sie eine neuere Version von Big Data-Clustern installieren, sollten Sie Ihre Daten sichern und den alten Cluster löschen, bevor Sie `azdata` aktualisieren und das neue Release installieren. Weitere Informationen finden Sie unter [Upgrade auf ein neues Release](../../big-data-cluster/deployment-upgrade.md).

## <a name="windows-azdata-installation"></a><a id="windows"></a> Installation von `azdata` unter Windows

1. Laden Sie das erforderliche Python-Paket aus [https://www.python.org/downloads/](https://www.python.org/downloads/) auf einen Windows-Client herunter. Für Python 3.5.3 und höher wird bei der Installation von Python auch pip3 installiert. 

   > [!TIP] 
   > Wenn Sie Python 3 installieren, wählen Sie aus, dass Python `PATH` hinzugefügt wird. Wenn nicht, können Sie später ermitteln, wo sich pip3 befindet, und pip3 manuell `PATH` hinzufügen.

1. Öffnen Sie eine neue Windows PowerShell-Sitzung, um den aktuellen Pfad mit Python zu verwenden.

1. Wenn Sie vorherige Releases von `azdata` installiert haben, müssen Sie diese zuerst deinstallieren, bevor Sie die neueste Version installieren.

   Führen Sie für CTP 3.2 oder RC1 den folgenden Befehl aus.

   ```bash
   pip3 uninstall -r https://azdatacli.blob.core.windows.net/python/azdata/2019-ctp3.2/requirements.txt
   ```
   oder
   ```bash
   pip3 uninstall -r https://azdatacli.blob.core.windows.net/python/azdata/2019-rc1/requirements.txt
   ```

1. Installieren Sie `azdata` mithilfe des folgenden Befehls:

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

1. Aktualisieren Sie pip3:

   ```bash
   sudo -H pip3 install --upgrade pip
   ```

1. Wenn Sie vorherige Releases von `azdata` installiert haben, müssen Sie diese zuerst deinstallieren, bevor Sie die neueste Version installieren.

   Führen Sie für CTP 3.2 oder RC1 den folgenden Befehl aus.

   ```bash
   pip3 uninstall -r https://azdatacli.blob.core.windows.net/python/azdata/2019-ctp3.2/requirements.txt
   ```
   oder
   ```bash
   pip3 uninstall -r https://azdatacli.blob.core.windows.net/python/azdata/2019-rc1/requirements.txt
   ```

1. Installieren Sie `azdata` mithilfe des folgenden Befehls:

   ```bash
   pip3 install -r https://aka.ms/azdata --user
   ```

   > [!NOTE]
   > Mit der Befehlszeilenoption `--user` wird `azdata` im Python-Benutzerinstallationsverzeichnis installiert. Dies ist unter Linux in der Regel `~/.local/bin`. Fügen Sie entweder dieses Verzeichnis dem Pfad hinzu, oder navigieren Sie zum Benutzerinstallationsverzeichnis, und führen Sie `./azdata` dort aus.

## <a name="install-azdata-on-macos-or-os-x"></a><a id="macOSX"></a> Installation von `azdata` unter macOS oder OS X

Befolgen Sie diese Schritte, um `azdata` unter macOS oder OS X zu installieren. Führen Sie für jeden Schritt das Beispiel im Terminal aus.

1. Installieren Sie auf einem macOS-Client [Homebrew](https://brew.sh), sofern Sie das noch nicht getan haben:

   ```
   /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
   ```

1. Installieren Sie mindestens Version 3.0 von Python und pip.

   ```
   brew install python3
   ```

1. Installieren von Abhängigkeiten:

   ```
   pip3 install -U requests
   brew install freetds
   ```

1. Wenn Sie vorherige Releases des Tools installiert haben, müssen Sie diese zuerst deinstallieren, bevor Sie die neueste Version von `azdata` installieren. Mit dem folgenden Befehl wird die Version von `azdata` entfernt.

   ```
   pip3 uninstall -r https://azdatacli.blob.core.windows.net/python/azdata/2019-rc1/requirements.txt
   ```

1. Installieren Sie `azdata` mithilfe des folgenden Befehls:

   ```
   pip3 install -r https://aka.ms/azdata
   ```

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu Big Data-Clustern finden Sie unter [Was sind [!INCLUDE[big-data-clusters-2019](../../includes/ssbigdataclusters-ver15.md)]?](../../big-data-cluster/big-data-cluster-overview.md).
