---
title: Richtlinien und Einschränkungen von XML-Massenladen (SQLXML 4.0) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XML Bulk Load [SQLXML], about XML Bulk Load
- bulk load [SQLXML], about bulk load
ms.assetid: c5885d14-c7c1-47b3-a389-455e99a7ece1
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: b5a003abd67746da4ab62996311ed98594e2f403
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56016491"
---
# <a name="guidelines-and-limitations-of-xml-bulk-load-sqlxml-40"></a>Richtlinien und Einschränkungen von XML-Massenladen (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Wenn Sie XML-Massenladen verwenden, sollten Sie mit den folgenden Richtlinien und Einschränkungen vertraut sein:  
  
-   Inlineschemas werden nicht unterstützt.  
  
     Wenn im XML-Quelldokument ein Inlineschema vorhanden ist, wird dieses Schema von XML-Massenladen ignoriert. Sie geben das Zuordnungsschema für XML-Massenladen außerhalb der XML-Daten an. Sie können nicht das Zuordnungsschema an einem Knoten angeben, indem die **Xmlns = "X: Schema"** Attribut.  
  
-   Es wird überprüft, ob ein XML-Dokument wohlgeformt ist, es wird jedoch nicht überprüft, ob es gültig ist.  
  
     XML-Massenladen überprüft, dass das XML-Dokument zu ermitteln, ob es well-formed, mit deren Hilfe wird um sicherzustellen, dass der XML-Code, den syntaxanforderungen der XML 1.0-Empfehlung des World Wide Web Consortium entspricht. Wenn das Dokument nicht wohlgeformt ist, wird die Verarbeitung durch XML-Massenladen abgebrochen und ein Fehler zurückgegeben. Die einzige Ausnahme hierbei stellen Dokumente dar, bei denen es sich um Fragmente handelt (wenn das Dokument beispielsweise kein einzelnes Stammelement aufweist). In diesem Fall wird das Dokument durch XML-Massenladen geladen.  
  
     XML-Massenladen überprüft das Dokument nicht im Hinblick auf XML-Daten oder DTD-Schemas, die in der XML-Datendatei definiert sind oder auf die in der XML-Datendatei verwiesen wird. XML-Massenladen überprüft die XML-Datendatei auch nicht im Hinblick auf das bereitgestellte Zuordnungsschema.  
  
-   Alle XML-Prologinformationen werden ignoriert.  
  
     XML-Massenladen ignoriert alle Informationen vor und nach der \<Stamm > Element im XML-Dokument. XML-Massenladen ignoriert beispielsweise sämtliche XML-Deklarationen, internen DTD-Definitionen, externen DTD-Verweise, Kommentare usw.  
  
-   Bei einem Zuordnungsschema, das eine Primärschlüssel-Fremdschlüssel-Beziehung zwischen zwei Tabellen (wie etwa zwischen den Tabellen Customer und CustOrder) definiert, muss die Tabelle mit dem Primärschlüssel im Schema zuerst beschrieben werden. Die Tabelle mit der Fremdschlüsselspalte muss später im Schema angezeigt werden. Der Grund dafür ist, dass die Reihenfolge, in der die Tabellen im Schema angegeben werden, die Reihenfolge, die verwendet wird ist, um sie in der Datenbank zu laden. Beispielsweise wird das folgende XSD-Schema einen Fehler generiert, wenn sie in der XML-Massenladen verwendet wird, da die  **\<Reihenfolge >** Element wird beschrieben, bevor Sie die  **\<Kunden >** Element. Die Spalte CustomerID in der Tabelle CustOrder ist eine Fremdschlüsselspalte, die auf die Primärschlüsselspalte CustomerID in der Tabelle Cust verweist.  
  
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
  
-   Wenn das Schema keine überlaufspalten mithilfe angibt der **SQL: Overflow-Feld** Anmerkung, XML-Massenladen ignoriert alle Daten, die in das XML-Dokument vorhanden ist, jedoch im Zuordnungsschema nicht beschrieben.  
  
     XML-Massenladen wendet das angegebene Zuordnungsschema an, sobald es im XML-Datenstrom auf bekannte Tags trifft. XML-Massenladen ignoriert Daten, die zwar im XML-Dokument vorhanden, im Schema jedoch nicht beschrieben sind. Nehmen wir beispielsweise an, Sie haben ein Zuordnungsschema, das beschreibt eine  **\<Kunden >** Element. Die XML-Datendatei verfügt über eine  **\<AllCustomers >** -Stammtag (das im Schema nicht beschrieben ist), die alle umschließt die  **\<Kunden >** Elemente:  
  
    ```  
    <AllCustomers>  
      <Customer>...</Customer>  
      <Customer>...</Customer>  
       ...  
    </AllCustomers>  
    ```  
  
     In diesem Fall die XML-Massenladen ignoriert die  **\<AllCustomers >** -Element und beginnt mit der Zuordnung an die  **\<Kunden >** Element. XML-Massenladen ignoriert die Elemente, die zwar im XML-Dokument vorhanden, im Schema jedoch nicht beschrieben sind.  
  
     Erwägen Sie eine andere XML-Quelldatendatei enthält, die  **\<Reihenfolge >** Elemente. Diese Elemente sind im Zuordnungsschema nicht beschrieben:  
  
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
  
     XML-Massenladen ignoriert diese  **\<Reihenfolge >** Elemente. Wenn Sie jedoch die **SQL: Overflow-Feld**-Anmerkung im Schema identifiziert eine Spalte als Überlaufspalte, XML-Massenladen speichert alle nicht verbrauchte Daten in dieser Spalte.  
  
