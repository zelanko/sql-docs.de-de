---
description: Schemaabschnitt
title: Schema Abschnitt | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Schema section [ADO]
ms.assetid: 4ac6e524-2c92-48e8-b871-0a4b5c8fda18
author: rothja
ms.author: jroth
ms.openlocfilehash: a1f294e9c0258f1cc9d108d1eb9a47087b456ca8
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88979721"
---
# <a name="schema-section"></a>Schemaabschnitt
Der Abschnitt "Schema" ist erforderlich. Wie das vorherige Beispiel zeigt, schreibt ADO ausführliche Metadaten zu jeder Spalte, um die Semantik der Datenwerte so weit wie möglich für die Aktualisierung beizubehalten. Zum Laden des XML-Codes erfordert ADO jedoch nur die Namen der Spalten und des Rowsets, zu dem Sie gehören. Im folgenden finden Sie ein Beispiel für ein minimales Schema:  
  
```  
<xml xmlns:s="uuid:BDC6E3F0-6DA3-11d1-A2A3-00AA00C14882"  
    xmlns:rs="urn:schemas-microsoft-com:rowset"  
    xmlns:z="#RowsetSchema">  
  <s:Schema id="RowsetSchema">  
    <s:ElementType name="row" content="eltOnly">  
      <s:AttributeType name="ShipperID"/>  
      <s:AttributeType name="CompanyName"/>  
      <s:AttributeType name="Phone"/>  
      <s:Extends type="rs:rowbase"/>  
    </s:ElementType>  
  </s:Schema>  
  <rs:data>  
...  
  </rs:data>  
</xml>  
```  
  
 Im vorherigen Beispiel behandelt ADO die Daten als Zeichen folgen mit variabler Länge, da keine Typinformationen im Schema enthalten sind.  
  
## <a name="creating-aliases-for-column-names"></a>Erstellen von Aliasen für Spaltennamen  
 Das RS: Name-Attribut ermöglicht es Ihnen, einen Alias für einen Spaltennamen zu erstellen, damit ein Anzeige Name in den vom Rowset verfügbar gemachten Spalten Informationen angezeigt werden kann und im Daten Abschnitt ein kürzerer Name verwendet werden kann. Beispielsweise könnte das vorherige Schema geändert werden, um ShipperID S1, CompanyName zu S2 und das Telefon an S3 wie folgt zuzuordnen:  
  
```  
<s:Schema id="RowsetSchema">   
<s:ElementType name="row" content="eltOnly" rs:updatable="true">   
<s:AttributeType name="s1" rs:name="ShipperID" rs:number="1" ...>   
...  
</s:AttributeType>   
<s:AttributeType name="s2" rs:name="CompanyName" rs:number="2" ...>   
...  
</s:AttributeType>   
<s:AttributeType name="s3" rs:name="Phone" rs:number="3" ...>   
...  
</s:AttributeType>   
...  
</s:ElementType>   
</s:Schema>  
```  
  
 Anschließend verwendet die Zeile im Daten Abschnitt das Name-Attribut (nicht RS: Name), um auf diese Spalte zu verweisen:  
  
```  
"<row s1="1" s2="Speedy Express" s3="(503) 555-9831"/>  
```  
  
 Das Erstellen von Aliasen für Spaltennamen ist erforderlich, wenn ein Spaltenname kein gültiger Attribut-oder Tagname in XML ist. Beispielsweise muss "LastName" einen Alias aufweisen, da Namen mit eingebetteten Leerzeichen ungültige Attribute sind. Die folgende Zeile wird vom XML-Parser nicht ordnungsgemäß behandelt, daher müssen Sie einen Alias für einen anderen Namen erstellen, der nicht über ein eingebettetes Leerzeichen verfügt.  
  
```  
<row last name="Jones"/>  
```  
  
 Jeder Wert, den Sie für das Name-Attribut verwenden, muss konsistent an allen Stellen verwendet werden, auf die in den Abschnitten Schema und Daten des XML-Dokuments auf die Spalte verwiesen wird. Das folgende Beispiel zeigt die konsistente Verwendung von S1:  
  
```  
<s:Schema id="RowsetSchema">  
  <s:ElementType name="row" content="eltOnly">  
    <s:attribute type="s1"/>  
    <s:attribute type="CompanyName"/>  
    <s:attribute type="s3"/>  
    <s:extends type="rs:rowbase"/>  
  </s:ElementType>  
  <s:AttributeType name="s1" rs:name="ShipperID" rs:number="1"   
    rs:maydefer="true" rs:writeunknown="true">  
    <s:datatype dt:type="i4" dt:maxLength="4" rs:precision="10"   
      rs:fixedlength="true" rs:maybenull="true"/>  
  </s:AttributeType>  
</s:Schema>  
<rs:data>  
  <z:row s1="1" CompanyName="Speedy Express" s3="(503) 555-9831"/>  
</rs:data>  
```  
  
 Ebenso muss, da im vorherigen Beispiel kein Alias für definiert ist `CompanyName` , im `CompanyName` gesamten Dokument konsistent verwendet werden.  
  
