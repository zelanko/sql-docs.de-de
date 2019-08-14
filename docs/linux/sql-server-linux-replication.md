---
title: SQL Server-Replikation unter Linux
description: In diesem Artikel ist SQL Server Replikation unter Linux beschrieben.
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
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2019
ms.locfileid: "68065192"
---
# <a name="sql-server-replication-on-linux"></a>SQL Server-Replikation unter Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Mit [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] wird SQL Server-Replikation für Instanzen von SQL Server für Linux eingeführt.

Sie konfigurieren Replikation unter Linux mit [gespeicherten Replikationsprozeduren ](../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md) von SQL Server Management Studio (SSMS).

Eine Instanz von SQL Server kann an jeder Replikationsrolle mitwirken:

* Verleger
* Verteiler
* Abonnent

In einem Replikationsschema können Betriebssystemplattformen gemischt und kombiniert werden. Beispielsweise kann ein Replikationsschema eine Instanz von SQL Server für Linux für Verleger und Verteiler enthalten, und die Abonnenten enthalten Instanzen von SQL Server für Windows und für Linux.

SQL Server-Instanzen für Linux können an jeder Art von Replikation beteiligt werden.

* Transaktion
* Merge
* Momentaufnahme

Ausführliche Informationen über Replikation finden Sie unter [SQL Server-Replikation](../relational-databases/replication/sql-server-replication.md).

## <a name="supported-features"></a>Unterstützte Features

Für [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] werden die folgenden Replikationsfeatures unterstützt:

* Momentaufnahmereplikation
* Transaktionsreplikation
* Mergereplikation
* Peer-zu-Peer-Replikation
* Replikation mit Nicht-Standardports <!--Add link to explanation-->
* Replikation mit AD-Authentifizierung
* Replikationskonfigurationen mit Windows und Linux
* Sofortige Updates für Transaktionsreplikation

## <a name="limitations"></a>Einschränkungen

[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] unterstützt die folgenden Features nicht:

* Abonnenten mit sofortigem Update
* Veröffentlichungen mit Oracle

## <a name="next-steps"></a>Nächste Schritte

[Konfigurieren von SQL Server-Replikation unter Linux](sql-server-linux-replication-tutorial-tsql.md)

[Beispiel: Konfigurieren von SQL Server-Replikation unter Linux](sql-server-linux-replication-configure.md)
