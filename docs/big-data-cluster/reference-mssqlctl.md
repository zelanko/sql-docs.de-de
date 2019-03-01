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
ms.openlocfilehash: be1ece46bd171370a91273c832bf89a0bf426cd3
ms.sourcegitcommit: 2533383a7baa03b62430018a006a339c0bd69af2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/01/2019
ms.locfileid: "57018366"
---
# <a name="mssqlctl"></a>mssqlctl

Der folgende Artikel bietet Referenz für die **Mssqlctl** Tool für SQL Server-2019 big Data-Cluster (Vorschau).

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