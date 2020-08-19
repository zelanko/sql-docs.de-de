---
description: Recordset, SourceRecordset-Eigenschaft (RDS)
title: Recordset, SourceRecordset-Eigenschaften (RDS) | Microsoft-Dokumentation
ms.technology: connectivity
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
ms.openlocfilehash: 8d64488fa60b6cc6bcdd7c45124a7dcedb60d4c2
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88438732"
---
# <a name="recordset-sourcerecordset-properties-rds"></a>Recordset, SourceRecordset-Eigenschaft (RDS)
Gibt das **Recordsetobjekt** an, das von einem benutzerdefinierten Geschäftsobjekt zurückgegeben wurde.  
  
 **Gilt für:** [DataControl Object (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DataControl.SourceRecordset = Recordset  
Recordset = DataControl.Recordset   
```  
  
#### <a name="parameters"></a>Parameter  
 *DataControl*  
 Eine Objekt Variable, die einen [RDS darstellt. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) -Objekt.  
  
 *Recordset*  
 Eine Objekt Variable, die ein **Recordset** -Objekt darstellt.  
  
## <a name="remarks"></a>Bemerkungen  
 Sie können die **SourceRecordset** -Eigenschaft auf ein [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) festlegen, das von einem benutzerdefinierten Geschäftsobjekt zurückgegeben wurde.  
  
 Diese Eigenschaften ermöglichen es einer Anwendung, den Bindungsprozess mithilfe eines benutzerdefinierten Prozesses zu verarbeiten. Sie erhalten ein Rowset, das in einem **Recordset** umschließt ist, sodass Sie direkt mit dem **Recordset**interagieren können, indem Sie Aktionen wie das Festlegen von Eigenschaften oder das Durchlaufen des **Recordsets**ausführen.  
  
 Sie können die **SourceRecordset** -Eigenschaft festlegen oder die **Recordset** -Eigenschaft zur Laufzeit im Skriptcode lesen.  
  
 **SourceRecordset** ist eine schreibgeschützte Eigenschaft, im Gegensatz zur **Recordset** -Eigenschaft, bei der es sich um eine schreibgeschützte Eigenschaft handelt.  
  
## <a name="applies-to"></a>Gilt für  
 [DataControl-Objekt (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für Recordset und SourceRecordset-Eigenschaften (VBScript)](../../../ado/reference/rds-api/recordset-and-sourcerecordset-properties-example-vbscript.md)   
 [Methode "samaterecordset" (RDS)](../../../ado/reference/rds-api/createrecordset-method-rds.md)   
 [Query-Methode (RDS)](../../../ado/reference/rds-api/query-method-rds.md)


