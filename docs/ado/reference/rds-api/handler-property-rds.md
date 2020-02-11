---
title: Handler-Eigenschaft (RDS) | Microsoft-Dokumentation
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
ms.openlocfilehash: a7423879b8263d87575d913c4863143faf3573e5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67964008"
---
# <a name="handler-property-rds"></a>Handler-Eigenschaft (RDS)
Gibt den Namen eines serverseitigen Anpassungsprogramms (Handler) an, das die Funktionalität von [RDSServer. DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)erweitert, sowie alle Parameter, die vom *Handler*verwendet werden.  
  
 **Gilt für:** [DataControl Object (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DataControl.Handler = String  
```  
  
#### <a name="parameters"></a>Parameter  
 *DataControl*  
 Eine Objekt Variable, die einen [RDS darstellt. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) -Objekt.  
  
 *String*  
 Ein **Zeichen** folgen Wert, der den Namen des Handlers und alle Parameter enthält, die alle durch Kommas getrennt sind `"handlerName,parm1,parm2,...,parm`(z. b. *N*`"`).  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Eigenschaft unterstützt [Anpassungen](../../../ado/guide/remote-data-service/datafactory-customization.md), eine Funktion, die das Festlegen der Eigenschaft " [Cursor Location](../../../ado/reference/ado-api/cursorlocation-property-ado.md) " auf " **adUseClient**" erfordert.  
  
 Der Name des Handlers und der zugehörigen Parameter werden ggf. durch Kommas (",") getrennt. Ein unvorhersehbares Verhalten ergibt sich, wenn ein Semikolon (";") an einer beliebigen Stelle innerhalb der *Zeichen*Folge Sie können einen eigenen Handler schreiben, sofern er die **idatafactoriyhandler** -Schnittstelle unterstützt.  
  
 Der Name des Standard Handlers ist **msdfmap. Der Handler**, und sein Standardparameter ist eine Anpassungs Datei namens **msdfmap. INI**. Verwenden Sie diese Eigenschaft, um alternative Anpassungs Dateien aufzurufen, die vom Server Administrator erstellt wurden.  
  
 Die Alternative zum Festlegen der **Handlereigenschaft** ist das Angeben eines Handlers und von Parametern in der [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) -Eigenschaft. Das heißt, "**Handler =**_HandlerName, Parameter1, Parameter2,...;_".  
  
## <a name="applies-to"></a>Gilt für  
 [DataControl-Objekt (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für Handlereigenschaft (VB)](../../../ado/reference/rds-api/handler-property-example-vb.md)   
 [DataFactory-Anpassung](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [DataFactory-Objekt (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)


