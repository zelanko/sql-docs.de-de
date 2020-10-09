---
description: ISSAsynchStatus (Native Client OLE DB-Anbieter)
title: ISSAsynchStatus (Native Client OLE DB-Anbieter) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- ISSAsynchStatus (OLE DB)
apitype: COM
helpviewer_keywords:
- ISSAsynchStatus interface
ms.assetid: c643f09f-9ccc-4d8b-9243-3cde86c2bd46
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 11a4356b4078c7c154a5c20fd62e1f0d8a5ae151
ms.sourcegitcommit: 4d370399f6f142e25075b3714e5c2ce056b1bfd0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2020
ms.locfileid: "91865453"
---
# <a name="issasynchstatus-native-client-ole-db-provider"></a>ISSAsynchStatus (Native Client OLE DB-Anbieter)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  **ISSAsynchStatus** unterstützt asynchrone [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Vorgänge. Hierbei handelt es sich um eine optionale Schnittstelle, die von der OLE DB-Kernschnittstelle **IDBAsynchStatus**erbt. Neben den von **IDBAsynchStatus** geerbten Methoden **Abort** und **GetStatus**stellt **ISSAsynchStatus** eine neue Methode bereit, die verwendet wird, um zu warten, bis ein asynchroner Vorgang abgeschlossen ist oder ein Timeout auftritt.  
  
|Methode|BESCHREIBUNG|  
|------------|-----------------|  
|[ISSAsynchStatus::Abort &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/issasynchstatus-abort-ole-db.md)|Bricht einen asynchron ausgeführten Vorgang ab.|  
|[ISSAsynchStatus::GetStatus &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/issasynchstatus-getstatus-ole-db.md)|Gibt den Status eines asynchron ausgeführten Vorgangs zurück.|  
|[ISSAsynchStatus::WaitForAsynchCompletion &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/issasynchstatus-waitforasynchcompletion-ole-db.md)|Wartet, bis der asynchron ausgeführte Vorgang abgeschlossen ist oder ein Timeout auftritt.|  
  
## <a name="remarks"></a>Bemerkungen  
 Die **ISSAsynchStatus** -Implementierung der **ISSAsynchStatus::GetStatus** -Methode ist mit der **IDBAsynchStatus::GetStatus** -Methode identisch, gibt jedoch anstelle von DB_E_CANCELED E_UNEXPECTED zurück, wenn die Initialisierung eines Datenquellenobjekts abgebrochen wird (wenngleich **ISSAsynchStatus::WaitForAsynchCompletion** DB_E_CANCELED zurückgibt). Dies ist darauf zurückzuführen, dass das Datenquellenobjekt nach einem Abbruchvorgang nicht mehr den gewöhnlichen Status aufweist, sodass weitere Initialisierungsvorgänge durchgeführt werden können.  
  
 Die folgenden Methoden unterstützen die Verwendung der asynchronen Ausführung in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
-   **ICommand::Execute**  
  
-   **IOpenRowset::OpenRowset**  
  
-   **IMultipleResults::GetResult**  
  
## <a name="see-also"></a>Weitere Informationen  
 [Schnittstellen &#40;OLE DB&#41;](./sql-server-native-client-ole-db-interfaces.md)   
 [Ausführen asynchroner Vorgänge](../../relational-databases/native-client/features/performing-asynchronous-operations.md)  
  
