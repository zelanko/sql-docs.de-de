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
manager: craigg
ms.openlocfilehash: a0655a76463f7a0a1507fa2767eade3cb37c48a8
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "51602620"
---
# <a name="submitchanges-method-rds"></a>SubmitChanges-Methode (RDS)
Ausstehende Änderungen lokal zwischengespeichert und aktualisierbare übermittelt [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) mit der Datenquelle angegeben, der [Connect](../../../ado/reference/rds-api/connect-property-rds.md) Eigenschaft oder die [URL](../../../ado/reference/rds-api/url-property-rds.md) Eigenschaft.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DataControl.SubmitChanges DataFactory.SubmitChanges Connection, Recordset  
```  
  
#### <a name="parameters"></a>Parameter  
 *DataControl*  
 Eine Objektvariable, steht ein [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) Objekt.  
  
 *DataFactory*  
 Eine Objektvariable, steht ein [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) Objekt.  
  
 *Verbindung*  
 Ein **Zeichenfolge** -Wert, der die Verbindung mit erstellt die **RDS. DataControl** des Objekts [Connect](../../../ado/reference/rds-api/connect-property-rds.md) Eigenschaft.  
  
 *Recordset*  
 Eine Objektvariable, steht ein **Recordset** Objekt.  
  
## <a name="remarks"></a>Hinweise  
 Die [verbinden](../../../ado/reference/rds-api/connect-property-rds.md), [Server](../../../ado/reference/rds-api/server-property-rds.md), und [SQL](../../../ado/reference/rds-api/sql-property.md) Eigenschaften müssen festgelegt werden, vor der Verwendung der **SubmitChanges** -Methode mit der  **RDS. DataControl** Objekt.  
  
 Aufrufen der [CancelUpdate](../../../ado/reference/rds-api/cancelupdate-method-rds.md) -Methode auf, nachdem Sie aufgerufen haben **SubmitChanges** für den gleichen **Recordset** -Objekt, das **CancelUpdate** Aufruf schlägt fehl, da die Änderungen bereits ein Commit ausgeführt wurden.  
  
 Nur die geänderten Datensätze werden für Änderungen und alle Änderungen gesendet werden, erfolgreich ausgeführt werden, oder alle Änderungen zusammen fehlschlagen.  
  
 Sie können **SubmitChanges** nur mit der standardmäßigen **RDSServer.DataFactory** Objekt. Benutzerdefinierte Geschäftsobjekte können nicht auf diese Methode verwenden.  
  
 Wenn die **URL** Eigenschaft festgelegt wurde, **SubmitChanges** übergeben von Änderungen an den Speicherort, der durch die URL angegeben werden.  
  
## <a name="applies-to"></a>Gilt für  
  
|||  
|-|-|  
|[DataControl-Objekt (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)|[DataFactory-Objekt (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [SubmitChanges-Methode – Beispiel (VBScript)](../../../ado/reference/rds-api/submitchanges-method-example-vbscript.md)   
 [Behandeln von Book-Befehlsschaltflächen](../../../ado/guide/remote-data-service/address-book-command-buttons.md)   
 [CancelUpdate-Methode (RDS)](../../../ado/reference/rds-api/cancelupdate-method-rds.md)   
 [Refresh-Methode (RDS)](../../../ado/reference/rds-api/refresh-method-rds.md)



