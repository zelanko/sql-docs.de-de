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
ms.openlocfilehash: a676bf5eb3d8d98f1b2eb9367aa8ad56f0da209d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67931254"
---
# <a name="refresh-method-ado"></a>Refresh-Methode (ADO)
Aktualisiert die Objekte in einer Auflistung, um die Objekte widerzuspiegeln, die von und für den Anbieter verfügbar sind.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
collection.Refresh  
```  
  
## <a name="remarks"></a>Bemerkungen  
 Die **Aktualisierungs** Methode führt verschiedene Aufgaben aus, abhängig von der Sammlung, von der Sie aufgerufen wird.  
  
### <a name="parameters"></a>Parameter  
 Wenn Sie die **Refresh** -Methode für die [Parameters](../../../ado/reference/ado-api/parameters-collection-ado.md) -Auflistung eines [Command](../../../ado/reference/ado-api/command-object-ado.md) -Objekts verwenden, werden Anbieter seitige Parameterinformationen für die gespeicherte Prozedur oder parametrisierte Abfrage abgerufen, die im **Command** -Objekt angegeben sind. Die Auflistung ist leer für Anbieter, die keine Aufrufe gespeicherter Prozeduren oder parametrisierte Abfragen unterstützen.  
  
 Sie sollten die [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) -Eigenschaft des **Befehls** Objekts auf ein gültiges [Verbindungs](../../../ado/reference/ado-api/connection-object-ado.md) Objekt, die [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) -Eigenschaft auf einen gültigen Befehl und die [CommandType](../../../ado/reference/ado-api/commandtype-property-ado.md) -Eigenschaft auf **adCmdStoredProc** festlegen, bevor Sie die **Refresh** -Methode aufrufen.  
  
 Wenn Sie auf die **Parameter** Auflistung zugreifen, bevor Sie die **Refresh** -Methode aufrufen, ruft ADO automatisch die-Methode auf und füllt die-Auflistung für Sie auf.  
  
> [!NOTE]
>  Wenn Sie die **Refresh** -Methode verwenden, um Parameterinformationen vom Anbieter abzurufen, und ein oder mehrere Datentyp [Parameter](../../../ado/reference/ado-api/parameter-object.md) Objekte variabler Länge zurückgibt, kann ADO Arbeitsspeicher für die Parameter basierend auf Ihrer maximalen potenziellen Größe zuweisen, was zu einem Fehler während der Ausführung führt. Sie sollten die [size](../../../ado/reference/ado-api/size-property-ado-parameter.md) -Eigenschaft für diese Parameter explizit festlegen, bevor Sie die [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md) -Methode aufrufen, um Fehler zu verhindern.  
  
### <a name="fields"></a>Felder  
 Die Verwendung der **Refresh** -Methode für die [Fields](../../../ado/reference/ado-api/fields-collection-ado.md) -Auflistung hat keinen sichtbaren Effekt. Zum Abrufen von Änderungen aus der zugrunde liegenden Datenbankstruktur müssen Sie entweder die [Requery](../../../ado/reference/ado-api/requery-method.md) -Methode oder, wenn das [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekt keine Lesezeichen unterstützt, die Methode " [muvefirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md) " verwenden.  
  
### <a name="properties"></a>Eigenschaften  
 Die Verwendung der **Refresh** -Methode für eine **Properties** -Auflistung einiger Objekte füllt die Auflistung mit den dynamischen Eigenschaften auf, die der Anbieter verfügbar macht. Diese Eigenschaften enthalten Informationen über die für den anbieterspezifischen Funktionen, die über die von ADO unterstützten integrierten Eigenschaften hinausgehen.  
  
## <a name="applies-to"></a>Gilt für  
  
||||  
|-|-|-|  
|[Achsen Sammlung](../../../ado/reference/ado-md-api/axes-collection-ado-md.md)|[Columns-Sammlung](../../../ado/reference/adox-api/columns-collection-adox.md)|[CubeDefs-Sammlung](../../../ado/reference/ado-md-api/cubedefs-collection-ado-md.md)|  
|[Dimensions Auflistung](../../../ado/reference/ado-md-api/dimensions-collection-ado-md.md)|[Fehlersammlung](../../../ado/reference/ado-api/errors-collection-ado.md)|[Fields-Auflistung](../../../ado/reference/ado-api/fields-collection-ado.md)|  
|[Groups-Sammlung](../../../ado/reference/adox-api/groups-collection-adox.md)|[Hierarchien-Auflistung](../../../ado/reference/ado-md-api/hierarchies-collection-ado-md.md)|[Index Sammlung](../../../ado/reference/adox-api/indexes-collection-adox.md)|  
|[Schlüssel Sammlung](../../../ado/reference/adox-api/keys-collection-adox.md)|[Levels-Auflistung](../../../ado/reference/ado-md-api/levels-collection-ado-md.md)|[Members-Auflistung](../../../ado/reference/ado-md-api/members-collection-ado-md.md)|  
|[Parameters-Auflistung](../../../ado/reference/ado-api/parameters-collection-ado.md)|[Positions Auflistung](../../../ado/reference/ado-md-api/positions-collection-ado-md.md)|[Prozeduren](../../../ado/reference/adox-api/procedures-collection-adox.md)|  
|['Properties'-Sammlung](../../../ado/reference/ado-api/properties-collection-ado.md)|[Tabellen Sammlung](../../../ado/reference/adox-api/tables-collection-adox.md)|[Benutzer Sammlung](../../../ado/reference/adox-api/users-collection-adox.md)|  
|[Views-Auflistung](../../../ado/reference/adox-api/views-collection-adox.md)|||  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für Aktualisierungs Methode (VB)](../../../ado/reference/ado-api/refresh-method-example-vb.md)   
 [Beispiel für eine Aktualisierungs Methode (VC + +)](../../../ado/reference/ado-api/refresh-method-example-vc.md)   
 [Count-Eigenschaft (ADO)](../../../ado/reference/ado-api/count-property-ado.md)   
 [Refresh-Methode (RDS)](../../../ado/reference/rds-api/refresh-method-rds.md)
