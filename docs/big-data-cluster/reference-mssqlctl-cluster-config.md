---
title: Referenz für Mssqlctl Cluster-Konfiguration
titleSuffix: SQL Server big data clusters
description: Der Referenzartikel für die Mssqlctl Cluster-Befehle.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 57b77e83994f8471e677ba2ba367acc48a66cddd
ms.sourcegitcommit: 2de5446fbc57787f18a907dd5deb02a7831ec07d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/02/2019
ms.locfileid: "58860021"
---
# <a name="mssqlctl-cluster-config"></a>Konfiguration des mssqlctl-Clusters

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Der folgende Artikel bietet Referenz für die **cluster Config** Befehle in der **Mssqlctl** Tool. Weitere Informationen zu anderen **Mssqlctl** Befehle finden Sie unter [Mssqlctl Verweis](reference-mssqlctl.md).

## <a id="commands"></a> Befehle

|||
|---|---|
| [Erhalten](#get) | Rufen Sie Cluster an. |

## <a id="get"></a> Mssqlctl Cluster-Konfiguration zu erhalten.

Rufen Sie Cluster an.

```
mssqlctl cluster config get
   --name
   --output-file
```

### <a name="parameters"></a>Parameter

| Parameter | Description |
|---|---|
| **: Benennen von - n** | Clustername für Kubernetes-Namespace verwendet. Erforderlich. |
| **--Ausgabedatei - f** | Die Ausgabedatei zum Speichern des Ergebnisses in. Erforderlich. |

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu anderen **Mssqlctl** Befehle finden Sie unter [Mssqlctl Verweis](reference-mssqlctl.md). Weitere Informationen zum Installieren der **Mssqlctl** finden Sie unter [Mssqlctl zum Verwalten von SQL Server-2019 big Data-Cluster installieren](deploy-install-mssqlctl.md).