-   CDATA-Abschnitte und Entitätsverweise werden vor dem Speichern in der Datenbank in das entsprechende Zeichenfolgenäquivalent übersetzt.  
  
     In diesem Beispiel umschließt ein CDATA-Abschnitt den Wert für die  **\<City >** Element. XML-Massenladen extrahiert den Zeichenfolgenwert ("NY"), bevor es fügt die  **\<City >** Element in der Datenbank.  
  
    ```  
    <City><![CDATA[NY]]> </City>  
    ```  
  
     XML-Massenladen behält Entitätsverweise nicht bei.  
  
-   Wenn in einem Zuordnungsschema der Standardwert eines Attributs angegeben ist, verwendet XML-Massenladen dieses Attribut, auch wenn das Attribut in den XML-Quelldaten nicht enthalten ist.  
  
     Das folgende Beispiel XDR-Schema weist einen Standardwert, der **HireDate** Attribut:  
  
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
  
     In dieser XML-Daten die **HireDate** Attribut ist nicht vorhanden, aus der zweiten  **\<Kunden >** Element. Wenn der XML-Massenladen das zweite fügt  **\<Kunden >** Element in der Datenbank, er verwendet den Standardwert, der im Schema angegeben ist.  
  
    ```  
    <ROOT>  
      <Customers CustomerID="1" HireDate="1999-01-01" Salary="10000" />  
      <Customers CustomerID="2" Salary="10000" />  
    </ROOT>  
    ```  
  
-   Die **SQL: URL-codieren** Anmerkung wird nicht unterstützt:  
  
     Eine in der XML-Dateneingabe angegebene URL wird von Massenladen an diesem Speicherort nicht gelesen.  
  
     Die im Zuordnungsschema angegebenen Tabellen werden erstellt (die Datenbank muss vorhanden sein). Wenn eine oder mehrere Tabellen in der Datenbank bereits vorhanden ist, bestimmt die SGDropTables-Eigenschaft an, ob diese bereits vorhandenen Tabellen gelöscht und neu erstellt werden.  
  
-   Wenn Sie die Eigenschaft "schemagen" angeben (z. B. "schemagen" = "true"), werden die Tabellen, die im Zuordnungsschema identifiziert werden erstellt. Aber "schemagen" erstellt keine Einschränkungen (z. B. die PRIMARY KEY/FOREIGN KEY-Einschränkungen) in diesen Tabellen mit einer Ausnahme: Wenn die XML-Knoten, die den Primärschlüssel in einer Beziehung bilden definiert werden, dass einen XML-Datentyp-ID (d. h. **Typ = "xsd: ID"** für XSD) SGUseID-Eigenschaft auf "true" für "schemagen" festgelegt ist, und werden nicht nur Primärschlüssel aus erstellt. die ID typisierten Knoten, aber die Primär-/Fremdschlüssel-Beziehungen aus Zuordnen von Schemas Beziehungen erstellt.  
  
-   SchemaGen verwendet keinen XSD-Schema-Facets und Erweiterungen zum Generieren des relationalen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Schema.  
  
-   Wenn Sie die Eigenschaft "schemagen" angeben (z. B. "schemagen" = "true") beim Massenladen, nur Tabellen (und nicht für Sichten von freigegebenen Namen), die angegeben werden, werden aktualisiert.  
  
-   "Schemagen" stellt nur grundlegende Funktionalität für das Generieren des relationalen Schemas von XSD mit Anmerkungen bereit. Der Benutzer muss die generierten Tabellen ggf. manuell ändern.  
  
-   In denen mehr als eine Beziehung zwischen Tabellen vorhanden ist, versucht "schemagen" um eine einzelne Beziehung zu erstellen, die alle Schlüssel an, die zwischen den beiden Tabellen enthält. Diese Einschränkung kann die Ursache eines [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Fehlers sein.  
  
-   Beim Massenladen von XML-Daten in eine Datenbank muss mindestens ein Attribut oder ein untergeordnetes Element im Zuordnungsschema vorhanden sein, das einer Datenbankspalte zugeordnet ist.  
  
-   Wenn Sie Datenwerte mithilfe von XML-Massenladen einfügen, müssen die Werte im Format (-)CCYY-MM-DD((+-)TZ) angegeben werden. Dies ist das XSD-Standardformat für das Datum.  
  
-   Einige Eigenschaftenflags sind mit anderen Eigenschaftenflags nicht kompatibel. Massenladen unterstützt beispielsweise keine **Ignoreduplicatekeys = True** zusammen mit **Keepidentity = False**. Wenn **Keepidentity = False**, Massenladen erwartet, dass den Server die Schlüsselwerte zu generieren. Tabellen müssen einen **Identität** Einschränkung für den Schlüssel. Der Server generiert keine doppelten Schlüssel, was bedeutet, dass keine Notwendigkeit für **Ignoreduplicatekeys** festgelegt werden, um **"true"**. **IgnoreDuplicateKeys** sollte festgelegt werden, um **"true"** nur beim Hochladen der Primärschlüsselwerte aus den eingehenden Daten in eine Tabelle mit Zeilen und es besteht die Gefahr Konflikte im Zusammenhang mit Primärschlüsselwerten.  
  
  
