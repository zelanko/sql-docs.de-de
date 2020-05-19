---
title: Richtlinien und Einschränkungen für XML-Massen laden (SQLXML 4,0) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XML Bulk Load [SQLXML], about XML Bulk Load
- bulk load [SQLXML], about bulk load
ms.assetid: c5885d14-c7c1-47b3-a389-455e99a7ece1
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 593e51e34be3b607af121bfcba92497e019eba3f
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/01/2020
ms.locfileid: "82703378"
---
# <a name="guidelines-and-limitations-of-xml-bulk-load-sqlxml-40"></a>Richtlinien und Einschränkungen von XML-Massenladen (SQLXML 4.0)
  Wenn Sie XML-Massenladen verwenden, sollten Sie mit den folgenden Richtlinien und Einschränkungen vertraut sein:  
  
-   Inlineschemas werden nicht unterstützt.  
  
     Wenn im XML-Quelldokument ein Inlineschema vorhanden ist, wird dieses Schema von XML-Massenladen ignoriert. Sie geben das Zuordnungsschema für XML-Massenladen außerhalb der XML-Daten an. Sie können das Zuordnungsschema nicht mit dem **xmlns = "x:Schema"** -Attribut auf einem Knoten angeben.  
  
-   Es wird überprüft, ob ein XML-Dokument wohlgeformt ist, es wird jedoch nicht überprüft, ob es gültig ist.  
  
     XML-Massen laden überprüft das XML-Dokument, um zu bestimmen, ob es wohl geformt ist, d. h., um sicherzustellen, dass der XML-Code den Syntax Anforderungen der XML 1,0-Empfehlung des World Wide Web Consortium entspricht. Wenn das Dokument nicht wohlgeformt ist, wird die Verarbeitung durch XML-Massenladen abgebrochen und ein Fehler zurückgegeben. Die einzige Ausnahme hierbei stellen Dokumente dar, bei denen es sich um Fragmente handelt (wenn das Dokument beispielsweise kein einzelnes Stammelement aufweist). In diesem Fall wird das Dokument durch XML-Massenladen geladen.  
  
     XML-Massenladen überprüft das Dokument nicht im Hinblick auf XML-Daten oder DTD-Schemas, die in der XML-Datendatei definiert sind oder auf die in der XML-Datendatei verwiesen wird. XML-Massenladen überprüft die XML-Datendatei auch nicht im Hinblick auf das bereitgestellte Zuordnungsschema.  
  
-   Alle XML-Prologinformationen werden ignoriert.  
  
     Beim XML-Massen laden werden alle Informationen vor und nach dem \< root>-Element im XML-Dokument ignoriert. XML-Massenladen ignoriert beispielsweise sämtliche XML-Deklarationen, internen DTD-Definitionen, externen DTD-Verweise, Kommentare usw.  
  
-   Bei einem Zuordnungsschema, das eine Primärschlüssel-Fremdschlüssel-Beziehung zwischen zwei Tabellen (wie etwa zwischen den Tabellen Customer und CustOrder) definiert, muss die Tabelle mit dem Primärschlüssel im Schema zuerst beschrieben werden. Die Tabelle mit der Fremdschlüsselspalte muss später im Schema angezeigt werden. Der Grund hierfür ist, dass die Reihenfolge, in der die Tabellen im Schema identifiziert werden, die Reihenfolge ist, in der Sie in die Datenbank geladen werden. Das folgende XDR-Schema erzeugt z. b. einen Fehler, wenn es beim XML-Massen Laden verwendet wird, da das ** \< Order>** -Element vor dem ** \< Customer>** -Element beschrieben wird. Die Spalte CustomerID in der Tabelle CustOrder ist eine Fremdschlüsselspalte, die auf die Primärschlüsselspalte CustomerID in der Tabelle Cust verweist.  
  
    ```  
    <?xml version="1.0" ?>  
    <Schema xmlns="urn:schemas-microsoft-com:xml-data"   
            xmlns:dt="urn:schemas-microsoft-com:xml:datatypes"    
            xmlns:sql="urn:schemas-microsoft-com:xml-sql" >  
  
        <ElementType name="Order" sql:relation="CustOrder" >  
          <AttributeType name="OrderID" />  
          <AttributeType name="CustomerID" />  
          <attribute type="OrderID" />  
          <attribute type="CustomerID" />  
        </ElementType>  
  
       <ElementType name="CustomerID" dt:type="int" />  
       <ElementType name="CompanyName" dt:type="string" />  
       <ElementType name="City" dt:type="string" />  
  
       <ElementType name="root" sql:is-constant="1">  
          <element type="Customers" />  
       </ElementType>  
       <ElementType name="Customers" sql:relation="Cust"   
                         sql:overflow-field="OverflowColumn"  >  
          <element type="CustomerID" sql:field="CustomerID" />  
          <element type="CompanyName" sql:field="CompanyName" />  
          <element type="City" sql:field="City" />  
          <element type="Order" >   
               <sql:relationship  
                   key-relation="Cust"  
                    key="CustomerID"  
                    foreign-key="CustomerID"  
                    foreign-relation="CustOrder" />  
          </element>  
       </ElementType>  
    </Schema>  
    ```  
  
