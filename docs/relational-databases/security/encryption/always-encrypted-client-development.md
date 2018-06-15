---
title: Always Encrypted (Cliententwicklung) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/29/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: security
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- CSharp
ms.assetid: 9595eb66-284c-4474-828f-8961a05ce989
caps.latest.revision: 33
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: f34940fce129a4a2d4921751d7691af99c071f9b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
ms.locfileid: "32965785"
---
# <a name="always-encrypted-client-development"></a>Always Encrypted (Cliententwicklung)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

[Always Encrypted](../../../relational-databases/security/encryption/always-encrypted-database-engine.md) ist eine clientseitige Verschlüsselungstechnologie, die sicherstellt, dass vertrauliche Daten (und die zugehörigen Verschlüsselungsschlüssel) niemals in der SQL Server- oder Azure SQL-Datenbank offengelegt werden. Mit Always Encrypted verschlüsselt ein Clienttreiber vertrauliche Daten transparent, bevor er die Daten an die Datenbank-Engine übergibt, und er entschlüsselt Daten transparent, die aus verschlüsselten Datenbankspalten abgerufen wurden.

Weitere Informationen zum Entwickeln von Anwendungen, die durch Always Encrypted geschützte Datenbanken verwenden, sowie Informationen dazu, welche Clienttreiber und Treiberversionen Always Encrypted unterstützen, finden Sie hier:

- [Verwenden von Always Encrypted mit dem .NET Framework-Datenanbieter für SQL Server](../../../relational-databases/security/encryption/develop-using-always-encrypted-with-net-framework-data-provider.md)
- [Verwenden von „Immer verschlüsselt“ mit dem JDBC-Treiber](../../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md)
- [Verwenden von „Immer verschlüsselt“ mit Windows ODBC Driver](../../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md)



## <a name="see-also"></a>Weitere Informationen finden Sie unter


  [„Immer verschlüsselt“ (Datenbank-Engine)](../../../relational-databases/security/encryption/always-encrypted-database-engine.md)

