---
title: Always Encrypted (Cliententwicklung) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/21/2018
ms.prod: sql
ms.reviewer: vanto
ms.technology: security
ms.topic: conceptual
dev_langs:
- CSharp
ms.assetid: 9595eb66-284c-4474-828f-8961a05ce989
author: VanMSFT
ms.author: vanto
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 475a030972819515a2f8f346b5644139dd7fdf90
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68086904"
---
# <a name="always-encrypted-client-development"></a>Always Encrypted (Cliententwicklung)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

[Always Encrypted](../../../relational-databases/security/encryption/always-encrypted-database-engine.md) ist eine clientseitige Verschlüsselungstechnologie, die sicherstellt, dass vertrauliche Daten (und die zugehörigen Verschlüsselungsschlüssel) niemals in der SQL Server- oder Azure SQL-Datenbank offengelegt werden. Mit Always Encrypted verschlüsselt ein Clienttreiber vertrauliche Daten transparent, bevor er die Daten an die Datenbank-Engine übergibt, und er entschlüsselt Daten transparent, die aus verschlüsselten Datenbankspalten abgerufen wurden.

Weitere Informationen zum Entwickeln von Anwendungen, die durch Always Encrypted geschützte Datenbanken verwenden, sowie Informationen dazu, welche Clienttreiber und Treiberversionen Always Encrypted unterstützen, finden Sie hier:

- [Verwenden von Always Encrypted mit dem .NET Framework-Datenanbieter für SQL Server](../../../relational-databases/security/encryption/develop-using-always-encrypted-with-net-framework-data-provider.md)
- [Verwenden von „Immer verschlüsselt“ mit dem JDBC-Treiber](../../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md)
- [Verwenden von Always Encrypted mit dem ODBC-Treiber](../../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md)
- [Verwenden von Always Encrypted mit den PHP-Treibern](../../../connect/php/using-always-encrypted-php-drivers.md)

> [!NOTE]
> Always Encrypted wird derzeit von [.NET CORE](https://docs.microsoft.com/dotnet/core/) nicht unterstützt.

## <a name="see-also"></a>Weitere Informationen

[„Immer verschlüsselt“ (Datenbank-Engine)](../../../relational-databases/security/encryption/always-encrypted-database-engine.md)

