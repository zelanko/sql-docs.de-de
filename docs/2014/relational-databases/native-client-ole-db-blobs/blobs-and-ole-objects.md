---
title: BLOBs und OLE-Objekte | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
manager: craigg
ms.openlocfilehash: e459682da63bac8359fa8310233c234e456f4e5b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63195217"
---
# <a name="blobs-and-ole-objects"></a>BLOBs und OLE-Objekte
  Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter stellt die **ISequentialStream** -Schnittstelle zur Unterstützung der Consumerzugriff auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Ntext**, **Text**, **Image**, **varchar(max)**, **nvarchar(max)**, **'varbinary(max)'**, und die Xml-Datentypen als binary large Objects (BLOBs ). Die Methode **Read** für **ISequentialStream** ermöglicht dem Consumer, große Datenmengen in überschaubaren Abschnitten abzurufen.  
  
 Ein Beispiel für diese Funktion ist, finden Sie unter [festlegen großer Datenmengen &#40;OLE DB&#41;](../native-client-ole-db-how-to/set-large-data-ole-db.md).  
  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter können ein vom Consumer implementierte **IStorage** Schnittstelle, wenn der Consumer den Schnittstellenzeiger in einem Accessor enthält, die für datenänderungen gebundenen.  
  
 Bei Datentypen mit umfangreichen Werten der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter überprüft Annahmen über die typgroße in **IRowset** und DDL-Schnittstellen. Spalten mit **Varchar**, **Nvarchar**, und **Varbinary** Datentypen mit max. Größe auf unlimited festgelegt werden, als ISLONG dargestellt werden, über die Schemarowsets und Schnittstellen Zurückgeben von Spaltendatentypen.  
  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter stellt die **varchar(max)**, **'varbinary(max)'** und **nvarchar(max)** Typen als DBTYPE_STR, DBTYPE_BYTES bzw. DBTYPE_ WSTR bzw.  
  
 Um mit diesen Typen zu arbeiten, hat eine Anwendung die folgenden Optionen:  
  
-   Als den betreffenden Typ binden (DBTYPE_STR, DBTYPE_BYTES, DBTYPE_WSTR). Wenn der Puffer nicht groß genug ist, werden Daten abgeschnitten, wie dies auch in früheren Versionen der Fall war (obwohl jetzt umfangreichere Werte verfügbar sind).  
  
-   Als den betreffenden Typ binden und zudem DBTYPE_BYREF angeben  
  
-   Als DBTYPE_IUNKNOWN binden und Streaming verwenden  
  
 Wenn die Bindung an DBTYPE_IUNKNOWN erfolgt, wird die Streamingfunktion ISequentialStream verwendet. Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter unterstützt Binden von Ausgabeparametern als DBTYPE_IUNKNOWN für Datentypen für hohe Werte in Szenarien nützlich, eine gespeicherte Prozedur, in denen diese Daten zurückgibt, Typen als Rückgabewerte der verfügbar gemacht werden, als DBTYPE_IUNKNOWN an den Client.  
  
## <a name="storage-object-limitations"></a>Speicherobjekteinschränkungen  
  
-   Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter kann nur ein einzelnes geöffnetes Speicherobjekt unterstützen. Wenn versucht wird, mehrere Speicherobjekte zu öffnen (um einen Verweis auf mehrere **ISequentialStream**-Schnittstellenzeiger abzurufen), wird DBSTATUS_E_CANTCREATE zurückgegeben.  
  
-   In der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter, der Standardwert der schreibgeschützten DBPROP_BLOCKINGSTORAGEOBJECTS-nur-Lese-Eigenschaft ist auf VARIANT_TRUE festgelegt. Das zeigt an, dass einige Methoden (solche, die sich nicht in den Speicherobjekten befinden) mit E_UNEXPECTED fehlschlagen, wenn ein Speicherobjekt aktiv ist.  
  
-   Die Länge der Daten eines von einem Consumer implementierten Speicherobjekts muss bekannt gemacht werden die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter, wenn die, die das Speicherobjekt verweisende zeilenaccessor erstellt wird. Der Consumer muss einen Längenindikator in der zur Accessorerstellung verwendeten DBBINDING-Struktur binden.  
  
-   Wenn eine Zeile mehr als einen großen Datenwert enthält und DBPROP_ACCESSORDER nicht DBPROPVAL_AO_RANDOM, muss der Consumer entweder ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter durch Cursor unterstütztes Rowset Zeilendaten abzurufen oder alle große Daten verarbeiten, bevor Werte Abrufen weiterer Zeilenwerte. Wenn DBPROP_ACCESSORDER auf DBPROPVAL_AO_RANDOM, lautet die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter alle Xml-Datentypen als binary large Objects (BLOBs) zwischenspeichert, damit sie in beliebiger Reihenfolge zugegriffen werden kann.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Abrufen großer Datenmengen](getting-large-data.md)  
  
-   [Festlegen großer Datenmengen](setting-large-data.md)  
  
-   [Streamingunterstützung für BLOB-Ausgabeparameter](streaming-support-for-blob-output-parameters.md)  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server Native Client &#40;OLE-DB&#41;](../native-client/ole-db/sql-server-native-client-ole-db.md)   
 [Verwenden von Datentypen mit umfangreichen Werten](../native-client/features/using-large-value-types.md)  
  
  
