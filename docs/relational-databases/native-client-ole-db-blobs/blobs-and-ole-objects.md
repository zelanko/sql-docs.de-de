---
title: Blobs und OLE-Objekte | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- BLOBs, OLE objects
- BLOBs
- storage object [OLE DB]
- SQL Server Native Client OLE DB provider, BLOBs
- large data, OLE objects
ms.assetid: 767fa2f6-9cd2-436f-add5-e760bed29a58
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d0cb9751940489513f939ab8ee52728c6b75e925
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297675"
---
# <a name="blobs-and-ole-objects"></a>BLOBs und OLE-Objekte
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter macht die **ISequentialStream-Schnittstelle** verfügbar, um den Consumerzugriff auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **ntext**, **text**, **image**, **varchar(max)**, **nvarchar(max)**, **varbinary(max)** und xml-Datentypen als binäre große Objekte (BLOBs) zu unterstützen. Die Methode **Read** für **ISequentialStream** ermöglicht dem Consumer, große Datenmengen in überschaubaren Abschnitten abzurufen.  
  
 Ein Beispiel für diese Feature finden Sie unter [Festlegen von großen Daten &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-how-to/set-large-data-ole-db.md).  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter kann eine vom Consumer implementierte **IStorage-Schnittstelle** verwenden, wenn der Consumer den Schnittstellenzeiger in einem für Datenänderungen gebundenen Accessor bereitstellt.  
  
 Bei Datentypen mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] großem Wert sucht der native Client-OLE-DB-Anbieter in **IRowset-** und DDL-Schnittstellen nach Typgrößenannahmen. Spalten mit **datentypen varchar**, **nvarchar**und **varbinary** mit maximaler Größe auf unbegrenzt werden über die Schemarowsets und Schnittstellen, die Spaltendatentypen zurückgeben, als ISLONG dargestellt.  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter macht die Typen **varchar(max),** **varbinary(max)** und **nvarchar(max)** als DBTYPE_STR, DBTYPE_BYTES und DBTYPE_WSTR verfügbar.  
  
 Um mit diesen Typen zu arbeiten, hat eine Anwendung die folgenden Optionen:  
  
-   Als den betreffenden Typ binden (DBTYPE_STR, DBTYPE_BYTES, DBTYPE_WSTR). Wenn der Puffer nicht groß genug ist, werden Daten abgeschnitten, wie dies auch in früheren Versionen der Fall war (obwohl jetzt umfangreichere Werte verfügbar sind).  
  
-   Als den betreffenden Typ binden und zudem DBTYPE_BYREF angeben  
  
-   Als DBTYPE_IUNKNOWN binden und Streaming verwenden  
  
 Wenn die Bindung an DBTYPE_IUNKNOWN erfolgt, wird die Streamingfunktion ISequentialStream verwendet. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter unterstützt das Binden von Ausgabeparametern als DBTYPE_IUNKNOWN für Datentypen mit großem Wert, um Szenarien zu erleichtern, in denen eine gespeicherte Prozedur diese Datentypen als Rückgabewerte zurückgibt, die als DBTYPE_IUNKNOWN für den Client verfügbar gemacht werden.  
  
## <a name="storage-object-limitations"></a>Speicherobjekteinschränkungen  
  
-   Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter kann nur ein einzelnes offenes Speicherobjekt unterstützen. Wenn versucht wird, mehrere Speicherobjekte zu öffnen (um einen Verweis auf mehrere **ISequentialStream**-Schnittstellenzeiger abzurufen), wird DBSTATUS_E_CANTCREATE zurückgegeben.  
  
-   Im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter ist der Standardwert der DBPROP_BLOCKINGSTORAGEOBJECTS schreibgeschützten Eigenschaft VARIANT_TRUE. Das zeigt an, dass einige Methoden (solche, die sich nicht in den Speicherobjekten befinden) mit E_UNEXPECTED fehlschlagen, wenn ein Speicherobjekt aktiv ist.  
  
-   Die Länge der Daten, die von einem vom Consumer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] implementierten Speicherobjekt angezeigt werden, muss dem nativen Client-OLE-DB-Anbieter bekannt gemacht werden, wenn der Zeilenaccessor erstellt wird, der auf das Speicherobjekt verweist. Der Consumer muss einen Längenindikator in der zur Accessorerstellung verwendeten DBBINDING-Struktur binden.  
  
-   Wenn eine Zeile mehr als einen einzelnen großen Datenwert enthält und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DBPROP_ACCESSORDER nicht DBPROPVAL_AO_RANDOM ist, muss der Consumer entweder ein vom Cursor unterstütztes Rowset des nativen Client-OLE-DB-Anbieters verwenden, um Zeilendaten abzurufen, oder alle großen Datenwerte verarbeiten, bevor andere Zeilenwerte abgerufen werden. Wenn DBPROP_ACCESSORDER DBPROPVAL_AO_RANDOM [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ist, speichert der native Client-OLE-DB-Anbieter alle XML-Datentypen als binäre große Objekte (BLOBs) zwischen, sodass in beliebiger Reihenfolge darauf zugegriffen werden kann.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Abrufen großer Datenmengen](../../relational-databases/native-client-ole-db-blobs/getting-large-data.md)  
  
-   [Festlegen großer Datenmengen](../../relational-databases/native-client-ole-db-blobs/setting-large-data.md)  
  
-   [Streamingunterstützung für BLOB-Ausgabeparameter](../../relational-databases/native-client-ole-db-blobs/streaming-support-for-blob-output-parameters.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)   
 [Verwenden von Datentypen mit umfangreichen Werten](../../relational-databases/native-client/features/using-large-value-types.md)  
  
  
