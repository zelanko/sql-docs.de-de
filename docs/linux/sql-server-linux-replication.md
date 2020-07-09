---
title: SQL Server-Replikation unter Linux
description: In diesem Artikel ist SQL Server Replikation unter Linux beschrieben.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 12/09/2019
ms.topic: article
ms.prod: sql
ms.prod_service: database-engine
ms.technology: linux
monikerRange: '>=sql-server-2017||>=sql-server-linux-2017||=sqlallproducts-allversions'
ms.openlocfilehash: cdd37963a419b33bb84353dee98c928179473bcb
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85882655"
---
# <a name="sql-server-replication-on-linux"></a>SQL Server-Replikation unter Linux

[!INCLUDE [SQL Server - Linux](../includes/applies-to-version/sql-linux.md)]

[!INCLUDE[SQL Server 2017](../includes/sssqlv14-md.md)] ([CU18](https://support.microsoft.com/help/4527377)) und später unterstützen SQL Server-Replikation für Instanzen von SQL Server für Linux eingeführt.

Sie konfigurieren Replikation unter Linux mit [gespeicherten Replikationsprozeduren ](../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md) von SQL Server Management Studio (SSMS).

Eine Instanz von SQL Server kann an jeder Replikationsrolle mitwirken:

* Herausgeber
* Verteiler
* Subscriber

In einem Replikationsschema können Betriebssystemplattformen gemischt und kombiniert werden. Beispielsweise kann ein Replikationsschema eine Instanz von SQL Server für Linux für Verleger und Verteiler enthalten, und die Abonnenten enthalten Instanzen von SQL Server für Windows und für Linux.

SQL Server-Instanzen für Linux können an jeder Art von Replikation beteiligt werden.

* Transaktionsreplikation
* Momentaufnahme

Ausführliche Informationen über Replikation finden Sie unter [SQL Server-Replikation](../relational-databases/replication/sql-server-replication.md).

## <a name="supported-features"></a>Unterstützte Features

Die folgenden Replikationsfeatures werden unterstützt:

* Momentaufnahmereplikation
* Transaktionsreplikation
* Replikation mit Nicht-Standardports <!--Add link to explanation-->
* Replikation mit AD-Authentifizierung
* Replikationskonfigurationen mit Windows und Linux
* Sofortige Updates für Transaktionsreplikation

## <a name="limitations"></a>Einschränkungen

Folgende Funktionen werden nicht unterstützt:

* Mergereplikation
* Peer-zu-Peer-Replikation
* Veröffentlichungen mit Oracle

## <a name="next-steps"></a>Nächste Schritte

[Konfigurieren von SQL Server-Replikation unter Linux](sql-server-linux-replication-tutorial-tsql.md)

[Beispiel: Konfigurieren von SQL Server-Replikation unter Linux](sql-server-linux-replication-configure.md)
