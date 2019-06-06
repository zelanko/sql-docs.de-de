---
title: Hierarchische Recordsets im XML-Code | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- hierarchical Recordsets [ADO], in XML
ms.assetid: 5d4b11c4-c94f-4910-b99b-5b9abc50d791
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 71b28233d8b687eff803a5897b31b2bc59bbd4e2
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66700626"
---
# <a name="hierarchical-recordsets-in-xml"></a>Hierarchische Recordsets im XML-Format
ADO ermöglicht das Speichern von hierarchischen Recordset-Objekte in XML. Mit hierarchischen Recordset-Objekte ist der Wert eines Felds in der übergeordneten Recordset einen anderen Recordset. Diese Felder werden als untergeordnete Elemente in der XML-Stream anstelle eines Attributs dargestellt.  
  
## <a name="remarks"></a>Hinweise  
 Im folgende Beispiel wird hier veranschaulicht:  
  
```  
Rs.Open "SHAPE {select stor_id, stor_name, state from stores} APPEND ({select stor_id, ord_num, ord_date, qty from sales} AS rsSales RELATE stor_id TO stor_id)", "Provider=MSDataShape;DSN=pubs;Integrated Security=SSPI;"  
```  
  
 Im folgenden finden die XML-Format des beibehaltenen Recordsets:  
  
```  
<xml xmlns:s="uuid:BDC6E3F0-6DA3-11d1-A2A3-00AA00C14882"     xmlns:dt="uuid:C2F41010-65B3-11d1-A29F-00AA00C14882"     xmlns:rs="urn:schemas-microsoft-com:rowset"   
    xmlns:z="#RowsetSchema">   
  <s:Schema id="RowsetSchema">   
    <s:ElementType name="row" content="eltOnly" rs:updatable="true">   
      <s:AttributeType name="stor_id" rs:number="1"   
        rs:writeunknown="true">   
        <s:datatype dt:type="string" dt:maxLength="4"   
          rs:fixedlength="true" rs:maybenull="false"/>   
      </s:AttributeType>   
      <s:AttributeType name="stor_name" rs:number="2" rs:nullable="true"   
        rs:writeunknown="true">   
          <s:datatype dt:type="string" dt:maxLength="40"/>   
      </s:AttributeType>   
      <s:AttributeType name="state" rs:number="3" rs:nullable="true"   
        rs:writeunknown="true">   
        <s:datatype dt:type="string" dt:maxLength="2"   
          rs:fixedlength="true"/>   
      </s:AttributeType>   
      <s:ElementType name="rsSales" content="eltOnly"   
        rs:updatable="true" rs:relation="010000000100000000000000">   
        <s:AttributeType name="stor_id" rs:number="1"   
          rs:writeunknown="true">   
          <s:datatype dt:type="string" dt:maxLength="4"   
            rs:fixedlength="true" rs:maybenull="false"/>   
        </s:AttributeType>   
        <s:AttributeType name="ord_num" rs:number="2"   
          rs:writeunknown="true">   
          <s:datatype dt:type="string" dt:maxLength="20"   
            rs:maybenull="false"/>   
        </s:AttributeType>   
        <s:AttributeType name="ord_date" rs:number="3"   
          rs:writeunknown="true">   
            <s:datatype dt:type="dateTime" dt:maxLength="16"   
              rs:scale="3" rs:precision="23" rs:fixedlength="true"   
              rs:maybenull="false"/>   
        </s:AttributeType>   
        <s:AttributeType name="qty" rs:number="4" rs:writeunknown="true">   
          <s:datatype dt:type="i2" dt:maxLength="2" rs:precision="5"   
            rs:fixedlength="true" rs:maybenull="false"/>   
        </s:AttributeType>   
        <s:extends type="rs:rowbase"/>   
      </s:ElementType>   
      <s:extends type="rs:rowbase"/>   
    </s:ElementType>   
  </s:Schema>   
  <rs:data>   
    <z:row stor_id="6380" stor_name="Eric the Read Books" state="WA">   
      <rsSales stor_id="6380" ord_num="6871"   
        ord_date="1994-09-14T00:00:00" qty="5"/>   
      <rsSales stor_id="6380" ord_num="722a"   
        ord_date="1994-09-13T00:00:00" qty="3"/>   
    </z:row>   
    <z:row stor_id="7066" stor_name="Barnum's" state="CA">   
      <rsSales stor_id="7066" ord_num="A2976"   
        ord_date="1993-05-24T00:00:00" qty="50"/>   
      <rsSales stor_id="7066" ord_num="QA7442.3"   
        ord_date="1994-09-13T00:00:00" qty="75"/>   
    </z:row>   
    <z:row stor_id="7067" stor_name="News & Brews" state="CA">   
      <rsSales stor_id="7067" ord_num="D4482"   
        ord_date="1994-09-14T00:00:00" qty="10"/>   
      <rsSales stor_id="7067" ord_num="P2121"   
        ord_date="1992-06-15T00:00:00" qty="40"/>   
      <rsSales stor_id="7067" ord_num="P2121"   
        ord_date="1992-06-15T00:00:00" qty="20"/>   
      <rsSales stor_id="7067" ord_num="P2121"   
        ord_date="1992-06-15T00:00:00" qty="20"/>   
    </z:row>   
  </rs:data>   
</xml>   
```  
  
 Die genaue Reihenfolge der Spalten in übergeordneten Recordset-Objekts ist nicht offensichtlich, wenn diese auf diese Weise gespeichert werden. Jedes Feld in das übergeordnete Element kann ein untergeordnetes Element Recordset enthalten. Der Persistenz-Provider speichert alle skalaren Spalten zuerst als Attribute und klicken Sie dann alle untergeordneten Recordsets "Spalten" als untergeordnete Elemente der übergeordneten Zeile speichert. Die Ordnungsposition des Felds im übergeordneten kann Recordset anhand der Schemadefinition des Recordset-Objekts abgerufen werden. Jedes Feld hat eine OLE DB-Eigenschaft Rs: Anzahl, definiert in den Recordset-Schemanamespace, der die Ordinalzahl für dieses Feld enthält.  
  
 Mit dem Namen des Felds im übergeordneten Recordset-Objekts, die dieses untergeordnete Element enthält, werden die Namen aller Felder in der untergeordneten Recordsets verkettet. Dadurch wird sichergestellt, dass keine Namenskonflikte in Fällen, in dem übergeordneten und untergeordneten Recordsets, die sowohl ein Feld enthalten, die aus zwei verschiedenen Tabellen abgerufen wird, aber ausschließlich mit dem Namen ist, vorhanden sind.  
  
 Wenn hierarchische Recordsets in XML speichern möchten, sollten Sie in ADO die folgenden Einschränkungen bewusst sein:  
  
