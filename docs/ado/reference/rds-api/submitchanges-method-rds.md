---
title: SubmitChanges-Methode (RDS) | Microsoft-Dokumentation
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- SubmitChanges method [ADO]
ms.assetid: 250062a4-13c4-4bed-807d-8b9ad81536d4
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 783ad55a2355759f7625d536272f5243cd1c61c4
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67963281"
---
# <a name="submitchanges-method-rds"></a>SubmitChanges-Methode (RDS)
Übermittelt ausstehende Änderungen des lokal zwischengespeicherten und aktualisierbaren [Recordsets](../../../ado/reference/ado-api/recordset-object-ado.md) an die Datenquelle, die in der [Connect](../../../ado/reference/rds-api/connect-property-rds.md) -Eigenschaft oder der [URL](../../../ado/reference/rds-api/url-property-rds.md) -Eigenschaft angegeben ist.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DataControl.SubmitChanges DataFactory.SubmitChanges Connection, Recordset  
```  
  
#### <a name="parameters"></a>Parameter  
 *DataControl*  
 Eine Objekt Variable, die einen [RDS darstellt. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) -Objekt.  
  
 *DataFactory*  
 Eine Objekt Variable, die ein [RDSServer. DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) -Objekt darstellt.  
  
 *Connection*  
 Ein **Zeichen** folgen Wert, der die mit dem RDS erstellte Verbindung darstellt **. ** [Connect](../../../ado/reference/rds-api/connect-property-rds.md) -Eigenschaft des DataControl-Objekts.  
  
 *Recordset*  
 Eine Objekt Variable, die ein **Recordset** -Objekt darstellt.  
  
## <a name="remarks"></a>Bemerkungen  
 Die Eigenschaften [Connect](../../../ado/reference/rds-api/connect-property-rds.md), [Server](../../../ado/reference/rds-api/server-property-rds.md)und [SQL](../../../ado/reference/rds-api/sql-property.md) müssen festgelegt werden, bevor Sie die **SubmitChanges** -Methode mit dem **RDS verwenden können. DataControl** -Objekt.  
  
 Wenn Sie die [CancelUpdate](../../../ado/reference/rds-api/cancelupdate-method-rds.md) -Methode aufrufen, nachdem Sie **SubmitChanges** für dasselbe **Recordset** -Objekt aufgerufen haben, schlägt der **CancelUpdate** -Aufruf fehl, da für die Änderungen bereits ein Commit ausgeführt wurde.  
  
 Nur die geänderten Datensätze werden zur Änderung gesendet, und entweder sind alle Änderungen erfolgreich, oder alle Änderungen schlagen fehl.  
  
 **SubmitChanges** können nur mit dem standardmäßigen **RDSServer. DataFactory** -Objekt verwendet werden. Benutzerdefinierte Geschäftsobjekte können diese Methode nicht verwenden.  
  
 Wenn die **URL** -Eigenschaft festgelegt wurde, übermitteln **SubmitChanges** Änderungen an den von der URL angegebenen Speicherort.  
  
## <a name="applies-to"></a>Gilt für  
  
|||  
|-|-|  
|[DataControl-Objekt (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)|[DataFactory-Objekt (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [SubmitChanges-Methode (Beispiel) (VBScript)](../../../ado/reference/rds-api/submitchanges-method-example-vbscript.md)   
 [Adressbuch-Befehls Schaltflächen](../../../ado/guide/remote-data-service/address-book-command-buttons.md)   
 [CancelUpdate-Methode (RDS)](../../../ado/reference/rds-api/cancelupdate-method-rds.md)   
 [Refresh-Methode (RDS)](../../../ado/reference/rds-api/refresh-method-rds.md)



