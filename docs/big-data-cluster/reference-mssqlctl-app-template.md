---
title: Referenz zu Mssqlctl app-Vorlagen
titleSuffix: SQL Server 2019 big data clusters
description: Der Referenzartikel für die Befehle für Mssqlctl app-Vorlage.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 16583ba970bfc13312864ea2e9d2571b04c20fcb
ms.sourcegitcommit: d7ed341b2c635dcdd6b0f5f4751bb919a75a6dfe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2019
ms.locfileid: "57527223"
---
# <a name="mssqlctl-app-template"></a>Mssqlctl-app-Vorlage

Der folgende Artikel bietet Referenz für die **-app-Vorlage** Befehle in der **Mssqlctl** Tool. Weitere Informationen zu anderen **Mssqlctl** Befehle finden Sie unter [Mssqlctl Verweis](reference-mssqlctl.md).

## <a id="commands"></a> Befehle

|||
|---|---|
| [list](#list) | Rufen Sie die unterstützte Vorlagen. |
| [pull](#pull) | Download unterstützt Vorlagen. |

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
| **--name -n** | Name der Vorlage. Führen Sie eine vollständige Liste deaktiviert unterstützten Vorlagennamen `mssqlctl app template list`. |
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