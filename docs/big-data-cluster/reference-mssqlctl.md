---
title: Mssqlctl-Referenz
titleSuffix: SQL Server 2019 big data clusters
description: Der Referenzartikel für die Mssqlctl Befehle.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: d15b4149fe336b173452030ec67fb7f229e6ae3d
ms.sourcegitcommit: d7ed341b2c635dcdd6b0f5f4751bb919a75a6dfe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2019
ms.locfileid: "57527283"
---
# <a name="mssqlctl"></a>mssqlctl

Der folgende Artikel bietet Referenz für die **Mssqlctl** tool für [SQL Server-2019 big Data-Clustern (Vorschau)](big-data-cluster-overview.md). Weitere Informationen zum Installieren der **Mssqlctl** finden Sie unter [Mssqlctl zum Verwalten von SQL Server-2019 big Data-Cluster installieren](deploy-install-mssqlctl.md).

## <a id="commands"></a> Befehle

|||
|---|---|
| [app](reference-mssqlctl-app.md) | Erstellen, löschen, ausführen und Verwalten von Anwendungen. |
| [cluster](reference-mssqlctl-cluster.md) | Wählen Sie, verwalten Sie und betreiben Sie Cluster. |
| [login](#login) | Melden Sie sich an den Cluster. |
| [logout](#logout) | Melden Sie sich der Cluster. |
| [storage](reference-mssqlctl-storage.md) | Verwalten von Clusterspeicher. |

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