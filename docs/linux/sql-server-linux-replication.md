---
title: SQL Server-Replikation unter Linux
description: Dieser Artikel beschreibt die SQL Server-Replikation unter Linux.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 10/17/2018
ms.topic: article
ms.prod: sql
ms.prod_service: database-engine
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: b049866d9752485cb1b9eb609404a3bd86f28a41
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68065192"
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
