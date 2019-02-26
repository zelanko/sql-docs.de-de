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
ms.openlocfilehash: ba2ed69239313a7933840d7a99ccbf3ce0864bfd
ms.sourcegitcommit: 8664c2452a650e1ce572651afeece2a4ab7ca4ca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/26/2019
ms.locfileid: "56828420"
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
  ndctl create-namespace -f -e namespace0.0 --mode=fsdax* --map=mem
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
    mount -o dax,noatime /dev/pmem0 /mnt/dax
    xfs_io -c "extsize 2m" /mnt/dax
    ```

    Z. B. mit EXT4

    ```bash
    mkfs.ext4 -b 4096 -E stride=512 -F /dev/pmem0
    mount -o dax,noatime /dev/pmem0 /mnt/dax
    ```

  Sobald das Gerät wurde mit Ndctl konfiguriert, formatiert und eingebunden wurde, können Sie Datenbankdateien darin platzieren. Sie können auch eine neue Datenbank erstellen. 

1. Da PMEM Geräte O_DIRECT sicher sind, aktivieren Sie das Ablaufverfolgungsflag 3979 erzwungenen leeren Mechanismus zu deaktivieren. Dieses Ablaufverfolgungsflag ist das Ablaufverfolgungsflag beim Start und muss daher mit dem Hilfsprogramm für die Mssql-Conf aktiviert werden. Bitte beachten Sie, dass dies eine serverweite konfigurationsänderung ist, und Sie dieses Ablaufverfolgungsflag nicht verwenden sollten, wenn Sie nicht kompatible Geräte O_DIRECT, die den erzwungenen leeren Mechanismus verfügen, um die Datenintegrität sicherzustellen. Weitere Informationen finden Sie unter https://support.microsoft.com/en-us/help/4131496/enable-forced-flush-mechanism-in-sql-server-2017-on-linux

1. Starten Sie SQL Server neu.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu SQL Server unter Linux finden Sie unter [SQL Server unter Linux](sql-server-linux-overview.md).
