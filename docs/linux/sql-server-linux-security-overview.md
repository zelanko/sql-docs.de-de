---
title: Sicherheitseinschränkungen für SQL Server on Linux | Microsoft Docs
description: Dieser Artikel beschreibt SQL Server auf Linux-Einschränkungen.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 01/30/2018
ms.topic: article
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: 64da74cc-14bf-4636-a55e-8cc1fce2aaff
ms.openlocfilehash: 259f1d466a5d05f882bd7d53041d58b8d85c5e32
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2018
ms.locfileid: "34318327"
---
# <a name="security-limitations-for-sql-server-on-linux"></a>Sicherheitseinschränkungen für SQL Server on Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

SQL Server on Linux ist zurzeit die folgenden Einschränkungen:

* Eine standard-Kennwortrichtlinie wird bereitgestellt. MUST_CHANGE ist die einzige Option, die Sie konfigurieren können.  
* Erweiterbare Schlüsselverwaltung wird nicht unterstützt. 
* Verwenden in Azure Key Vault gespeicherte Schlüsseln wird nicht unterstützt.
* SQL Server generiert ein eigenes selbstsignierte Zertifikat zum Verschlüsseln von Verbindungen. SQL Server kann konfiguriert werden, um ein Zertifikat für den TLS bereitgestellt Benutzer verwenden. 

Weitere Informationen zu Sicherheitsfunktionen, die in SQL Server verfügbar sind, finden Sie unter der [Sicherheitscenter für SQL Server-Datenbankmodul und Azure SQL-Datenbank](../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md).

## <a name="next-steps"></a>Nächste Schritte

Der allgemeinen Sicherheitsaufgaben finden Sie unter [erste Schritte mit Sicherheitsfeatures von SQL Server on Linux](sql-server-linux-security-get-started.md). Für ein Skript so ändern Sie die TCP port-Nummer, die SQL Server-Verzeichnisse, und Konfigurieren von Traceflags oder Sortierung, finden Sie unter [konfigurieren Sie SQL Server unter Linux mit Mssql-Conf](sql-server-linux-configure-mssql-conf.md).