-   Wenn im Schema keine Überlaufspalten mithilfe der `sql:overflow-field`-Anmerkung angegeben wurden, ignoriert XML-Massenladen Daten, die zwar im XML-Dokument vorhanden, im Zuordnungsschema jedoch nicht beschrieben sind.  
  
     XML-Massenladen wendet das angegebene Zuordnungsschema an, sobald es im XML-Datenstrom auf bekannte Tags trifft. XML-Massenladen ignoriert Daten, die zwar im XML-Dokument vorhanden, im Schema jedoch nicht beschrieben sind. Nehmen Sie beispielsweise an, Sie verfügen über ein Mapping-Schema, das ein ** \< Customer->** Element beschreibt. Die XML-Datendatei verfügt über ein ** \< AllCustomers>** root-Tag (das im Schema nicht beschrieben ist), das alle ** \< Kunden>** Elemente einschließt:  
  
    ```  
    <AllCustomers>  
      <Customer>...</Customer>  
      <Customer>...</Customer>  
       ...  
    </AllCustomers>  
    ```  
  
     In diesem Fall ignoriert XML-Massen laden das ** \< AllCustomers->** Element und beginnt mit der Zuordnung des ** \< Customer->** Elements. XML-Massenladen ignoriert die Elemente, die zwar im XML-Dokument vorhanden, im Schema jedoch nicht beschrieben sind.  
  
     Angenommen, eine andere XML-Quell Datendatei enthält ** \< Order>** -Elemente. Diese Elemente sind im Zuordnungsschema nicht beschrieben:  
  
    ```  
    <AllCustomers>  
      <Customer>...</Customer>  
        <Order> ... </Order>  
        <Order> ... </Order>  
         ...  
      <Customer>...</Customer>  
        <Order> ... </Order>  
        <Order> ... </Order>  
         ...  
      ...  
    </AllCustomers>  
    ```  
  
     XML-Massen laden ignoriert diese ** \< Reihenfolge>** Elemente. Wenn Sie jedoch die-Anmerkung `sql:overflow-field` im Schema verwenden, um eine Spalte als Überlauf Spalte zu identifizieren, speichert XML-Massen laden alle nicht verbrauchten Daten in dieser Spalte.  
  
-   CDATA-Abschnitte und Entitätsverweise werden vor dem Speichern in der Datenbank in das entsprechende Zeichenfolgenäquivalent übersetzt.  
  
     In diesem Beispiel umschließt ein CDATA-Abschnitt den Wert für das ** \< City->** Element. XML-Massen laden extrahiert den Zeichen folgen Wert ("NY"), bevor das ** \< City>** -Element in die Datenbank eingefügt wird.  
  
    ```  
    <City><![CDATA[NY]]> </City>  
    ```  
  
     XML-Massenladen behält Entitätsverweise nicht bei.  
  
-   Wenn in einem Zuordnungsschema der Standardwert eines Attributs angegeben ist, verwendet XML-Massenladen dieses Attribut, auch wenn das Attribut in den XML-Quelldaten nicht enthalten ist.  
  
     Das folgende XDR-Beispiel Schema weist dem **HireDate** -Attribut einen Standardwert zu:  
  
    ```  
    <?xml version="1.0" ?>  
    <Schema xmlns="urn:schemas-microsoft-com:xml-data"   
            xmlns:dt="urn:schemas-microsoft-com:xml:datatypes"    
            xmlns:sql="urn:schemas-microsoft-com:xml-sql" >  
       <ElementType name="root" sql:is-constant="1">  
          <element type="Customers" />  
       </ElementType>  
  
       <ElementType name="Customers" sql:relation="Cust3" >  
          <AttributeType name="CustomerID" dt:type="int"  />  
          <AttributeType name="HireDate"  default="2000-01-01" />  
          <AttributeType name="Salary"   />  
  
          <attribute type="CustomerID" sql:field="CustomerID" />  
          <attribute type="HireDate"   sql:field="HireDate"  />  
          <attribute type="Salary"     sql:field="Salary"    />  
       </ElementType>  
    </Schema>  
    ```  
  
     In diesen XML-Daten fehlt das **HireDate** -Attribut in den zweiten ** \< Kunden>** -Elements. Wenn beim XML-Massen laden die zweiten ** \< Kunden>** -Element in die Datenbank eingefügt werden, wird der im Schema angegebene Standardwert verwendet.  
  
    ```  
    <ROOT>  
      <Customers CustomerID="1" HireDate="1999-01-01" Salary="10000" />  
      <Customers CustomerID="2" Salary="10000" />  
    </ROOT>  
    ```  
  
