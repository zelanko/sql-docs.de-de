---
title: Save-Methode | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Recordset::Save
- _Recordset::raw_Save
helpviewer_keywords:
- Save method [ADO]
ms.assetid: ed3d9678-5c28-4e61-8bb3-7dfb66d99cf5
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 0953b76ff642387679c907e6f0b3364cbac898df
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66711387"
---
# <a name="save-method"></a>Save-Methode
Speichert die [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) in einer Datei oder [Stream](../../../ado/reference/ado-api/stream-object-ado.md) Objekt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
recordset.Save Destination, PersistFormat  
```  
  
#### <a name="parameters"></a>Parameter  
 *Ziel*  
 Optional. Ein **Variant** , die den vollständigen Pfadnamen der Datei darstellt, in denen die **Recordset** gespeichert werden soll, oder ein Verweis auf eine **Stream** Objekt.  
  
 *PersistFormat*  
 Optional. Ein [PersistFormatEnum](../../../ado/reference/ado-api/persistformatenum.md) -Wert, der angibt, in dem das Format der **Recordset** (XML oder ADTG) gespeichert werden soll. Der Standardwert ist **AdPersistADTG**.  
  
## <a name="remarks"></a>Hinweise  
 Die [Methode speichern](../../../ado/reference/ado-api/save-method.md) Methode kann nur aufgerufen werden, auf einem geöffneten **Recordset**. Verwenden der [Open-Methode (ADO Recordset)](../../../ado/reference/ado-api/open-method-ado-recordset.md) Methode, um spätere Wiederherstellung der **Recordset** aus *Ziel*.  
  
 Wenn die [Filtereigenschaft](../../../ado/reference/ado-api/filter-property.md) Eigenschaft ist aktiviert, die **Recordset**, und klicken Sie dann nur die Zeilen zugegriffen werden kann, unter dem Filter gespeichert werden. Wenn die **Recordset** hierarchisch aufgebaut ist, klicken Sie dann auf der aktuellen untergeordneten **Recordset** und seine untergeordneten Elemente gespeichert werden, einschließlich der übergeordneten **Recordset**. Wenn die Save-Methode eines untergeordneten Elements **Recordset** wird aufgerufen, das untergeordnete Element und alle zugehörigen untergeordneten Elemente werden gespeichert, das übergeordnete Element ist jedoch nicht.  
  
 Beim ersten Sie speichern die **Recordset**, ist er optional an *Ziel*. Wenn Sie weglassen *Ziel*, eine neue Datei erstellt werden mit einem Namen, die auf den Wert der Source-Eigenschaft des festgelegt die **Recordset**.  
  
 Lassen Sie *Ziel* anschließend aufgerufen **speichern** nach dem ersten Speichern oder einen Fehler zur Laufzeit erfolgt. Wenn Sie anschließend einen Aufruf **speichern** mit einem neuen *Ziel*, **Recordset** auf das neue Ziel gespeichert wird. Allerdings werden das neue Ziel und das ursprüngliche Ziel sowohl geöffnet sein.  
  
 **Speichern** schließt nicht die **Recordset** oder *Ziel*, sodass Sie fortfahren können, um die Arbeit mit der **Recordset** und die neuesten Änderungen zu speichern. *Ziel* bleibt bestehen, bis die **Recordset** geschlossen wird.  
  
 Aus Gründen der Sicherheit der **speichern** Methode lässt nur die Verwendung von niedrigen und benutzerdefinierte Einstellungen aus einem Skript, das von Microsoft Internet Explorer ausgeführt werden.  
  
 Wenn die **speichern** Methode wird aufgerufen, während eines asynchronen **Recordset** abzurufen, ausführen oder Aktualisieren der Vorgang wird ausgeführt, klicken Sie dann **speichern** wartet, bis der asynchrone Vorgang ist abgeschlossen.  
  
 Datensätze gespeichert werden, beginnend mit der ersten Zeile der **Recordset**. Wenn die **speichern** -Methode abgeschlossen ist, wird die aktuelle Zeilenposition verschoben, in die erste Zeile des der **Recordset**.  
  
 Legen Sie für optimale Ergebnisse die [CursorLocation-Eigenschaft (ADO)](../../../ado/reference/ado-api/cursorlocation-property-ado.md) Eigenschaft **AdUseClient** mit **speichern**. Wenn Ihr Anbieter nicht alle Funktionen zum Speichern von unterstützt **Recordset** Objekten, die der Cursor-Dienst wird diese Funktionalität bereitstellen.  
  
 Wenn eine **Recordset** wird beibehalten, mit der **CursorLocation** -Eigenschaft auf festgelegt **AdUseServer**, die Updatefunktion für die **Recordset**ist beschränkt. In der Regel nur für einzelne Tabellen Updates, einfügungen und löschungen (hängt von Anbieterfunktionen) sind. Die [Resync-Methode](../../../ado/reference/ado-api/resync-method.md) Methode ist auch in dieser Konfiguration nicht verfügbar.  
  
> [!NOTE]
>  Speichern einer **Recordset** mit **Felder** des Typs **AdVariant**, **AdIDispatch**, oder **AdIUnknown** ist nicht von ADO unterstützt und kann zu unvorhersehbare Ergebnissen führen.  
  
 Nur Filter in Form von Zeichenfolgen mit Kriterien (z. B. OrderDate > "12/31/1999") Auswirkungen auf den Inhalt, der eine persistierte **Recordset**. Filter, die mit einem Array von erstellten **Lesezeichen** oder mithilfe eines Werts aus der [FilterGroupEnum](../../../ado/reference/ado-api/filtergroupenum.md) wirkt sich nicht auf den Inhalt des beibehaltenen **Recordset**. Diese Regeln gelten für **Recordset**s, die mit einem clientseitigen oder serverseitigen Cursor erstellt.  
  
 Da die *Ziel* Parameter akzeptiert jedes Objekt, das die OLE DB-IStream-Schnittstelle unterstützt, können Sie speichern einen **Recordset** direkt an das ASP-Response-Objekt. Weitere Informationen finden Sie unter den **Speicherszenario für XML-Recordset**.  
  
 Sie können auch speichern eine **Recordset** im XML-Format mit einer Instanz von einem MSXML-DOM-Objekt, wie in den folgenden Visual Basic-Code angezeigt wird:  
  
```  
Dim xDOM As New MSXML.DOMDocument  
Dim rsXML As New ADODB.Recordset  
Dim sSQL As String, sConn As String  
  