-   Ein hierarchisches Recordset mit ausstehenden Updates kann in XML gespeichert werden.  
  
-   Ein hierarchisches Recordset, das mit einem parametrisierten Shape-Befehl erstellt kann (im XML- oder ADTG-Format) gespeichert werden.  
  
-   ADO wird derzeit die Beziehung zwischen übergeordneten und untergeordneten Recordsets als ein binary large Object (BLOB) gespeichert. XML-Tags zur Beschreibung dieser Beziehung verfügen noch nicht in der Rowset-Schema-Namespace definiert.  
  
-   Wenn ein hierarchisches Recordset gespeichert wird, werden alle untergeordneten Recordsets mit gespeichert. Wenn das aktuelle Recordset ein untergeordnetes Element von einem anderen Recordset ist, wird das übergeordnete Element nicht gespeichert werden. Alle untergeordneten Recordsets, die die Teilstruktur des aktuellen Recordset bilden gespeichert.  
  
 Wenn ein hierarchisches Recordset aus dem Format XML gespeichert erneut geöffnet wird Ihnen die folgenden Einschränkungen bewusst sein müssen:  
  
-   Wenn der Datensatz untergeordnete Datensätze enthält, für die keine entsprechenden übergeordneten Datensätze vorhanden sind, werden diese Zeilen nicht in der XML-Darstellung des hierarchischen Recordsets geschrieben. Daher verloren diese Zeilen, wenn das Recordset vom persistenten Speicherort erneut geöffnet wird.  
  
-   Wenn ein untergeordneter Datensatz Verweise auf mehr als einem übergeordneten Datensatz verfügt, kann dann bei erneutem Öffnen des Recordsets, untergeordneten Recordsets doppelte Datensätze enthalten. Aber werden diese Duplikate nur angezeigt, wenn der Benutzer direkt mit dem zugrunde liegenden untergeordneten Rowset arbeitet. Wenn ein Kapitel, das untergeordnete Element Recordset zu navigieren (die die einzige Möglichkeit zum Navigieren in ADO ist) verwendet wird, sind die Duplikate nicht sichtbar.  
  
## <a name="see-also"></a>Siehe auch  
 [Beibehalten von Datensätzen im XML-Format](../../../ado/guide/data/persisting-records-in-xml-format.md)
