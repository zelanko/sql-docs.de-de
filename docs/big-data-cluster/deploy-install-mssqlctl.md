---
title: Installieren von mssqlctl
titleSuffix: SQL Server big data clusters
description: Erfahren Sie, wie das Mssqlctl-Tool zum Installieren und Verwalten von SQL Server-2019 big Data-Clustern (Vorschau) zu installieren.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 03/27/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: d9c35971c0c0acf69065734cdcdbe670710ef5e4
ms.sourcegitcommit: 46a2c0ffd0a6d996a3afd19a58d2a8f4b55f93de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/15/2019
ms.locfileid: "59582384"
---
# <a name="install-mssqlctl-to-manage-sql-server-big-data-clusters"></a>Installieren Sie Mssqlctl zum Verwalten von SQL Server-big Data-Cluster

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

In diesem Artikel wird beschrieben, wie zum Installieren der **Mssqlctl** Tool unter Windows oder Linux.

**Mssqlctl** ist ein Befehlszeilenprogramm, das in Python geschrieben wurde, ermöglicht das Clustern von Administratoren zum Starten und Verwalten der big Data-Cluster über REST-APIs. Die Python-Mindestversion erforderlich ist, V3. 5. Außerdem benötigen Sie `pip` dient zum Herunterladen und installieren **Mssqlctl** Tool. Die folgenden Anweisungen finden Sie Beispiele für Windows und Ubuntu. Installieren von Python auf anderen Plattformen, finden Sie unter den [Python-Dokumentation](https://wiki.python.org/moin/BeginnersGuide/Download).

> [!IMPORTANT]
> Wenn Sie eine neuere Version von big Data-Cluster installieren, müssen Sie sichern Sie Ihre Daten und löschen Sie den alten Cluster *vor* aktualisieren **Mssqlctl** und die neue Version installieren. Weitere Informationen finden Sie unter [ein Upgrade auf ein neues Release](deployment-guidance.md#upgrade).

## <a id="windows"></a> Windows-Mssqlctl-installation

1. Laden Sie auf einem Windows-Client die erforderlichen Python-Pakets aus [ https://www.python.org/downloads/ ](https://www.python.org/downloads/). Für python3.5.3 und höher, ist auch pip3 installiert, bei der Installation von Python. 

   > [!TIP] 
   > Wählen Sie bei der Installation von Python3 Hinzufügen von Python auf Ihrer **Pfad**. Wenn Sie nicht, können Sie später zu finden, wo sich pip3 befindet und manuell hinzufügen, damit Ihre **Pfad**.

1. Öffnen Sie eine neue Windows PowerShell-Sitzung aus, sodass wird den aktuellsten Pfad mit Python in es.

1. Wenn Sie alle früheren Versionen von haben **Mssqlctl** installiert, es ist wichtig, deinstallieren Sie **Mssqlctl** vor der Installation der neuesten Version.

   Wenn Sie Unisntalling Mssqlctl sind, CTP-Version entspricht Version 2.2 oder niedriger ausführen:

   ```powershell
   pip3 uninstall mssqlctl
   ```

   Für CTP 2.3 oder höher ausführen (ersetzen Sie dies `ctp-2.3` im Befehl mit der Version der Mssqlctl, die Sie deinstallieren):

   ```powershell
   pip3 uninstall -r  https://private-repo.microsoft.com/python/ctp-2.3/mssqlctl/requirements.txt
   ```

1. Installieren Sie **Mssqlctl** mit den folgenden Befehl aus:

   ```powershell
   pip3 install -r  https://private-repo.microsoft.com/python/ctp-2.4/mssqlctl/requirements.txt
   ```

## <a id="linux"></a> Linux-Mssqlctl-installation

Unter Linux müssen Sie Python 3.5 zu installieren und aktualisieren Sie Pip. Das folgende Beispiel zeigt die Befehle, die für Ubuntu funktionieren würden. Andere Linux-Plattformen finden Sie unter den [Python-Dokumentation](https://wiki.python.org/moin/BeginnersGuide/Download).

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

1. Wenn Sie alle früheren Versionen von haben **Mssqlctl** installiert, es ist wichtig, deinstallieren Sie **Mssqlctl** vor der Installation der neuesten Version.

   Wenn Sie Unisntalling Mssqlctl sind, CTP-Version entspricht Version 2.2 oder niedriger ausführen:

   ```bash
   pip3 uninstall mssqlctl
   ```

   Für CTP 2.3 oder höher ausführen (ersetzen Sie dies `ctp-2.3` im Befehl mit der Version der Mssqlctl, die Sie deinstallieren):

   ```bash
   pip3 uninstall -r  https://private-repo.microsoft.com/python/ctp-2.3/mssqlctl/requirements.txt
   ```

1. Installieren Sie **Mssqlctl** mit den folgenden Befehl aus:

   ```bash
   pip3 install -r  https://private-repo.microsoft.com/python/ctp-2.4/mssqlctl/requirements.txt --user
   ```

   > [!NOTE]
   > Die `--user` Switch Mssqlctl installiert, für das Installationsverzeichnis des Python-Benutzer. Dies ist normalerweise `~/.local/bin` unter Linux. Dieses Verzeichnis zu Ihrem Pfad hinzufügen oder navigieren Sie zum Verzeichnis installieren, und führen Sie `./mssqlctl` von dort aus.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen über big Data-Cluster finden Sie unter [was SQL Server-2019 big Data-Cluster sind?](big-data-cluster-overview.md).
