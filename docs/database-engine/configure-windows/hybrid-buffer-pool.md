---
title: Hybrider Pufferpool | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/22/2019
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: ''
author: briancarrig
ms.author: brcarrig
ms.openlocfilehash: 8bbc7670f3a4d6d8a017e7284c5a661d38594f08
ms.sourcegitcommit: 1c3f56deaa4c1ffbe5d7f75752ebe10447c3e7af
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/25/2019
ms.locfileid: "71251057"
---
# <a name="hybrid-buffer-pool"></a>Hybrider Pufferpool
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Mit dem hybriden Pufferpool kann die Datenbank-Engine direkt auf Datenseiten in Datenbankdateien zugreifen, die auf Geräten mit persistentem Speicher (PMEM) gespeichert sind. Dieses Feature wird in [!INCLUDE[sqlv15](../../includes/sssqlv15-md.md)] eingeführt.

Bei einem herkömmlichen System ohne PMEM werden Datenseiten von SQL Server im Pufferpool zwischengespeichert. Bei Verwendung des hybriden Pufferpools kopiert SQL Server die Seite nicht in den DRAM-basierten Teil des Pufferpools, sondern greift stattdessen direkt auf die Seite in der Datenbankdatei auf einem PMEM-Gerät zu. Der Lesezugriff auf Datendateien auf PMEM-Geräten für den Hybridpufferpool erfolgt direkt durch das Folgen eines Zeigers auf die Datenseiten auf dem PMEM-Gerät.  

Auf einem PMEM-Gerät kann nur auf nicht modifizierte Seiten direkt zugegriffen werden. Wenn eine Seite als geändert markiert ist, wird sie in den DRAM-Pufferpool kopiert, bevor sie schließlich zurück auf das PMEM-Gerät geschrieben und als nicht modifiziert markiert wird. Dies findet während normaler Prüfpunktvorgänge statt. Der Mechanismus zum Kopieren der Datei vom PMEM-Gerät in DRAM ist eine direkte, dem zugeordnete E/A (MMIO) und wird auch als *Optimierung* von Datendateien in SQL Server bezeichnet.


Die Funktion für hybriden Pufferpool ist für Windows und Linux verfügbar. Das PMEM-Gerät muss mit einem Dateisystem formatiert sein, das DAX (DirectAccess) unterstützt. Die Dateisystem XFS, EXT4 und NTFS bieten Unterstützung für DAX. SQL Server erkennt automatisch, ob sich Datendateien auf einem entsprechend formatierten PMEM-Gerät befinden, und führt die Speicherzuordnung im Benutzerbereich aus. Diese Speicherzuordnung erfolgt beim Start, wenn eine neue Datenbank angefügt, wiederhergestellt oder erstellt wird, oder wenn die Funktion für hybriden Pufferpool für eine Datenbank aktiviert ist.

Weitere Informationen zur Windows Server-Unterstützung für PMEM finden Sie unter [Bereitstellen von persistentem Speicher unter Windows Server](/windows-server/storage/storage-spaces/deploy-pmem/).

Weitere Informationen zum Konfigurieren von SQL Server unter Linux für PMEM-Geräte finden Sie unter [Bereitstellen von persistentem Speicher](../../linux/sql-server-linux-configure-pmem.md).

## <a name="enable-hybrid-buffer-pool"></a>Aktivieren des hybriden Pufferpools

Mit [!INCLUDE[sqlv15](../../includes/sssqlv15-md.md)] wird DDL (Dynamic Data Language) zum Steuern des hybriden Pufferpools eingeführt.

Im folgenden Beispiel wird der hybride Pufferpool für eine Instanz von SQL Server aktiviert:

```sql
ALTER SERVER CONFIGURATION SET MEMORY_OPTIMIZED HYBRID_BUFFER_POOL = ON;
```