## <a name="data-types"></a>Datentypen  
 Sie können einen Datentyp auf eine Spalte mit dem dt: Type-Attribut anwenden. Das definitive Handbuch zu zulässigen XML-Typen finden Sie im Abschnitt "Datentypen" der [W3C-Spezifikation für XML-Daten](http://www.w3.org/TR/1998/NOTE-XML-data/). Sie können einen Datentyp auf zwei Arten angeben: Geben Sie entweder das dt: Type-Attribut direkt für die Spaltendefinition selbst an, oder verwenden Sie das Konstrukt s:datatype als gescheites Element der Spaltendefinition. Beispiel:  
  
```  
<s:AttributeType name="Phone" >  
  <s:datatype dt:type="string"/>  
</s:AttributeType>  
```  
  
 für die folgende Syntax:  
  
```  
<s:AttributeType name="Phone" dt:type="string"/>  
```  
  
 Wenn Sie das dt: Type-Attribut vollständig aus der Zeilen Definition weglassen, ist der Typ der Spalte standardmäßig eine Zeichenfolge variabler Länge.  
  
 Wenn Sie mehr Typinformationen als einfach den Typnamen haben (z. b. dt: maxLength), ist es besser lesbar, das untergeordnete s:DataType-Element zu verwenden. Dies ist jedoch lediglich eine Konvention und keine Anforderung.  
  
 In den folgenden Beispielen wird gezeigt, wie Typinformationen in das Schema eingeschlossen werden.  
  
```  
<!-- 1. String with no max length -->  
<s:AttributeType name="title_id"/>  
<!-or -->  
<s:AttributeType name="title_id" dt:type="string"/>  
  
<!-- 2. Fixed length string with max length of 6 -->  
<s:AttributeType name="title_id">  
    <s:datatype dt:type="string" dt:maxLength="6" rs:fixedlength="true" />  
</s:AttributeType>  
  
<!-- 3. Variable length string with max length of 6 -->  
<s:AttributeType name="title_id">  
    <s:datatype dt:type="string" dt:maxLength="6" />  
</s:AttributeType>  
  
<!-- 4. Integer -->  
<s:AttributeType name="title_id" dt:type="int"/>  
```  
  
 Es gibt eine feine Verwendung des RS: FixedLength-Attributs im zweiten Beispiel. Eine Spalte, deren RS: FixedLength-Attribut auf "true" festgelegt ist, bedeutet, dass die Daten die im Schema definierte Länge aufweisen müssen. In diesem Fall ist ein gültiger Wert für title_id "123456", wie z. h. "123". "123" ist jedoch nicht gültig, da die Länge 3 und nicht 6 beträgt. Eine ausführlichere Beschreibung der FixedLength-Eigenschaft finden Sie im OLE DB Programmierer-Handbuch.  
  
## <a name="handling-nulls"></a>Behandeln von NULL-Werten  
 NULL-Werte werden vom RS: maybenull-Attribut behandelt. Wenn dieses Attribut auf true festgelegt ist, kann der Inhalt der Spalte einen NULL-Wert enthalten. Wenn die Spalte in einer Daten Zeile nicht gefunden wird, erhält der Benutzer, der die Daten aus dem Rowset liest, einen NULL-Status von IRowset:: GetData (). Sehen Sie sich die folgenden Spaltendefinitionen aus der Tabelle "Spediteure" an.  
  
```  
<s:AttributeType name="ShipperID">  
  <s:datatype dt:type="int" dt:maxLength="4"/>  
</s:AttributeType>  
<s:AttributeType name="CompanyName">  
  <s:datatype dt:type="string" dt:maxLength="40" rs:maybenull="true"/>  
</s:AttributeType>  
```  
  
 Die Definition lässt `CompanyName` null zu, darf aber keinen `ShipperID` NULL-Wert enthalten. Wenn der Daten Abschnitt die folgende Zeile enthält, legt der Persistenzanbieter den Status der Daten für die `CompanyName` Spalte auf die OLE DB Status Konstante DBSTATUS_S_ISNULL:  
  
```  
<z:row ShipperID="1"/>  
```  
  
 Wenn die Zeile wie folgt vollständig leer war, gibt der Persistenzanbieter den OLE DB Status DBSTATUS_E_UNAVAILABLE für `ShipperID` und DBSTATUS_S_ISNULL für CompanyName zurück.  
  
```  
<z:row/>   
```  
  
 Beachten Sie, dass eine Zeichenfolge der Länge 0 (null) nicht identisch ist.  
  
```  
<z:row ShipperID="1" CompanyName=""/>  
```  
  
 Für die vorangehende Zeile gibt der Persistenzanbieter für beide Spalten einen OLE DB Status DBSTATUS_S_OK zurück. Der `CompanyName` in diesem Fall ist einfach "" (eine Zeichenfolge der Länge 0 (null)).  
  
 Weitere Informationen zu den OLE DB-Konstrukten, die zur Verwendung innerhalb des Schemas eines XML-Dokuments für OLE DB verfügbar sind, finden Sie in der Definition von "urn: Schemas-Microsoft-com: Rowset" und im OLE DB Programmierer-Handbuch.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beibehalten von Datensätzen im XML-Format](../../../ado/guide/data/persisting-records-in-xml-format.md)
