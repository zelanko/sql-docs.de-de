---
title: Lebenszyklus der SqlClient-Treiberunterstützung
description: Seite mit Informationen zum Support-Lebenszyklus des Produkts
ms.date: 09/08/2020
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
ms.reviewer: v-kaywon
ms.openlocfilehash: 5b9b461454db98de77ed6003477b7a02114067eb
ms.sourcegitcommit: 71a334c5120a1bc3809d7657294fe44f6c909282
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/09/2020
ms.locfileid: "89614595"
---
# <a name="sqlclient-driver-support-lifecycle"></a>Lebenszyklus der SqlClient-Treiberunterstützung

[!INCLUDE[Driver_ADONET_Download](../../includes/driver_adonet_download.md)]

Die Microsoft.Data.SqlClient-Bibliothek unterliegt der neuesten .NET Core-Unterstützungsrichtlinie für alle Releases.

[Anzeigen der .NET Core-Unterstützungsrichtlinie](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)

## <a name="microsoftdatasqlclient-release-cadence"></a>Microsoft.Data.SqlClient-Releaseintervall

Neue stabile Releases werden alle sechs Monate beginnend mit Version 1.2 mit zwei bis drei Previewreleases dazwischen veröffentlicht. LTS-Releases (Long Term Support, langfristige Unterstützung) werden basierend auf einigen Qualifikationen und der Kundenreaktion von Projektbeteiligten und Verwaltern ausgewählt.

### <a name="release-life-cycles"></a>Releaselebenszyklen

| Version | Offizielles Veröffentlichungsdatum | Aktuelle Patchversion | Veröffentlichungsdatum für Patch | Supportebene  | Supportende |
| -- | -- | -- | -- | -- | -- |
| 2.0 | 16. Juni 2020 | 2.0.1 | 25. August 2020 | Aktuell | |
| 1.1 | 20. November 2019 | 1.1.3 | 15. Mai 2020 | LTS | 21. November 2022 |
| 1.0 | 28. August 2019 | 1.0.19269.1 | 26. September 2019 | Aktuell | 20. Februar 2020 |

### <a name="long-term-support-lts-releases"></a>LTS-Releases

LTS-Releases werden drei Jahre nach der Veröffentlichung unterstützt.

### <a name="current-releases"></a>Aktuelle Releases

Aktuelle Releases werden bis zu drei Monate nach nachfolgenden aktuellen oder LTS-Releases unterstützt.

## <a name="sql-version-compatibility-with-microsoftdatasqlclient"></a>SQL-Versionskompatibilität mit Microsoft.Data.SqlClient

|Datenbankversion&nbsp;&#8594;<br />&#8595; Treiberversion|Azure SQL-Datenbank|Azure Synapse Analytics|Verwaltete Azure SQL-Instanz|SQL Server 2019|SQL Server 2017|SQL Server 2016|SQL Server 2014|SQL Server 2012|
|---|---|---|---|---|---|---|---|---|
|2.0|Ja|Ja|Ja|Ja|Ja|Ja|Ja|Ja|
|1.1|Ja|Ja|Ja|Ja|Ja|Ja|Ja|Ja|
|1.0|Ja|Ja|Ja|Ja|Ja|Ja|Ja|Ja|
