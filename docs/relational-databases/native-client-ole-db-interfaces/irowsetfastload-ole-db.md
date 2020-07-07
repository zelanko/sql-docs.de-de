---
title: IRowsetFastLoad (OLE DB) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: COM
helpviewer_keywords:
- IRowsetFastLoad interface
ms.assetid: d19a7097-48d9-409a-aff9-277891b7aca7
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 66af5f470d5b2d32fbdae29d08b92bccb6e1b101
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2020
ms.locfileid: "86011166"
---
# <a name="irowsetfastload-ole-db"></a>IRowsetFastLoad (OLE DB)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Die **IRowsetFastLoad**-Schnittstelle unterstützt speicherbasierte Massenkopiervorgänge in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB-Anbieter Consumer verwenden die-Schnittstelle, um schnell Daten zu einer vorhandenen Tabelle hinzuzufügen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Wenn Sie SSPROP_ENABLEFASTLOAD für eine Sitzung auf VARIANT_TRUE festlegen, können Sie keine Daten aus Rowsets lesen, die danach von dieser Sitzung zurückgegeben werden. Wenn SSPROP_ENABLEFASTLOAD auf VARIANT_TRUE festgelegt wird, sind alle Rowsets, die in dieser Sitzung erstellt werden, vom Typ „IRowsetFastLoad“. IRowsetFastLoad-Rowsets unterstützen die Funktionalität zum Abrufen von Rowsets nicht. Daher können aus diesen Rowsets keine Daten gelesen werden.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Methode|BESCHREIBUNG|  
|------------|-----------------|  
|[IRowsetFastLoad::Commit &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-commit-ole-db.md)|Markiert das Ende eines Batches eingefügter Zeilen und schreibt die Zeilen in die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Tabelle.|  
|[IRowsetFastLoad::InsertRow &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-insertrow-ole-db.md)|Fügt dem Rowset für das Massenkopieren eine Zeile hinzu.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Schnittstellen &#40;OLE DB&#41;](https://msdn.microsoft.com/library/34c33364-8538-45db-ae41-5654481cda93)   
 [Massen Daten kopieren mithilfe der IRowsetFastLoad-&#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-how-to/bulk-copy-data-using-irowsetfastload-ole-db.md)   
 [Senden von BLOB-Daten an SQL SERVER mit IROWSETFASTLOAD und ISEQUENTIALSTREAM &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md)  
  
  
