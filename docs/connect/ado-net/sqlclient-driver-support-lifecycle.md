---
title: Lebenszyklus der SqlClient-Treiberunterstützung
description: Seite mit Informationen zum Support-Lebenszyklus des Produkts
ms.date: 11/19/2020
dev_langs:
- csharp
- vb
ms.assetid: 6f5ff56a-a57e-49d7-8ae9-bbed697e42e3
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-jizho2
ms.openlocfilehash: eef9e81c94c930b9f00689b41339d54a0f0302be
ms.sourcegitcommit: 0c0e4ab90655dde3e34ebc08487493e621f25dda
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/01/2020
ms.locfileid: "96442716"
---
# <a name="sqlclient-driver-support-lifecycle"></a>Lebenszyklus der SqlClient-Treiberunterstützung

[!INCLUDE[Driver_ADONET_Download](../../includes/driver_adonet_download.md)]

Die Microsoft.Data.SqlClient-Bibliothek unterliegt der neuesten .NET Core-Unterstützungsrichtlinie für alle Releases.

[Anzeigen der .NET Core-Unterstützungsrichtlinie](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)

## <a name="microsoftdatasqlclient-release-cadence"></a>Microsoft.Data.SqlClient-Releaseintervall

Neue stabile Releases mit allgemeiner Verfügbarkeit werden beginnend mit Version 1.2 alle sechs Monate veröffentlicht. Innerhalb dieses sechsmonatigen Zeitraums werden zwei bis drei Previewreleases verfügbar gemacht. LTS-Releases (Long Term Support, langfristige Unterstützung) werden basierend auf einigen Qualifikationen und der Kundenreaktion von Projektbeteiligten und Verwaltern ausgewählt.

### <a name="actively-supported-releases"></a>Aktiv unterstützte Releases

| Version | Offizielles Veröffentlichungsdatum | Aktuelle Patchversion | Veröffentlichungsdatum für Patch | Supportebene  | Supportende |
| -- | -- | -- | -- | -- | -- |
| 2.1 | 19. November 2020 | 2.1.0 | 19. November 2020 | Aktuell | |
| 2.0 | 16. Juni 2020 | 2.0.1 | 25. August 2020 | Aktuell | 19. Februar 2021 |
| 1.1 | 20. November 2019 | 1.1.3 | 15. Mai 2020 | LTS | 21. November 2022 |

### <a name="out-of-support-releases"></a>Nicht mehr unterstützte Releases

| Version | Veröffentlichungsdatum des letzten Patches | Aktuelle Patchversion | Ende des Supportzeitraums |
| -- | -- | -- | -- |
| 1.0 | 26. September 2019 | 1.0.19269.1 | 20. Februar 2020 |

### <a name="long-term-support-lts-releases"></a>LTS-Releases (Long Term Support, langfristiger Support)

LTS-Releases werden drei Jahre nach der Veröffentlichung unterstützt.

### <a name="current-releases"></a>Aktuelle Releases

Aktuelle Releases werden bis zu drei Monate nach nachfolgenden aktuellen oder LTS-Releases unterstützt.

## <a name="sql-version-compatibility-with-microsoftdatasqlclient"></a>SQL-Versionskompatibilität mit Microsoft.Data.SqlClient

|Datenbankversion&nbsp;&#8594;<br />&#8595; Treiberversion|Azure SQL-Datenbank|Azure Synapse Analytics|Verwaltete Azure SQL-Instanz|SQL Server 2019|SQL Server 2017|SQL Server 2016|SQL Server 2014|SQL Server 2012|
|---|---|---|---|---|---|---|---|---|
|2.1|Ja|Ja|Ja|Ja|Ja|Ja|Ja|Ja|
|2.0|Ja|Ja|Ja|Ja|Ja|Ja|Ja|Ja|
|1.1|Ja|Ja|Ja|Ja|Ja|Ja|Ja|Ja|
|1.0|Ja|Ja|Ja|Ja|Ja|Ja|Ja|Ja|

## <a name="supported-os-versions"></a>Unterstützte Betriebssystemversionen

### <a name="support-for-net-framework-applications"></a>Unterstützung für .NET Framework-Anwendungen

Microsoft.Data.SqlClient unterstützt alle Betriebssysteme, die von .NET Framework v4.6 und höher unterstützt werden.

[.NET Framework-Systemanforderungen](/dotnet/framework/get-started/system-requirements).

### <a name="support-for-net-core-applications"></a>Unterstützung für .NET Core-Anwendungen

Microsoft.Data.SqlClient unterstützt alle Betriebssysteme, die von .NET Core v2.1 und höher unterstützt werden.

[Von .NET Core unterstützte Betriebssystem-Lebenszyklusrichtlinie](https://github.com/dotnet/core/blob/master/os-lifecycle-policy.md).

> [!NOTE]
> Der invariante Globalisierungsmodus wird aktuell nicht unterstützt.
