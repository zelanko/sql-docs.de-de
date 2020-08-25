---
description: Hierarchische Recordsets im XML-Format
title: Hierarchische Recordsets in XML | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 3e6180c8aa422c5833234afba7881a1a4c8b9049
ms.sourcegitcommit: 33e774fbf48a432485c601541840905c21f613a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88806016"
---
# <a name="hierarchical-recordsets-in-xml"></a>Hierarchische Recordsets im XML-Format
ADO ermöglicht die Persistenz hierarchischer Recordsetobjekte in XML. Bei hierarchischen recordsetobjekten ist der Wert eines Felds im übergeordneten Recordset ein weiteres Recordset. Diese Felder werden als untergeordnete Elemente im XML-Stream anstelle eines Attributs dargestellt.  
  
## <a name="remarks"></a>Bemerkungen  
 Im folgenden Beispiel wird dieser Fall veranschaulicht:  
  
```  
Rs.Open "SHAPE {select stor_id, stor_name, state from stores} APPEND ({select stor_id, ord_num, ord_date, qty from sales} AS rsSales RELATE stor_id TO stor_id)", "Provider=MSDataShape;DSN=pubs;Integrated Security=SSPI;"  
```  
  
 Im folgenden finden Sie das XML-Format des beibehaltenen Recordsets:  
  
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
  
 Die genaue Reihenfolge der Spalten im übergeordneten Recordset ist nicht offensichtlich, wenn Sie auf diese Weise persistent gespeichert wird. Jedes Feld in der übergeordneten kann ein untergeordnetes Recordset enthalten. Der Persistenzanbieter behält alle skalaren Spalten zuerst als Attribute bei und speichert dann alle untergeordneten Recordset-Spalten als untergeordnete Elemente der übergeordneten Zeile. Die Ordinalposition des Felds im übergeordneten Recordset kann durch betrachten der Schema Definition des Recordsets abgerufen werden. Jedes Feld verfügt über eine OLE DB-Eigenschaft RS: Number, die im Recordset-Schema Namespace definiert ist, der die Ordinalzahl für dieses Feld enthält.  
  
 Die Namen aller Felder im untergeordneten Recordset werden mit dem Namen des Felds im übergeordneten Recordset verkettet, das dieses untergeordnete Recordset enthält. Dadurch wird sichergestellt, dass es keine Namenskonflikte gibt, wenn übergeordnete und untergeordnete Recordsets beide ein Feld enthalten, das aus zwei verschiedenen Tabellen abgerufen wird, aber als Singular benannt wird.  
  
 Wenn Sie hierarchische Recordsets in XML speichern, sollten Sie die folgenden Einschränkungen in ADO beachten:  
  
-   Ein hierarchisches Recordset mit ausstehenden Updates kann nicht in XML persistent gespeichert werden.  
  
-   Ein hierarchisches Recordset, das mit einem parametrisierten Shape-Befehl erstellt wurde, kann nicht persistent gespeichert werden (im XML-oder ADTG-Format).  
  
-   ADO speichert die Beziehung zwischen dem übergeordneten und den untergeordneten Recordsets derzeit als Binary Large Object (BLOB). XML-Tags, die diese Beziehung beschreiben, wurden noch nicht im Rowsetschema-Namespace definiert.  
  
-   Beim Speichern eines hierarchischen Recordsets werden alle untergeordneten Recordsets zusammen mit dem Datensatz gespeichert. Wenn das aktuelle Recordset ein untergeordnetes Element eines anderen Recordsets ist, wird das übergeordnete Element nicht gespeichert. Alle untergeordneten Recordsets, die die Teilstruktur des aktuellen Recordsets bilden, werden gespeichert.  
  
 Wenn ein hierarchisches Recordset aus seinem XML-beibehaltenen Format wieder geöffnet wird, müssen Sie die folgenden Einschränkungen beachten:  
  
-   Wenn der untergeordnete Datensatz Datensätze enthält, für die keine entsprechenden übergeordneten Datensätze vorhanden sind, werden diese Zeilen nicht in die XML-Darstellung des hierarchischen Recordsets geschrieben. Diese Zeilen gehen daher verloren, wenn das Recordset von seinem beibehaltenen Speicherort erneut geöffnet wird.  
  
-   Wenn ein untergeordneter Datensatz Verweise auf mehr als einen übergeordneten Datensatz enthält, kann das untergeordnete Recordset beim erneuten Öffnen des Recordsets doppelte Datensätze enthalten. Diese Duplikate werden jedoch nur angezeigt, wenn der Benutzer direkt mit dem zugrunde liegenden untergeordneten Rowset arbeitet. Wenn ein Kapitel verwendet wird, um durch das untergeordnete Recordset zu navigieren (Dies ist die einzige Möglichkeit, durch ADO zu navigieren), sind die Duplikate nicht sichtbar.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beibehalten von Datensätzen im XML-Format](./persisting-records-in-xml-format.md)