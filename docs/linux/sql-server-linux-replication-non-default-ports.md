---
title: Konfigurieren der Replikation eines Momentaufnahmeordners (vom Standard abweichende Ports)
titleSuffix: SQL Server on Linux
description: Hier erfahren Sie, wie Sie Momentaufnahmeordnerfreigaben mit vom Standard abweichenden Ports für die SQL Server-Replikation unter Linux konfigurieren.
ms.custom: seo-lt-2019
author: MikeRayMSFT
ms.author: mikerayW
ms.reviewer: vanto
ms.date: 09/24/2018
ms.topic: article
ms.prod: sql
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: cb715e2a0a056c18352361b58ce8ffd67e3da78e
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "75558593"
---
# <a name="configure-replication-with-non-default-ports-sql-server-linux"></a>Konfigurieren der Replikation mit vom Standard abweichenden Ports (SQL Server für Linux)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Sie können Replikation mit SQL Server für Linux Instanzen konfigurieren, die an einem Port lauschen, der mit der „mssql-conf“-Einstellung „network.tcpport“ konfiguriert wurde. Der Port muss während der Konfiguration an den Servernamen angehängt werden, wenn die folgenden Bedingungen zutreffen:

1. Zur Replikationseinrichtung gehört eine Instanz von SQL Server für Linux.
2. Jede Instanz (Windows oder Linux) lauscht an einem Nicht-Standardport. 

Der Servername einer Instanz kann ermittelt werden, indem @@servername für die Instanz ausgeführt wird.

## <a name="examples"></a>Beispiele

„Server1“ lauscht an Port 1500 unter Linux. Um „Server1“ als Verteiler zu konfigurieren, führen Sie `sp_adddistributor` mit `@distributor` aus. Beispiel: 

```sql
exec sp_adddistributor @distributor = 'Server1,1500'
```

„Server1“ lauscht an Port 1500 unter Linux. Um einen Verleger für den Verteiler zu konfigurieren, führen Sie `sp_adddistpublisher` mit `@publisher` aus. Beispiel:

```sql
exec sp_adddistpublisher @publisher = 'Server1,1500' ,  ,  
```

„Server2“ lauscht an Port 6549 unter Linux. Um „Server2“ als Abonnenten zu konfigurieren, führen Sie `sp_addsubscription` mit `@subscriber` aus. Beispiel:

```sql
exec sp_addsubscription @subscriber = 'Server2,6549' ,  ,  
```

„Server3“ lauscht an Port 6549 unter Windows mit dem Servernamen „Server3“ und dem Instanznamen „MSSQL2017“. Um „Server3“ als Abonnenten zu konfigurieren, führen Sie `sp_addsubscription` mit `@subscriber` aus. Beispiel:

```sql
exec sp_addsubscription @subscriber = 'Server3/MSSQL2017,6549',  ,  
```

## <a name="next-steps"></a>Nächste Schritte

[Konzepte: SQL Server-Replikation unter Linux](sql-server-linux-replication.md)

[Gespeicherte Prozeduren für die Replikation](../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md).

