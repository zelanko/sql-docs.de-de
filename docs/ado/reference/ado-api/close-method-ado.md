---
description: Close-Methode (ADO)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 2cfdee50d0b5699e1f6eca4eb8e22375e4e5a672
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88450952"
---
# <a name="close-method-ado"></a>Close-Methode (ADO)
Schließt ein offenes Objekt und alle abhängigen Objekte.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.Close  
```  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie die **Close** -Methode, um eine [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md), einen Datensatz, ein [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)oder ein [Daten](../../../ado/reference/ado-api/record-object-ado.md) [Strom](../../../ado/reference/ado-api/stream-object-ado.md) Objekt zu schließen, um alle zugeordneten Systemressourcen freizugeben. Durch das Schließen eines Objekts wird es nicht aus dem Arbeitsspeicher entfernt. Sie können die Eigenschaften Einstellungen ändern und Sie später erneut öffnen. Wenn Sie ein Objekt vollständig aus dem Arbeitsspeicher entfernen möchten, schließen Sie das-Objekt, und legen Sie die-Objekt Variable auf *Nothing* (in Visual Basic)  
  
## <a name="connection"></a>Verbindung  
 Wenn Sie ein **Verbindungs** Objekt mithilfe der **Close** -Methode schließen, werden auch alle aktiven **Recordset** -Objekte geschlossen, die der Verbindung zugeordnet sind. Ein [Command](../../../ado/reference/ado-api/command-object-ado.md) -Objekt, das dem zu schließenden **Verbindungs** Objekt zugeordnet ist, wird beibehalten, es wird jedoch nicht mehr einem **Verbindungs** Objekt zugeordnet. Das heißt, die [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) -Eigenschaft wird auf " **Nothing**" festgelegt. Außerdem wird die [Parameter](../../../ado/reference/ado-api/parameters-collection-ado.md) Auflistung des **Befehls** Objekts von allen Anbieter definierten Parametern gelöscht.  
  
 Sie können später die [Open](../../../ado/reference/ado-api/open-method-ado-connection.md) -Methode aufzurufen, um die Verbindung mit derselben oder einer anderen Datenquelle wiederherzustellen. Während das **Verbindungs** Objekt geschlossen wird, wird beim Aufrufen von Methoden, die eine geöffnete Verbindung mit der Datenquelle erfordern, ein Fehler generiert.  
  
 Wenn Sie ein **Verbindungs** Objekt schließen, während für die Verbindung geöffnete Recordsetobjekte vorhanden sind, wird für alle ausstehenden Änderungen in allen **Recordset** -Objekten ein Rollback ausgeführt. **Recordset** Das explizite Schließen eines **Verbindungs** Objekts (Aufrufen der **Close** -Methode) während einer Transaktion wird ein Fehler generiert. Wenn ein **Verbindungs** Objekt den Gültigkeitsbereich verlässt, während eine Transaktion ausgeführt wird, führt ADO automatisch ein Rollback für die Transaktion aus.  
  
## <a name="recordset-record-stream"></a>Recordset, Datensatz, Stream  
 Mithilfe der **Close** -Methode zum Schließen eines **Recordsets**, eines **Datensatzes**oder eines **Stream** -Objekts werden die zugeordneten Daten und alle exklusiven Zugriffe freigegeben, die Sie möglicherweise über dieses bestimmte Objekt haben. Sie können später die [Open](../../../ado/reference/ado-api/open-method-ado-recordset.md) -Methode aufzurufen, um das Objekt mit den gleichen oder geänderten Attributen erneut zu öffnen.  
  
 Während ein **Recordset** -Objekt geschlossen wird, wird beim Aufrufen von Methoden, die einen Live Cursor erfordern, ein Fehler generiert.  
  
 Wenn im sofortigen Update Modus eine Bearbeitung ausgeführt wird, generiert der Aufruf der **Close** -Methode einen Fehler. Stattdessen müssen Sie zuerst die [Update](../../../ado/reference/ado-api/update-method.md) -oder [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) -Methode aufzurufen. Wenn Sie das **Recordset** -Objekt im Batch Aktualisierungs Modus schließen, gehen alle Änderungen seit dem letzten [Update Batch](../../../ado/reference/ado-api/updatebatch-method.md) -Vorgang verloren.  
  
 Wenn Sie die [Clone](../../../ado/reference/ado-api/clone-method-ado.md) -Methode verwenden, um Kopien eines geöffneten **Recordset** -Objekts zu erstellen, wirkt sich das Schließen des ursprünglichen oder eines Klons nicht auf andere Kopien aus.  
  
## <a name="applies-to"></a>Gilt für  

:::row:::
    :::column:::
        [Connection-Objekt (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
        [Record-Objekt (ADO)](../../../ado/reference/ado-api/record-object-ado.md)  
    :::column-end:::
    :::column:::
        [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
        [Stream-Objekt (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>Weitere Informationen  
 [Open-und Close-Methoden Beispiel (VB)](../../../ado/reference/ado-api/open-and-close-methods-example-vb.md)   
 [Open-und Close-Methoden Beispiel (VBScript)](../../../ado/reference/ado-api/open-and-close-methods-example-vbscript.md)   
 [Open-und Close-Methoden Beispiel (VC + +)](../../../ado/reference/ado-api/open-and-close-methods-example-vc.md)   
 [Open-Methode (ADO-Verbindung)](../../../ado/reference/ado-api/open-method-ado-connection.md)   
 [Open-Methode (ADO-Recordset)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Save-Methode](../../../ado/reference/ado-api/save-method.md)
