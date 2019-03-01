---
title: Referenz für Mssqlctl Cluster-Konfiguration
titleSuffix: SQL Server 2019 big data clusters
description: Der Referenzartikel für die Mssqlctl Cluster-Befehle.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 26e93151a1150bbbbd1798b38486ca5b01aaab1d
ms.sourcegitcommit: 2533383a7baa03b62430018a006a339c0bd69af2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/01/2019
ms.locfileid: "57018436"
---
# <a name="mssqlctl-cluster-config"></a>Mssqlctl Cluster-Konfiguration

Der folgende Artikel bietet Referenz für die **cluster Config** Befehle in der **Mssqlctl** Tool. Weitere Informationen zu anderen **Mssqlctl** Befehle finden Sie unter [Mssqlctl Verweis](reference-mssqlctl.md).

## <a id="commands"></a> Befehle

|||
|---|---|
| [get](#get) | Rufen Sie Cluster an. |

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
| **--name -n** | Clustername für Kubernetes-Namespace verwendet. Erforderlich. |
| **--output-file -f** | Die Ausgabedatei zum Speichern des Ergebnisses in. Erforderlich. |

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu anderen **Mssqlctl** Befehle finden Sie unter [Mssqlctl Verweis](reference-mssqlctl.md). Weitere Informationen zum Installieren der **Mssqlctl** finden Sie unter [Mssqlctl zum Verwalten von SQL Server-2019 big Data-Cluster installieren](deploy-install-mssqlctl.md).