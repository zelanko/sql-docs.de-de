---
title: Schema-Abschnitt | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Schema section [ADO]
ms.assetid: 4ac6e524-2c92-48e8-b871-0a4b5c8fda18
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 45e8e37d8bb85e727771072abda9249b8155076f
ms.sourcegitcommit: bfa10c54e871700de285d7f819095d51ef70d997
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2019
ms.locfileid: "54256195"
---
# <a name="schema-section"></a>Schemaabschnitt
Schema-Abschnitt ist erforderlich. Wie im vorherige Beispiel gezeigt wird, schreibt ADO detaillierter Metadaten zu jeder Spalte, um die Semantik der Datenwerte für die Aktualisierung so weit wie möglich beizubehalten. Allerdings erfordert um in der XML-Code zu laden, ADO nur die Namen der Spalten und das Rowset, das sie angehören. Hier ist ein Beispiel für ein Schema "minimal":  
  
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
  
 Im vorherigen Beispiel wird ADO die Daten als Zeichenfolgen mit variabler Länge behandelt, da keine Typinformationen im Schema enthalten ist.  
  
## <a name="creating-aliases-for-column-names"></a>Erstellen Aliase für Spaltennamen  
 Das Rs: Name-Attribut können Sie einen Alias für den Namen einer Spalte zu erstellen, sodass ein Anzeigename möglicherweise, in die Spalteninformationen, die vom Rowset verfügbar gemacht angezeigt, und ein kürzerer Namen kann, im Data-Abschnitt verwendet werden. Beispielsweise kann das vorherige Schema geändert werden, s1, CompanyName auf s2 Herunterskalieren, Firmen-Nr zuordnen und Phone s3 wie folgt:  
  
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
  
 Klicken Sie dann würde im Datenabschnitt die Zeile das Name-Attribut (nicht Rs: Name) verwenden, an diese Spalte verweisen:  
  
```  
"<row s1="1" s2="Speedy Express" s3="(503) 555-9831"/>  
```  
  
 Erstellen Aliase für Spaltennamen ist erforderlich, wenn ein Spaltenname kein gültiges Attribut oder in XML-Tagnamen ist. Z. B. "LastName" einen Alias besitzen muss, da Namen mit Leerzeichen ungültige Attribute sind. Die folgende Zeile wird nicht ordnungsgemäß durch den XML-Parser behandelt werden, daher müssen Sie einen Alias in einen anderen Namen erstellen, die nicht über ein eingebettetes Leerzeichen verfügt.  
  
```  
<row last name="Jones"/>  
```  
  
 Der Wert, den Sie für das Name-Attribut verwenden, muss konsistent an jeder Stelle verwendet werden, dass die Spalte in Abschnitten das XML-Dokument dem Schema und die Daten verwiesen wird. Das folgende Beispiel zeigt die konsistente Verwendung von s1:  
  
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
  
 Auf ähnliche Weise, da es ist kein Alias definiert für `CompanyName` im vorherigen Beispiel `CompanyName` muss konsistent im gesamten Dokument verwendet werden.  
  
