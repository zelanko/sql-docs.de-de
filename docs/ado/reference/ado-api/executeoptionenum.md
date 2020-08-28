---
description: ExecuteOptionEnum
title: Executeoptionumum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 2b89d582d839c1eea382d09d922c6fa0dd988725
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88973341"
---
# <a name="executeoptionenum"></a>ExecuteOptionEnum
Gibt an, wie ein Anbieter einen Befehl ausführen soll.  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|**adAsyncExecute**|0x10|Gibt an, dass der Befehl asynchron ausgeführt werden soll.<br /><br /> Dieser Wert kann nicht mit dem commandtypeenumerationswert **adCmdTableDirect**kombiniert werden. [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md)|  
|**adasyncfetch**|0x20|Gibt an, dass die verbleibenden Zeilen nach der anfänglichen Menge, die in der [CacheSize](../../../ado/reference/ado-api/cachesize-property-ado.md) -Eigenschaft angegeben wurde, asynchron abgerufen werden sollen.|  
|**adasyncfetchnonblocking**|0x40|Gibt an, dass der Haupt Thread beim Abrufen nie blockiert wird. Wenn die angeforderte Zeile nicht abgerufen wurde, wird die aktuelle Zeile automatisch an das Ende der Datei verschoben.<br /><br /> Wenn Sie ein [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) aus einem [Stream](../../../ado/reference/ado-api/stream-object-ado.md) öffnen, der ein permanent gespeichertes **Recordset**enthält, hat **adasyncfetchnonblocking** keinen Effekt. der Vorgang ist synchron und wird blockiert.<br /><br /> **adAsynchFetchNonBlocking** hat keine Auswirkung, wenn die [adCmdTableDirect](../../../ado/reference/ado-api/commandtypeenum.md) -Option zum Öffnen des **Recordsets**verwendet wird.|  
|**adExecuteNoRecords**|0x80|Gibt an, dass der Befehls Text ein Befehl oder eine gespeicherte Prozedur ist, die keine Zeilen zurückgibt (z. b. ein Befehl, der nur Daten einfügt). Wenn Zeilen abgerufen werden, werden Sie verworfen und nicht zurückgegeben.<br /><br /> **adExecuteNoRecords** kann nur als optionaler Parameter **an die** Execute-oder **Connection** -Methode übergeben werden.|  
|**adExecuteStream**|0x400|Gibt an, dass die Ergebnisse einer Befehlsausführung als Stream zurückgegeben werden sollen.<br /><br /> **adExecuteStream** kann nur als optionaler Parameter an die Execute-Methode des **Befehls** übergeben werden.|  
|**adexecuterecord**||Gibt an, dass **CommandText** ein Befehl oder eine gespeicherte Prozedur ist, der eine einzelne Zeile zurückgibt, die als **Datensatz** -Objekt zurückgegeben werden soll.|  
|**adoptionunspezifiziert**|-1|Gibt an, dass der Befehl nicht angegeben ist.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Paket: **com. ms. wfc. Data**  
  
|Konstante|  
|--------------|  
|AdoEnums.Executeoption. asyncexecute|  
|AdoEnums.Executeoption. asyncfetch|  
|AdoEnums.Executeoption. asyncfetchnonblocking|  
|AdoEnums.Executeoption. norecords|  
|AdoEnums.Executeoption. nicht angegeben|  
  
## <a name="applies-to"></a>Gilt für  

:::row:::
    :::column:::
        [Execute-Methode (ADO-Befehl)](../../../ado/reference/ado-api/execute-method-ado-command.md)  
        [Execute-Methode (ADO-Verbindung)](../../../ado/reference/ado-api/execute-method-ado-connection.md)  
    :::column-end:::
    :::column:::
        [Open-Methode (ADO-Recordset)](../../../ado/reference/ado-api/open-method-ado-recordset.md)  
        [Requery-Methode](../../../ado/reference/ado-api/requery-method.md)  
    :::column-end:::
:::row-end:::
