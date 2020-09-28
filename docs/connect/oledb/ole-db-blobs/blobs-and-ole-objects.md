---
title: Blobs und OLE-Objekte (OLE DB-Treiber) | Microsoft-Dokumentation
description: Erfahren Sie, wie die ISequentialStream-Schnittstelle den Zugriff von Consumern auf SQL Server-Datentypen als Blobs im OLE DB-Treiber für SQL Server unterstützt.
ms.custom: ''
ms.date: 05/25/2020
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- BLOBs, OLE objects
- BLOBs
- storage object [OLE DB]
- OLE DB Driver for SQL Server, BLOBs
- large data, OLE objects
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 50c19527b536da0a61d8aa6c7c76ec34010ea268
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88861413"
---
# <a name="blobs-and-ole-objects"></a>BLOBs und OLE-Objekte
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Der OLE DB-Treiber für SQL Server macht die Schnittstelle **ISequentialStream** verfügbar, um den Consumerzugriff auf die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datentypen **ntext**, **text**<a href="#text_note"><sup>**1**</sup></a>, **image**, **varchar(max)** , **nvarchar(max)** , **varbinary(max)** und XML als Binary Large Objects (Blobs) zu unterstützen. Die Methode **Read** für **ISequentialStream** ermöglicht dem Consumer, große Datenmengen in überschaubaren Abschnitten abzurufen.

 <b id="text_note">[1]:</b> Die Schnittstelle „ISequentialStream“ zum Einfügen von UTF-8-codierten Daten in eine Legacytextspalte kann nur auf Servern eingesetzt werden, die UTF-8 unterstützen. Der Versuch, dieses Szenario für einen Server auszuführen, der UTF-8 nicht unterstützt, führt zu folgender Fehlermeldung des Treibers: „*Streaming über den ausgewählten Spaltentyp ist nicht zugelassen*“.

 Ein Beispiel für diese Feature finden Sie unter [Festlegen von großen Daten &#40;OLE DB&#41;](../../oledb/ole-db-how-to/set-large-data-ole-db.md).  
  
 Der OLE DB-Treiber für SQL Server kann eine vom Consumer implementierte **IStorage**-Schnittstelle verwenden, wenn der Consumer den Schnittstellenzeiger in einem für Datenänderungen gebundenen Accessor bereitstellt.  
  
 Für Datentypen mit umfangreichen Werten prüft der OLE DB-Treiber für SQL Server, ob in **IRowset** und DDL-Schnittstellen Annahmen über die Typgröße vorhanden sind. Spalten mit den Datentypen **varchar**, **nvarchar** und **varbinary**, bei denen die maximale Größe auf „Unlimited“ festgelegt ist, werden von den Schemarowsets und Schnittstellen, die Spaltendatentypen wiedergeben, als ISLONG dargestellt.  
  
 Der OLE DB-Treiber für SQL Server macht die Datentypen **varchar(max)** , **varbinary(max)** und **nvarchar(max)** als DBTYPE_STR, DBTYPE_BYTES bzw. DBTYPE_WSTR verfügbar.  
  
 Um mit diesen Typen zu arbeiten, stehen der Anwendung die folgenden Optionen zur Verfügung:  
  
-   Als den betreffenden Typ binden (DBTYPE_STR, DBTYPE_BYTES, DBTYPE_WSTR). Wenn der Puffer nicht groß genug ist, werden Daten abgeschnitten, wie dies auch in früheren Versionen der Fall war (obwohl jetzt umfangreichere Werte verfügbar sind).  
  
-   Als den betreffenden Typ binden und zudem DBTYPE_BYREF angeben  
  
-   Als DBTYPE_IUNKNOWN binden und Streaming verwenden  
  
 Wenn die Bindung an DBTYPE_IUNKNOWN erfolgt, wird die Streamingfunktion ISequentialStream verwendet. Der OLE DB-Treiber für SQL Server unterstützt das Binden von Ausgabeparametern als DBTYPE_IUNKNOWN für Datentypen mit großen Werten. Damit werden Szenarios unterstützt, in denen gespeicherte Prozeduren diese Datentypen als Rückgabewerte zurückgeben, die alle als DBTYPE_IUNKNOWN an den Client zurückgegeben werden.  
  
## <a name="storage-object-limitations"></a>Speicherobjekteinschränkungen  
  
-   Der OLE DB-Treiber für SQL Server kann nur ein einzelnes geöffnetes Speicherobjekt unterstützen. Wenn versucht wird, mehrere Speicherobjekte zu öffnen (um einen Verweis auf mehrere **ISequentialStream**-Schnittstellenzeiger abzurufen), wird DBSTATUS_E_CANTCREATE zurückgegeben.  
  
-   Im OLE DB-Treiber für SQL Server lautet der Standardwert der schreibgeschützten DBPROP_BLOCKINGSTORAGEOBJECTS-Eigenschaft VARIANT_TRUE. Deshalb schlagen einige Methoden (solche, die sich nicht in den Speicherobjekten befinden) mit E_UNEXPECTED fehl, wenn ein Speicherobjekt aktiv ist.  
  
-   Die Länge der Daten eines von einem Consumer implementierten Speicherobjekts muss dem OLE DB-Treiber für SQL Server mitgeteilt werden, wenn der auf das Speicherobjekt verweisende Zeilenaccessor erstellt wird. Der Consumer muss einen Längenindikator in der zur Accessorerstellung verwendeten DBBINDING-Struktur binden.  
  
-   Wenn eine Zeile mehrere große Datenwerte enthält und DBPROP_ACCESSORDER nicht auf DBPROPVAL_AO_RANDOM lautet, muss der Consumer entweder ein vom Cursor des OLE DB-Treibers für SQL Server unterstütztes Rowset verwenden, um Zeilendaten abzurufen, oder alle großen Datenwerte vor dem Abrufen weiterer Zeilenwerte verarbeiten. Wenn DBPROP_ACCESSORDER auf DBPROPVAL_AO_RANDOM lautet, speichert der OLE DB-Treiber für SQL Server alle XML-Datentypen als Binary Large Objects (BLOBs) zwischen, damit in jeder beliebigen Reihenfolge auf sie zugegriffen werden kann.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Abrufen großer Datenmengen](../../oledb/ole-db-blobs/getting-large-data.md)  
  
-   [Festlegen großer Datenmengen](../../oledb/ole-db-blobs/setting-large-data.md)  
  
-   [Streamingunterstützung für BLOB-Ausgabeparameter](../../oledb/ole-db-blobs/streaming-support-for-blob-output-parameters.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [OLE DB Driver for SQL Server Programming (OLE DB-Treiber für SQL Server-Programmierung)](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)        
 [Verwenden von Datentypen mit umfangreichen Werten](../../oledb/features/using-large-value-types.md)  
  
  
