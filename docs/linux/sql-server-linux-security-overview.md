---
title: Sicherheitseinschränkungen für SQL Server für Linux
description: In diesem Artikel sind Einschränkungen für SQL Server für Linux beschrieben.
author: VanMSFT
ms.author: vanto
ms.date: 09/12/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 64da74cc-14bf-4636-a55e-8cc1fce2aaff
ms.openlocfilehash: 8a9094977597fd7c2d76f2c80a1773c176b9c6dc
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "70929812"
---
# <a name="security-limitations-for-sql-server-on-linux"></a>Sicherheitseinschränkungen für SQL Server für Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Für SQL Server für Linux gibt es derzeit die folgenden Einschränkungen:

* Es wird eine Standardkennwortrichtlinie bereitgestellt. MUST_CHANGE ist die einzige Option, die Sie konfigurieren können. Die Option „CHECK_POLICY“ wird nicht unterstützt.
* Die erweiterbare Schlüsselverwaltung wird nicht unterstützt. 
* Das Verwenden von Schlüsseln, die im Azure Key Vault gespeichert sind, wird nicht unterstützt.
* SQL Server generiert ein eigenes selbstsigniertes Zertifikat zum Verschlüsseln von Verbindungen. SQL Server kann so konfiguriert werden, dass ein vom Benutzer bereitgestelltes Zertifikat für TLS verwendet wird. 

Weitere Informationen zu den in SQL Server verfügbaren Sicherheitsfunktionen finden Sie unter [Sicherheitscenter für SQL Server-Datenbank-Engine und Azure SQL-Datenbank](../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md).

## <a name="next-steps"></a>Nächste Schritte

Informationen zu allgemeinen Sicherheitsaufgaben finden Sie unter [Exemplarische Vorgehensweise für die Sicherheitsfeatures von SQL Server für Linux](sql-server-linux-security-get-started.md). Ein Skript, mit dem Sie die TCP-Portnummer und die SQL Server-Verzeichnisse ändern sowie Ablaufverfolgungsflags oder die Sortierung konfigurieren können, finden Sie unter [Konfigurieren von SQL Server für Linux mit dem mssql-conf-Tool](sql-server-linux-configure-mssql-conf.md).
