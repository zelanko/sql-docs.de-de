---
title: Installieren von mssqlctl
titleSuffix: SQL Server 2019 big data clusters
description: Erfahren Sie, wie das Mssqlctl-Tool zum Installieren und Verwalten von SQL Server-2019 big Data-Clustern (Vorschau) zu installieren.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/13/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: cb012492811383154d10358e1c3ee40c422e3813
ms.sourcegitcommit: 202ef5b24ed6765c7aaada9c2f4443372064bd60
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/12/2019
ms.locfileid: "54241691"
---
# <a name="install-mssqlctl-to-manage-sql-server-2019-big-data-clusters"></a>Installieren Sie Mssqlctl zum Verwalten von SQL Server-2019 big Data-Cluster

In diesem Artikel wird beschrieben, wie zum Installieren der **Mssqlctl** Tool unter Windows oder Linux.

**Mssqlctl** ist ein Befehlszeilenprogramm, das in Python geschrieben wurde, ermöglicht das Clustern von Administratoren zum Starten und Verwalten der big Data-Cluster über REST-APIs. Die Python-Mindestversion erforderlich ist, V3. 5. Außerdem benötigen Sie `pip` dient zum Herunterladen und installieren **Mssqlctl** Tool. Die folgenden Anweisungen finden Sie Beispiele für Windows und Ubuntu. Installieren von Python auf anderen Plattformen, finden Sie unter den [Python-Dokumentation](https://wiki.python.org/moin/BeginnersGuide/Download).

> [!IMPORTANT]
> Bei der Installation einer früheren Version von **Mssqlctl**, müssen Sie den Cluster löschen *vor* aktualisieren **Mssqlctl** und die neue Version installieren. Weitere Informationen finden Sie unter [ein Upgrade auf ein neues Release](deployment-guidance.md#upgrade).

## <a id="windows"></a> Windows-Mssqlctl-installation

1. Laden Sie auf einem Windows-Client die erforderlichen Python-Pakets aus [ https://www.python.org/downloads/ ](https://www.python.org/downloads/). Für python3.5.3 und höher, ist auch pip3 installiert, bei der Installation von Python. 

   > [!TIP] 
   > Wählen Sie bei der Installation von Python3 Hinzufügen von Python auf Ihrer **Pfad**. Wenn Sie nicht, können Sie später zu finden, wo sich pip3 befindet und manuell hinzufügen, damit Ihre **Pfad**.

1. Öffnen Sie eine neue Windows PowerShell-Sitzung aus, sodass wird den aktuellsten Pfad mit Python in es.

2. Installieren Sie **Mssqlctl** mit den folgenden Befehl aus:

   ```bash
   pip3 install --extra-index-url https://private-repo.microsoft.com/python/ctp-2.2 mssqlctl
   ```

## <a id="linux"></a> Linux-Mssqlctl-installation

Unter Linux müssen Sie Python 3.5 zu installieren und aktualisieren Sie Pip. Das folgende Beispiel zeigt die Befehle, die für Ubuntu funktionieren würden. Andere Linux-Plattformen finden Sie unter den [Python-Dokumentation](https://wiki.python.org/moin/BeginnersGuide/Download).

1. Installieren Sie die erforderlichen Python-Pakete:

   ```bash
   sudo apt-get update && /
   sudo apt-get install -y python3 && /
   sudo apt-get install -y python3-pip && /
   sudo -H pip3 install --upgrade pip
   ```

1. Installieren Sie **Mssqlctl** mit den folgenden Befehl aus:

   ```bash
   pip3 install --extra-index-url https://private-repo.microsoft.com/python/ctp-2.2 mssqlctl
   ```

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen über big Data-Cluster finden Sie unter [was SQL Server-2019 big Data-Cluster sind?](big-data-cluster-overview.md).