## <a name="data-types"></a>Datentypen  
 Sie können einen Datentyp an eine Spalte mit dem dt: Type-Attribut anwenden. Das umfassende Handbuch zu zulässige XML-Datentypen, finden Sie im Abschnitt "Datentypen" von der [W3C XML-Data-Spezifikation](http://www.w3.org/TR/1998/NOTE-XML-data/). Sie können einen Datentyp angeben, gibt es zwei Möglichkeiten: das dt: Type-Attribut direkt auf die Definition der Spalte selbst angeben, oder verwenden Sie das Konstrukt S:datatype als ein geschachteltes Element der Spaltendefinition. Beispiel:  
  
```  
<s:AttributeType name="Phone" >  
  <s:datatype dt:type="string"/>  
</s:AttributeType>  
```  
  
 ist gleich  
  
```  
<s:AttributeType name="Phone" dt:type="string"/>  
```  
  
 Wenn Sie das dt: Type-Attribut, vollständig aus der Zeilendefinition, in der Standardeinstellung weglassen, werden den Datentyp der Spalte eine Zeichenfolge variabler Länge.  
  
 Wenn Sie weitere Informationen als einfach den Typnamen (z. B. dt: MaxLength) verfügen, ist es besser lesbar ist, verwenden Sie das S:datatype untergeordnete Element. Dies ist lediglich eine Konvention, allerdings und nicht erforderlich.  
  
 Die folgenden Beispiele zeigen weitere Vorgehensweise Typinformationen in das Schema einfügen.  
  
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
  
 Es ist eine geringfügige Verwendung des Rs: Fixedlength-Attributs im zweiten Beispiel. Legen Sie eine Spalte mit dem Rs: Fixedlength-Attribut auf "true" bedeutet, dass die Daten die im Schema definierte Länge müssen. In diesem Fall wird ein gültiger Wert für Title_id "123456," unverändert "123". Allerdings würde "123" nicht gültig sein, da seine Länge 3, nicht 6 ist. Finden Sie in der OLE DB Programmer's Guide für eine Beschreibung der Eigenschaft Fixedlength abzuschließen.  
  
## <a name="handling-nulls"></a>Behandeln von NULL-Werte  
 NULL-Werte werden durch das Attribut Rs: Maybenull verarbeitet. Wenn dieses Attribut festgelegt ist, auf "true", den Inhalt der Spalte einen null-Wert enthalten können. Darüber hinaus, wenn die Spalte in einer Zeile der Daten nicht gefunden wird, wird der Benutzer, die Lesen der Daten wieder aus dem Rowset einen null-Status aus IRowset::GetData() abrufen. Erwägen Sie die folgenden Definitionen der Spalten aus der Shippers-Tabelle.  
  
```  
<s:AttributeType name="ShipperID">  
  <s:datatype dt:type="int" dt:maxLength="4"/>  
</s:AttributeType>  
<s:AttributeType name="CompanyName">  
  <s:datatype dt:type="string" dt:maxLength="40" rs:maybenull="true"/>  
</s:AttributeType>  
```  
  
 Ermöglicht die Definition `CompanyName` null ist, ist aber `ShipperID` darf keinen null-Wert enthalten. Wenn Data-Abschnitt die folgende Zeile enthält, würde der Persistenz-Provider Festlegen des Status der Daten für die `CompanyName` Spalte in der OLE DB-Status-Konstante DBSTATUS_S_ISNULL:  
  
```  
<z:row ShipperID="1"/>  
```  
  
 Wenn die Zeile wie folgt vollständig leer war, würde der Persistenz-Provider DBSTATUS_E_UNAVAILABLE für OLE DB-Status zurückgeben `ShipperID` und DBSTATUS_S_ISNULL für CompanyName.  
  
```  
<z:row/>   
```  
  
 Beachten Sie, dass eine Zeichenfolge der Länge 0 (null) nicht identisch mit Null ist.  
  
```  
<z:row ShipperID="1" CompanyName=""/>  
```  
  
 Der vorherigen Zeile und gibt den Persistenz-Provider OLE DB-Status DBSTATUS_S_OK für beide Spalten zurück. Die `CompanyName` einfach in diesem Fall ist "" (eine Zeichenfolge der Länge 0 (null)).  
  
 Weitere Informationen zu den OLE DB zur Verwendung innerhalb des Schemas eines XML-Dokuments für OLE DB-Konstrukte, finden Sie unter der Definition von "Urn: Schemas-Microsoft-Com:rowset" und der OLE DB Programmer's Guide.  
  
## <a name="see-also"></a>Siehe auch  
 [Beibehalten von Datensätzen im XML-Format](../../../ado/guide/data/persisting-records-in-xml-format.md)
