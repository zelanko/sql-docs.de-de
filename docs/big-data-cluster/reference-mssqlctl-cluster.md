---
title: Mssqlctl Cluster-Referenz
titleSuffix: SQL Server 2019 big data clusters
description: Der Referenzartikel für die Mssqlctl Cluster-Befehle.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 130d3019d49deb7851696f6a1db2f77040734b31
ms.sourcegitcommit: d7ed341b2c635dcdd6b0f5f4751bb919a75a6dfe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2019
ms.locfileid: "57527213"
---
# <a name="mssqlctl-cluster"></a>Mssqlctl-cluster

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