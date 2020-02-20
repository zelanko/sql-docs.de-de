---
title: Tabellenwertparameter (OLE DB) | Microsoft-Dokumentation
description: Tabellenwertparameter (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB, table-valued parameters
- table-valued parameters (OLE DB)
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 3f942130244aaf08d533ac4a1abdc1752971209d
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "68015272"
---
# <a name="table-valued-parameters-ole-db"></a>Tabellenwertparameter (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  In diesem Abschnitt wird die Unterstützung für Tabellenwertparameter im OLE DB-Treiber für SQL Server beschrieben. Weitere allgemeine Informationen finden Sie im Artikel [Tabellenwertparameter (OLE DB-Treiber für SQL Server)](../../oledb/features/table-valued-parameters-oledb-driver-for-sql-server.md). Ein Beispiel finden Sie unter [Verwenden von Tabellenwertparametern (OLE DB)](../../oledb/ole-db-how-to/use-table-valued-parameters-ole-db.md).  
  
## <a name="remarks"></a>Bemerkungen  
 Derzeit können Sie mehrzeilige Daten an den Server als Parameter an eine Prozedur mit Parametersätzen senden (der DBPARAMS-Parameter in **ICommand::Execute**). Bei Parametersätzen muss jedes Element des Satzes in einer separaten Remoteprozeduranforderung (Remote Procedure Call, RPC) an den Server gesendet werden. Tabellenwertparameter stellen eine ähnliche Funktionalität bereit, bieten jedoch eine bessere Integration mit dem Server. Dadurch werden die Anzahl von RPC-Anforderungen reduziert und setbasierte Vorgänge auf dem Server aktiviert.  
  
 Tabellenwertparameter werden im OLE DB-Treiber für SQL Server als OLE DB-**Rowsetobjekte** unterstützt. Jedes **Rowset**-Objekt kann vom Consumer (d.h. von der Clientanwendung, die den OLE DB-Treiber für SQL Server verwendet) als Platzhalter für Tabellenwertparameter bereitgestellt werden. Tabellenwertparameter werden wie andere [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Parametertypen behandelt. Der OLE DB-Treiber für SQL Server stellt Schnittstellen für das Erstellen, für die Ermittlung, Spezifikation und Bindung sowie Schemaschnittstellen zur Verfügung.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Tabellenwertparameter-Rowseterstellung](../../oledb/ole-db-table-valued-parameters/table-valued-parameter-rowset-creation.md)  
  
-   [Tabellenwertparameter-Typermittlung](../../oledb/ole-db-table-valued-parameters/table-valued-parameter-type-discovery.md)  
  
-   [Ausführen von Befehlen, die Tabellenwertparameter enthalten](../../oledb/ole-db-table-valued-parameters/executing-commands-containing-table-valued-parameters.md)  
  
-   [Einfügen von Daten in Tabellenwertparameter](../../oledb/ole-db-table-valued-parameters/inserting-data-into-table-valued-parameters.md)  
  
-   [Schemarowsets für OLE DB-Tabellenwertparameter geändert](../../oledb/ole-db-table-valued-parameters/schema-rowsets-changed-for-ole-db-table-valued-parameters.md)  
  
-   [OLE DB-Typunterstützung für Tabellenwertparameter](../../oledb/ole-db-table-valued-parameters/ole-db-table-valued-parameter-type-support.md)  
  
-   [OLE DB-Unterstützung für Tabellenwertparameter-Typen &#40;Methoden&#41;](../../oledb/ole-db-table-valued-parameters/ole-db-table-valued-parameter-type-support-methods.md)  
  
-   [OLE DB-Unterstützung für Tabellenwertparameter-Typen &#40;Eigenschaften&#41;](../../oledb/ole-db-table-valued-parameters/ole-db-table-valued-parameter-type-support-properties.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [OLE DB Driver for SQL Server Programming (OLE DB-Treiber für SQL Server-Programmierung)](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)   
 [Verwenden von Tabellenwertparametern &#40;OLE DB&#41;](../../oledb/ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
