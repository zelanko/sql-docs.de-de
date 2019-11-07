---
title: Konfigurieren von persistentem Speicher (PMEM) für SQL Server für Linux
description: Dieser Artikel bietet eine exemplarische Vorgehensweise zum Konfigurieren von PMEM für Linux.
author: briancarrig
ms.author: brcarrig
ms.reviewer: vanto
ms.date: 11/04/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
monikerRange: '>= sql-server-linux-ver15  || >= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 6e1a935dcaa605caf9483fadd5707bafbfb6b83b
ms.sourcegitcommit: 830149bdd6419b2299aec3f60d59e80ce4f3eb80
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73531302"
---
# <a name="how-to-configure-persistent-memory-pmem-for-sql-server-on-linux"></a>Konfigurieren von persistentem Speicher (PMEM) für SQL Server für Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

In diesem Artikel ist beschrieben, wie der persistente Speicher (persistent memory, PMEM) für SQL Server für Linux konfiguriert wird. Die Unterstützung für PMEM für Linux wurde in SQL Server 2019 eingeführt.

## <a name="overview"></a>Übersicht

In SQL Server 2016 wurden die Unterstützung für nicht flüchtige DIMMs (Non-Volatile DIMMs) und eine Optimierung namens [Tail Of Log Caching on NVDIMM]( https://blogs.msdn.microsoft.com/bobsql/2016/11/08/how-it-works-it-just-runs-faster-non-volatile-memory-sql-server-tail-of-log-caching-on-nvdimm/) eingeführt. Diese Optimierungen verringern die Anzahl der Vorgänge, die erforderlich sind, um einen Protokollpuffer in persistenten Speicher zu überführen. Dies nutzt den direkten Zugriff von Windows Server auf ein Gerät mit persistentem Speicher im DAX-Modus.

SQL Server 2019 erweitert die Unterstützung für Geräte mit persistentem Speicher (PMEM) auf Linux, wodurch vollständige Offenlegung von Daten- und Transaktionsprotokolldateien erreicht wird, die in PMEM abgelegt sind. Die Offenlegung bezieht sich auf die Methode für den Zugriff auf das Speichergerät über effiziente `memcpy()`-Vorgänge im Benutzerbereich. Anstatt das Dateisystem und den Speicherstapel zu durchlaufen, nutzt SQL Server die DAX-Unterstützung unter Linux, um Daten direkt in Geräten zu platzieren, wodurch die Wartezeit verringert wird.

## <a name="enable-enlightenment-of-database-files"></a>Aktivieren der Offenlegung von Datenbankdateien
Führen Sie die folgenden Schritte aus, um die Offenlegung von Datenbankdateien in SQL Server für Linux zu aktivieren:

1. Konfigurieren Sie die Geräte.

  Verwenden Sie in Linux das Hilfsprogramm `ndctl`.

  - Installieren Sie `ndctl`, um das PMEM-Gerät zu konfigurieren. Sie finden das Hilfsprogramm [hier](https://docs.pmem.io/getting-started-guide/installing-ndctl).
  - Verwenden Sie [ndctl], um einen Namespace zu erstellen.

  ```bash 
  ndctl create-namespace -f -e namespace0.0 --mode=fsdax* --map=mem
  ```

  >[!NOTE]
  >Wenn Sie `ndctl` in einer Version verwenden, die niedriger ist als 59, verwenden Sie `--mode=memory`.

  Verwenden Sie `ndctl`, um den Namespace zu überprüfen. Die Beispielausgabe sieht wie folgt aus:

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

  - Erstellen Sie ein PMEM-Gerät, und binden Sie es ein (mounten Sie es).

    Beispielsweise mit XFS

    ```bash
    mkfs.xfs -f /dev/pmem0
    mount -o dax,noatime /dev/pmem0 /mnt/dax
    xfs_io -c "extsize 2m" /mnt/dax
    ```

    Beispielsweise mit EXT4

    ```bash
    mkfs.ext4 -b 4096 -E stride=512 -F /dev/pmem0
    mount -o dax,noatime /dev/pmem0 /mnt/dax
    ```

  Sobald das Gerät mit „ndctl“ konfiguriert, formatiert und eingebunden wurde, können Sie Datenbankdateien in ihm ablegen. Sie können auch eine neue Datenbank erstellen. 

1. Da PMEM-Geräte O_DIRECT-sicher sind, aktivieren Sie das Ablaufverfolgungsflag 3979, um den Mechanismus für erzwungenes Leeren zu deaktivieren. Dieses Ablaufverfolgungsflag ist ein Startablaufverfolgungsflag und muss daher mit dem Hilfsprogramm „mssql-conf“ aktiviert werden. Beachten Sie, dass es sich hierbei um eine serverweite Konfigurationsänderung handelt. Außerdem sollten Sie dieses Ablaufverfolgungsflag nicht verwenden, wenn Sie O_DIRECT-inkompatible Geräte haben, für die der Mechanismus für erzwungenes Leeren (forced flush) erforderlich ist, um Datenintegrität sicherzustellen. Weitere Informationen finden Sie unter https://support.microsoft.com/en-us/help/4131496/enable-forced-flush-mechanism-in-sql-server-2017-on-linux.

1. Starten Sie SQL Server neu.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu SQL Server für Linux finden Sie unter [SQL Server für Linux](sql-server-linux-overview.md).
