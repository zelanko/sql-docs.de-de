---
description: Refresh-Methode (ADO)
title: Refresh-Methode (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 66324860f931a919cccc36d3de9464d2ad2e48d0
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88989611"
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
 Wenn Sie die **Refresh** -Methode für die [Parameters](./parameters-collection-ado.md) -Auflistung eines [Command](./command-object-ado.md) -Objekts verwenden, werden Anbieter seitige Parameterinformationen für die gespeicherte Prozedur oder parametrisierte Abfrage abgerufen, die im **Command** -Objekt angegeben sind. Die Auflistung ist leer für Anbieter, die keine Aufrufe gespeicherter Prozeduren oder parametrisierte Abfragen unterstützen.  
  
 Sie sollten die [ActiveConnection](./activeconnection-property-ado.md) -Eigenschaft des **Befehls** Objekts auf ein gültiges [Verbindungs](./connection-object-ado.md) Objekt, die [CommandText](./commandtext-property-ado.md) -Eigenschaft auf einen gültigen Befehl und die [CommandType](./commandtype-property-ado.md) -Eigenschaft auf **adCmdStoredProc** festlegen, bevor Sie die **Refresh** -Methode aufrufen.  
  
 Wenn Sie auf die **Parameter** Auflistung zugreifen, bevor Sie die **Refresh** -Methode aufrufen, ruft ADO automatisch die-Methode auf und füllt die-Auflistung für Sie auf.  
  
> [!NOTE]
>  Wenn Sie die **Refresh** -Methode verwenden, um Parameterinformationen vom Anbieter abzurufen, und ein oder mehrere Datentyp [Parameter](./parameter-object.md) Objekte variabler Länge zurückgibt, kann ADO Arbeitsspeicher für die Parameter basierend auf Ihrer maximalen potenziellen Größe zuweisen, was zu einem Fehler während der Ausführung führt. Sie sollten die [size](./size-property-ado-parameter.md) -Eigenschaft für diese Parameter explizit festlegen, bevor Sie die [Execute](./execute-method-ado-command.md) -Methode aufrufen, um Fehler zu verhindern.  
  
### <a name="fields"></a>Felder  
 Die Verwendung der **Refresh** -Methode für die [Fields](./fields-collection-ado.md) -Auflistung hat keinen sichtbaren Effekt. Zum Abrufen von Änderungen aus der zugrunde liegenden Datenbankstruktur müssen Sie entweder die [Requery](./requery-method.md) -Methode oder, wenn das [Recordset](./recordset-object-ado.md) -Objekt keine Lesezeichen unterstützt, die Methode " [muvefirst](./movefirst-movelast-movenext-and-moveprevious-methods-ado.md) " verwenden.  
  
### <a name="properties"></a>Eigenschaften  
 Die Verwendung der **Refresh** -Methode für eine **Properties** -Auflistung einiger Objekte füllt die Auflistung mit den dynamischen Eigenschaften auf, die der Anbieter verfügbar macht. Diese Eigenschaften enthalten Informationen über die für den anbieterspezifischen Funktionen, die über die von ADO unterstützten integrierten Eigenschaften hinausgehen.  
  
## <a name="applies-to"></a>Gilt für  

:::row:::
    :::column:::
        [Achsen Sammlung](../ado-md-api/axes-collection-ado-md.md)  
        [Columns-Sammlung](../adox-api/columns-collection-adox.md)  
        [CubeDefs-Sammlung](../ado-md-api/cubedefs-collection-ado-md.md)  
        [Dimensions Auflistung](../ado-md-api/dimensions-collection-ado-md.md)  
        [Fehlersammlung](./errors-collection-ado.md)  
        [Fields-Auflistung](./fields-collection-ado.md)  
        [Groups-Sammlung](../adox-api/groups-collection-adox.md)  
    :::column-end:::
    :::column:::
        [Hierarchien-Auflistung](../ado-md-api/hierarchies-collection-ado-md.md)  
        [Index Sammlung](../adox-api/indexes-collection-adox.md)  
        [Schlüssel Sammlung](../adox-api/keys-collection-adox.md)  
        [Levels-Auflistung](../ado-md-api/levels-collection-ado-md.md)  
        [Members-Auflistung](../ado-md-api/members-collection-ado-md.md)  
        [Parameters-Auflistung](./parameters-collection-ado.md)  
    :::column-end:::
    :::column:::
        [Positions Auflistung](../ado-md-api/positions-collection-ado-md.md)  
        [Prozeduren](../adox-api/procedures-collection-adox.md)  
        ['Properties'-Sammlung](./properties-collection-ado.md)  
        [Tabellen Sammlung](../adox-api/tables-collection-adox.md)  
        [Benutzer Sammlung](../adox-api/users-collection-adox.md)  
        [Views-Auflistung](../adox-api/views-collection-adox.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für Aktualisierungs Methode (VB)](./refresh-method-example-vb.md)   
 [Beispiel für eine Aktualisierungs Methode (VC + +)](./refresh-method-example-vc.md)   
 [Count-Eigenschaft (ADO)](./count-property-ado.md)   
 [Refresh-Methode (RDS)](../rds-api/refresh-method-rds.md)