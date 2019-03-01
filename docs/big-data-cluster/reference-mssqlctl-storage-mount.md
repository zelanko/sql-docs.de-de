---
title: Mssqlctl Storage Mount-Referenz
titleSuffix: SQL Server 2019 big data clusters
description: Der Referenzartikel für die Speicherbefehle Mssqlctl.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: a8580c3c52cda484581f1c88ccfc039d8bd0bf78
ms.sourcegitcommit: 2533383a7baa03b62430018a006a339c0bd69af2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/01/2019
ms.locfileid: "57018456"
---
# <a name="mssqlctl-storage-mount"></a>Mssqlctl Speicher bereitstellen

Der folgende Artikel bietet Referenz für die **Speicher bereitstellen** Befehle in der **Mssqlctl** Tool. Weitere Informationen zu anderen **Mssqlctl** Befehle finden Sie unter [Mssqlctl Verweis](reference-mssqlctl.md).

## <a id="commands"></a> Befehle

|||
|---|---|
| [create](#create) | Erstellen Sie Bereitstellungen von remote-speichern in HDFS. |
| [delete](#delete) | Löschen Sie Bereitstellungen von remote-speichern in HDFS. |
| [status](#status) | Status des Mount(s). |

## <a id="create"></a> Erstellen Sie Mssqlctl Speicher bereitstellen

Erstellen Sie Bereitstellungen von remote-speichern in HDFS.

```
mssqlctl storage mount create
   --mount-path
   --remote-uri
   [--credential-file]
```

### <a name="parameters"></a>Parameter

| Parameter | Description |
|---|---|
| **--mount-path** | HDFS-Pfad, in dem Bereitstellungspunkt (Ziel der Bereitstellung) erstellt werden muss. Erforderlich. |
| **--remote-uri** | Der URI der Remotespeicher, die bereitgestellte (Quelle Mount) verwendet werden soll. Erforderlich. |
| **--credential-file** | Datei mit den Anmeldeinformationen für den Zugriff auf die remote-Speicher. Die Anmeldeinformationen als Schlüssel angegeben werden, müssen = Wert-Paaren mit einem Schlüssel = Wert pro Zeile. Alle entspricht, in dem Schlüssel oder Werte müssen mit Escapezeichen versehen werden. Standardmäßig sind keine Anmeldeinformationen erforderlich. Die erforderlichen Schlüssel hängt davon ab, den Typ des remote-Speicher bereitgestellt wird und den Typ der Autorisierung verwendet. |

### <a name="examples"></a>Beispiele

Zum Bereitstellen der Container "Daten" in ADLS Gen 2-Konto "adlsv2example" HDFS-Pfad `/mounts/adlsv2/data` den gemeinsam verwendeten Schlüssel verwenden:

```
mssqlctl storage mount create --remote-uri abfs://data@adlsv2example.dfs.core.windows.net/ --mount-path /mounts/adlsv2/data --credentials credential_file
```

Zum Bereitstellen von eines Remotecluster mit HDFS (`hdfs://namenode1:8080/`) im lokalen HDFS-Pfad `/mounts/hdfs/`:

```
mssqlctl storage mount create --remote-uri hdfs://namenode1:8080/ --mount-path /mounts/hdfs/
```

## <a id="delete"></a> Mssqlctl Speicher Bereitstellung löschen

Löschen Sie Bereitstellungen von remote-speichern in HDFS.

```
mssqlctl storage mount delete
   --mount-path
```

### <a name="parameters"></a>Parameter

| Parameter | Description |
|---|---|
| **--mount-path** | Der HDFS-Pfad für die Bereitstellung, die gelöscht werden. Erforderlich. |

### <a name="examples"></a>Beispiele

Löschen Sie bereitstellen, die auf /mounts/adlsv2/data für ein ADLS-Gen-2-Speicherkonto erstellt.

```
mssqlctl storage mount delete --mount-path /mounts/adlsv2/data
```

## <a id="status"></a> Mssqlctl Storage-Bereitstellungsstatus

Status des Mount(s).

```
mssqlctl storage mount status
   --mount-path
```

### <a name="parameters"></a>Parameter

| Parameter | Description |
|---|---|
| **--mount-path** | Der Bereitstellungspfad. Erforderlich. |

### <a name="examples"></a>Beispiele

Bereitstellungsstatus anhand des Pfads abrufen

```
mssqlctl storage mount status --mount-path /mounts/hdfs
```

Status alle Bereitstellungen zu erhalten.

```
mssqlctl storage mount status
```

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu anderen **Mssqlctl** Befehle finden Sie unter [Mssqlctl Verweis](reference-mssqlctl.md). Weitere Informationen zum Installieren der **Mssqlctl** finden Sie unter [Mssqlctl zum Verwalten von SQL Server-2019 big Data-Cluster installieren](deploy-install-mssqlctl.md).