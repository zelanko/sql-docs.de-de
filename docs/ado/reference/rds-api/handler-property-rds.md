---
title: Handlereigenschaft (RDS) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Handler property [ADO]
ms.assetid: fdc34362-6d47-4727-b171-8d033159408e
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 6b538767f62a3d80b9cf2cd9b558f14c5de91549
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66712470"
---
# <a name="handler-property-rds"></a>Handler-Eigenschaft (RDS)
Gibt den Namen eines Programms für serverseitige Anpassung (Handler), die die Funktionalität von erweitert die [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md), und alle Parameter ein, die die *Handler*.  
  
 **Gilt für:** [DataControl-Objekt (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DataControl.Handler = String  
```  
  
#### <a name="parameters"></a>Parameter  
 *DataControl*  
 Eine Objektvariable, steht ein [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) Objekt.  
  
 *String*  
 Ein **Zeichenfolge** -Wert, der den Namen der der Handler und Parameter enthält, die alle durch Kommas getrennte (z. B. `"handlerName,parm1,parm2,...,parm` *N*`"`).  
  
## <a name="remarks"></a>Hinweise  
 Diese Eigenschaft unterstützt [Anpassung](../../../ado/guide/remote-data-service/datafactory-customization.md), eine Funktion, die Einstellung muss der [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) Eigenschaft **AdUseClient**.  
  
 Der Name der der Handler und den zugehörigen Parametern ggf. durch Kommas getrennt (","). Zu einem unvorhersehbaren Verhalten führt, wenn ein Semikolon (";") wird an einer beliebigen Stelle innerhalb *Zeichenfolge*. Sie können einen eigenen Handler schreiben, bereitgestellte unterstützt die **IDataFactoryHandler** Schnittstelle.  
  
 Der Name der Standard-Handler ist **MSDFMAP. Handler**, und der Standardparameter ist eine Anpassungsdatei, die mit dem Namen **MSDFMAP. INI**. Verwenden Sie diese Eigenschaft, um alternative, durch den Server-Administrator erstellt Setupanpassungsdateien aufzurufen.  
  
 Die Alternative zur Einstellung der **Handler** Eigenschaft ist, geben Sie einen Handler und die Parameter in der ["ConnectionString"](../../../ado/reference/ado-api/connectionstring-property-ado.md) Eigenschafts-, also "**Handler =** _HandlerName, parameter1, parameter2,_ ".  
  
## <a name="applies-to"></a>Gilt für  
 [DataControl-Objekt (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Handler-Eigenschaft – Beispiel (VB)](../../../ado/reference/rds-api/handler-property-example-vb.md)   
 [DataFactory-Anpassung](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [DataFactory-Objekt (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)


