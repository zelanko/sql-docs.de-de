---
title: Sicherheitseinschränkungen für SQL Server unter Linux | Microsoft-Dokumentation
description: Dieser Artikel beschreibt die SQL Server auf Linux-Einschränkungen.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 01/30/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 64da74cc-14bf-4636-a55e-8cc1fce2aaff
ms.openlocfilehash: 71aa2424a7fddb7abeb9d68e59f6b94693b0cb5c
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66705075"
---
# <a name="security-limitations-for-sql-server-on-linux"></a>Sicherheitseinschränkungen für SQL Server unter Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

SQL Server unter Linux ist derzeit die folgenden Einschränkungen:

* Eine standard-Kennwortrichtlinie wird bereitgestellt. MUST_CHANGE ist die einzige Möglichkeit, die Sie konfigurieren können.  
* Erweiterbare Schlüsselverwaltung wird nicht unterstützt. 
* Mit in Azure Key Vault gespeicherten Schlüsseln wird nicht unterstützt.
* SQL Server generiert, über ein eigenes selbstsignierte Zertifikat zum Verschlüsseln von Verbindungen. SQL Server können konfiguriert werden, um einem vom Benutzer bereitgestellten Zertifikat für TLS zu verwenden. 

Weitere Informationen zu Sicherheitsfunktionen in SQL Server verfügbar sind, finden Sie unter den [Sicherheitscenter für SQL Server-Datenbank-Engine und Azure SQL-Datenbank](../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md).

## <a name="next-steps"></a>Nächste Schritte

Häufig anfallender Sicherheitsaufgaben, finden Sie unter [erste Schritte mit den Sicherheitsfunktionen von SQL Server unter Linux](sql-server-linux-security-get-started.md). Ein Skript zum Ändern von TCP die Portnummer der SQL Server-Verzeichnisse, und Konfigurieren von Ablaufverfolgungsflags oder Sortierung, finden Sie unter [Konfigurieren von SQL Server unter Linux mit Mssql-Conf](sql-server-linux-configure-mssql-conf.md).
