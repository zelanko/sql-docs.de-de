---
description: Recordset, SourceRecordset-Eigenschaft (RDS)
title: Recordset, SourceRecordset-Eigenschaften (RDS) | Microsoft-Dokumentation
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Recordset property [ADO]
ms.assetid: a29e3fb9-306d-497a-9a59-1856a914e5e9
author: rothja
ms.author: jroth
ms.openlocfilehash: cdf8a894341343fee7576daed45c75a46857b909
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/05/2020
ms.locfileid: "91724297"
---
# <a name="recordset-sourcerecordset-properties-rds"></a>Recordset, SourceRecordset-Eigenschaft (RDS)
Gibt das **Recordsetobjekt** an, das von einem benutzerdefinierten Geschäftsobjekt zurückgegeben wurde.  
  
 **Gilt für:** [DataControl Object (RDS)](./datacontrol-object-rds.md)  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](/dotnet/framework/wcf/)migriert werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DataControl.SourceRecordset = Recordset  
Recordset = DataControl.Recordset   
```  
  
#### <a name="parameters"></a>Parameter  
 *DataControl*  
 Eine Objekt Variable, die einen [RDS darstellt. DataControl](./datacontrol-object-rds.md) -Objekt.  
  
 *Recordset*  
 Eine Objekt Variable, die ein **Recordset** -Objekt darstellt.  
  
## <a name="remarks"></a>Bemerkungen  
 Sie können die **SourceRecordset** -Eigenschaft auf ein [Recordset](../ado-api/recordset-object-ado.md) festlegen, das von einem benutzerdefinierten Geschäftsobjekt zurückgegeben wurde.  
  
 Diese Eigenschaften ermöglichen es einer Anwendung, den Bindungsprozess mithilfe eines benutzerdefinierten Prozesses zu verarbeiten. Sie erhalten ein Rowset, das in einem **Recordset** umschließt ist, sodass Sie direkt mit dem **Recordset**interagieren können, indem Sie Aktionen wie das Festlegen von Eigenschaften oder das Durchlaufen des **Recordsets**ausführen.  
  
 Sie können die **SourceRecordset** -Eigenschaft festlegen oder die **Recordset** -Eigenschaft zur Laufzeit im Skriptcode lesen.  
  
 **SourceRecordset** ist eine schreibgeschützte Eigenschaft, im Gegensatz zur **Recordset** -Eigenschaft, bei der es sich um eine schreibgeschützte Eigenschaft handelt.  
  
## <a name="applies-to"></a>Gilt für  
 [DataControl-Objekt (RDS)](./datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für Recordset und SourceRecordset-Eigenschaften (VBScript)](./recordset-and-sourcerecordset-properties-example-vbscript.md)   
 [Methode "samaterecordset" (RDS)](./createrecordset-method-rds.md)   
 [Query-Methode (RDS)](./query-method-rds.md)