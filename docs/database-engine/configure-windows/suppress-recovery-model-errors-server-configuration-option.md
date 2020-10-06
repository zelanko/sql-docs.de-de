---
description: Unterdrücken von Wiederherstellungsmodellfehlern – Serverkonfigurationsoption
title: Unterdrücken von Wiederherstellungsmodellfehlern – Serverkonfiguration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/20/2020
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 942dfc62bd55d1843babb78d89b95ad602f3d938
ms.sourcegitcommit: 2f868a77903c1f1c4cecf4ea1c181deee12d5b15
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2020
ms.locfileid: "91670743"
---
# <a name="suppress-recovery-model-errors-server-configuration-option"></a>Serverkonfigurationsoption für das Unterdrücken von Wiederherstellungsmodellfehlern

[!INCLUDE[tsql-appliesto-xxxxxx-asdbmi-xxxx-xxx-md.md](../../includes/tsql-appliesto-xxxxxx-asdbmi-xxxx-xxx-md.md)]

[Wiederherstellungsmodelle](../../relational-databases/backup-restore/recovery-models-sql-server.md) von SQL Server steuern die Wartung des Transaktionsprotokolls. Das vollständige Wiederherstellungsmodell stellt sicher, dass keine Arbeit aufgrund einer verlorenen oder beschädigten Datendatei verloren geht, und es unterstützt die Wiederherstellung zu einem beliebigen Zeitpunkt innerhalb der Sicherungsaufbewahrungsrichtlinie. Das vollständige Wiederherstellungsmodell ist das standardmäßige und einzige in einer SQL Managed Instance unterstützte Wiederherstellungsmodell. Versuche, das Wiederherstellungsmodell in SQL Managed Instance zu ändern, geben eine Fehlermeldung zurück.

Verwenden Sie die erweiterte Konfigurationsoption **Wiederherstellungsmodellfehler unterdrücken**, um anzugeben, ob Befehle zum Ändern des Datenbank-Wiederherstellungsmodells, die auf SQL Managed Instance ausgeführt werden, nur Fehler oder nur Warnungen zurückgeben. Wenn diese Option in SQL Managed Instance auf „1“ (EIN) festgelegt ist, wird durch das Ausführen des Befehls ALTER DATABASE SET RECOVERY nicht das Wiederherstellungsmodell der Datenbank geändert. Es gibt jedoch auch weiterhin keine Fehlermeldungen, sondern stattdessen Warnmeldung zurück. Wenn diese Option in SQL Managed Instance auf „0“ (AUS) festgelegt ist, wird beim Ausführen des Befehls ALTER DATABASE SET RECOVERY eine Fehlermeldung zurückgegeben.

Die Option **Wiederherstellungsmodellfehler unterdrücken** ist in Fällen hilfreich, in denen Legacy- oder Drittanbieteranwendungen versuchen, die Protokollierung des Wiederherstellungsmodells in „Simple“ (Einfach) oder „Bulk“ (Massenhaft) zu ändern, auch wenn es sich nicht um eine kritische oder obligatorische Anforderung handelt. Wenn die Änderung des Wiederherstellungsmodells die einzige Blockierung für die Verwendung von SQL Managed Instance ist, wird diese Blockierung durch das Aktivieren der Konfigurationsoption „Wiederherstellungsmodellfehler unterdrücken“ entfernt. Diese Option ist besonders nützlich, wenn eine alternative Lösung zum Ändern des Anwendungscodes nicht praktikabel oder erschwinglich ist.

## <a name="examples"></a>Beispiele

Im folgenden Beispiel wird die Unterdrückung von Fehlermeldungen im Zusammenhang mit der Änderung des Datenbank-Wiederherstellungsmodells aktiviert und anschließend der Befehl zum Ändern des Wiederherstellungsmodells der Datenbank ausgeführt, der nur eine Warnung zurückgibt. Das Wiederherstellungsmodell wird tatsächlich nicht geändert. Stellen Sie sicher, dass Sie *my_database* durch den tatsächlichen Datenbanknamen ersetzen.

```sql
-- Turn advanced configuration options on:
sp_configure 'show advanced options', 1 ;  
GO
RECONFIGURE ;  
GO

-- Enable suppression of error messages for recovery model change:
sp_configure 'suppress recovery model errors', 1 ;  
GO
RECONFIGURE ;  
GO

-- Execute command for changing recovery model to Simple:
ALTER DATABASE my_database SET RECOVERY SIMPLE;
GO
```

## <a name="see-also"></a>Weitere Informationen

[Serverkonfigurationsoptionen &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)

[sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)

[RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)