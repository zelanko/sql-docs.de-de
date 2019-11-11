---
title: Entwickeln von Anwendungen mithilfe von Always Encrypted | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/30/2019
ms.prod: sql
ms.reviewer: vanto
ms.technology: security
ms.topic: conceptual
dev_langs:
- CSharp
ms.assetid: 9595eb66-284c-4474-828f-8961a05ce989
author: jaszymas
ms.author: jaszymas
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 235dc20ca94affa5f022bc242aa0ef6726f1542c
ms.sourcegitcommit: 312b961cfe3a540d8f304962909cd93d0a9c330b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2019
ms.locfileid: "73594447"
---
# <a name="develop-applications-using-always-encrypted"></a>Entwickeln von Anwendungen mithilfe von Always Encrypted
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

[Always Encrypted](../../../relational-databases/security/encryption/always-encrypted-database-engine.md) ist eine clientseitige Verschlüsselungstechnologie, die sicherstellt, dass vertrauliche Daten (und die zugehörigen Verschlüsselungsschlüssel) niemals in der SQL Server- oder Azure SQL-Datenbank offengelegt werden. Mit Always Encrypted verschlüsselt ein Clienttreiber vertrauliche Daten transparent, bevor er die Daten an die Datenbank-Engine übergibt, und er entschlüsselt Daten transparent, die aus verschlüsselten Datenbankspalten abgerufen wurden.

Weitere Informationen zum Entwickeln von Anwendungen, die durch Always Encrypted geschützte Datenbanken verwenden, sowie Informationen dazu, welche Clienttreiber und Treiberversionen Always Encrypted unterstützen, finden Sie hier:

- [Verwenden von Always Encrypted mit dem .NET Framework-Datenanbieter für SQL Server](../../../relational-databases/security/encryption/develop-using-always-encrypted-with-net-framework-data-provider.md)
- [Verwenden von „Immer verschlüsselt“ mit dem JDBC-Treiber](../../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md)
- [Verwenden von Always Encrypted mit dem ODBC-Treiber](../../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md)
- [Verwenden von Always Encrypted mit den PHP-Treibern](../../../connect/php/using-always-encrypted-php-drivers.md)
- [Verwenden von Always Encrypted mit dem Microsoft.Data.SqlClient in .NET Core- und .NET Framework-Anwendungen](https://github.com/dotnet/sqlclient/tree/master/release-notes)
- [Always Encrypted](../../../relational-databases/security/encryption/always-encrypted-database-engine.md)
