---
title: Unterstützungsmatrix für Treiberfeatures
description: In diesem Artikel erfahren Sie, welche beliebten Features von Treibern für SQL Server unterstützt werden und wo Sie Informationen zu diesen Features finden.
ms.custom: ''
ms.date: 08/05/2020
ms.prod: sql
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-daenge
ms.openlocfilehash: 4071353214f7ffde54ecd1097defaa6c60aa19d6
ms.sourcegitcommit: 777704aefa7e574f4b7d62ad2a4c1b10ca1731ff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/06/2020
ms.locfileid: "87823355"
---
# <a name="driver-feature-support-matrix-for-microsoft-sql-server"></a>Unterstützungsmatrix für Treiberfeatures für Microsoft SQL Server

Features, die Sie in Microsoft SQL Server verwenden möchten, sind möglicherweise nicht in allen Treibern verfügbar. Mögliche Gründe, warum ein Feature in einem bestimmten Treiber nicht enthalten ist, sind beispielsweise die folgenden:

- Das Feature wird auf die betreffende Treibertechnologie nicht angewendet.
- Das Feature ist neu und wurde noch nicht in allen Treibern implementiert.
- Es besteht keine Nachfrage nach dem Feature als Teil eines bestimmten Treibers.
- Andere Features werden zuerst implementiert.

Wir möchten, dass alle Treiber alle Features unterstützen und arbeiten mit Nachdruck daran, Featureparität für die Treiber sicherzustellen. Dies ist jedoch nicht immer möglich. Die folgende Liste mit beliebten Features und den Treibern, die diese jeweils implementieren, soll Sie bei der Auswahl eines für Ihre Bedürfnisse geeigneten Treibers unterstützen.