Standardmäßig ist der hybride Pufferpool im Instanzbereich deaktiviert. Beachten Sie, dass die SQL Server-Instanz neu gestartet werden muss, damit die Einstellungsänderung in Kraft tritt. Ein Neustart ist erforderlich, um eine Zuordnung ausreichender Hashseiten entsprechend der PMEM-Gesamtkapazität auf dem Server zu ermöglichen.

Im folgenden Beispiel wird der hybride Pufferpool für eine bestimmte Datenbank aktiviert.

```sql
ALTER DATABASE <databaseName> SET MEMORY_OPTIMIZED = ON;
```

Standardmäßig ist der hybride Pufferpool im Datenbankbereich aktiviert.

## <a name="disable-hybrid-buffer-pool"></a>Deaktivieren des hybriden Pufferpools

Im folgenden Beispiel wird der hybride Pufferpool für eine Instanz von SQL Server deaktiviert:

```sql
ALTER SERVER CONFIGURATION SET MEMORY_OPTIMIZED HYBRID_BUFFER_POOL = OFF;
```

Standardmäßig ist der hybride Pufferpool im Instanzbereich deaktiviert. Beachten Sie, dass die SQL Server-Instanz neu gestartet werden muss, damit die Einstellungsänderung in Kraft tritt. Ein Neustart ist erforderlich, um eine überhöhte Zuordnung von Hashseiten zu verhindern, da die PMEM-Kapazität auf dem Server nicht berücksichtigt werden muss.

Im folgenden Beispiel wird der hybride Pufferpool für eine bestimmte Datenbank deaktiviert.

```sql
ALTER DATABASE <databaseName> SET MEMORY_OPTIMIZED = OFF;
```

Standardmäßig ist der hybride Pufferpool im Datenbankbereich aktiviert.

## <a name="view-hybrid-buffer-pool-configuration"></a>Anzeigen der Konfiguration des hybriden Pufferpools

Das folgende Beispiel gibt den aktuellen Status der Systemkonfiguration des hybriden Pufferpools für eine Instanz von SQL Server zurück.

```sql
SELECT *
FROM sys.configurations
WHERE
    name = 'hybrid_buffer_pool';
```

Das folgende Beispiel gibt zwei Tabellen zurück:

- Die erste Tabelle zeigt den aktuellen Status der Systemkonfiguration des hybriden Pufferpools für eine Instanz von SQL Server.
- In der zweiten Tabelle sind die Datenbanken und die Einstellung auf Datenbankebene für den hybriden Pufferpool (`is_memory_optimized_enabled`) aufgeführt.

```sql
SELECT * FROM sys.configurations WHERE name = 'hybrid_buffer_pool';

SELECT name, is_memory_optimized_enabled FROM sys.databases;
```

## <a name="best-practices-for-hybrid-buffer-pool"></a>Bewährte Methoden für den hybriden Pufferpool

Es wird nicht empfohlen, den hybriden Pufferpool für Instanzen mit weniger als 16 GB RAM zu aktivieren.

Verwenden Sie beim Formatieren Ihres PMEM-Geräts unter Windows die größte verfügbare Zuordnungseinheit für NTFS (2 MB in Windows Server 2019), und stellen Sie sicher, dass das Gerät für DAX (DirectAccess) formatiert wurde.

Dateigrößen müssen ein Vielfaches von 2 MB sein (Modulo 2 MB muss 0 (Null) sein).

Wenn die Einstellung des Serverbereichs für den hybriden Pufferpool deaktiviert ist, wird der hybride Pufferpool von keiner Benutzerdatenbank verwendet.

Wenn die Einstellung des Serverbereichs für den hybriden Pufferpool aktiviert ist, können Sie die Verwendung des hybriden Pufferpools für einzelne Benutzerdatenbanken deaktivieren. Dazu führen Sie die Schritte zum Deaktivieren des hybriden Pufferpools auf Datenbereichsebene für diese Benutzerdatenbanken aus.
