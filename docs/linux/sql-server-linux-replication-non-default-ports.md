---
title: Konfigurieren von SQL Server-Replikation momentaufnahmefreigaben Ordner unter Linux
description: Dieser Artikel beschreibt, wie SQLServer-Replikation von Momentaufnahmen Ordner Freigaben unter Linux konfigurieren.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 09/24/2018
ms.topic: article
ms.prod: sql
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 6959b2073871f70fb33823b50419c208a23df2dd
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68093182"
---
# <a name="configure-replication-with-non-default-ports"></a>Konfigurieren der Replikation mit nicht standardmäßigen ports

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Sie können mit SQL Server auf Linux-Instanzen Lauschen an einem beliebigen Port konfiguriert werden, mit der Mssql-Conf-Einstellung network.tcpport Replikation konfigurieren. Der Port muss, um den Namen des Servers während der Konfiguration angefügt werden soll, wenn die folgenden Bedingungen erfüllt sind:

1. Einrichten der Replikation umfasst eine Instanz von SQL Server unter Linux
2. Jede Instanz (Windows oder Linux) lauscht an einem nicht standardmäßigen Port. 

Der Servername einer Instanz von ausgeführt wird, @ finden@servername auf der Instanz.

## <a name="examples"></a>Beispiele

"Server1" lauscht an Port 1500 für Linux. Führen Sie zum Konfigurieren von "Server1" für die Verteilung `sp_adddistributor` mit `@distributor`. Zum Beispiel: 

```sql
exec sp_adddistributor @distributor = 'Server1,1500'
```

"Server1" lauscht an Port 1500 für Linux. Um einen Verleger für den Verteiler konfigurieren, führen Sie `sp_adddistpublisher` mit `@publisher`. Zum Beispiel:

```sql
exec sp_adddistpublisher @publisher = 'Server1,1500' ,  ,  
```

"Server2" Lauscht auf Port 6549 unter Linux. Führen Sie zum Konfigurieren von "Server2" als einen Abonnenten `sp_addsubscription` mit `@subscriber`. Zum Beispiel:

```sql
exec sp_addsubscription @subscriber = 'Server2,6549' ,  ,  
```

"Server3" Lauscht auf Port 6549 auf Windows, die mit Server3 Servernamen und Instanznamen des MSSQL2017. Um "Server3" als einen Abonnenten zu konfigurieren, führen die `sp_addsubscription` mit `@subscriber`. Zum Beispiel:

```sql
exec sp_addsubscription @subscriber = 'Server3/MSSQL2017,6549',  ,  
```

## <a name="next-steps"></a>Nächste Schritte

[Konzepte: SQL Server-Replikation unter Linux](sql-server-linux-replication.md)

[Gespeicherte Replikationsprozeduren](../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md).

