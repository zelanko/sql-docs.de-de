---
title: Parameters-Auflistung (ADO) | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4e062c67f0dedf55d63a076725b46d4405918741
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67917704"
---
# <a name="parameters-collection-ado"></a>Parameters-Collection (ADO)
Enthält alle der [Parameter](../../../ado/reference/ado-api/parameter-object.md) Objekte von einem [Befehl](../../../ado/reference/ado-api/command-object-ado.md) Objekt.  
  
## <a name="remarks"></a>Hinweise  
 Ein **Befehl** Objekt verfügt über eine **Parameter** -Auflistung, die von **Parameter** Objekte.  
  
 Mithilfe der [aktualisieren](../../../ado/reference/ado-api/refresh-method-ado.md) Methode für eine **Befehl** des Objekts **Parameter** Auflistung abruft, Anbieter von Parameterinformationen für die gespeicherte Prozedur oder eine parametrisierte Abfrage Angabe in der **Befehl** Objekt. Einige Anbieter unterstützen kein Aufrufe gespeicherter Prozeduren oder parametrisierte Abfragen. Aufrufen der **aktualisieren** Methode für die **Parameter** Auflistung, die bei Verwendung eines solchen Anbieters einen Fehler zurück.  
  
 Wenn Sie keine eigene definiert haben **Parameter** Zugriff auf Objekte, und Sie die **Parameter** Auflistung vor dem Aufruf der **aktualisieren** -Methode, ADO ruft automatisch die Methode, und füllen Sie die Sammlung für Sie.  
  
 Sie können Aufrufe an den Anbieter zur Verbesserung der Leistung, wenn Sie wissen, die Eigenschaften der Parameter der gespeicherten Prozedur zugeordnet oder einer parametrisierten Abfrage, dass Sie aufrufen möchten, minimieren. Verwenden Sie die [CreateParameter](../../../ado/reference/ado-api/createparameter-method-ado.md) Methode zum Erstellen **Parameter** Objekte und die entsprechenden Einstellungen und die Verwendung der [Anfügen](../../../ado/reference/ado-api/append-method-ado.md) Methode zum Hinzufügen der  **Parameter** Auflistung. Dadurch können Sie festlegen und Zurückgeben von Werten ohne den Anbieter für die Parameterinformationen aufrufen. Wenn Sie an einen Anbieter schreiben, die keine Parameterinformationen enthält, müssen Sie manuell Auffüllen der **Parameter** Auflistung, die mit dieser Methode, um die Parameter verwenden zu können. Verwenden der [löschen](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md) Methode, um entfernen **Parameter** Objekte aus der **Parameter** Auflistung bei Bedarf.  
  
 Die Objekte in der **Parameter** Auflistung von einer **Recordset** außerhalb des gültigen Bereichs (somit nicht verfügbar) wechseln Sie bei der **Recordset** geschlossen wird.  
  
 Beim Aufrufen einer gespeicherten Prozedur mit **Befehl**, der zurückgegeben Wert/Output-Parameter einer gespeicherten Prozedur wird wie folgt abgerufen:  
  
1.  Beim Aufrufen einer gespeicherten Prozedur, die keine Parameter besitzt, die **aktualisieren** Methode für die **Parameter** Auflistung aufgerufen werden soll, bevor die **Execute** Methode für die **Befehl** Objekt.  
  
2.  Beim Aufrufen einer gespeicherten Prozedur mit Parametern und Anfügen von explizit Parameter für die **Parameter** Sammlung mit **Append**, die return-Wert/Output-Parameter angefügt werden muss, um die **Parameter** Auflistung. Der Rückgabewert muss zuerst angefügt werden, um die **Parameter** Auflistung. Verwendung **Anfügen** , fügen die anderen Parameter in der **Parameter** Auflistung in der Reihenfolge der Definition. Die gespeicherte Prozedur SPWithParam hat beispielsweise zwei Parameter. Der erste Parameter, *InParam*, ist ein Eingabeparameter als AdVarChar (20) definiert, und der zweite Parameter, *OutParam*, ist ein Ausgabeparameter, der als AdVarChar (20) definiert. Sie können die return-Wert/Output-Parameter mit dem folgenden Code abrufen.  
  
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
  
3.  Beim Aufrufen einer gespeicherten Prozedur mit Parametern und konfigurieren die Parameter durch Aufrufen der **Element** Methode für die **Parameter** -Auflistung, der zurückgegeben Wert/Output-Parameter der gespeicherten Prozedur kann aus abgerufen werden, die **Parameter** Auflistung. Die gespeicherte Prozedur SPWithParam hat beispielsweise zwei Parameter. Der erste Parameter, *InParam*, ist ein Eingabeparameter als AdVarChar (20) definiert, und der zweite Parameter, *OutParam*, ist ein Ausgabeparameter, der als AdVarChar (20) definiert. Sie können die return-Wert/Output-Parameter mit dem folgenden Code abrufen.  
  
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
  
-   [Parameter-Auflistungseigenschaften, Methoden und Ereignisse](../../../ado/reference/ado-api/parameters-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Append-Methode (ADO)](../../../ado/reference/ado-api/append-method-ado.md)   
 [CreateParameter-Methode (ADO)](../../../ado/reference/ado-api/createparameter-method-ado.md)   
 [Parameter-Objekt](../../../ado/reference/ado-api/parameter-object.md)
