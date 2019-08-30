---
title: Installieren von azdata mithilfe von PIP
titleSuffix: SQL Server big data clusters
description: Erfahren Sie, wie Sie das Tool azdata für die Installation [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] und Verwaltung von (Vorschau) mit PIP installieren.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: a72e2ab39a17adef6c330f1ae17dcdc8a5dd8ddf
ms.sourcegitcommit: 71fac5fee00e0eca57e555f44274dd7e08d47e1e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/29/2019
ms.locfileid: "70160733"
---
# <a name="install-azdata-for-includebig-data-clusters-2019includesssbigdataclusters-ss-novermd-using-pip"></a>Installation `azdata` für [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] die Verwendung von`pip`

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

In diesem Artikel wird beschrieben, wie `azdata` Sie das Tool für die Release Candidate unter Windows oder `pip`Linux mit installieren.

## <a id="prerequisites"></a> Erforderliche Komponenten

`azdata`ist ein in Python geschriebenes Befehlszeilen-Hilfsprogramm, mit dem Cluster Administratoren den Big Data Cluster über Rest-APIs Bootstrap und verwalten können. Die mindestens erforderliche Python-Version ist v3.5. Sie müssen auch über `pip` das verfügen, das zum Herunterladen `azdata` und Installieren des Tools verwendet wird. Die nachfolgenden Anweisungen enthalten Beispiele für Windows und Ubuntu. Informationen zum Installieren von Python auf anderen Plattformen finden Sie in der [Python-Dokumentation](https://wiki.python.org/moin/BeginnersGuide/Download).
Außerdem müssen Sie die aktuelle Version von *Anforderungen* des Python-Pakets installieren und aktualisieren:
```bash
pip3 install -U requests
```

> [!IMPORTANT]
> Wenn Sie eine neuere Version von Big Data Clustern installieren, müssen Sie die Daten sichern und den alten Cluster löschen, *bevor* Sie `azdata` das Upgrade ausführen und das neue Release installieren. Weitere Informationen finden Sie unter [Upgrade auf ein neues Release](deployment-upgrade.md).

## <a id="windows"></a>Windows `azdata` -Installation

1. Laden Sie das erforderliche Python-Paket aus [https://www.python.org/downloads/](https://www.python.org/downloads/) auf einen Windows-Client herunter. Für Python 3.5.3 und höher wird bei der Installation von Python auch pip3 installiert. 

   > [!TIP] 
   > Wenn Sie Python3 installieren, wählen Sie aus, dass Python Ihrem **PATH** hinzugefügt wird. Wenn Sie dies nicht tun, können Sie später ermitteln, wo sich pip3 befindet, und pip3 manuell Ihrem **PATH** hinzufügen.

1. Öffnen Sie eine neue Windows PowerShell-Sitzung, um den aktuellen Pfad mit Python zu verwenden.

1. Wenn Sie frühere Versionen des Tools installiert haben (vor CTP 3,2 wurde das Tool als **mssqlctl**bezeichnet), ist es wichtig, es zuerst zu deinstallieren, bevor Sie die neueste Version von `azdata`installieren. Der folgende Befehl entfernt die CTP 3,1-Version von **mssqlctl**.

   ```powershell
   pip3 uninstall -r https://private-repo.microsoft.com/python/ctp3.1/mssqlctl/requirements.txt
   ```

1. Wenn Sie frühere Versionen von `azdata` installiert haben, ist es wichtig, diese zuerst zu deinstallieren, bevor Sie die neueste Version installieren.

   Führen Sie für CTP 3,2 den folgenden Befehl aus.

   ```powershell
   pip3 uninstall -r https://azdatacli.blob.core.windows.net/python/azdata/2019-ctp3.2/requirements.txt
   ```

1. Installieren `azdata` Sie mit dem folgenden Befehl:

   ```powershell
   pip3 install -r https://aka.ms/azdata
   ```

## <a id="linux"></a>Linux `azdata` -Installation

Unter Linux müssen Sie Python 3.5 installieren und dann pip aktualisieren. Das folgende Beispiel zeigt die Befehle, die für Ubuntu funktionieren. Informationen zu anderen Linux-Plattformen finden Sie in der [Python-Dokumentation](https://wiki.python.org/moin/BeginnersGuide/Download).

1. Installieren Sie die erforderlichen Python-Pakete:

   ```bash
   sudo apt-get update && \
   sudo apt-get install -y python3 && \
   sudo apt-get install -y python3-pip
   ```

1. Aktualisieren Sie pip3:

   ```bash
   sudo -H pip3 install --upgrade pip
   ```

1. Wenn Sie frühere Versionen des Tools installiert haben (vor CTP 3,2 wurde das Tool als **mssqlctl**bezeichnet), ist es wichtig, es zuerst zu deinstallieren, bevor Sie die neueste Version von `azdata`installieren. Der folgende Befehl entfernt die CTP 3,1-Version von **mssqlctl**.

   ```bash
   pip3 uninstall -r https://private-repo.microsoft.com/python/ctp3.1/mssqlctl/requirements.txt
   ```

1. Wenn Sie frühere Versionen von `azdata` installiert haben, ist es wichtig, diese zuerst zu deinstallieren, bevor Sie die neueste Version installieren.

   Führen Sie für CTP 3,2 den folgenden Befehl aus.

   ```bash
   pip3 uninstall -r https://azdatacli.blob.core.windows.net/python/azdata/2019-ctp3.2/requirements.txt
   ```

1. Installieren `azdata` Sie mit dem folgenden Befehl:

   ```bash
   pip3 install -r https://aka.ms/azdata --user
   ```

   > [!NOTE]
   > Der `--user` Switch wird `azdata` im python-Benutzer Installationsverzeichnis installiert. Dies ist unter Linux in der Regel `~/.local/bin`. Fügen Sie entweder dieses Verzeichnis dem Pfad hinzu, oder navigieren Sie zum Benutzerinstallationsverzeichnis, und führen Sie `./azdata` dort aus.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu Big Data Clustern finden Sie unter [was [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]ist?](big-data-cluster-overview.md).
