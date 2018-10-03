---
title: ExecuteOptionEnum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ExecuteOptionEnum
helpviewer_keywords:
- ExecuteOptionEnum enumeration [ADO]
ms.assetid: 68bfa83a-5df4-4bef-8736-0f88ae8c29ea
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7512f456d1423caf6318903119c2ad55c1938dec
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47719118"
---
# <a name="executeoptionenum"></a>ExecuteOptionEnum
Gibt an, wie ein Anbieter einen Befehl ausführen soll.  
  
|Konstante|value|Description|  
|--------------|-----------|-----------------|  
|**adAsyncExecute**|0x10|Gibt an, dass der Befehl asynchron ausgeführt werden soll.<br /><br /> Dieser Wert kann nicht kombiniert werden, mit der [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md) Wert **AdCmdTableDirect**.|  
|**adAsyncFetch**|0x20|Gibt an, dass die verbleibenden Zeilen nach der ersten Menge in angegeben die [CacheSize](../../../ado/reference/ado-api/cachesize-property-ado.md) Eigenschaft asynchron abgerufen werden soll.|  
|**adAsyncFetchNonBlocking**|0x40|Gibt an, dass der Hauptthread nie beim Abrufen von blockiert. Wenn nicht die angeforderte Zeile abgerufen wurde, wird die aktuelle Zeile automatisch an das Ende der Datei verschoben.<br /><br /> Beim Öffnen einer [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) aus einem [Stream](../../../ado/reference/ado-api/stream-object-ado.md) mit einem dauerhaft gespeicherten **Recordset**, **AdAsyncFetchNonBlocking** keine angewendet wird. der Vorgang wird synchron und blockiert werden.<br /><br /> **AdAsynchFetchNonBlocking** hat keine Auswirkungen, wenn die [AdCmdTableDirect](../../../ado/reference/ado-api/commandtypeenum.md) Option dient zum Öffnen der **Recordset**.|  
|**adExecuteNoRecords**|0x80|Gibt an, dass der Befehlstext ist, einen Befehl oder gespeicherte Prozedur, der keinen Zeilen (z. B. ein Befehl, die nur Daten einfügt) zurückgibt. Wenn keine Zeilen abgerufen werden, werden sie verworfen und nicht zurückgegeben.<br /><br /> **AdExecuteNoRecords** kann nur als ein optionaler Parameter zum übergeben werden die **Befehl** oder **führen Sie die Verbindung** Methode.|  
|**adExecuteStream**|0x400|Gibt an, dass die Ergebnisse der Ausführung des Befehls als einen Datenstrom zurückgegeben werden sollen.<br /><br /> **AdExecuteStream** kann nur als ein optionaler Parameter zum übergeben werden die **Befehlsausführung** Methode.|  
|**adExecuteRecord**||Gibt an, dass die **CommandText** ist ein Befehl oder gespeicherte Prozedur, die eine einzelne Zeile zurückgibt, die als zurückgegeben werden sollen eine **Datensatz** Objekt.|  
|**adOptionUnspecified**|-1|Gibt an, dass der Befehl nicht angegeben ist.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-äquivalent  
 Paket: **com.ms.wfc.data**  
  
|Konstante|  
|--------------|  
|AdoEnums.ExecuteOption.ASYNCEXECUTE|  
|AdoEnums.ExecuteOption.ASYNCFETCH|  
|AdoEnums.ExecuteOption.ASYNCFETCHNONBLOCKING|  
|AdoEnums.ExecuteOption.NORECORDS|  
|AdoEnums.ExecuteOption.UNSPECIFIED|  
  
## <a name="applies-to"></a>Gilt für  
  
|||  
|-|-|  
|[Execute-Methode (ADO Command)](../../../ado/reference/ado-api/execute-method-ado-command.md)|[Execute-Methode (ADO Connection)](../../../ado/reference/ado-api/execute-method-ado-connection.md)|  
|[Open-Methode (ADO Recordset)](../../../ado/reference/ado-api/open-method-ado-recordset.md)|[Requery-Methode](../../../ado/reference/ado-api/requery-method.md)|
