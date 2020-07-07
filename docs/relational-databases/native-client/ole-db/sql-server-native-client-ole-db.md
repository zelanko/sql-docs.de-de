---
title: OLE DB
description: Der SQL Server Native Client OLE DB Provider ist eine com-API für den Zugriff auf Daten, die für Tools, Hilfsprogramme oder Low-Level-Komponenten verwendet werden, die eine hohe Leistung erfordern.
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, about SQL Server Native Client OLE DB provider
- OLE DB, SQL Server Native Client OLE DB provider
- data access [SQL Server Native Client], OLE DB
- SQLNCLI, OLE DB
- OLE DB
- SQL Server Native Client OLE DB provider
- SQL Server Native Client, OLE DB
ms.assetid: da846da4-ec19-4a4f-81fb-7d5a2b2bf80a
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a220573b38f7aff0296e1ec2c507a4b8389ea3ce
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2020
ms.locfileid: "85998859"
---
# <a name="sql-server-native-client-ole-db"></a>SQL Server Native Client (OLE DB)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter (SQLNCLI) ist eine com-API auf niedriger Ebene, die für den Datenzugriff verwendet wird. Der OLE DB-Anbieter von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client wird für die Entwicklung von Tools, Hilfsprogrammen oder untergeordneten Komponenten empfohlen, die eine hohe Leistung erfordern. Der OLE DB-Anbieter von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ist ein systemeigener Hochleistungsanbieter, der direkt auf das [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-TDS-Protokoll (Tabular Data Stream) zugreift.  
  
 Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client stellt OLE DB-Unterstützung für Anwendungen zur Verfügung, die eine Verbindung zu [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] herstellen.  
  
 Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter ist ein OLE DB, Version 2,0-kompatibler Anbieter.  
 
> [!IMPORTANT]
> Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB (SQLNCLI) ist weiterhin veraltet, und es wird nicht empfohlen, ihn für neue Entwicklungsarbeiten zu verwenden. Verwenden Sie stattdessen den neuen [Microsoft OLE DB-Treiber für SQL Server](../../../connect/oledb/oledb-driver-for-sql-server.md) (MSOLEDBSQL), der mit den aktuellsten Serverfeatures aktualisiert wird.
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Erstellen einer SQL Server Native Client OLE DB-Anbieteranwendung](../../../relational-databases/native-client-ole-db-provider/creating-a-sql-server-native-client-ole-db-provider-application.md)  
  
-   [Datenquellenobjekte &#40;OLE DB&#41;](../../../relational-databases/native-client-ole-db-data-source-objects/data-source-objects-ole-db.md)  
  
-   [Befehle](../../../relational-databases/native-client-ole-db-commands/commands.md)  
  
-   [Rowsets](../../../relational-databases/native-client-ole-db-rowsets/rowsets.md)  
  
-   [Gespeicherte Prozeduren](../../../relational-databases/native-client/ole-db/stored-procedures.md)  
  
-   [BLOBs und OLE-Objekte](../../../relational-databases/native-client-ole-db-blobs/blobs-and-ole-objects.md)  
  
-   [Tabellen und Indizes](../../../relational-databases/native-client-ole-db-tables-indexes/tables-and-indexes.md)  
  
-   [Datentypen &#40;OLE DB&#41;](../../../relational-databases/native-client-ole-db-data-types/data-types-ole-db.md)  
  
-   [Schema Rowset Support &#40;OLE DB&#41; (Schemarowset-Unterstützung &#40;OLE DB&#41;)](../../../relational-databases/native-client/ole-db/schema-rowset-support-ole-db.md)  
  
-   [Tabellenwertparameter &#40;OLE DB&#41;](../../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)  
  
-   [Date and Time Improvements &#40;OLE DB&#41; (Verbesserungen bei Datum und Uhrzeit &#40;OLE DB&#41;)](../../../relational-databases/native-client-ole-db-date-time/date-and-time-improvements-ole-db.md)  
  
-   [Große benutzerdefinierte CLR-Typen &#40;OLE DB&#41;](../../../relational-databases/native-client/ole-db/large-clr-user-defined-types-ole-db.md)  
  
-   [FILESTREAM-Unterstützung &#40;OLE DB&#41;](../../../relational-databases/native-client/ole-db/filestream-support-ole-db.md)  
  
-   [Transaktionen](../../../relational-databases/native-client-ole-db-transactions/transactions.md)  
  
-   [Fehler](../../../relational-databases/native-client-ole-db-errors/errors.md)  
  
-   [Dienstprinzipalnamen (SPN) in Clientverbindungen (OLE DB)](../../../relational-databases/native-client/ole-db/service-principal-names-spns-in-client-connections-ole-db.md)  
  
-   [Unterstützung für Sparsespalten &#40;OLE DB&#41;](../../../relational-databases/native-client/ole-db/sparse-columns-support-ole-db.md)  
  
-   [SQL Server Native Client &#40;OLE DB&#41; Referenz](../../../relational-databases/native-client-ole-db-interfaces/sql-server-native-client-ole-db-interfaces.md)  
  
-   [Vorgehensweisen für OLE DB](../../../relational-databases/native-client-ole-db-how-to/ole-db-how-to-topics.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Programmierung für SQL Server Native Client](../../../relational-databases/native-client/sql-server-native-client-programming.md)  
  
  
