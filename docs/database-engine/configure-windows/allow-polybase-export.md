---
title: Konfigurationsoption „Allow PolyBase export“ | Microsoft-Dokumentation
description: Festlegen der Konfigurationsoption `allow polybase export` in den SQL Server-Einstellungen
ms.custom: ''
ms.date: 07/10/2020
ms.prod: sql
ms.prod_service: ''
ms.reviewer: ''
ms.technology: polybase
ms.topic: conceptual
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c25a7e42b55561ed6337281497e847999d722292
ms.sourcegitcommit: dacd9b6f90e6772a778a3235fb69412662572d02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2020
ms.locfileid: "86279649"
---
# <a name="set-allow-polybase-export-configuration-option"></a>Festlegen der Konfigurationsoption `allow polybase export`

[!INCLUDE [sqlserver2016](../../includes/applies-to-version/sqlserver2016.md)]

Mit der Serverkonfigurationsoption `allow polybase export` wird `INSERT` in einer externen Hadoop-Tabelle zugelassen. 

Dieses Feature unterstützt nicht das Einfügen in andere externe Datenquellen.

 Eine Beschreibung der möglichen Werte finden Sie in der folgenden Tabelle: 

| Wert | Bedeutung                                |
|-------|----------------------------------------|
| 0     | Deaktiviert. Dies ist die Standardeinstellung. |
| 1     | Aktiviert                                |


Diese Einstellung wird sofort wirksam.

## <a name="example"></a>Beispiel

Diese Einstellung wird im folgenden Beispiel aktiviert.

```sql
sp_configure 'show advanced options', 1;
GO
RECONFIGURE;
GO
sp_configure 'allow polybase export', 0;
GO
RECONFIGURE;
GO
```

## <a name="next-steps"></a>Nächste Schritte

 [Exportieren von Daten](../../relational-databases/polybase/polybase-configure-hadoop.md#exporting-data)