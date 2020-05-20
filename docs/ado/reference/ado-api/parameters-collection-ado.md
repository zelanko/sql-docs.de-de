---
title: Parameter Auflistung (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Command15::get_Parameters
- Command15::Parameters
- Command15::GetParameters
helpviewer_keywords:
- Parameters collection [ADO]
ms.assetid: 497cae10-3913-422a-9753-dcbb0a639b1b
author: rothja
ms.author: jroth
ms.openlocfilehash: e087c769fe84e79ca9a41c33912f150249ab2cd9
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82763391"
---
# <a name="parameters-collection-ado"></a>Parameters-Collection (ADO)
Enthält alle [Parameter](../../../ado/reference/ado-api/parameter-object.md) Objekte eines [Befehls](../../../ado/reference/ado-api/command-object-ado.md) Objekts.  
  
## <a name="remarks"></a>Bemerkungen  
 Ein **Command** -Objekt verfügt über eine **Parameter** Auflistung aus **Parameter** Objekten.  
  
 Wenn Sie die [Refresh](../../../ado/reference/ado-api/refresh-method-ado.md) -Methode für die **Parameter** Auflistung eines **Befehls** Objekts verwenden, werden Anbieter Parameterinformationen für die gespeicherte Prozedur oder parametrisierte Abfrage abgerufen, die im **Command** -Objekt angegeben sind. Einige Anbieter unterstützen keine Aufrufe gespeicherter Prozeduren oder parametrisierte Abfragen. Wenn Sie die **Refresh** -Methode für die **Parameter** Auflistung aufrufen, wenn Sie einen solchen Anbieter verwenden, wird ein Fehler zurückgegeben.  
  
 Wenn Sie keine eigenen **Parameter** Objekte definiert haben und auf die **Parameter** Auflistung zugreifen, bevor Sie die **Aktualisierungs** Methode aufrufen, ruft ADO die-Methode automatisch auf und füllt die-Auflistung für Sie auf.  
  
 Sie können die Aufrufe des Anbieters minimieren, um die Leistung zu verbessern, wenn Sie die Eigenschaften der Parameter kennen, die der gespeicherten Prozedur oder der parametrisierten Abfrage zugeordnet sind, die Sie aufrufen möchten. Verwenden Sie die Methode " [kreateparameter](../../../ado/reference/ado-api/createparameter-method-ado.md) ", um **Parameter** Objekte mit den entsprechenden Eigenschaften Einstellungen zu erstellen, und fügen Sie Sie mithilfe der [Append](../../../ado/reference/ado-api/append-method-ado.md) -Methode der **Parameter** Auflistung hinzu. Dies ermöglicht es Ihnen, Parameterwerte festzulegen und zurückzugeben, ohne den Anbieter für die Parameterinformationen aufrufen zu müssen. Wenn Sie in einen Anbieter schreiben, der keine Parameterinformationen bereitstellt, müssen Sie die **Parameter** Auflistung mithilfe dieser Methode manuell auffüllen, damit Sie Parameter verwenden können. Verwenden Sie die [Delete](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md) -Methode, um bei Bedarf **Parameter** Objekte aus der **Parameter** Auflistung zu entfernen.  
  
 Die Objekte in der **Parameters** -Auflistung eines **Recordsets** gehen außerhalb des gültigen Bereichs (daher nicht verfügbar), wenn das **Recordset** geschlossen wird.  
  
 Beim Aufrufen einer gespeicherten Prozedur mit einem **Befehl**wird der Rückgabewert/Output-Parameter einer gespeicherten Prozedur wie folgt abgerufen:  
  
1.  Wenn Sie eine gespeicherte Prozedur aufrufen, die über keine Parameter verfügt, sollte die **Aktualisierungs** Methode für die **Parameter** Auflistung aufgerufen werden, bevor die **Execute** -Methode für das **Command** -Objekt aufgerufen wird.  
  
2.  Beim Aufrufen einer gespeicherten Prozedur mit Parametern und dem expliziten Anfügen eines Parameters an die **Parameter** Auflistung mit **Append**sollte der Rückgabewert/Ausgabeparameter an die **Parameter** Auflistung angehängt werden. Der Rückgabewert muss zuerst an die **Parameter** Auflistung angehängt werden. Verwenden **Sie anfügen,** um die anderen Parameter der **Parameter** Auflistung in der Reihenfolge der Definition hinzuzufügen. Beispielsweise verfügt die gespeicherte Prozedur spwithparam über zwei Parameter. Der erste Parameter, *InParam*, ist ein als adVarChar (20) definierter Eingabeparameter, und der zweite Parameter, *outParam*, ist ein Output-Parameter, der als adVarChar (20) definiert ist. Sie können den Rückgabewert/Output-Parameter mit dem folgenden Code abrufen.  
  
    ```vb
    ' Open Connection Conn  
    set ccmd = CreateObject("ADODB.Command")  
    ccmd.Activeconnection= Conn  
  
    ccmd.CommandText="SPWithParam"  
    ccmd.commandType = 4 'adCmdStoredProc  
  
    ccmd.parameters.Append ccmd.CreateParameter(, adInteger, adParamReturnValue, , NULL)   ' return value  
    ccmd.parameters.Append ccmd.CreateParameter("InParam", adVarChar, adParamInput, 20, "hello world")   ' input parameter  
    ccmd.parameters.Append ccmd.CreateParameter("OutParam", adVarChar, adParamOutput, 20, NULL)   ' output parameter  
  
    ccmd.execute()  
  
    ' Access ccmd.parameters(0) as return value of this stored procedure  
    ' Access ccmd.parameters("OutParam") as the output parameter of this stored procedure.  
  
    ```  
  
3.  Wenn eine gespeicherte Prozedur mit Parametern aufgerufen und die Parameter durch Aufrufen der **Item** -Methode für die **Parameter** Auflistung konfiguriert werden, kann der Rückgabewert/Output-Parameter der gespeicherten Prozedur aus der **Parameter** Auflistung abgerufen werden. Beispielsweise verfügt die gespeicherte Prozedur spwithparam über zwei Parameter. Der erste Parameter, *InParam*, ist ein als adVarChar (20) definierter Eingabeparameter, und der zweite Parameter, *outParam*, ist ein Output-Parameter, der als adVarChar (20) definiert ist. Sie können den Rückgabewert/Output-Parameter mit dem folgenden Code abrufen.  
  
    ```vb
    ' Open Connection Conn  
    set ccmd = CreateObject("ADODB.Command")  
    ccmd.Activeconnection= Conn  
  
    ccmd.CommandText="SPWithParam"  
    ccmd.commandType = 4 'adCmdStoredProc  
  
    ccmd.parameters.Item("InParam").value = "hello world" ' input parameter  
    ccmd.execute()  
  
    ' Access ccmd.parameters(0) as return value of stored procedure  
    ' Access ccmd.parameters(2) or ccmd.parameters("OutParam") as the output parameter.  
    ```  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Parameter Sammlungs Eigenschaften, Methoden und Ereignisse](../../../ado/reference/ado-api/parameters-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Append-Methode (ADO)](../../../ado/reference/ado-api/append-method-ado.md)   
 [Kreateparameter-Methode (ADO)](../../../ado/reference/ado-api/createparameter-method-ado.md)   
 [Parameter-Objekt](../../../ado/reference/ado-api/parameter-object.md)
