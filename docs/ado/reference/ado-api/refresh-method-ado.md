---
title: Refresh-Methode (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Collection::Refresh
- Parameters::Refresh
- Properties::Refresh
helpviewer_keywords:
- Refresh method [ADO]
ms.assetid: 089b7ca7-684f-4259-8032-5bd1ecc54426
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 0fee14a397104f8320fc01ce29f8364384151922
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66711713"
---
# <a name="refresh-method-ado"></a>Refresh-Methode (ADO)
Aktualisiert die Objekte in eine Sammlung von verfügbaren Objekte entsprechend, und klicken Sie auf spezifische an den Anbieter an.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
collection.Refresh  
```  
  
## <a name="remarks"></a>Hinweise  
 Die **aktualisieren** Methode führt verschiedene Aufgaben abhängig von der Sammlung, von dem Sie ihn aufrufen.  
  
### <a name="parameters"></a>Parameter  
 Mit der **aktualisieren** Methode für die [Parameter](../../../ado/reference/ado-api/parameters-collection-ado.md) Auflistung von einer [Befehl](../../../ado/reference/ado-api/command-object-ado.md) Objekt ruft Anbieters Parameterinformationen für die gespeicherte Prozedur oder parametrisierte Abfrage angegeben der **Befehl** Objekt. Die Auflistung werden leer, um Anbieter, die keine Aufrufe von gespeicherten Prozeduren oder parametrisierte Abfragen unterstützen.  
  
 Legen Sie die [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) Eigenschaft der **Befehl** Objekt auf eine gültige [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md) -Objekt, die [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) Eigenschaft auf einen gültigen Befehl ein und die [CommandType](../../../ado/reference/ado-api/commandtype-property-ado.md) Eigenschaft **AdCmdStoredProc** vor dem Aufruf der **aktualisieren** Methode.  
  
 Wenn Sie Zugriff auf die **Parameter** Auflistung vor dem Aufruf der **aktualisieren** ADO-Methode wird automatisch die Methode aufrufen und füllen Sie die Sammlung für Sie.  
  
> [!NOTE]
>  Bei Verwendung der **aktualisieren** Methode zum Abrufen von Informationen zu den Parametern aus dem Anbieter, und es gibt eine oder mehrere Daten variabler Länge-Typ zurück, [Parameter](../../../ado/reference/ado-api/parameter-object.md) Objekten, die ADO möglicherweise arbeitsspeicherzuweisung für die Parameter basierend Klicken Sie auf ihre maximal möglichen Größe, die während der Ausführung einen Fehler verursachen werden. Sollten Sie explizit festlegen der [Größe](../../../ado/reference/ado-api/size-property-ado-parameter.md) -Eigenschaft für diese Parameter vor dem Aufruf der [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md) Methode, um Fehler zu vermeiden.  
  
### <a name="fields"></a>Felder  
 Mithilfe der **aktualisieren** Methode für die [Felder](../../../ado/reference/ado-api/fields-collection-ado.md) Auflistung wirkt sich nicht sichtbar. Um Änderungen aus der zugrunde liegenden Datenbankstruktur abzurufen, müssen Sie verwenden entweder die [Requery](../../../ado/reference/ado-api/requery-method.md) Methode oder, wenn Sie die [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekt unterstützt keine Lesezeichen die [MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)Methode.  
  
### <a name="properties"></a>Eigenschaften  
 Mithilfe der **aktualisieren** Methode für eine **Eigenschaften** Auflistung einiger Objekte füllt die Auflistung mit den dynamischen Eigenschaften, die der Anbieter verfügbar macht. Diese Eigenschaften stellen Informationen über spezifische Funktionen bereit, an den Anbieter, über die integrierten Eigenschaften ADO unterstützt.  
  
## <a name="applies-to"></a>Gilt für  
  
||||  
|-|-|-|  
|[Axes-Auflistung](../../../ado/reference/ado-md-api/axes-collection-ado-md.md)|[Columns-Auflistung](../../../ado/reference/adox-api/columns-collection-adox.md)|[CubeDefs-Auflistung](../../../ado/reference/ado-md-api/cubedefs-collection-ado-md.md)|  
|[Auflistung von Dimensionen](../../../ado/reference/ado-md-api/dimensions-collection-ado-md.md)|[Errors-Collection](../../../ado/reference/ado-api/errors-collection-ado.md)|[Fields-Sammlung](../../../ado/reference/ado-api/fields-collection-ado.md)|  
|[Groups-Sammlung](../../../ado/reference/adox-api/groups-collection-adox.md)|[Hierarchies-Auflistung](../../../ado/reference/ado-md-api/hierarchies-collection-ado-md.md)|[Auflistung von Indizes](../../../ado/reference/adox-api/indexes-collection-adox.md)|  
|[Keys-Auflistung](../../../ado/reference/adox-api/keys-collection-adox.md)|[Levels-Auflistung](../../../ado/reference/ado-md-api/levels-collection-ado-md.md)|[Members-Auflistung](../../../ado/reference/ado-md-api/members-collection-ado-md.md)|  
|[Parameters-Auflistung](../../../ado/reference/ado-api/parameters-collection-ado.md)|[Positionen-Auflistung](../../../ado/reference/ado-md-api/positions-collection-ado-md.md)|[Procedures-Auflistung](../../../ado/reference/adox-api/procedures-collection-adox.md)|  
|[Properties-Auflistung](../../../ado/reference/ado-api/properties-collection-ado.md)|[Tables-Auflistung](../../../ado/reference/adox-api/tables-collection-adox.md)|[Users-Sammlung](../../../ado/reference/adox-api/users-collection-adox.md)|  
|[Views-Auflistung](../../../ado/reference/adox-api/views-collection-adox.md)|||  
  
## <a name="see-also"></a>Siehe auch  
 [Refresh – Methodenbeispiel (VB)](../../../ado/reference/ado-api/refresh-method-example-vb.md)   
 [Refresh – Methodenbeispiel (VC++)](../../../ado/reference/ado-api/refresh-method-example-vc.md)   
 [Count-Eigenschaft (ADO)](../../../ado/reference/ado-api/count-property-ado.md)   
 [Refresh-Methode (RDS)](../../../ado/reference/rds-api/refresh-method-rds.md)
