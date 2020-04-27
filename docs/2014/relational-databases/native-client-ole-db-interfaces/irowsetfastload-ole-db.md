---
title: IRowsetFastLoad (OLE DB) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- IRowsetFastLoad interface
ms.assetid: d19a7097-48d9-409a-aff9-277891b7aca7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 35cee52e9a85989123bcb10d998d37ce86a28601
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63209812"
---
# <a name="irowsetfastload-ole-db"></a>IRowsetFastLoad (OLE DB)
  Die `IRowsetFastLoad` -Schnittstelle unter [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stützt speicherbasierte Massen Kopiervorgänge. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB-Anbieter Consumer verwenden die-Schnittstelle, um schnell Daten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zu einer vorhandenen Tabelle hinzuzufügen.  
  
 Wenn Sie SSPROP_ENABLEFASTLOAD für eine Sitzung auf VARIANT_TRUE festlegen, können Sie keine Daten aus Rowsets lesen, die danach von dieser Sitzung zurückgegeben werden. Wenn SSPROP_ENABLEFASTLOAD auf VARIANT_TRUE festgelegt wird, sind alle Rowsets, die in dieser Sitzung erstellt werden, vom Typ „IRowsetFastLoad“. IRowsetFastLoad-Rowsets unterstützen die Funktionalität zum Abrufen von Rowsets nicht. Daher können aus diesen Rowsets keine Daten gelesen werden.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Methode|BESCHREIBUNG|  
|------------|-----------------|  
|[IRowsetFastLoad::Commit &#40;OLE DB&#41;](irowsetfastload-commit-ole-db.md)|Markiert das Ende eines Batches eingefügter Zeilen und schreibt die Zeilen in die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Tabelle.|  
|[IRowsetFastLoad::InsertRow &#40;OLE DB&#41;](irowsetfastload-insertrow-ole-db.md)|Fügt dem Rowset für das Massenkopieren eine Zeile hinzu.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Schnittstellen &#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md)   
 [Massen Daten kopieren mithilfe der IRowsetFastLoad-&#40;OLE DB&#41;](../native-client-ole-db-how-to/bulk-copy-data-using-irowsetfastload-ole-db.md)   
 [Senden von BLOB-Daten an SQL SERVER mit IROWSETFASTLOAD und ISEQUENTIALSTREAM &#40;OLE DB&#41;](../native-client-ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md)  
  
  
