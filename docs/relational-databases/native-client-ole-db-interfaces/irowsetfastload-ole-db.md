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
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 39a9f660f39a27a189c81d24d4d155d8764037d1
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73789399"
---
# <a name="irowsetfastload-ole-db"></a>IRowsetFastLoad (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Die **IRowsetFastLoad** -Schnittstelle unterstützt speicherbasierte Massenkopiervorgänge in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB Provider-Consumer verwenden die-Schnittstelle, um schnell Daten zu einer vorhandenen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Tabelle hinzuzufügen.  
  
 Wenn Sie SSPROP_ENABLEFASTLOAD für eine Sitzung auf VARIANT_TRUE festlegen, können Sie keine Daten aus Rowsets lesen, die danach von dieser Sitzung zurückgegeben werden. Wenn SSPROP_ENABLEFASTLOAD auf VARIANT_TRUE festgelegt wird, sind alle Rowsets, die in dieser Sitzung erstellt werden, vom Typ „IRowsetFastLoad“. IRowsetFastLoad-Rowsets unterstützen die Funktionalität zum Abrufen von Rowsets nicht. Daher können aus diesen Rowsets keine Daten gelesen werden.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Methode|und Beschreibung|  
|------------|-----------------|  
|[IRowsetFastLoad::Commit &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-commit-ole-db.md)|Markiert das Ende eines Batches eingefügter Zeilen und schreibt die Zeilen in die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Tabelle.|  
|[IRowsetFastLoad::InsertRow &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-insertrow-ole-db.md)|Fügt dem Rowset für das Massenkopieren eine Zeile hinzu.|  
  
## <a name="see-also"></a>Siehe auch  
 [Schnitt &#40;stellen&#41; OLE DB](https://msdn.microsoft.com/library/34c33364-8538-45db-ae41-5654481cda93)   
 [Massenkopieren von Daten mithilfe von IRowsetFastLoad &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-how-to/bulk-copy-data-using-irowsetfastload-ole-db.md)   
 [Senden von BLOB-Daten an SQL SERVER mit IROWSETFASTLOAD und ISEQUENTIALSTREAM &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md)  
  
  
