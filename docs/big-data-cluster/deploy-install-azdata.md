---
title: Installieren von azdata
titleSuffix: SQL Server big data clusters
description: Erfahren Sie, wie Sie das azdata-Tool zum Installieren und Verwalten von SQL Server 2019-Big Data-Clustern (Vorschauversion) installieren.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 9444842081456563f411ad618f32b8dbd59f7513
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2019
ms.locfileid: "68426440"
---
# <a name="install-azdata-to-manage-sql-server-big-data-clusters"></a>Installieren von „azdata“ zum Verwalten von SQL Server-Big Data-Clustern

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

In diesem Artikel wird beschrieben, wie Sie das **azdata**-Tool für CTP 3.2 unter Windows oder Linux installieren.

## <a id="prerequisites"></a> Erforderliche Komponenten

**azdata** ist ein in Python geschriebenes Befehlszeilen-Hilfsprogramm, das Clusteradministratoren ermöglicht, den Big Data-Cluster über REST-APIs zu starten und zu verwalten. Die mindestens erforderliche Python-Version ist v3.5. Sie benötigen auch `pip`, das zum Herunterladen und Installieren des **azdata**-Tools verwendet wird. Die nachfolgenden Anweisungen enthalten Beispiele für Windows und Ubuntu. Informationen zum Installieren von Python auf anderen Plattformen finden Sie in der [Python-Dokumentation](https://wiki.python.org/moin/BeginnersGuide/Download).
Außerdem müssen Sie die aktuelle Version von *Anforderungen* des Python-Pakets installieren und aktualisieren:
```bash
pip3 install -U requests
```

> [!IMPORTANT]
> Wenn Sie eine neuere Version von Big Data-Clustern installieren, müssen Sie die Daten sichern und den alten Cluster löschen, *bevor* Sie **azdata** aktualisieren und das neue Release installieren. Weitere Informationen finden Sie unter [Upgrade auf ein neues Release](deployment-upgrade.md).

## <a id="windows"></a> Installation von azdata unter Windows

1. Laden Sie das erforderliche Python-Paket aus [https://www.python.org/downloads/](https://www.python.org/downloads/) auf einen Windows-Client herunter. Für Python 3.5.3 und höher wird bei der Installation von Python auch pip3 installiert. 

   > [!TIP] 
   > Wenn Sie Python3 installieren, wählen Sie aus, dass Python Ihrem **PATH** hinzugefügt wird. Wenn Sie dies nicht tun, können Sie später ermitteln, wo sich pip3 befindet, und pip3 manuell Ihrem **PATH** hinzufügen.

1. Öffnen Sie eine neue Windows PowerShell-Sitzung, um den aktuellen Pfad mit Python zu verwenden.

1. Wenn Sie vorherige Releases des (früher als **mssqlctl** bezeichneten) Tools installiert haben, müssen Sie diese zuerst deinstallieren, bevor Sie die neueste Version von **azdata** installieren.

   Führen Sie für CTP 3.1 oder niedriger den folgenden Befehl aus. Ersetzen Sie `ctp3.1` im Befehl durch die Version von **mssqlctl**, die Sie deinstallieren. 

   ```powershell
   pip3 uninstall -r https://private-repo.microsoft.com/python/ctp3.1/mssqlctl/requirements.txt
   ```

1. Wenn Sie vorherige Releases von **azdata** installiert haben, müssen Sie diese zuerst deinstallieren, bevor Sie die neueste Version installieren.

   Führen Sie für CTP 3.2 oder höher den folgenden Befehl aus. Ersetzen Sie `ctp3.2` im Befehl durch die Version von **azdata**, die Sie deinstallieren.

   ```powershell
   pip3 uninstall -r https://aka.ms/azdata
   ```

1. Installieren Sie **azdata** mit folgendem Befehl:

   ```powershell
   pip3 install -r https://aka.ms/azdata
   ```

## <a id="linux"></a> Installation von azdata unter Linux

Unter Linux müssen Sie Python 3.5 installieren und dann pip aktualisieren. Das folgende Beispiel zeigt die Befehle, die für Ubuntu funktionieren. Informationen zu anderen Linux-Plattformen finden Sie in der [Python-Dokumentation](https://wiki.python.org/moin/BeginnersGuide/Download).

1. Installieren Sie die erforderlichen Python-Pakete:

   ```bash
   sudo apt-get update && /
   sudo apt-get install -y python3 && /
   sudo apt-get install -y python3-pip
   ```

1. Aktualisieren Sie pip3:

   ```bash
   sudo -H pip3 install --upgrade pip
   ```

1. Wenn Sie vorherige Releases des (früher als **mssqlctl** bezeichneten) Tools installiert haben, müssen Sie diese zuerst deinstallieren, bevor Sie die neueste Version von **azdata** installieren.

   Führen Sie für CTP 3.1 oder niedriger den folgenden Befehl aus. Ersetzen Sie `ctp3.1` im Befehl durch die Version von **mssqlctl**, die Sie deinstallieren. 

   ```powershell
   pip3 uninstall -r https://private-repo.microsoft.com/python/ctp3.1/mssqlctl/requirements.txt
   ```

1. Wenn Sie vorherige Releases von **azdata** installiert haben, müssen Sie diese zuerst deinstallieren, bevor Sie die neueste Version installieren.

   Führen Sie für CTP 3.2 oder höher den folgenden Befehl aus. Ersetzen Sie `ctp3.2` im Befehl durch die Version von **azdata**, die Sie deinstallieren.

   ```powershell
   pip3 uninstall -r https://aka.ms/azdata
   ```

1. Installieren Sie **azdata** mit folgendem Befehl:

   ```bash
   pip3 install -r https://aka.ms/azdata --user
   ```

   > [!NOTE]
   > Mit der Befehlszeilenoption `--user` wird azdata im Python-Benutzerinstallationsverzeichnis installiert. Dies ist unter Linux in der Regel `~/.local/bin`. Fügen Sie entweder dieses Verzeichnis dem Pfad hinzu, oder navigieren Sie zum Benutzerinstallationsverzeichnis, und führen Sie `./azdata` dort aus.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu Big Data-Clustern finden Sie unter [Was sind SQL Server 2019-Big Data-Cluster?](big-data-cluster-overview.md).
