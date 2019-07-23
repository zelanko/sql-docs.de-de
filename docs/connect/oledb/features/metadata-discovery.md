---
title: Metadatenermittlung | Microsoft-Dokumentation
description: Metadatenermittlung in OLE DB Treiber für SQL Server
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 9891e5708110be83a4ef33cb2a142accaf93ffe2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67989062"
---
# <a name="metadata-discovery"></a>Metadatenermittlung
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Aufgrund der verbesserten Metadatenermittlung in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] können OLE DB-Treiber für SQL Server-Anwendungen sicherstellen, dass Spalten- oder Parametermetadaten, die von der Ausführung einer Abfrage zurückgegeben werden, mit dem Metadatenformat identisch oder kompatibel sind, das Sie vor dem Ausführen der Abfrage angegeben haben. Wenn die nach der Ausführung der Abfrage zurückgegebenen Metadaten nicht mit dem Metadatenformat identisch sind, das Sie vor der Ausführung der Abfrage angegeben haben, wird ein Fehler ausgegeben.  
  
 Sie können jetzt in bcp sowie in IBCPSession- und IBCPSession2-Schnittstellen verzögertes Lesen (verzögerte Metadatenerkennung) angeben, um Metadatenermittlung für Abfrageausgabevorgänge zu verhindern. Dies verbessert die Leistung und schließt Metadatenermittlungsfehler aus.  
  
 Wenn Sie eine Anwendung mit dem OLE DB-Treiber für SQL Server entwickeln, jedoch eine Verbindung mit einer früheren Serverversion als [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] herstellen, entspricht die Funktionalität der Metadatenermittlung der Version des Servers.  
  
## <a name="remarks"></a>Remarks   
 Die folgenden OLE DB-Elementfunktionen wurden in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] verbessert, um verbesserte Metadatenermittlung bereitzustellen:  
  
-   IColumnsInfo::GetColumnInfo  
  
-   IColumnsRowset::GetColumnsRowset  
  
-   ICommandWithParameters:: GetParameterInfo (Weitere Informationen finden Sie unter [ICommandWithParameters](../../oledb/ole-db-interfaces/icommandwithparameters.md) )  
  
 Das Angeben des Metadatenformats mit IBCPSession::BCPSetBulkMode führt ebenfalls zu einer Leistungsverbesserung.  
  
 Die verbesserte metadatenermittlung in OLE DB Treiber für SQL Server ist aufgrund der Addition von zwei gespeicherten Prozeduren [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]in möglich:  
  
-   sp_describe_first_result_set  
  
-   sp_describe_undeclared_parameters  
  
## <a name="see-also"></a>Weitere Informationen  
 [OLE DB-Treiber für SQL Server-Features](../../oledb/features/oledb-driver-for-sql-server-features.md)  
  
  