-   Die `sql:url-encode`-Anmerkung wird nicht unterstützt:  
  
     Eine in der XML-Dateneingabe angegebene URL wird von Massenladen an diesem Speicherort nicht gelesen.  
  
     Die im Zuordnungsschema angegebenen Tabellen werden erstellt (die Datenbank muss vorhanden sein). Wenn eine oder mehrere Tabellen bereits in der Datenbank vorhanden sind, bestimmt die SGDropTables-Eigenschaft, ob diese bereits vorhandenen Tabellen gelöscht und neu erstellt werden sollen.  
  
-   Wenn Sie die SchemaGen-Eigenschaft angeben (z. b. SchemaGen = true), werden die Tabellen erstellt, die im Mapping-Schema identifiziert werden. SchemaGen erstellt jedoch keine Einschränkungen (z. b. die PRIMARY KEY/FOREIGN KEY-Einschränkungen) für diese Tabellen mit einer Ausnahme: Wenn die XML-Knoten, die den Primärschlüssel in einer Beziehung bilden, als XML-Typ der ID definiert sind (d. h. `type="xsd:ID"` für XSD) und die SGUseID-Eigenschaft für SchemaGen auf true festgelegt ist, werden nicht nur Primärschlüssel aus den typisierten ID-Knoten erstellt, sondern es werden Primärschlüssel-/Fremdschlüssel Beziehungen aus Zuordnungsschema Beziehungen erstellt  
  
-   SchemaGen verwendet keine XSD-Schema Facetten und-Erweiterungen zum Generieren des relationalen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Schemas.  
  
-   Wenn Sie die SchemaGen-Eigenschaft (z. b. SchemaGen = true) beim Massen Laden angeben, werden nur die angegebenen Tabellen (und keine Sichten des freigegebenen namens) aktualisiert.  
  
-   SchemaGen stellt nur grundlegende Funktionen zum Erstellen des relationalen Schemas aus XSD mit Anmerkungen bereit. Der Benutzer muss die generierten Tabellen ggf. manuell ändern.  
  
-   Wenn zwischen Tabellen mehr als eine Beziehung besteht, versucht SchemaGen, eine einzelne Beziehung zu erstellen, die alle Schlüssel enthält, die zwischen den beiden Tabellen beteiligt sind. Diese Einschränkung kann die Ursache eines [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Fehlers sein.  
  
-   Beim Massenladen von XML-Daten in eine Datenbank muss mindestens ein Attribut oder ein untergeordnetes Element im Zuordnungsschema vorhanden sein, das einer Datenbankspalte zugeordnet ist.  
  
-   Wenn Sie Datenwerte mithilfe von XML-Massenladen einfügen, müssen die Werte im Format (-)CCYY-MM-DD((+-)TZ) angegeben werden. Dies ist das XSD-Standardformat für das Datum.  
  
-   Einige Eigenschaftenflags sind mit anderen Eigenschaftenflags nicht kompatibel. Beispielsweise wird beim Massenladen `Ignoreduplicatekeys=true` nicht gleichzeitig mit `Keepidentity=false` unterstützt. Bei `Keepidentity=false` wird für das Massenladen erwartet, dass der Server die Schlüsselwerte generiert. Tabellen sollten für den Schlüssel eine `IDENTITY`-Einschränkung besitzen. Der Server generiert keine doppelten Schlüssel, was bedeutet, dass `Ignoreduplicatekeys` nicht auf `true` festgelegt werden muss. `Ignoreduplicatekeys` muss nur dann auf `true` festgelegt werden, wenn Primärschlüsselwerte aus den eingehenden Daten in eine Tabelle mit Zeilen hochgeladen werden und es möglicherweise Konflikte im Zusammenhang mit Primärschlüsselwerten gibt.  
  
  
