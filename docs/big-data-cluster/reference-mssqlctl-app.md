---
title: Referenz zu app mssqlctl
titleSuffix: SQL Server 2019 big data clusters
description: Der Referenzartikel für die Mssqlctl app Befehle.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: fa2b43c352fbab39cd00112b9646a87a2b752f5b
ms.sourcegitcommit: 2533383a7baa03b62430018a006a339c0bd69af2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/01/2019
ms.locfileid: "57018486"
---
# <a name="mssqlctl-app"></a>Mssqlctl-app

Der folgende Artikel bietet Referenz für die **app** Befehle in der **Mssqlctl** Tool. Weitere Informationen zu anderen **Mssqlctl** Befehle finden Sie unter [Mssqlctl Verweis](reference-mssqlctl.md).

## <a id="commands"></a> Befehle

|||
|---|---|
| [create](#create) | Erstellen Sie die Anwendung. |
| [delete](#delete) | Löschen Sie die Anwendung. |
| [describe](#describe) | Beschreiben Sie die Anwendung. |
| [init](#init) | KickStart neue Anwendung Gerüst. |
| [list](#list) | Auflisten von Anwendungen. |
| [run](#run) | Führen Sie die Anwendung. |
| [update](#update) | Aktualisieren Sie die Anwendung. |
| [template](reference-mssqlctl-app-template.md) | Vorlage-Befehle. |

## <a id="create"></a> Mssqlctl-app erstellen

Erstellen Sie die Anwendung.

```
mssqlctl app create
   --assets
   --code
   --description
   --entrypoint
   --inputs
   --name
   --outputs
   --runtime
   --spec
   --version
   --yes
```

### <a name="parameters"></a>Parameter

| Parameter | Description |
|---|---|
| **– Objekte – ein** | Liste der zusätzlichen Datei Anwendungsressourcen eingeschlossen werden sollen. |
| **--code -c** | Pfad zum R oder Python-Codedatei. |
| **--description -d** | Beschreibung der Anwendung. |
| **--entrypoint** |  |
| **--inputs** | Schema für Eingabeparameter. |
| **--name -n** | Anwendungsname |
| **--outputs** | Schema der Ausgabe-Parameter. |
| **--Common Language Runtime - r** | Laufzeit der Anwendung.  Zulässige Werte: Mleap, Python, R, SSIS. |
| **--spec -s** | Der Pfad zu einem Verzeichnis mit einer Spezifikation YAML-Datei, die die Anwendung beschreibt. |
| **--Version - V** | Version der Anwendung. |
| **--yes -y** | Keine Aufforderung zur Bestätigung beim Erstellen einer Anwendung aus der CWD spec.yaml-Datei. |

### <a name="examples"></a>Beispiele

Erstellen einer neuen Anwendung über spec.yaml (empfohlen).

```
mssqlctl app create --spec /path/to/dir/with/spec/yaml
```

Erstellen Sie eine neue Python-app-Inline mit Argumenten.

```
mssqlctl app create --name add --version v1 --inputs x=float, y=float --outputs result=float --runtime Python --code add.py  --init init.py
```

Erstellen Sie eine neue R-Anwendung-Inline mit Argumenten.

```
mssqlctl app create --name add --version v1 --inputs x=numeric, y=numeric --outputs result=numeric --runtime R --code add.R  --init init.R
```

Erstellen Sie Inline eine neue R-Anwendung, mit zusätzlichen Dateiressourcen eingeschlossen werden sollen.

```
mssqlctl app create --name add --version v1 --runtime R --code  add.R --assets file.RData,/path/to/more/files
```

## <a id="delete"></a> Mssqlctl app löschen

Löschen Sie die Anwendung.

```
mssqlctl app delete
   --name
   --version
```

### <a name="parameters"></a>Parameter

| Parameter | Description |
|---|---|
| **--name -n** | Anwendungsname |
| **--Version - V** | Version der Anwendung. |

### <a name="examples"></a>Beispiele

Löschen Sie die Anwendung nach Name und Version.

```
mssqlctl app delete --name reduce --version v1
```

## <a id="describe"></a> Beschreiben Sie Mssqlctl-app

Beschreiben Sie die Anwendung.

```
mssqlctl app describe
   --name
   --spec
   --version
```

### <a name="parameters"></a>Parameter

| Parameter | Description |
|---|---|
| **--name -n** | Anwendungsname |
| **--spec -s** | Der Pfad zu einem Verzeichnis mit einer Spezifikation YAML-Datei, die die Anwendung beschreibt. |
| **--Version - V** | Version der Anwendung. |

### <a name="examples"></a>Beispiele

Eine Beschreibung der Anwendung.

```
mssqlctl app describe --name reduce --version v1
```

## <a id="init"></a> Mssqlctl app init

KickStart neue Anwendung Gerüst.

```
mssqlctl app init
   --destination
   --name
   --spec
   --template
   --url
   --version
```

### <a name="parameters"></a>Parameter

| Parameter | Description |
|---|---|
| **--Destination -d.** | Die Position, um das Gerüst für die Anwendung zu platzieren. Standard: Aktuelles Arbeitsverzeichnis. |
| **--name -n** | Anwendungsname |
| **--spec -s** | Generieren Sie nur eine Anwendung spec.yaml. |
| **--template -t** | Name der Vorlage. Führen Sie eine vollständige Liste deaktiviert unterstützten Vorlagennamen `mssqlctl app template list`. |
| **--url -u** | Geben Sie einen andere Vorlage Repository-Speicherort. Standardwert: https://github.com/Microsoft/sql-server-samples.git. |
| **--Version - V** | Version der Anwendung. |

### <a name="examples"></a>Beispiele

Erstellen des Gerüsts für einer neuen Anwendung `spec.yaml` nur.

```
mssqlctl app init --spec
```

Erstellen des Gerüsts für eine neue R-Anwendung Anwendung Gerüst basierend auf den `r` Vorlage.

```
mssqlctl app init --name reduce --template r
```

Erstellen ein neues Python-Anwendung Anwendung Gerüsts basierend auf den `python` Vorlage.

```
mssqlctl app init --name reduce --template python
```

Erstellen Sie ein neues SSIS-Anwendung Anwendung Grundgerüst basierend auf den `ssis` Vorlage.

```
mssqlctl app init --name reduce --template ssis
```

## <a id="list"></a> Mssqlctl app-Liste

Auflisten von Anwendungen.

```
mssqlctl app list
   --name
   --version
```

### <a name="parameters"></a>Parameter

| Parameter | Description |
|---|---|
| **--name -n** | Anwendungsname |
| **--Version - V** | Version der Anwendung. |

### <a name="examples"></a>Beispiele

Listen Sie die Anwendung nach Name und Version.

```
mssqlctl app list --name reduce  --version v1
```

Alle Anwendungsprogrammversionen nach Name auflisten.

```
mssqlctl app list --name reduce
```

Listen Sie alle Anwendungen.

```
mssqlctl app list
```

## <a id="run"></a> Mssqlctl-app-Ausführung

Führen Sie die Anwendung.

```
mssqlctl app run
   --name
   --version
   --inputs
```

### <a name="parameters"></a>Parameter

| Parameter | Description |
|---|---|
| **--name -n** | Anwendungsname |
| **--Version - V** | Version der Anwendung. |
| **--inputs** | Parameter in eine CSV-Datei der eingabeanwendung `name=value` Format. |

### <a name="examples"></a>Beispiele

Führen Sie Anwendung ohne Eingabeparameter aus.

```
mssqlctl app run --name reduce --version v1
```

Führen Sie Anwendung mit 1 Eingabeparameter an.

```
mssqlctl app run --name reduce --version v1 --inputs x=10
```

Die Anwendung mit mehreren Eingabeparametern ausführen.

```
mssqlctl app run --name reduce --version v1 --inputs x=10,y5.6
```

## <a id="update"></a> Aktualisieren der Mssqlctl-app

Aktualisieren Sie die Anwendung.

```
mssqlctl app update
   --spec
   --yes
```

### <a name="parameters"></a>Parameter

| Parameter | Description |
|---|---|
| **--spec -s** | Der Pfad zu einem Verzeichnis mit einer Spezifikation YAML-Datei, die die Anwendung beschreibt. |
| **--yes -y** | Keine Aufforderung zur Bestätigung bei der Aktualisierung einer Anwendung aus der CWD spec.yaml-Datei. |

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu anderen **Mssqlctl** Befehle finden Sie unter [Mssqlctl Verweis](reference-mssqlctl.md). Weitere Informationen zum Installieren der **Mssqlctl** finden Sie unter [Mssqlctl zum Verwalten von SQL Server-2019 big Data-Cluster installieren](deploy-install-mssqlctl.md).