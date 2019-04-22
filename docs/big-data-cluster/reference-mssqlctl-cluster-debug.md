---
title: Mssqlctl Cluster Debug-Referenz
titleSuffix: SQL Server big data clusters
description: Der Referenzartikel für die Mssqlctl Cluster-Befehle.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: b12b0421cf32a36cfd6d681bc90ad9ca7c3f9209
ms.sourcegitcommit: 323d2ea9cb812c688cfb7918ab651cce3246c296
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2019
ms.locfileid: "58860551"
---
# <a name="mssqlctl-cluster-debug"></a>Debuggen des mssqlctl-Clusters

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Der folgende Artikel bietet Referenz für die **Cluster Debug** Befehle in der **Mssqlctl** Tool. Weitere Informationen zu anderen **Mssqlctl** Befehle finden Sie unter [Mssqlctl Verweis](reference-mssqlctl.md).

## <a id="commands"></a> Befehle

|||
|---|---|
| [copy-logs](#copy-logs) | Kopieren Sie Protokolle. |
| [dump](#dump) | Dump der Trigger-Protokollierung. |

## <a id="copy-logs"></a> Cluster-Debug-Protokolle kopieren

Kopieren Sie Protokolle.

```
mssqlctl cluster debug copy-logs
   --namespace
   [--container]
   [--pod]
   [--target-folder]
   [--timeout]
```

### <a name="parameters"></a>Parameter

| Parameter | Description |
|---|---|
| **– Namespace - n** | Clustername für Kubernetes-Namespace verwendet. Erforderlich. |
| **--container -c** | Kopieren Sie die Protokolle für Container mit einem ähnlichen Namen, Optional, standardmäßig kopiert Protokolle für alle Container. Kann nicht mehrmals angegeben werden. Wenn mehrere Male angegeben, wird zuletzt eines verwendet werden. |
| **--pod -p** | Kopieren Sie die Protokolle für die Pods mit ähnlichen Namen ein. Optional, Kopien der Standardprotokolle für alle Pods. Kann nicht mehrmals angegeben werden. Wenn mehrere Male angegeben, wird zuletzt eines verwendet werden. |
| **--Target-Ordner "" - d** | Ziel-Ordnerpfad zum Kopieren der Protokolle an. Optional, erstellt standardmäßig das Ergebnis in den lokalen Ordner.  Kann nicht mehrmals angegeben werden. Wenn mehrere Male angegeben, wird zuletzt eines verwendet werden. |
| **--timeout -t** | Die Anzahl der Sekunden warten, bis der Befehl ausgeführt werden soll. Der Standardwert ist 0 unbegrenzt ist. |

## <a id="dump"></a> Cluster-debugdumpdateien

Dump der Trigger-Protokollierung.

```
mssqlctl cluster debug dump
   [--container]
   [--namespace]
   --target-folder
```

### <a name="parameters"></a>Parameter

| Parameter | Description |
|---|---|
| **--container -c** | Kopieren Sie die Protokolle für Container mit einem ähnlichen Namen, Optional, standardmäßig kopiert Protokolle für alle Container. Kann nicht mehrmals angegeben werden. Wenn mehrere Male angegeben, wird zuletzt eines verwendet werden.  Zulässige Werte: Mssql-Controller. |
| **– Namespace - n** | Clustername für Kubernetes-Namespace verwendet. Erforderlich. |
| **--Target-Ordner "" - d** | Ziel-Ordnerpfad zum Kopieren der Protokolle an. Optional, erstellt standardmäßig das Ergebnis in den lokalen Ordner.  Kann nicht mehrmals angegeben werden. Wenn mehrere Male angegeben, wird zuletzt eines verwendet werden.  Standardwert: `./output/dump`. Erforderlich. |

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu anderen **Mssqlctl** Befehle finden Sie unter [Mssqlctl Verweis](reference-mssqlctl.md). Weitere Informationen zum Installieren der **Mssqlctl** finden Sie unter [Mssqlctl zum Verwalten von SQL Server-2019 big Data-Cluster installieren](deploy-install-mssqlctl.md).