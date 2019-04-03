---
title: Referenz zu mssqlctl
titleSuffix: SQL Server big data clusters
description: Der Referenzartikel für die Mssqlctl Befehle.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: b050638ee0ca600c5df0ecdbe5616b801f41e7a8
ms.sourcegitcommit: 2de5446fbc57787f18a907dd5deb02a7831ec07d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/02/2019
ms.locfileid: "58860352"
---
# <a name="mssqlctl"></a>mssqlctl

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Der folgende Artikel bietet Referenz für die **Mssqlctl** tool für [SQL Server-2019 big Data-Clustern (Vorschau)](big-data-cluster-overview.md). Weitere Informationen zum Installieren der **Mssqlctl** finden Sie unter [Mssqlctl zum Verwalten von SQL Server-2019 big Data-Cluster installieren](deploy-install-mssqlctl.md).

## <a id="commands"></a> Befehle

|||
|---|---|
| [app](reference-mssqlctl-app.md) | Erstellen, löschen, ausführen und Verwalten von Anwendungen. |
| [Cluster](reference-mssqlctl-cluster.md) | Wählen Sie, verwalten Sie und betreiben Sie Cluster. |
| [login](#login) | Melden Sie sich an den Cluster. |
| [Abmelden](#logout) | Melden Sie sich der Cluster. |
| [Speicher](reference-mssqlctl-storage.md) | Verwalten von Clusterspeicher. |

## <a id="login"></a> Mssqlctl-Anmeldung

Melden Sie sich an den Cluster.

```
mssqlctl login
   --endpoint
   --password
   --username
```

### <a name="parameters"></a>Parameter

| Parameter | Description |
|---|---|
|**--Endpoint -e**| Cluster-Host und Port (z. b) `http://host:port"`. |
|**– Kennwort -p**| Kennwortanmeldeinformationen. |
|**--Username -u**| Benutzer des Kontos. |

### <a name="examples"></a>Beispiele

Melden Sie sich interaktiv an.

```
mssqlctl login
```

Melden Sie sich mit Benutzername und Kennwort.

```
mssqlctl login -u johndoe@contoso.com -p VerySecret
```

Melden Sie sich den Benutzernamen, Kennwort und clusterendpunkt.

```
mssqlctl login -u johndoe@contoso.com -p VerySecret --endpoint https://host.com:12800
```

## <a id="logout"></a> Mssqlctl Abmelden

Melden Sie sich der Cluster.

```
mssqlctl logout
   --username
```

### <a name="parameters"></a>Parameter

| Parameter | Description |
|---|---|
| **--Username -u** | Konto-Benutzer, sofern nicht vorhanden ist, werden Abmelden der aktuellen Aktives Konto. |

### <a name="examples"></a>Beispiele

Melden Sie sich diesen Benutzer.

```
mssqlctl logout --username admin
```

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Installieren der **Mssqlctl** finden Sie unter [Mssqlctl zum Verwalten von SQL Server-2019 big Data-Cluster installieren](deploy-install-mssqlctl.md).