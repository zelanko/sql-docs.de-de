---
description: XML-Beibehaltungsformat
title: XML-Persistenzformat | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- XML persistence [ADO], persistence format
ms.assetid: 6e146738-ac4d-47bb-b6cd-d87b2260aead
author: rothja
ms.author: jroth
ms.openlocfilehash: 2da0090b9e06a9df7692a27242a08303174f51aa
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88978831"
---
# <a name="xml-persistence-format"></a>XML-Beibehaltungsformat
ADO verwendet UTF-8-Codierung für den persistent verwendeten XML-Stream.  
  
 Das ADO-XML-Format ist in zwei Abschnitte unterteilt: ein Schema Abschnitt, auf den der Daten Abschnitt folgt. Im folgenden finden Sie eine XML-Beispieldatei für die Tabelle "Spediteure" aus der Datenbank "Northwind". Im folgenden Beispiel werden verschiedene Teile des XML-Codes erläutert.  
  
## <a name="remarks"></a>Bemerkungen  
  
```  
<xml xmlns:s="uuid:BDC6E3F0-6DA3-11d1-A2A3-00AA00C14882"   
xmlns:dt="uuid:C2F41010-65B3-11d1-A29F-00AA00C14882"   
xmlns:rs="urn:schemas-microsoft-com:rowset"   
xmlns:z="#RowsetSchema">   
  <s:Schema id="RowsetSchema">   
    <s:ElementType name="row" content="eltOnly" rs:updatable="true">   
      <s:AttributeType name="ShipperID" rs:number="1"   
        rs:basetable="shippers" rs:basecolumn="ShipperID"  
        rs:keycolumn="true">   
        <s:datatype dt:type="int" dt:maxLength="4" rs:precision="10"   
          rs:fixedlength="true" rs:maybenull="false"/>   
      </s:AttributeType>   
      <s:AttributeType name="CompanyName" rs:number="2"   
        rs:nullable="true" rs:write="true" rs:basetable="shippers"   
        rs:basecolumn="CompanyName">   
        <s:datatype dt:type="string" dt:maxLength="40" />   
      </s:AttributeType>   
      <s:AttributeType name="Phone" rs:number="3" rs:nullable="true"   
        rs:write="true" rs:basetable="shippers"   
        rs:basecolumn="Phone">   
        <s:datatype dt:type="string" dt:maxLength="24"/>   
      </s:AttributeType>   
      <s:extends type="rs:rowbase"/>   
    </s:ElementType>   
  </s:Schema>   
  
  <rs:data>   
    <z:row ShipperID="1" CompanyName="Speedy Express"   
      Phone="(503) 555-9831"/>   
    <z:row ShipperID="2" CompanyName="United Package"   
      Phone="(503) 555-3199"/>   
    <z:row ShipperID="3" CompanyName="Federal Shipping"   
      Phone="(503) 555-9931"/>   
  </rs:data>   
</xml>  
```  
  
 Das Schema zeigt die Deklarationen von Namespaces, den Abschnitt "Schema" und den Abschnitt "Data". Der Abschnitt Schema enthält Definitionen für "Row", "ShipperID", "CompanyName" und "Phone".  
  
 Schema Definitionen entsprechen der [W3C-XML-Daten Spezifikation](http://www.w3.org/TR/1998/NOTE-XML-data/) und können vollständig überprüft werden (obwohl die Validierung in Internet Explorer 5 nicht erfolgt). XML-Data ist derzeit das einzige unterstützte Schema Format für die recordsetpersistenz.  
  
 Der Daten Abschnitt enthält drei Zeilen, die Informationen über die Verlader enthalten. Für ein leeres Rowset ist der Daten Abschnitt möglicherweise leer, aber die \<rs:data> Tags müssen vorhanden sein. Wenn keine Daten angezeigt werden, können Sie die tagkurzform einfach schreiben \<rs:data/> . Jedes Tag mit dem Präfix "RS" weist darauf hin, dass es sich im Namespace befindet, der durch "urn: Schemas-Microsoft-com: Rowset" definiert ist.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beibehalten von Datensätzen im XML-Format](./persisting-records-in-xml-format.md)