- [.NET](#table1)
- [ODBC](#table2)
- [OLE DB](#table2)
- [JDBC](#table2)
- [PHP](#table3)
- [Node.js/JavaScript](#table3)
- [Python](#table3)

| <a id="table1"></a>Feature | [Microsoft.<wbr>Data.<wbr>SqlClient (.NET Core)](ado-net/microsoft-ado-net-sql-server.md) | [Microsoft.<wbr>Data.<wbr>SqlClient (.NET Framework)](ado-net/microsoft-ado-net-sql-server.md) | System.<wbr>Data.<wbr>SqlClient (.NET Core) | [System.<wbr>Data.<wbr>SqlClient (.NET Framework)](/dotnet/framework/data/adonet/sql/) |
| :-- | :-- | :-- | :-- | :-- |
| [Always Encrypted](../relational-databases/security/encryption/always-encrypted-database-engine.md) | [Ja](ado-net/sql/sqlclient-support-always-encrypted.md) | [Ja](ado-net/sql/sqlclient-support-always-encrypted.md) | | [Ja](ado-net/sql/sqlclient-support-always-encrypted.md) |
| [Always Encrypted mit Secure Enclaves](../relational-databases/security/encryption/always-encrypted-enclaves.md) | [Ja](ado-net/sql/sqlclient-support-always-encrypted.md#enabling-always-encrypted-with-secure-enclaves) | [Ja](ado-net/sql/sqlclient-support-always-encrypted.md#enabling-always-encrypted-with-secure-enclaves) | | [Ja](ado-net/sql/sqlclient-support-always-encrypted.md#enabling-always-encrypted-with-secure-enclaves) |
| [Azure Active Directory-Authentifizierung mit Zugriffstoken](/azure/active-directory/develop/access-tokens) | [Ja](/dotnet/api/system.data.sqlclient.sqlconnection.accesstoken) | [Ja](/dotnet/api/microsoft.data.sqlclient.sqlconnection.accesstoken) | [Ja](/dotnet/api/microsoft.data.sqlclient.sqlconnection.accesstoken) | [Ja](/dotnet/api/microsoft.data.sqlclient.sqlconnection.accesstoken) |
| [Azure Active Directory-Kennwortauthentifizierung](/azure/sql-database/sql-database-aad-authentication) | Ja | Ja | | Ja |
| [Integrierte Azure Active Directory-Authentifizierung](/azure/sql-database/sql-database-aad-authentication) | Ja | Ja | | Ja |
| [Interaktive Azure Active Directory-Authentifizierung (MFA)](/azure/sql-database/sql-database-aad-authentication) | Ja | Ja | | Ja |
| [Azure Active Directory-Authentifizierung mit einer verwalteten Identität](/azure/active-directory/managed-identities-azure-resources/overview) | | | | |
| [Azure Active Directory-Authentifizierung mit einem Dienstprinzipal](/azure/active-directory/develop/app-objects-and-service-principals) | Ja | Ja | | |
| [Integrierte Windows-Authentifizierung](/windows-server/security/windows-authentication/windows-authentication-overview) | [Ja](ado-net/sql/authentication-sql-server.md) | [Ja](ado-net/sql/authentication-sql-server.md) | [Ja](/dotnet/framework/data/adonet/sql/authentication-in-sql-server) | [Ja](/dotnet/framework/data/adonet/sql/authentication-in-sql-server) |
| [Massenkopieren](../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md) | [Ja](ado-net/sql/bulk-copy-operations-sql-server.md) | [Ja](ado-net/sql/bulk-copy-operations-sql-server.md) | [Ja](/dotnet/framework/data/adonet/sql/bulk-copy-operations-in-sql-server) | [Ja](/dotnet/framework/data/adonet/sql/bulk-copy-operations-in-sql-server) |
| [Metadaten für Datenvertraulichkeit und -klassifizierung](../relational-databases/security/sql-data-discovery-and-classification.md) | Ja | Ja | Ja | Ja |
| [Mehrere aktive Resultsets (MARS)](../relational-databases/native-client/features/using-multiple-active-result-sets-mars.md) | [Ja](ado-net/sql/multiple-active-result-sets-mars.md) | [Ja](ado-net/sql/multiple-active-result-sets-mars.md) | [Ja](/dotnet/framework/data/adonet/sql/multiple-active-result-sets-mars) | [Ja](/dotnet/framework/data/adonet/sql/multiple-active-result-sets-mars) |
| [Räumliche Datentypen](../relational-databases/spatial/spatial-data-sql-server.md) | | Ja | | Ja |
| [Tabellenwertparameter (Table-Valued Parameters, TVP)](../relational-databases/tables/use-table-valued-parameters-database-engine.md) | [Ja](ado-net/sql/table-valued-parameters.md) | [Ja](ado-net/sql/table-valued-parameters.md) | [Ja](/dotnet/framework/data/adonet/sql/table-valued-parameters) | [Ja](/dotnet/framework/data/adonet/sql/table-valued-parameters) |
| [MultiSubnetFailover](../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md#connecting-with-multisubnetfailover) | [Ja](ado-net/sql/sqlclient-support-high-availability-disaster-recovery.md#connecting-with-multisubnetfailover) | [Ja](ado-net/sql/sqlclient-support-high-availability-disaster-recovery.md#connecting-with-multisubnetfailover) | [Ja](/dotnet/api/system.data.sqlclient.sqlconnectionstringbuilder.multisubnetfailover?view=netcore-1.0) | [Ja](/dotnet/api/system.data.sqlclient.sqlconnectionstringbuilder.multisubnetfailover?view=netframework-4.8) |
| [Transparente Netzwerk-IP-Adressauflösung](odbc/using-transparent-network-ip-resolution.md) | | [Ja](/dotnet/api/microsoft.data.sqlclient.sqlconnection.connectionstring?view=sqlclient-dotnet-1.1) | | [Ja](/dotnet/api/system.data.sqlclient.sqlconnection.connectionstring?view=netframework-4.8) |
| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |

| <a id="table2"></a>Feature | [ODBC Driver for SQL Server unter Windows](odbc/microsoft-odbc-driver-for-sql-server.md) | [ODBC Driver for SQL Server unter Linux und macOS](odbc/microsoft-odbc-driver-for-sql-server.md) | [JDBC-Treiber für SQL Server](jdbc/microsoft-jdbc-driver-for-sql-server.md) | [OLE DB-Treiber für SQL-Server](oledb/oledb-driver-for-sql-server.md) |
| :-- | :-- | :-- | :-- | :-- |
| [Always Encrypted](../relational-databases/security/encryption/always-encrypted-database-engine.md) | [Ja](odbc/using-always-encrypted-with-the-odbc-driver.md) | [Ja](odbc/using-always-encrypted-with-the-odbc-driver.md) | [Ja](jdbc/using-always-encrypted-with-the-jdbc-driver.md) |
| [Always Encrypted mit Secure Enclaves](../relational-databases/security/encryption/always-encrypted-enclaves.md) | [Ja](odbc/using-always-encrypted-with-the-odbc-driver.md#enabling-always-encrypted-with-secure-enclaves) | [Ja](odbc/using-always-encrypted-with-the-odbc-driver.md#enabling-always-encrypted-with-secure-enclaves) | [Ja](jdbc/using-always-encrypted-with-the-jdbc-driver.md) | |
| [Azure Active Directory-Authentifizierung mit Zugriffstoken](/azure/active-directory/develop/access-tokens) | [Ja](odbc/using-azure-active-directory.md#authenticating-with-an-access-token) | [Ja](odbc/using-azure-active-directory.md#authenticating-with-an-access-token) | [Ja](jdbc/connecting-using-azure-active-directory-authentication.md#connecting-using-access-token) | [Ja](oledb/features/using-azure-active-directory.md) |
| [Azure Active Directory-Kennwortauthentifizierung](/azure/sql-database/sql-database-aad-authentication) |  [Ja](odbc/using-azure-active-directory.md) | [Ja](odbc/using-azure-active-directory.md) | [Ja](jdbc/connecting-using-azure-active-directory-authentication.md) | [Ja](oledb/features/using-azure-active-directory.md) |
| [Integrierte Azure Active Directory-Authentifizierung](/azure/sql-database/sql-database-aad-authentication) | [Ja](odbc/using-azure-active-directory.md) | [Ja](odbc/using-azure-active-directory.md) | [Ja](jdbc/connecting-using-azure-active-directory-authentication.md) | [Ja](oledb/features/using-azure-active-directory.md) |
| [Interaktive Azure Active Directory-Authentifizierung (MFA)](/azure/sql-database/sql-database-aad-authentication) | [Ja](odbc/using-azure-active-directory.md) | | | [Ja](oledb/features/using-azure-active-directory.md) |
| [Azure Active Directory-Authentifizierung mit einer verwalteten Identität](/azure/active-directory/managed-identities-azure-resources/overview) | [Ja](odbc/using-azure-active-directory.md) | [Ja](odbc/using-azure-active-directory.md) | [Ja](jdbc/connecting-using-azure-active-directory-authentication.md) | [Ja](oledb/features/using-azure-active-directory.md) |
| [Azure Active Directory-Authentifizierung mit einem Dienstprinzipal](/azure/active-directory/develop/app-objects-and-service-principals) | | | | |
| [Integrierte Windows-Authentifizierung](/windows-server/security/windows-authentication/windows-authentication-overview) | Ja | [Ja](odbc/linux-mac/using-integrated-authentication.md) | [Ja](jdbc/using-kerberos-integrated-authentication-to-connect-to-sql-server.md) | Ja |
| [Massenkopieren](../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md) | [Ja](../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md) | [Ja](../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md) | [Ja](jdbc/using-bulk-copy-with-the-jdbc-driver.md) | [Ja](oledb/features/performing-bulk-copy-operations.md) |
| [Metadaten für Datenerkennung und -klassifizierung](../relational-databases/security/sql-data-discovery-and-classification.md) | [Ja](odbc/data-classification.md) | [Ja](odbc/data-classification.md) | [Ja](jdbc/data-discovery-classification-sample.md) | |
| [Mehrere aktive Resultsets (MARS)](../relational-databases/native-client/features/using-multiple-active-result-sets-mars.md) | [Ja](../relational-databases/native-client/features/using-multiple-active-result-sets-mars.md) | [Ja](../relational-databases/native-client/features/using-multiple-active-result-sets-mars.md) | | [Ja](oledb/features/using-multiple-active-result-sets-mars.md) |
| [Räumliche Datentypen](../relational-databases/spatial/spatial-data-sql-server.md) | | | [Ja](jdbc/use-spatial-datatypes.md) | |
| [Tabellenwertparameter (TVP)](../relational-databases/tables/use-table-valued-parameters-database-engine.md) | [Ja](../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md) | [Ja](../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md) | [Ja](jdbc/using-table-valued-parameters.md) | [Ja](oledb/ole-db-table-valued-parameters/table-valued-parameters-ole-db.md) |
| [MultiSubnetFailover](../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md#connecting-with-multisubnetfailover) | [Ja](../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md#connecting-with-multisubnetfailover) | [Ja](../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md#connecting-with-multisubnetfailover) | [Ja](jdbc/jdbc-driver-support-for-high-availability-disaster-recovery.md) | [Ja](oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md#connecting-with-multisubnetfailover) |
| [Transparente Netzwerk-IP-Adressauflösung](odbc/using-transparent-network-ip-resolution.md) | [Ja](odbc/using-transparent-network-ip-resolution.md) | [Ja](odbc/using-transparent-network-ip-resolution.md) | [Ja](jdbc/setting-the-connection-properties.md) | [Ja](oledb/features/using-transparent-network-ip-resolution.md) |
| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |

| <a id="table3"></a>Feature | [Treiber für PHP für SQL Server unter Windows](php/microsoft-php-driver-for-sql-server.md)<sup>[1](#note1)</sup> | [Treiber für PHP für SQL Server unter Linux und macOS](php/microsoft-php-driver-for-sql-server.md)<sup>[1](#note1)</sup> | [Tedious (Node.js)](node-js/node-js-driver-for-sql-server.md) | [pyODBC (Python)](python/pyodbc/python-sql-driver-pyodbc.md)<sup>[1](#note1)</sup> |
| :-- | :-- | :-- | :-- | :-- |
| [Always Encrypted](../relational-databases/security/encryption/always-encrypted-database-engine.md) | [Ja](php/using-always-encrypted-php-drivers.md) | [Ja](php/using-always-encrypted-php-drivers.md) | | Ja |
| [Always Encrypted mit Secure Enclaves](../relational-databases/security/encryption/always-encrypted-enclaves.md) | [Ja](php/always-encrypted-secure-enclaves.md) | [Ja](php/always-encrypted-secure-enclaves.md) | | Ja |
| [Azure Active Directory-Authentifizierung mit Zugriffstoken](/azure/active-directory/develop/access-tokens) | [Ja](php/azure-active-directory.md) | [Ja](php/azure-active-directory.md) | [Ja](https://tediousjs.github.io/tedious/api-connection.html#function_newConnection) | Ja |
| [Azure Active Directory-Kennwortauthentifizierung](/azure/sql-database/sql-database-aad-authentication) | [Ja](php/azure-active-directory.md) | [Ja](php/azure-active-directory.md) | [Ja](https://tediousjs.github.io/tedious/api-connection.html#function_newConnection) | Ja |
| [Integrierte Azure Active Directory-Authentifizierung](/azure/sql-database/sql-database-aad-authentication) | [Ja](php/azure-active-directory.md) | [Ja](php/azure-active-directory.md) | | Ja |
| [Interaktive Azure Active Directory-Authentifizierung (MFA)](/azure/sql-database/sql-database-aad-authentication) | | | | Ja<sup>[2](#note2)</sup> |
| [Azure Active Directory-Authentifizierung mit einer verwalteten Identität](/azure/active-directory/managed-identities-azure-resources/overview) | [Ja](php/azure-active-directory.md) | [Ja](php/azure-active-directory.md) | [Ja](https://tediousjs.github.io/tedious/api-connection.html#function_newConnection) | Ja |
| [Azure Active Directory-Authentifizierung mit einem Dienstprinzipal](/azure/active-directory/develop/app-objects-and-service-principals) | | | | |
| [Integrierte Windows-Authentifizierung](/windows-server/security/windows-authentication/windows-authentication-overview) | [Ja](php/how-to-connect-using-windows-authentication.md) | [Ja](odbc/linux-mac/using-integrated-authentication.md) | | Ja |
| [Massenkopieren](../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md) | | | [Ja](https://tediousjs.github.io/tedious/bulk-load.html) | |
| [Metadaten für Datenerkennung und -klassifizierung](../relational-databases/security/sql-data-discovery-and-classification.md) | Ja | Ja | | |
| [Mehrere aktive Resultsets (MARS)](../relational-databases/native-client/features/using-multiple-active-result-sets-mars.md) | [Ja](php/how-to-disable-multiple-active-resultsets-mars.md) | [Ja](php/how-to-disable-multiple-active-resultsets-mars.md) | | Ja |
| [Räumliche Datentypen](../relational-databases/spatial/spatial-data-sql-server.md) | | | | |
| [Tabellenwertparameter (TVP)](../relational-databases/tables/use-table-valued-parameters-database-engine.md) | | | [Ja](https://tediousjs.github.io/tedious/parameters.html) | Ja |
| [MultiSubnetFailover](../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md#connecting-with-multisubnetfailover) | [Ja](php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md) | [Ja](php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md) | | [Ja](../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md#connecting-with-multisubnetfailover) |
| [Transparente Netzwerk-IP-Adressauflösung](odbc/using-transparent-network-ip-resolution.md) | [Ja](php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md) | [Ja](php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md) | | [Ja](odbc/using-transparent-network-ip-resolution.md) |
| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |

<a id="note1"></a><sup>1</sup> Da diese Treiber auf dem Microsoft ODBC-Treiber für SQL Server basieren, muss auch eine Version dieses Treibers verwendet werden, die das Feature unterstützt.

<a id="note2"></a><sup>2</sup> Nur unter Windows

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]

[!INCLUDE[contribute-to-content](../includes/paragraph-content/contribute-to-content.md)]
