---
title: Referenz zu Mssqlctl app-Vorlagen
titleSuffix: SQL Server big data clusters
description: Der Referenzartikel für die Befehle für Mssqlctl app-Vorlage.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: c67ed74750ac36d1a5c79503417414a9dd8ab6b5
ms.sourcegitcommit: 2de5446fbc57787f18a907dd5deb02a7831ec07d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/02/2019
ms.locfileid: "58860101"
---
# <a name="mssqlctl-app-template"></a>mssqlctl-App-Vorlage

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Der folgende Artikel bietet Referenz für die **-app-Vorlage** Befehle in der **Mssqlctl** Tool. Weitere Informationen zu anderen **Mssqlctl** Befehle finden Sie unter [Mssqlctl Verweis](reference-mssqlctl.md).

## <a id="commands"></a> Befehle

|||
|---|---|
| [Auflisten](#list) | Rufen Sie die unterstützte Vorlagen. |
| [Pullabonnement](#pull) | Download unterstützt Vorlagen. |

## <a id="list"></a> Liste der Mssqlctl app-Vorlage

Rufen Sie die unterstützte Vorlagen.

```
mssqlctl app template list
   --url
```

### <a name="parameters"></a>Parameter

| Parameter | Description |
|---|---|
| **--url -u** | Geben Sie einen andere Vorlage Repository-Speicherort. Standardwert: https://github.com/Microsoft/sql-server-samples.git. |

### <a name="examples"></a>Beispiele

Rufen Sie alle Vorlagen unter dem Standardspeicherort des Repositorys Vorlage.

```
mssqlctl app template list
```

Rufen Sie alle Vorlagen unter einem anderen Repository-Speicherort ab.

```
mssqlctl app template list --url https://github.com/diffrent/templates.git
```

## <a id="pull"></a> Mssqlctl app-Vorlage pull

Download unterstützt Vorlagen.

```
mssqlctl app template pull
   --destination
   --name
   --url
```

### <a name="parameters"></a>Parameter

| Parameter | Description |
|---|---|
| **--Destination -d.** | Position, an die Skelett-Anwendungsvorlage platzieren.  Standardwert:. / Vorlagen. |
| **: Benennen von - n** | Name der Vorlage. Führen Sie eine vollständige Liste deaktiviert unterstützten Vorlagennamen `mssqlctl app template list`. |
| **--url -u** | Geben Sie einen andere Vorlage Repository-Speicherort. Standard:
https://github.com/Microsoft/sql-server-samples.git. installiert haben. |

### <a name="examples"></a>Beispiele

Laden Sie alle Vorlagen unter dem Standardspeicherort des Repositorys Vorlage herunter.

```
mssqlctl app template pull
```

Laden Sie alle Vorlagen unter einem anderen Repository-Speicherort herunter.

```
mssqlctl app template list --url https://github.com/diffrent/templates.git
```

Laden Sie einzelne Vorlage anhand des Namens.

```
mssqlctl app template pull --name ssis
```

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu anderen **Mssqlctl** Befehle finden Sie unter [Mssqlctl Verweis](reference-mssqlctl.md). Weitere Informationen zum Installieren der **Mssqlctl** finden Sie unter [Mssqlctl zum Verwalten von SQL Server-2019 big Data-Cluster installieren](deploy-install-mssqlctl.md).