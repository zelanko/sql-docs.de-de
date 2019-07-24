---
title: Installieren von azdata
titleSuffix: SQL Server big data clusters
description: Erfahren Sie, wie Sie das Tool azdata zum Installieren und Verwalten von SQL Server 2019 Big Data Clustern (Vorschauversion) installieren.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 9444842081456563f411ad618f32b8dbd59f7513
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426440"
---
# <a name="install-azdata-to-manage-sql-server-big-data-clusters"></a>Installieren von azdata zum Verwalten von SQL Server Big Data Clustern

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

In diesem Artikel wird beschrieben, wie Sie das **azdata** -Tool für CTP 3,2 unter Windows oder Linux installieren.

## <a id="prerequisites"></a> Erforderliche Komponenten

**azdata** ist ein in Python geschriebenes Befehlszeilen-Hilfsprogramm, mit dem Cluster Administratoren den Big Data Cluster über Rest-APIs Bootstrap und verwalten können. Die mindestens erforderliche Python-Version ist v 3.5. Sie müssen auch über `pip` das verfügen, das zum herunterladen und Installieren des **azdata** -Tools verwendet wird. Die nachfolgenden Anweisungen enthalten Beispiele für Windows und Ubuntu. Informationen zum Installieren von python auf anderen Plattformen finden Sie in der [Python-Dokumentation](https://wiki.python.org/moin/BeginnersGuide/Download).
Außerdem müssen Sie die aktuellste Version von *Anforderungen* des python-Pakets installieren und aktualisieren:
```bash
pip3 install -U requests
```

> [!IMPORTANT]
> Wenn Sie eine neuere Version von Big Data Clustern installieren, müssen Sie die Daten sichern und den alten Cluster löschen, *bevor* Sie **azdata** aktualisieren und die neue Version installieren. Weitere Informationen finden Sie unter [Aktualisieren auf eine neue Version](deployment-upgrade.md).

## <a id="windows"></a>Windows azdata-Installation

1. Laden Sie auf einem Windows-Client das erforderliche python- [https://www.python.org/downloads/](https://www.python.org/downloads/)Paket aus herunter. Für python 3.5.3 und höher wird PIP3 auch bei der Installation von Python installiert. 

   > [!TIP] 
   > Wenn Sie Python3 installieren, wählen Sie aus, um python dem **Pfad**hinzuzufügen. Wenn Sie dies nicht tun, können Sie später ermitteln, wo sich PIP3 befindet, und Sie manuell zu Ihrem **Pfad**hinzufügen.

1. Öffnen Sie eine neue Windows PowerShell-Sitzung, sodass Sie den neuesten Pfad mit python in Ihr erhält.

1. Wenn Sie frühere Versionen des Tools installiert haben (previosly mit dem Namen **mssqlctl**), ist es wichtig, es zuerst zu deinstallieren, bevor Sie die neueste Version von **azdata**installieren.

   Führen Sie für CTP 3,1 oder niedriger den folgenden Befehl aus. Ersetzen `ctp3.1` Sie im Befehl durch die Version von **mssqlctl** , die Sie deinstallieren. 

   ```powershell
   pip3 uninstall -r https://private-repo.microsoft.com/python/ctp3.1/mssqlctl/requirements.txt
   ```

1. Wenn Sie frühere Versionen von **azdata** installiert haben, ist es wichtig, diese zuerst zu deinstallieren, bevor Sie die neueste Version installieren.

   Führen Sie für CTP 3,2 oder höher den folgenden Befehl aus. Ersetzen `ctp3.2` Sie im Befehl durch die Version von **azdata** , die Sie deinstallieren.

   ```powershell
   pip3 uninstall -r https://aka.ms/azdata
   ```

1. Installieren Sie **azdata** mit dem folgenden Befehl:

   ```powershell
   pip3 install -r https://aka.ms/azdata
   ```

## <a id="linux"></a>Linux azdata-Installation

Unter Linux müssen Sie Python 3,5 installieren und dann PIP aktualisieren. Das folgende Beispiel zeigt die Befehle, die für Ubuntu funktionieren. Informationen zu anderen Linux-Plattformen finden Sie in der [Python-Dokumentation](https://wiki.python.org/moin/BeginnersGuide/Download).

1. Installieren Sie die erforderlichen Python-Pakete:

   ```bash
   sudo apt-get update && /
   sudo apt-get install -y python3 && /
   sudo apt-get install -y python3-pip
   ```

1. Upgrade PIP3:

   ```bash
   sudo -H pip3 install --upgrade pip
   ```

1. Wenn Sie frühere Versionen des Tools installiert haben (zuvor " **mssqlctl**" genannt), ist es wichtig, es zuerst zu deinstallieren, bevor Sie die neueste Version von **azdata**installieren.

   Führen Sie für CTP 3,1 oder niedriger den folgenden Befehl aus. Ersetzen `ctp3.1` Sie im Befehl durch die Version von **mssqlctl** , die Sie deinstallieren. 

   ```powershell
   pip3 uninstall -r https://private-repo.microsoft.com/python/ctp3.1/mssqlctl/requirements.txt
   ```

1. Wenn Sie frühere Versionen von **azdata** installiert haben, ist es wichtig, diese zuerst zu deinstallieren, bevor Sie die neueste Version installieren.

   Führen Sie für CTP 3,2 oder höher den folgenden Befehl aus. Ersetzen `ctp3.2` Sie im Befehl durch die Version von **azdata** , die Sie deinstallieren.

   ```powershell
   pip3 uninstall -r https://aka.ms/azdata
   ```

1. Installieren Sie **azdata** mit dem folgenden Befehl:

   ```bash
   pip3 install -r https://aka.ms/azdata --user
   ```

   > [!NOTE]
   > Der `--user` Switch installiert azdata im python-Benutzer Installationsverzeichnis. Dies erfolgt in `~/.local/bin` der Regel unter Linux. Fügen Sie dieses Verzeichnis dem Pfad hinzu, oder navigieren Sie zum Benutzer Installationsverzeichnis, `./azdata` und führen Sie dort aus.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu Big Data Clustern finden Sie unter [Was sind SQL Server 2019 Big Data Cluster?](big-data-cluster-overview.md).
