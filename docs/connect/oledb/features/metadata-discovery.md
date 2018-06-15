---
title: Metadatenermittlung | Microsoft Docs
description: Metadatenermittlung in OLE DB-Treiber für SQL Server
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|features
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 3980b8064b565dc09ebb79e9d81be9c6f85fc21a
ms.sourcegitcommit: 354ed9c8fac7014adb0d752518a91d8c86cdce81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/14/2018
ms.locfileid: "35611635"
---
# <a name="metadata-discovery"></a>Metadatenermittlung
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Die verbesserten metadatenermittlung in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] ermöglicht OLE DB-Treiber für SQL Server-Anwendungen, um sicherzustellen, dass diese Spalte oder Parametermetadaten, die von der Ausführung einer Abfrage zurückgegeben wird, identisch oder kompatibel mit dem Metadatenformat identisch angegeben vor die Abfrage wird ausgeführt. Wenn die nach der Ausführung der Abfrage zurückgegebenen Metadaten nicht mit dem Metadatenformat identisch sind, das Sie vor der Ausführung der Abfrage angegeben haben, wird ein Fehler ausgegeben.  
  
 In Bcp und Ibcpsession- und IBCPSession2-Schnittstellen, Sie können jetzt angeben verzögertes lesen (verzögerte Metadatenerkennung), um metadatenermittlung für abfrageausgabevorgänge zu vermeiden. Dies verbessert die Leistung und schließt Metadatenermittlungsfehler aus.  
  
 Wenn der Entwicklung einer Anwendung mithilfe von OLE DB-Treiber für SQL Server aber beim Herstellen einer mit einer Serverversion Verbindung vor [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], metadatenermittlung Funktionalität auf die Version des Servers.  
  
## <a name="remarks"></a>Hinweise   
 Die folgenden OLE DB-Elementfunktionen wurden in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] verbessert, um verbesserte Metadatenermittlung bereitzustellen:  
  
-   IColumnsInfo::GetColumnInfo  
  
-   IColumnsRowset::GetColumnsRowset  
  
-   ICommandWithParameters:: GetParameterInfo (finden Sie unter [ICommandWithParameters](../../oledb/ole-db-interfaces/icommandwithparameters.md) für Weitere Informationen)  
  
 Verbessert die Leistung wird auch angezeigt werden, wenn Metadatenformat mit IBCPSession::BCPSetBulkMode angeben  
  
 Die verbesserte metadatenermittlung in OLE DB-Treiber für SQL Server kann durch das Hinzufügen von zwei gespeicherten Prozeduren in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]:  
  
-   sp_describe_first_result_set  
  
-   sp_describe_undeclared_parameters  
  
## <a name="see-also"></a>Siehe auch  
 [OLE DB-Treiber für SQL Server-Features](../../oledb/features/oledb-driver-for-sql-server-features.md)  
  
  
