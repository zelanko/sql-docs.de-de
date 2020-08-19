---
description: Datenabschnitt
title: Daten Abschnitt | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- data section [ADO]
ms.assetid: 43dc42a8-7057-48e6-93d6-880d5c5c51a4
author: rothja
ms.author: jroth
ms.openlocfilehash: abf0202e75ef64825d6dc815624adc1c1d337174
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88453572"
---
# <a name="data-section"></a>Datenabschnitt
Der Daten Abschnitt definiert die Daten des Rowsets sowie alle ausstehenden Updates, Einfügungen oder Löschungen. Der Daten Abschnitt kann NULL oder mehr Zeilen enthalten. Es können nur Daten aus einem Rowset enthalten sein, in dem die Zeile durch das Schema definiert ist. Auch, wie bereits erwähnt, können Spalten ohne Daten ausgelassen werden. Wenn ein Attribut oder ein Unterelement im Daten Abschnitt verwendet wird und dieses Konstrukt nicht im Schema Abschnitt definiert wurde, wird es automatisch ignoriert.  
  
## <a name="string"></a>Zeichenfolge  
 Reservierte XML-Zeichen in Textdaten müssen durch entsprechende Zeichen Entitäten ersetzt werden. Beispielsweise muss das einfache Anführungszeichen im Firmennamen "Joe es Garage" durch eine Entität ersetzt werden. Die tatsächliche Zeile ähnelt der folgenden:  
  
```  
<z:row CompanyName="Joe's Garage"/>  
```  
  
 Die folgenden Zeichen sind in XML reserviert und müssen durch Zeichen Entitäten ersetzt werden: {",", &, \<,> }.  
  
## <a name="binary"></a>Binary  
 Binäre Daten sind bin. Hex-codiert (d. h. ein Byte ist zwei Zeichen zugeordnet, ein Zeichen pro Nibble).  
  
## <a name="datetime"></a>Datetime  
 Das Variant VT_DATE-Format wird von XML-Daten Datentypen nicht direkt unterstützt. Das richtige Format für Datumsangaben mit einer Daten-und Zeitkomponente lautet yyyy-mm-ddThh: mm: SS.  
  
 Weitere Informationen zu den von XML angegebenen Datumsformaten finden Sie in der [W3C-Spezifikation für XML-Daten](https://go.microsoft.com/fwlink/?LinkId=5692).  
  
 Wenn in der XML-Data-Spezifikation zwei äquivalente Datentypen (z. b. I4 = = int) definiert sind, schreibt ADO den anzeigen Amen, aber beide werden gelesen.  
  
## <a name="managing-pending-changes"></a>Verwalten von ausstehenden Änderungen  
 Ein Recordset kann direkt oder im Batch Aktualisierungs Modus geöffnet werden. Wenn Sie mit Client seitigen Cursorn im Batch Aktualisierungs Modus geöffnet werden, sind alle am Recordset vorgenommenen Änderungen in einem ausstehenden Zustand, bis die UpdateBatch-Methode aufgerufen wird. Ausstehende Änderungen werden auch beibehalten, wenn das Recordset gespeichert wird. In XML werden Sie durch die Verwendung der "Update"-Elemente dargestellt, die in urn: Schemas-Microsoft-com: Rowset definiert sind. Wenn ein Rowset aktualisiert werden kann, muss die aktualisierbare Eigenschaft in der Definition der Zeile auf true festgelegt werden. Um z. b. zu definieren, dass die Tabelle "Spediteure" ausstehende Änderungen enthält, sieht die Zeilen Definition wie folgt aus.  
  
```  
<s:ElementType name="row" content="eltOnly" updatable="true">  
  <s:attribute type="ShipperID"/>  
  <s:attribute type="CompanyName"/>  
  <s:attribute type="Phone"/>  
  <s:extends type="rs:rowbase"/>  
</s:ElementType>  
```  
  
 Dadurch wird dem Dauerhaftigkeits Anbieter mitgeteilt, dass Daten angezeigt werden, damit ADO ein Aktualisier bares Recordset-Objekt erstellen kann.  
  
 Die folgenden Beispiel Daten zeigen, wie insertions, Änderungen und Löschungen in der persistenten Datei aussehen.  
  
```  
<rs:data>  
  <z:row ShipperID="2" CompanyName="United Package"   
    Phone="(503) 555-3199"/>  
<rs:update>  
  <rs:original>  
    <z:row ShipperID="3" CompanyName="Federal Shipping"   
      Phone="(503) 555-9931"/>  
  </rs:original>  
  <z:row Phone="(503) 552-7134"/>  
</rs:update>  
<rs:insert>  
  <z:row ShipperID="12" CompanyName="Lightning Shipping"   
    Phone="(505) 111-2222"/>  
  <z:row ShipperID="13" CompanyName="Thunder Overnight"   
    Phone="(505) 111-2222"/>  
  <z:row ShipperID="14" CompanyName="Blue Angel Air Delivery"   
    Phone="(505) 111-2222"/>  
</rs:insert>  
<rs:delete>  
  <z:row ShipperID="1" CompanyName="Speedy Express" Phone="(503) 555-9831"/>  
</rs:delete>  
</rs:data>  
```  
  
 Ein Update enthält immer die gesamten ursprünglichen Zeilendaten, gefolgt von den geänderten Zeilendaten. Die geänderte Zeile enthält möglicherweise alle Spalten oder nur die Spalten, die tatsächlich geändert wurden. Im vorherigen Beispiel wird die Zeile für den shipper2 nicht geändert, und nur die Spalte "Phone" hat Werte für den shipperwert 3 geändert und ist daher die einzige Spalte, die in der geänderten Zeile enthalten ist. Die eingefügten Zeilen für die Lader 12, 13 und 14 werden zusammen mit einem RS: Insert-Tag zusammengefasst. Beachten Sie, dass gelöschte Zeilen auch in einem Batch zusammengefasst werden können, obwohl dies im vorherigen Beispiel nicht gezeigt wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beibehalten von Datensätzen im XML-Format](../../../ado/guide/data/persisting-records-in-xml-format.md)
