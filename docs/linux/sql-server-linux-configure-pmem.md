---
title: Konfigurieren von persistenten Speicher (PMEM) für SQL Server unter Linux | Microsoft-Dokumentation
description: Dieser Artikel enthält eine schrittweise Anleitung zum Konfigurieren von PMEM unter Linux.
author: DBArgenis
ms.author: argenisf
manager: craigg
ms.date: 11/06/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 07f068a24c60fe82c299387fe859f07296f21df8
ms.sourcegitcommit: a2be75158491535c9a59583c51890e3457dc75d6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2018
ms.locfileid: "51269434"
---
# <a name="how-to-configure-persistent-memory-pmem-for-sql-server-on-linux"></a>Konfigurieren von persistenten Speicher (PMEM) für SQL Server unter Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

In diesem Artikel wird beschrieben, konfigurieren Sie den persistenten Speicher (PMEM) für SQL Server unter Linux. PMEM-Unterstützung unter Linux wurde in der SQL Server-2019 Vorschau eingeführt.

## <a name="overview"></a>Übersicht

SQL Server 2016 wurde die Unterstützung für Non-Volatile-DIMMs und eine Optimierung namens [Ende der Protokoll-Zwischenspeicherung auf NVDIMM]( https://blogs.msdn.microsoft.com/bobsql/2016/11/08/how-it-works-it-just-runs-faster-non-volatile-memory-sql-server-tail-of-log-caching-on-nvdimm/). Diese Optimierungen reduziert die Anzahl von Vorgängen, die zum Absichern einer Protokollpuffer in den permanenten Speicher erforderlich sind. Diese nutzt die Windows-Server direkten Zugriff auf ein Gerät persistenten Speicher in DAX-Modus.

Vorschau der SQL Server-2019 erweitert die Unterstützung für den persistenten Speicher (PMEM) Geräte zu Linux, vollständige Erleuchtung von Daten- und Protokolldateien auf PMEM platziert bereitstellen. Erleuchtung bezieht sich auf die Methode des Zugriffs auf das Speichergerät mithilfe von effizienten Benutzerbereich `memcpy()` Vorgänge. Anstatt laufende über den Datei-System und Speicher-Stapel nutzt SQL Server DAX-Unterstützung unter Linux für das Hinzufügen von Daten direkt in Geräte, die Wartezeit reduziert.

## <a name="enable-enlightenment-of-database-files"></a>Aktivieren Sie an Aufklärung von Datenbankdateien
Um Erleuchtung von Datenbankdateien in SQL Server unter Linux zu aktivieren, führen Sie die folgenden Schritte aus:

1. Konfigurieren Sie die Geräte an.

  Unter Linux verwenden die `ndctl` Hilfsprogramm.

  - Installieren Sie `ndctl` PMEM Gerät konfigurieren. Sie finden es [hier](https://docs.pmem.io/getting-started-guide/installing-ndctl).
  - Verwenden Sie [Ndctl], um einen Namespace zu erstellen.

  ```bash 
  ndctl create-namespace -f -e namespace0.0 --mode=fsdax* -–map=mem
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

  - Erstellen und Bereitstellen von PMEM-Gerät

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
