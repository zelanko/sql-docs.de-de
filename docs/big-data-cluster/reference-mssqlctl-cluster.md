---
title: Mssqlctl Cluster-Referenz
titleSuffix: SQL Server big data clusters
description: Der Referenzartikel für die Mssqlctl Cluster-Befehle.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: e4e54ac3c7206ad8a6592c8cfe0b45d9ea4b8fd8
ms.sourcegitcommit: 323d2ea9cb812c688cfb7918ab651cce3246c296
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2019
ms.locfileid: "58860471"
---
# <a name="mssqlctl-cluster"></a>mssqlctl-Cluster

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Der folgende Artikel bietet Referenz für die **Cluster** Befehle in der **Mssqlctl** Tool. Weitere Informationen zu anderen **Mssqlctl** Befehle finden Sie unter [Mssqlctl Verweis](reference-mssqlctl.md).

## <a id="commands"></a> Befehle

|||
|---|---|
| [create](#create) | Cluster zu erstellen. |
| [delete](#delete) | Löschen Sie Cluster. |
| [config](reference-mssqlctl-cluster-config.md) | Konfigurationsbefehle-Cluster. |
| [debug](reference-mssqlctl-cluster-debug.md) | Debug-Befehle. |

## <a id="create"></a> Mssqlctl-Cluster erstellen

Cluster zu erstellen.

```
mssqlctl cluster create
   --name
   --accept-eula
```

### <a name="parameters"></a>Parameter

| Parameter | Description |
|---|---|
| **--name -n** | Clustername für Kubernetes-Namespace verwendet. |
| **--accept-eula -e** | Stimmen Sie den Lizenzbedingungen zu? \[Ja/Nein\].  Zulässige Werte: Nein, Ja. Erforderlich. |

## <a id="delete"></a> Mssqlctl Cluster löschen

Löschen Sie Cluster.

```
mssqlctl cluster delete
   --name
   [--force]
```

### <a name="parameters"></a>Parameter

| Parameter | Description |
|---|---|
| **--name -n** | Clustername für Kubernetes-Namespace verwendet. Erforderlich. |
| **--force -f** | -Force-Delete Cluster. |

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu anderen **Mssqlctl** Befehle finden Sie unter [Mssqlctl Verweis](reference-mssqlctl.md). Weitere Informationen zum Installieren der **Mssqlctl** finden Sie unter [Mssqlctl zum Verwalten von SQL Server-2019 big Data-Cluster installieren](deploy-install-mssqlctl.md).