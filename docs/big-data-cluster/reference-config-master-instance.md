---
title: Konfigurationseigenschaften der SQL Server-Masterinstanz
titleSuffix: SQL Server big data clusters
description: Referenzartikel zu den Konfigurationseigenschaften der SQL Server-Masterinstanz.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: rahul.ajmera
ms.date: 08/04/2020
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 60888246623796d9b4d17c498da47ab4b6557cf2
ms.sourcegitcommit: 6ab28d954f3a63168463321a8bc6ecced099b247
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87790449"
---
# <a name="sql-server-master-instance-configuration-properties"></a>Konfigurationseigenschaften der SQL Server-Masterinstanz

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

## <a name="properties"></a>Eigenschaften

Sie können die folgenden SQL Server-Optionen für die Masterinstanz zum Zeitpunkt der Bereitstellung konfigurieren.

|Eigenschaft|Optionen|
| --- | --- |
|`[sqlagent]`|`enabled = { true | false }` |
|`[telemetry]`|`customerfeedback = { true | false }` |
|`[telemetry]`|`userRequestedLocalAuditDirectory = </path/file>`|
|`[licensing]`| `pid = { Enterprise | Developer }`|
|`[traceflag]`|` traceflag<#> = <####>`|

### <a name="examples"></a>Beispiele

Im folgenden Beispiel werden der SQL Server-Agent, die Telemetrie und das Ablaufverfolgungsflag 1204 aktiviert sowie eine PID für die Enterprise Edition festgelegt:

```
[sqlagent]
enabled=true

[telemetry]
customerfeedback=true
userRequestedLocalAuditDirectory = /tmp/audit

[licensing]
pid = Enterprise

[traceflag]
traceflag0 = 1204
```

Entsprechende Anweisungen finden Sie unter [Konfigurieren der Masterinstanz von [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]](configure-sql-server-master-instance.md).

## <a name="next-steps"></a>Nächste Schritte

[Konfigurieren der Masterinstanz von [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]](configure-sql-server-master-instance.md)
