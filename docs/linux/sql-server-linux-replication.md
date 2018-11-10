---
title: SQL Server-Replikation unter Linux | Microsoft-Dokumentation
description: Dieser Artikel beschreibt die SQL Server-Replikation unter Linux.
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 10/17/2018
ms.topic: article
ms.prod: sql
ms.prod_service: database-engine
ms.custom: sql-linux
ms.technology: linux
ms.workload: On Demand
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: c2a9d64b0ef55afb02022b7be27c096ea1221e6b
ms.sourcegitcommit: af1d9fc4a50baf3df60488b4c630ce68f7e75ed1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/06/2018
ms.locfileid: "51030432"
---
# <a name="sql-server-replication-on-linux"></a>SQL Server-Replikation unter Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] führt SQL Server-Replikation für Instanzen von SQL Server unter Linux.

Konfigurieren der Replikation unter Linux mit SQL Server Management Studio (SSMS) [gespeicherte Replikationsprozeduren](../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md).

Eine Instanz von SQL Server kann replikationsrolle teilnehmen:

* Verleger
* Verteiler
* Abonnent

Ein Replikationsschema mischen und Zuordnen von Betriebssystem-Plattformen. Z. B. ein Replikationsschema kann eine Instanz von SQL Server unter Linux für den Verleger und Verteiler enthalten, und die Abonnenten umfassen Instanzen von SQL Server unter Windows als auch für Linux.

SQL Server-Instanzen unter Linux können jede Art von Replikation teilnehmen.

* Transaktion
* Merge
* Momentaufnahme

Ausführliche Informationen zur Replikation finden Sie unter [Dokumentation zu SQL Server-Replikation](../relational-databases/replication/sql-server-replication.md).

## <a name="supported-features"></a>Unterstützte Funktionen

Für [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] die folgenden Replikationsfunktionen werden unterstützt:

* Momentaufnahmereplikation
* Transaktionsreplikation
* Mergereplikation
* Peer-zu-Peer-Replikation
* Replikation mit nicht standardmäßigen ports <!--Add link to explanation-->
* Replikation mit AD-Authentifizierung
* Konfigurationen für Windows und Linux
* Sofortige Updates für die Transaktionsreplikation

## <a name="limitations"></a>Einschränkungen

[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] unterstützt nicht die folgenden Funktionen:

* Sofortiges Update-Abonnenten
* Veröffentlichungen mit Oracle

## <a name="next-steps"></a>Nächste Schritte

[Konfigurieren von SQL Server-Replikation unter Linux](sql-server-linux-replication-tutorial-tsql.md)

[Beispiel: Konfigurieren von SQL Server-Replikation unter Linux](sql-server-linux-replication-configure.md)
