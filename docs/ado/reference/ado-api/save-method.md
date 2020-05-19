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
author: rothja
ms.author: jroth
ms.openlocfilehash: 4134e34cc494185ec384bd9900ba578e9fa3034d
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82755869"
---
# <a name="save-method"></a>Save-Methode
Speichert das [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) in einer Datei oder einem [Streamobjekt](../../../ado/reference/ado-api/stream-object-ado.md) .  
  
## <a name="syntax"></a>Syntax  
  
```  
  
recordset.Save Destination, PersistFormat  
```  
  
#### <a name="parameters"></a>Parameter  
 *Ziel*  
 Dies ist optional. Eine **Variante** , die den kompletten Pfadnamen der Datei darstellt, in der das **Recordset** gespeichert werden soll, oder einen Verweis auf ein **Stream** -Objekt.  
  
 *PersistFormat*  
 Dies ist optional. Ein [PersistFormatEnum](../../../ado/reference/ado-api/persistformatenum.md) -Wert, der das Format angibt, in dem das **Recordset** gespeichert werden soll (XML oder ADTG). Der Standardwert ist **adPersistADTG**.  
  
## <a name="remarks"></a>Bemerkungen  
 Die Methode zum [Speichern der Methode](../../../ado/reference/ado-api/save-method.md) kann nur für ein offenes **Recordset**aufgerufen werden. Verwenden Sie die [Open-Methode (ADO Recordset)](../../../ado/reference/ado-api/open-method-ado-recordset.md) -Methode, um das **Recordset** später aus dem *Ziel*wiederherzustellen.  
  
 Wenn die Eigenschaft [Filter Eigenschaft](../../../ado/reference/ado-api/filter-property.md) für das **Recordset**wirksam ist, werden nur die Zeilen, auf die der Filter zugreifen kann, gespeichert. Wenn das **Recordset** hierarchisch ist, werden das aktuelle untergeordnete **Recordset** und seine untergeordneten Elemente gespeichert, einschließlich des übergeordneten **Recordsets**. Wenn die Save-Methode eines untergeordneten **Recordsets** aufgerufen wird, werden das untergeordnete Element und alle zugehörigen untergeordneten Elemente gespeichert, das übergeordnete Element ist jedoch nicht.  
  
 Wenn Sie das **Recordset**zum ersten Mal speichern, ist es optional, das *Ziel*anzugeben. Wenn Sie das *Ziel*weglassen, wird eine neue Datei mit einem Namen erstellt, der auf den Wert der Source-Eigenschaft des **Recordsets**festgelegt ist.  
  
 Lassen Sie das *Ziel* aus, wenn Sie anschließend " **Speichern** " nach dem ersten Speichern aufzurufen, oder ein Laufzeitfehler auftritt. Wenn Sie anschließend **Speichern** mit einem neuen *Ziel*aufzurufen, wird das **Recordset** im neuen Ziel gespeichert. Allerdings sind das neue Ziel und das ursprüngliche Ziel beide geöffnet.  
  
 Durch **Speichern** wird das **Recordset** oder das *Ziel*nicht geschlossen, sodass Sie weiterhin mit dem **Recordset** arbeiten und die neuesten Änderungen speichern können. Das *Ziel* bleibt geöffnet, bis das **Recordset** geschlossen ist.  
  
 Aus Sicherheitsgründen ermöglicht die **Save** -Methode nur die Verwendung von niedrigen und benutzerdefinierten Sicherheitseinstellungen aus einem Skript, das von Microsoft Internet Explorer ausgeführt wird.  
  
 Wenn die **Save** -Methode während des asynchronen **Recordsets** zum Abrufen, ausführen oder Aktualisieren aufgerufen wird, wird die Wartezeit bis zum Abschluss des asynchronen Vorgangs **gespeichert** .  
  
 Datensätze werden ab der ersten Zeile des **Recordsets**gespeichert. Wenn die **Save** -Methode abgeschlossen ist, wird die aktuelle Zeilen Position in die erste Zeile des **Recordsets**verschoben.  
  
 Um optimale Ergebnisse zu erzielen, legen Sie die Eigenschaft für die [Cursor Location-Eigenschaft (ADO)](../../../ado/reference/ado-api/cursorlocation-property-ado.md) mithilfe von **Save**auf **adUseClient** fest. Wenn Ihr Anbieter nicht alle Funktionen unterstützt, die zum Speichern von **Recordset** -Objekten erforderlich sind, stellt der Cursor Dienst diese Funktionalität bereit.  
  
 Wenn ein **Recordset** persistent ist und die Eigenschaft **Cursor Location** auf **adeeserver**festgelegt ist, ist die Aktualisierungs Funktion für das **Recordset** eingeschränkt. In der Regel sind nur Aktualisierungen der einzelnen Tabelle, Einfügungen und Löschungen zulässig (abhängig von der Anbieter Funktionalität). Die Methode Methode der [erneuten Synchronisierung](../../../ado/reference/ado-api/resync-method.md) ist in dieser Konfiguration ebenfalls nicht verfügbar.  
  
