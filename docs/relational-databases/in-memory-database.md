---
title: In-Memory Database | Microsoft-Dokumentation
ms.date: 05/22/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- in-memory database
- feature, in-memory database
- in-memory
ms.assetid: 11f8017e-5bc3-4bab-8060-c16282cfbac1
author: briancarrig
ms.author: brcarrig
manager: amitban
ms.openlocfilehash: d61ea85f5c1d7784faaf1d094e2fa858bffcd8c2
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/16/2019
ms.locfileid: "68255411"
---
# <a name="in-memory-database"></a>In-Memory Database

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In-Memory Database ist ein Oberbegriff für die Funktionen in SQL Server, die In-Memory-basierte Technologien nutzen. Da immer neue In-Memory-basierte Funktionen entwickelt werden, wird diese Seite weiterhin aktualisiert.

## <a name="hybrid-buffer-pool"></a>Hybrider Pufferpool

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Mit dem [hybriden Pufferpool](../database-engine/configure-windows/hybrid-buffer-pool.md) kann die Datenbank-Engine direkt auf Datenseiten in Datenbankdateien zugreifen, die auf Geräten mit persistentem Speicher (PMEM) gespeichert sind.

## <a name="memory-optimized-tempdb-metadata"></a>Speicheroptimierte TempDB-Metadaten

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Mit [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] wird eine neue Funktion für [speicheroptimierte tempdb-Metadaten](./databases/tempdb-database.md#memory-optimized-tempdb-metadata) eingeführt, durch die einige Engpässe aufgrund von Konflikten effektiv behoben werden und sich eine neue Ebene der Skalierbarkeit für tempdb-intensive Workloads ergibt.

## <a name="in-memory-oltp"></a>In-Memory-OLTP

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

[In-Memory-OLTP](./in-memory-oltp/in-memory-oltp-in-memory-optimization.md) ist in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] und [!INCLUDE[ssSDS](../includes/sssds-md.md)] die wichtigste verfügbare Technologie für die Optimierung der Transaktionsverarbeitung, das Erfassen und Laden von Daten sowie für vorübergehende Datenszenarios.

**Gilt für:** [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] bis [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].

## <a name="persistent-memory-support-for-linux"></a>Unterstützung von persistentem Speicher für Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

[!INCLUDE[sqlv15](../includes/sssqlv15-md.md)] bietet Unterstützung für Geräte mit persistentem Speicher (PMEM) unter Linux und dadurch vollständige Optimierung von Daten- und Transaktionsprotokolldateien, die im [persistenten Speicher](../linux/sql-server-linux-configure-pmem.md) abgelegt werden.

**Gilt für:** [!INCLUDE[sqlv15](../includes/sssqlv15-md.md)] bis [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].