sSQL = "SELECT customerid, companyname, contactname FROM customers"  
sConn="Provider=Microsoft.Jet.OLEDB.4.0;Data Source=Northwind.mdb"  
rsXML.Open sSQL, sConn  
rsXML.Save xDOM, adPersistXML   'Save Recordset directly into a DOM tree.  
...  
```  
  
> [!NOTE]
>  Zwei Einschränkungen gelten beim Speichern von hierarchischen Recordsets (Daten-Shapes) im XML-Format. Sie können nicht in XML gespeichert, wenn die hierarchische **Recordset** ausstehende Updates enthält und Sie können eine parametrisierte speichern hierarchische **Recordset**.  
  
 Ein **Recordset** gespeichert in XML ist Format gespeichert, mit UTF-8-Format. Wenn eine solche Datei in eine ADO-Stream geladen wird, das Stream-Objekt wird nicht versucht, öffnen Sie eine **Recordset** aus dem Stream, wenn die Charset-Eigenschaft des Streams auf den entsprechenden Wert für das UTF-8-Format festgelegt ist.  
  
## <a name="applies-to"></a>Gilt für  
  
|||  
|-|-|  
|[Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|[Stream-Objekt (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [Speichern Sie und öffnen Sie die Methode – Beispiel (VB)](../../../ado/reference/ado-api/save-and-open-methods-example-vb.md)   
 [Speichern Sie und öffnen Sie die Methode – Beispiel (VC++)](../../../ado/reference/ado-api/save-and-open-methods-example-vc.md)   
 [Open Sie-Methode (ADO Recordset)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Open Sie-Methode (ADO Stream)](../../../ado/reference/ado-api/open-method-ado-stream.md)   
 [SaveToFile-Methode](../../../ado/reference/ado-api/savetofile-method.md)