> [!NOTE]
>  Das Speichern eines **Recordsets** mit **Feldern** vom Typ " **advariant**", " **adidispatch**" oder " **adiunknown** " wird nicht von ADO unterstützt und kann zu unvorhersehbaren Ergebnissen führen.  
  
 Nur Filter in Form von Kriterienzeichenfolgen (z. b. OrderDate > ' 12/31/1999 ') wirken sich auf den Inhalt eines persistent gespeicherten **Recordsets**aus. Filter, die mit einem Array von **Lesezeichen** erstellt wurden oder einen Wert aus dem [filtergroupum](../../../ado/reference/ado-api/filtergroupenum.md) verwenden, wirken sich nicht auf den Inhalt des beibehaltenen **Recordsets**aus. Diese Regeln gelten für **Recordsets**, die entweder mit Client seitigen oder serverseitigen Cursorn erstellt wurden.  
  
 Da der *Destination* -Parameter jedes Objekt akzeptieren kann, das die OLE DB IStream-Schnittstelle unterstützt, können Sie ein **Recordset** direkt im ASP-Antwortobjekt speichern. Weitere Informationen finden Sie im XML- **Recordset-persistenzszenario**.  
  
 Sie können auch ein **Recordset** im XML-Format in einer Instanz eines MSXML-DOM-Objekts speichern, wie im folgenden Visual Basic Code gezeigt:  
  
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
>  Beim Speichern hierarchischer Recordsets (Daten Formen) im XML-Format gelten zwei Einschränkungen. In XML kann nicht gespeichert werden, wenn das hierarchische **Recordset** ausstehende Updates enthält, und Sie können kein parametrisiertes hierarchisches **Recordset**speichern.  
  
 Ein im XML-Format gespeichertes **Recordset** wird mit dem UTF-8-Format gespeichert. Wenn eine solche Datei in einen ADO-Stream geladen wird, versucht das Stream-Objekt nicht, ein **Recordset** aus dem Stream zu öffnen, es sei denn, die CharSet-Eigenschaft des Streams wird auf den entsprechenden Wert für das UTF-8-Format festgelegt.  
  
## <a name="applies-to"></a>Gilt für  
  
|||  
|-|-|  
|[Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|[Stream-Objekt (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für das Speichern und Öffnen von Methoden (VB)](../../../ado/reference/ado-api/save-and-open-methods-example-vb.md)   
 [Beispiel für das Speichern und Öffnen von Methoden (VC + +)](../../../ado/reference/ado-api/save-and-open-methods-example-vc.md)   
 [Open-Methode (ADO-Recordset)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Open-Methode (ADO-Stream)](../../../ado/reference/ado-api/open-method-ado-stream.md)   
 [SaveToFile-Methode](../../../ado/reference/ado-api/savetofile-method.md)
