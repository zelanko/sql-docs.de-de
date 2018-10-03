---
title: Close-Methode (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::Close
- _Stream::Close
- _Record::Close
helpviewer_keywords:
- Close method [ADO]
ms.assetid: 3cdf27d1-a180-4cff-8e42-95dec5fb1b55
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f43e59ed38dfde8091cb851f75a133c60874a6af
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47644690"
---
# <a name="close-method-ado"></a>Close-Methode (ADO)
Schließt ein geöffnetes Objekt und alle abhängigen Objekte.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.Close  
```  
  
## <a name="remarks"></a>Hinweise  
 Verwenden der **schließen** Methode zum Schließen einer [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md), [Datensatz](../../../ado/reference/ado-api/record-object-ado.md), [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md), oder ein [Stream](../../../ado/reference/ado-api/stream-object-ado.md) Objekt Um alle zugeordneten Systemressourcen frei. Schließen ein Objekt entfernt es nicht aus dem Arbeitsspeicher. Sie können ändern Sie die eigenschafteneinstellungen, und öffnen sie es später noch mal. Um ein Objekt vom Arbeitsspeicher vollständig zu vermeiden, schließen Sie das Objekt aus, und legen Sie die Objektvariable auf *nichts* (in Visual Basic).  
  
## <a name="connection"></a>Verbindung  
 Mithilfe der **schließen** Methode zum Schließen einer **Verbindung** Objekt schließt auch alle aktiven **Recordset** Objekte, die der Verbindung zugeordnet. Ein [Befehl](../../../ado/reference/ado-api/command-object-ado.md) zugeordnete Objekt der **Verbindung** Sie schließen das Objekt wird beibehalten, aber es nicht mehr zugeordnet wird eine **Verbindung** -Objekt, d. h., seine [ ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) Eigenschaft auf festgelegt **nichts**. Darüber hinaus die **Befehl** des Objekts [Parameter](../../../ado/reference/ado-api/parameters-collection-ado.md) Auflistung aller Anbieter definierte Parameter werden gelöscht.  
  
 Sie können später aufrufen, die [öffnen](../../../ado/reference/ado-api/open-method-ado-connection.md) Methode, um die Verbindung mit der gleichen oder einer anderen Datenquelle erneut herzustellen. Während der **Verbindung** -Objekt ist geschlossen, Aufrufen von Methoden, die eine geöffnete Verbindung zur Datenquelle erforderlich ist, wird ein Fehler generiert.  
  
 Schließen einer **Verbindung** Objekt es zwar öffnen **Recordset** Objekte für die Verbindung ein Rollback alle ausstehenden Änderungen in allen der **Recordset** Objekte. Explizit schließen eine **Verbindung** Objekt (Aufrufen der **schließen** Methode) während eine Transaktion wird ausgeführt, generieren Fehler. Wenn eine **Verbindung** Objekt außerhalb des gültigen Bereichs liegt, während eine Transaktion ausgeführt wird, ADO automatisch ein Rollback der Transaktions.  
  
## <a name="recordset-record-stream"></a>Recordset, Datensatz, Stream  
 Mithilfe der **schließen** Methode zum Schließen einer **Recordset**, **Datensatz**, oder **Stream** Objekt frei, die zugehörigen Daten und exklusiven Zugriff haben Sie möglicherweise auf die Daten über dieses Objekt. Sie können später aufrufen, die [öffnen](../../../ado/reference/ado-api/open-method-ado-recordset.md) Attribute der Methode, um das Objekt mit dem gleichen oder geänderten erneut öffnen.  
  
 Während einer **Recordset** -Objekt ist geschlossen, Aufrufen von Methoden, die erfordern einen live-Cursor wird ein Fehler generiert.  
  
 Wenn ein Bearbeitungsvorgang ausgeführt, während er sich im sofortupdatemodus ist, wird beim Aufrufen der **schließen** Methode wird ein Fehler generiert, rufen Sie stattdessen die [aktualisieren](../../../ado/reference/ado-api/update-method.md) oder [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) Methode erste. Wenn Sie schließen die **Recordset** im Batchmodus Update verwendet wird, alle Änderungen seit dem letzten Objekt [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) Aufruf verloren.  
  
 Bei Verwendung der [Klon](../../../ado/reference/ado-api/clone-method-ado.md) Methode zum Erstellen von Kopien eines geöffneten **Recordset** Objekt ist, schließen die ursprünglichen oder einen Klon hat keine Auswirkungen auf der anderen Kopien.  
  
## <a name="applies-to"></a>Gilt für  
  
|||  
|-|-|  
|[Connection-Objekt (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)|[Record-Objekt (ADO)](../../../ado/reference/ado-api/record-object-ado.md)|  
|[Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|[Stream-Objekt (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [Öffnen Sie und schließen Sie die Methode – Beispiel (VB)](../../../ado/reference/ado-api/open-and-close-methods-example-vb.md)   
 [Öffnen Sie und schließen Sie die Methode – Beispiel (VBScript)](../../../ado/reference/ado-api/open-and-close-methods-example-vbscript.md)   
 [Öffnen Sie und schließen Sie die Methode – Beispiel (VC++)](../../../ado/reference/ado-api/open-and-close-methods-example-vc.md)   
 [Open Sie-Methode (ADO Connection)](../../../ado/reference/ado-api/open-method-ado-connection.md)   
 [Open Sie-Methode (ADO Recordset)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Save-Methode](../../../ado/reference/ado-api/save-method.md)
