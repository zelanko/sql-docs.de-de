---
title: ISSAsynchStatus (OLE DB) | Microsoft-Dokumentation
description: ISSAsynchStatus (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-interfaces
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISSAsynchStatus (OLE DB)
apitype: COM
helpviewer_keywords:
- ISSAsynchStatus interface
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 6c94fe229ab8b00ded7e0d32f45e6e2de8cdaaf4
ms.sourcegitcommit: 50838d7e767c61dd0b5e677b6833dd5c139552f2
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/18/2018
ms.locfileid: "39105786"
---
# <a name="issasynchstatus-ole-db"></a>ISSAsynchStatus (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Die **ISSAsynchStatus**-Schnittstelle unterstützt asynchrone [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Vorgänge. Hierbei handelt es sich um eine optionale Schnittstelle, die von der OLE DB-Schnittstelle **IDBAsynchStatus**erbt. Neben den von **IDBAsynchStatus** geerbten Methoden **Abort** und **GetStatus**stellt **ISSAsynchStatus** eine neue Methode bereit, die verwendet wird, um zu warten, bis ein asynchroner Vorgang abgeschlossen ist oder ein Timeout auftritt.  
  
|Methode|und Beschreibung|  
|------------|-----------------|  
|[ISSAsynchStatus::Abort (OLE DB)](../../oledb/ole-db-interfaces/issasynchstatus-abort-ole-db.md)|Bricht einen asynchron ausgeführten Vorgang ab.|  
|[ISSAsynchStatus::GetStatus (OLE DB)](../../oledb/ole-db-interfaces/issasynchstatus-getstatus-ole-db.md)|Gibt den Status eines asynchron ausgeführten Vorgangs zurück.|  
|[ISSAsynchStatus::WaitForAsynchCompletion (OLE DB)](../../oledb/ole-db-interfaces/issasynchstatus-waitforasynchcompletion-ole-db.md)|Wartet, bis der asynchron ausgeführte Vorgang abgeschlossen ist oder ein Timeout auftritt.|  
  
## <a name="remarks"></a>Remarks  
 Die **ISSAsynchStatus** -Implementierung der **ISSAsynchStatus::GetStatus** -Methode ist mit der **IDBAsynchStatus::GetStatus** -Methode identisch, gibt jedoch anstelle von DB_E_CANCELED E_UNEXPECTED zurück, wenn die Initialisierung eines Datenquellenobjekts abgebrochen wird (wenngleich **ISSAsynchStatus::WaitForAsynchCompletion** DB_E_CANCELED zurückgibt). Dies ist darauf zurückzuführen, dass das Datenquellenobjekt nach einem Abbruchvorgang nicht mehr den gewöhnlichen Status aufweist, sodass weitere Initialisierungsvorgänge durchgeführt werden können.  
  
 Die folgenden Methoden unterstützen die Verwendung der asynchronen Ausführung in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]:  
  
-   **ICommand::Execute**  
  
-   **IOpenRowset::OpenRowset**  
  
-   **IMultipleResults::GetResult**  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Schnittstellen &#40;OLE-DB&#41;](../../oledb/ole-db-interfaces/oledb-driver-for-sql-server-ole-db-interfaces.md)    
 [Ausführen asynchroner Vorgänge](../../oledb/features/performing-asynchronous-operations.md)  
  
  
