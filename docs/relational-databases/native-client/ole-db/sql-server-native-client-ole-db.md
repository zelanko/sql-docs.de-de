---
title: SQL Server Native Client (OLE DB) | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a895b11786628a1a43103607337d4d972d81cdfd
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68031850"
---
# <a name="sql-server-native-client-ole-db"></a>SQL Server Native Client (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

Die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieters (SQLNCLI) ist eine untergeordnete COM-API, die für den Zugriff auf Daten verwendet wird. Der OLE DB-Anbieter von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client wird für die Entwicklung von Tools, Hilfsprogrammen oder untergeordneten Komponenten empfohlen, die eine hohe Leistung erfordern. Der OLE DB-Anbieter von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ist ein systemeigener Hochleistungsanbieter, der direkt auf das [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-TDS-Protokoll (Tabular Data Stream) zugreift.  
  
 Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client stellt OLE DB-Unterstützung für Anwendungen zur Verfügung, die eine Verbindung zu [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] herstellen.  
  
 Die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter ist ein OLE DB Version 2.0-konforme-Anbieter.  
 
> [!IMPORTANT]
> Die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB (SQLNCLI) bleibt als veraltet markierte und es wird nicht empfohlen, für das Entwickeln neuer Anwendungen nicht verwendet. Verwenden Sie stattdessen die neuen [Microsoft OLE DB-Treiber für SQL Server](../../../connect/oledb/oledb-driver-for-sql-server.md) (MSOLEDBSQL) wird die mit den neuesten Serverfunktionen aktualisiert.
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Erstellen einer SQL Server Native Client OLE DB-Anbieteranwendung](../../../relational-databases/native-client-ole-db-provider/creating-a-sql-server-native-client-ole-db-provider-application.md)  
  
-   [Datenquellenobjekte &#40;OLE-DB&#41;](../../../relational-databases/native-client-ole-db-data-source-objects/data-source-objects-ole-db.md)  
  
-   [Befehle](../../../relational-databases/native-client-ole-db-commands/commands.md)  
  
-   [Rowsets](../../../relational-databases/native-client-ole-db-rowsets/rowsets.md)  
  
-   [Gespeicherte Prozeduren](../../../relational-databases/native-client/ole-db/stored-procedures.md)  
  
-   [BLOBs und OLE-Objekte](../../../relational-databases/native-client-ole-db-blobs/blobs-and-ole-objects.md)  
  
-   [Tabellen und Indizes](../../../relational-databases/native-client-ole-db-tables-indexes/tables-and-indexes.md)  
  
-   [Datentypen &#40;OLE-DB&#41;](../../../relational-databases/native-client-ole-db-data-types/data-types-ole-db.md)  
  
-   [Schema Rowset Support &#40;OLE DB&#41; (Schemarowset-Unterstützung &#40;OLE DB&#41;)](../../../relational-databases/native-client/ole-db/schema-rowset-support-ole-db.md)  
  
-   [Tabellenwertparameter &#40;OLE DB&#41;](../../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)  
  
-   [Date and Time Improvements &#40;OLE DB&#41; (Verbesserungen bei Datum und Uhrzeit &#40;OLE DB&#41;)](../../../relational-databases/native-client-ole-db-date-time/date-and-time-improvements-ole-db.md)  
  
-   [Große benutzerdefinierte CLR-Typen &#40;OLE DB&#41;](../../../relational-databases/native-client/ole-db/large-clr-user-defined-types-ole-db.md)  
  
-   [FILESTREAM-Unterstützung &#40;OLE-DB&#41;](../../../relational-databases/native-client/ole-db/filestream-support-ole-db.md)  
  
-   [Transaktionen](../../../relational-databases/native-client-ole-db-transactions/transactions.md)  
  
-   [Fehler](../../../relational-databases/native-client-ole-db-errors/errors.md)  
  
-   [Dienstprinzipalnamen (SPN) &#40;SPNs&#41; in Clientverbindungen &#40;(OLE DB&#41;)](../../../relational-databases/native-client/ole-db/service-principal-names-spns-in-client-connections-ole-db.md)  
  
-   [Unterstützung für Sparsespalten &#40;OLE DB&#41;](../../../relational-databases/native-client/ole-db/sparse-columns-support-ole-db.md)  
  
-   [SQL Server Native Client &#40;OLE DB&#41; Verweis](../../../relational-databases/native-client-ole-db-interfaces/sql-server-native-client-ole-db-interfaces.md)  
  
-   [Vorgehensweisen für OLE DB](../../../relational-databases/native-client-ole-db-how-to/ole-db-how-to-topics.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Programmierung für SQL Server Native Client](../../../relational-databases/native-client/sql-server-native-client-programming.md)  
  
  
