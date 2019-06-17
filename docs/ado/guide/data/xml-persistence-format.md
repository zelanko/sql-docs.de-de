---
title: XML Persistenzformat | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- XML persistence [ADO], persistence format
ms.assetid: 6e146738-ac4d-47bb-b6cd-d87b2260aead
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 49a3c276aa17d8f2bd7f48296eeecb69ad91d04d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66718369"
---
# <a name="xml-persistence-format"></a>XML-Beibehaltungsformat
ADO verwendet die UTF-8-Codierung für die XML-Datenstrom.  
  
 Das ADO-XML-Format wird in zwei Abschnitte, einen Schemaabschnitt, gefolgt von dem Datenbereich aufgeteilt. Folgendes ist eine XML-Beispieldatei für die Shippers-Tabelle aus der Northwind-Datenbank. Verschiedene Teile der XML-Code werden dem Beispiel erläutert.  
  
## <a name="remarks"></a>Hinweise  
  
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
  
 Das Schema zeigt die Deklarationen des Namespaces, Schemaabschnitt und Data-Abschnitt. Schema-Abschnitt enthält die Definitionen für die Zeile, Firmen-Nr, CompanyName und Telefon.  
  
 Schemadefinitionen entsprechen den [W3C XML-Data-Spezifikation](http://www.w3.org/TR/1998/NOTE-XML-data/) und können überprüft werden, vollständig (auch wenn die Validierung nicht in Internet Explorer 5 erfolgt). XML-Daten ist derzeit das einzige unterstützte Schemaformat für Recordset-Beibehaltung.  
  
 Data-Abschnitt enthält drei Zeilen, die mit Informationen zu Lieferanten. Für ein leeres Rowset, Data-Abschnitt kann leer sein, aber die \<Rs: Data >-Tags müssen vorhanden sein. Ohne Daten, könnten Sie einfach das Tag die Kurzform schreiben \<Rs: Daten-/ >. Alle Tags, die mit dem Präfix "Rs" gibt an, dass es in das vom Urn: Schemas definierten Namespace-Microsoft-Com:rowset.  
  
## <a name="see-also"></a>Siehe auch  
 [Beibehalten von Datensätzen im XML-Format](../../../ado/guide/data/persisting-records-in-xml-format.md)
