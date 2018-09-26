---
title: Konfigurieren von persistenten Speicher (PMEM) für SQL Server unter Linux | Microsoft-Dokumentation
description: Dieser Artikel enthält eine schrittweise Anleitung zum Konfigurieren von PMEM unter Linux.
author: DBArgenis
ms.author: argenisf
manager: craigg
ms.date: 09/24/2018
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 42b51f28682ea7c53b5aa6f33ac2e6aa61a121ed
ms.sourcegitcommit: b7fd118a70a5da9bff25719a3d520ce993ea9def
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2018
ms.locfileid: "46715096"
---
# <a name="how-to-configure-persistent-memory-pmem-for-sql-server-on-linux"></a>Konfigurieren von persistenten Speicher (PMEM) für SQL Server unter Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

In diesem Artikel wird beschrieben, konfigurieren Sie den persistenten Speicher (PMEM) für SQL Server unter Linux. PMEM-Unterstützung unter Linux wurde in SQL Server 2019 CTP 2.0 eingeführt.

## <a name="overview"></a>Übersicht

SQL Server 2016 wurde die Unterstützung für Non-Volatile-DIMMs und eine Optimierung namens [Ende der Protokoll-Zwischenspeicherung auf NVDIMM]( https://blogs.msdn.microsoft.com/bobsql/2016/11/08/how-it-works-it-just-runs-faster-non-volatile-memory-sql-server-tail-of-log-caching-on-nvdimm/) , der verkürzt der Menge der Vorgänge, die zum Absichern einer Protokollpuffer in den permanenten Speicher benötigt. Diese nutzt die Windows Server Funktion, um direkt auf einem persistenten Speicher-Gerät im DAX-Modus zuzugreifen.

Vorschau der SQL Server-2019 erweitert die Unterstützung für den persistenten Speicher (PMEM) Geräte zu Linux, vollständige Erleuchtung von Daten- und Protokolldateien auf PMEM platziert bereitstellen. Erleuchtung bezieht sich auf die Methode des Zugriffs auf das Speichergerät mithilfe von effizienten Benutzerbereich Memcpy-Vorgängen. Anstatt dann die Datei Dateisystem- und Stapel, SQL Server nutzt die DAX-Unterstützung für Linux, um Daten in die Geräte, die Gebühren in minimaler Latenz direkt zu platzieren.

## <a name="enable-enlightenment-of-database-files"></a>Aktivieren Sie an Aufklärung von Datenbankdateien
Um Erleuchtung von Datenbankdateien in SQL Server unter Linux zu aktivieren, führen Sie die folgenden Schritte aus:

1. Konfigurieren Sie die Geräte In Linux, dies erfolgt mithilfe der `ndctl` Hilfsprogramm.

  - Installieren Sie die Installation `ndctl` Pmem Gerät konfigurieren. Sie finden es [hier](https://docs.pmem.io/getting-started-guide/installing-ndctl).
  - Verwenden Sie [Ndctl], um einen Namespace zu erstellen.

  ```bash 
  ndctl create-namespace -f -e namespace0.0 --mode=fsdax* –map=mem
  ```

  >[!NOTE]
  >Bei Verwendung von `ndctl` niedrigeren Version als 59, Verwendung `--mode=memory`.

  Verwendung `ndctl` um den Namespace zu überprüfen. Die folgende Beispielausgabe:

```bash
ndctl list
[
  {
    "dev":"namespace0.0",
    "mode":"memory",
    "size":1099511627776,
    "blockdev":"pmem0",
    "numa_node":0
  }
]
```

  - Erstellen und Bereitstellen von Pmem-Gerät

    Z. B. mit XFS

    ```bash
    mkfs.xfs -f /dev/pmem0
    mount –o dax,noatime /dev/pmem0 /mnt/dax
    xfs_io -c "extsize 2m" /mnt/dax
    ```

    Z. B. mit EXT4

    ```bash
    mkfs.ext4 -b 4096 -E stride=512 -F /dev/pmem0
    mount –o dax,noatime /dev/pmem0 /mnt/dax
    ```

  Sobald das Gerät wurde mit Ndctl konfiguriert, formatiert und eingebunden wurde, können Sie Datenbankdateien darin platzieren. Sie können auch eine neue Datenbank erstellen. 

1. Aktivieren Sie SQL Server-Datenbank, Datei Erleuchtung mithilfe von Ablaufverfolgungsflags 3979. Dieses Ablaufverfolgungsflag ist das Ablaufverfolgungsflag beim Start und muss daher mit dem Hilfsprogramm für die Mssql-Conf aktiviert werden.

1. Starten Sie SQL Server neu.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu SQL Server unter Linux finden Sie unter [SQL Server unter Linux](sql-server-linux-overview.md).
