---
title: BLOB-und OLE-Objekte | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b4e284d2086684af232c17b59675b834b26f497b
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73790638"
---
# <a name="blobs-and-ole-objects"></a>BLOBs und OLE-Objekte
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter macht die **ISequentialStream** -Schnittstelle verfügbar, um den Consumerzugriff auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **ntext**, **Text**, **Image**, **varchar (max)** , **nvarchar (max)** , **varbinary (max) zu unterstützen.** und XML-Datentypen als Binary Large Objects (BLOB). Die Methode **Read** für **ISequentialStream** ermöglicht dem Consumer, große Datenmengen in überschaubaren Abschnitten abzurufen.  
  
 Ein Beispiel für diese Funktion finden Sie unter [Festlegen von großen &#40;Daten&#41;OLE DB](../../relational-databases/native-client-ole-db-how-to/set-large-data-ole-db.md).  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter kann eine vom Consumer implementierte **IStorage** -Schnittstelle verwenden, wenn der Consumer den Schnittstellen Zeiger in einem Accessor bereitstellt, der für die Datenänderung gebunden ist.  
  
 Bei Datentypen mit umfangreichen Werten überprüft der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter in **IRowset** -und DDL-Schnittstellen auf typgrößen Annahmen. Spalten mit den Datentypen **varchar**, **nvarchar**und **varbinary** , deren maximale Größe auf Unlimited festgelegt ist, werden durch die Schemarowsets und Schnittstellen, die Spaltendatentypen zurückgeben, als ISLONG dargestellt.  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter macht die Typen **varchar (max)** , **varbinary (max)** und **nvarchar (max)** als DBTYPE_STR, DBTYPE_BYTES bzw. DBTYPE_WSTR verfügbar.  
  
 Um mit diesen Typen zu arbeiten, hat eine Anwendung die folgenden Optionen:  
  
-   Als den betreffenden Typ binden (DBTYPE_STR, DBTYPE_BYTES, DBTYPE_WSTR). Wenn der Puffer nicht groß genug ist, werden Daten abgeschnitten, wie dies auch in früheren Versionen der Fall war (obwohl jetzt umfangreichere Werte verfügbar sind).  
  
-   Als den betreffenden Typ binden und zudem DBTYPE_BYREF angeben  
  
-   Als DBTYPE_IUNKNOWN binden und Streaming verwenden  
  
 Wenn die Bindung an DBTYPE_IUNKNOWN erfolgt, wird die Streamingfunktion ISequentialStream verwendet. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter unterstützt das Binden von Ausgabeparametern als DBTYPE_IUNKNOWN für Datentypen mit umfangreichen Werten, um Szenarios zu vereinfachen, in denen eine gespeicherte Prozedur diese Datentypen als Rückgabewerte zurückgibt, die als DBTYPE_IUNKNOWN für den Client verfügbar gemacht werden.  
  
## <a name="storage-object-limitations"></a>Speicherobjekteinschränkungen  
  
-   Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter kann nur ein einzelnes geöffnetes Speicher Objekt unterstützen. Wenn versucht wird, mehrere Speicherobjekte zu öffnen (um einen Verweis auf mehrere **ISequentialStream**-Schnittstellenzeiger abzurufen), wird DBSTATUS_E_CANTCREATE zurückgegeben.  
  
-   Im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter ist der Standardwert der Eigenschaft DBPROP_BLOCKINGSTORAGEOBJECTS schreibgeschützt VARIANT_TRUE. Das zeigt an, dass einige Methoden (solche, die sich nicht in den Speicherobjekten befinden) mit E_UNEXPECTED fehlschlagen, wenn ein Speicherobjekt aktiv ist.  
  
-   Die Länge der Daten, die von einem vom Consumer implementierten Speicher Objekt vorgelegt werden, muss dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter bekannt gemacht werden, wenn der Zeilen Accessor erstellt wird, der auf das Speicher Objekt verweist. Der Consumer muss einen Längenindikator in der zur Accessorerstellung verwendeten DBBINDING-Struktur binden.  
  
-   Wenn eine Zeile mehr als einen einzelnen großen Datenwert enthält und DBPROP_ACCESSORDER nicht DBPROPVAL_AO_RANDOM ist, muss der Consumer entweder ein vom Cursor unterstütztes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB Anbieter-Rowset verwenden, um Zeilendaten abzurufen oder alle großen Datenwerte zu verarbeiten, bevor andere Zeilen Werte abgerufen werden. Wenn DBPROP_ACCESSORDER DBPROPVAL_AO_RANDOM ist, speichert der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter alle XML-Datentypen als Binary Large Objects (BLOB) zwischen, sodass in beliebiger Reihenfolge auf ihn zugegriffen werden kann.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Abrufen großer Datenmengen](../../relational-databases/native-client-ole-db-blobs/getting-large-data.md)  
  
-   [Festlegen großer Datenmengen](../../relational-databases/native-client-ole-db-blobs/setting-large-data.md)  
  
-   [Streamingunterstützung für BLOB-Ausgabeparameter](../../relational-databases/native-client-ole-db-blobs/streaming-support-for-blob-output-parameters.md)  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server Native Client &#40;OLE DB&#41; ](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)   
 [Verwenden von Datentypen mit umfangreichen Werten](../../relational-databases/native-client/features/using-large-value-types.md)  
  
  
