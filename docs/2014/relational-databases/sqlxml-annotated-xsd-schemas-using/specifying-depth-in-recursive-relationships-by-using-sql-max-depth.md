---
title: 'Angeben von Tiefe in rekursiven Beziehungen mithilfe von SQL: Max-Tiefe | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- max-depth annotation
- XPath queries [SQLXML], recursive relationships
- depth in recursive relationships [SQLXML]
- annotated XSD schemas, recursive relationships
- relationships [SQLXML], recursive relationships
- self joins
- recursive relationships [SQLXML]
- recursion [SQLXML]
- sql:max-depth
- recursive joins [SQLXML]
ms.assetid: 0ffdd57d-dc30-44d9-a8a0-f21cadedb327
author: rothja
ms.author: jroth
ms.openlocfilehash: 6dfbb6c237c63d3a6d7b8e324bde42d4e8851abe
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85003019"
---
# <a name="specifying-depth-in-recursive-relationships-by-using-sqlmax-depth"></a>Angeben der Tiefe von rekursiven Beziehungen mit 'sql:max-depth'
  Wenn in einer relationalen Datenbank eine Tabelle in einer Beziehung zu sich selbst steht, wird dies als rekursive Beziehung bezeichnet. Beispielsweise steht eine Tabelle, in der Mitarbeiterdatensätze gespeichert werden, in einer Beziehung zwischen Vorgesetzten und unterstellten Mitarbeitern mit sich selbst in Beziehung. In diesem Fall spielt die Mitarbeitertabelle auf der einen Seite der Beziehung die Rolle des Vorgesetzten und auf der anderen Seite spielt dieselbe Tabelle die Rolle des unterstellten Mitarbeiters.  
  
 Zuordnungsschemas können rekursive Beziehungen enthalten, wenn ein Element und sein Vorgänger vom gleichen Typ sind.  
  
## <a name="example-a"></a>Beispiel A  
 Betrachten Sie die folgende Tabelle.  
  
```  
Emp (EmployeeID, FirstName, LastName, ReportsTo)  
```  
  
 In dieser Tabelle enthält die Spalte ReportsTo die Mitarbeiter-ID des Vorgesetzten.  
  
 Angenommen, Sie möchten eine XML-Hierarchie der Mitarbeiter generieren, in der sich der Vorgesetzte an der Spitze der Hierarchie befindet, und die Mitarbeiter, die diesem Vorgesetzten unterstellt sind, wie in folgendem XML-Beispielfragment dargestellt, in der zugehörigen Hierarchie angezeigt werden. Dieses Fragment zeigt die *rekursive* Struktur für Employee 1 an.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<root>  
  <Emp FirstName="Nancy" EmployeeID="1" LastName="Devolio">  
     <Emp FirstName="Andrew" EmployeeID="2" LastName="Fuller" />   
     <Emp FirstName="Janet" EmployeeID="3" LastName="Leverling">  
        <Emp FirstName="Margaret" EmployeeID="4" LastName="Peacock">  
          <Emp FirstName="Steven" EmployeeID="5" LastName="Devolio">  
...  
...  
</root>  
```  
  
 In diesem Fragment berichtet Mitarbeiter 5 an Mitarbeiter 4, Mitarbeiter 4 berichtet an Mitarbeiter 3, und die Mitarbeiter 3 und 2 berichten an Mitarbeiter 1.  
  
 Sie können das folgende XSD-Schema verwenden und eine XPath-Abfrage damit ausführen, um dieses Ergebnis zu erhalten. Das Schema beschreibt ein **\<Emp>** Element des Typs Mitarbeiter Type, das aus einem untergeordneten **\<Emp>** Element desselben Typs, Mitarbeiter Type, besteht. Dies ist eine rekursive Beziehung (das Element und sein Vorgänger sind vom gleichen Typ). Außerdem verwendet das Schema eine **\<sql:relationship>** , um die über-/Unterordnungsbeziehung zwischen dem Supervisor und dem Supervisor zu beschreiben. Beachten Sie, dass **\<sql:relationship>** EMP in diesem sowohl die übergeordnete als auch die untergeordnete Tabelle ist.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:dt="urn:schemas-microsoft-com:datatypes"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:annotation>  
    <xsd:appinfo>  
      <sql:relationship name="SupervisorSupervisee"  
                                  parent="Emp"  
                                  parent-key="EmployeeID"  
                                  child="Emp"  
                                  child-key="ReportsTo" />  
    </xsd:appinfo>  
  </xsd:annotation>  
  <xsd:element name="Emp" type="EmployeeType"   
                          sql:relation="Emp"   
                          sql:key-fields="EmployeeID"   
                          sql:limit-field="ReportsTo" />  
  <xsd:complexType name="EmployeeType">  
    <xsd:sequence>  
      <xsd:element name="Emp" type="EmployeeType"   
                              sql:relation="Emp"   
                              sql:key-fields="EmployeeID"  
                              sql:relationship="SupervisorSupervisee"  
                              sql:max-depth="6" />  
    </xsd:sequence>   
    <xsd:attribute name="EmployeeID" type="xsd:ID" />  
    <xsd:attribute name="FirstName" type="xsd:string"/>  
    <xsd:attribute name="LastName" type="xsd:string"/>  
  </xsd:complexType>  
</xsd:schema>  
```  
  
 Weil die Beziehung rekursiv ist, müssen Sie auf irgendeine Weise die Rekursionstiefe im Schema angeben können. Andernfalls enthält das Ergebnis eine endlose Rekursion (ein Mitarbeiter berichtet an den Mitarbeiter, der an den Mitarbeiter berichtet usw.). Mit der `sql:max-depth`-Anmerkung können Sie die Rekursionstiefe angeben. In diesem Beispiel müssen Sie wissen, über wie viele Ebenen die Managementhierarchie der betreffenden Firma verfügt, um einen Wert für `sql:max-depth` angeben zu können.  
  
> [!NOTE]  
>  Im Schema wird die `sql:limit-field`-Anmerkung, nicht jedoch die `sql:limit-value`-Anmerkung angegeben. Dadurch wird der oberste Knoten der resultierenden Hierarchie lediglich auf diejenigen Mitarbeiter beschränkt, die niemandem unterstellt sind. (ReportsTo ist NULL.) Durch angeben `sql:limit-field` von und ohne Angabe `sql:limit-value` von (standardmäßig NULL) wird die Anmerkung erreicht. Wenn die resultierende XML-Hierarchie alle möglichen Berichtsstrukturen enthalten soll (die Berichtsstruktur für jeden in der Tabelle enthaltenen Mitarbeiter), dann entfernen Sie die `sql:limit-field`-Anmerkung aus dem Schema.  
  
> [!NOTE]  
>  In der folgenden Prozedur wird die Datenbank tempdb verwendet.  
  
#### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>So testen Sie eine XPath-Beispiel Abfrage für das Schema  
  
1.  Erstellen Sie eine Beispieltabelle namens Emp in der Datenbank tempdb, auf die das virtuelle Stammverzeichnis zeigt.  
  
    ```  
    USE tempdb  
    CREATE TABLE Emp (  
           EmployeeID int primary key,   
           FirstName  varchar(20),   
           LastName   varchar(20),   
           ReportsTo int)  
    ```  
  
2.  Fügen Sie diese Beispieldaten hinzu:  
  
    ```  
    INSERT INTO Emp values (1, 'Nancy', 'Devolio',NULL)  
    INSERT INTO Emp values (2, 'Andrew', 'Fuller',1)  
    INSERT INTO Emp values (3, 'Janet', 'Leverling',1)  
    INSERT INTO Emp values (4, 'Margaret', 'Peacock',3)  
    INSERT INTO Emp values (5, 'Steven', 'Devolio',4)  
    INSERT INTO Emp values (6, 'Nancy', 'Buchanan',5)  
    INSERT INTO Emp values (7, 'Michael', 'Suyama',6)  
    ```  
  
3.  Kopieren Sie den oben stehenden Schemacode, und fügen Sie ihn in eine Textdatei ein. Speichern Sie die Datei unter dem Dateinamen maxDepth.xml.  
  
4.  Kopieren Sie die folgende Vorlage, und fügen Sie sie in eine Textdatei ein. Speichern Sie die Datei unter dem Namen maxDepthT.xml im gleichen Verzeichnis, in dem Sie maxDepth.xml gespeichert haben. Die Abfrage in der Vorlage gibt alle in der Emp-Tabelle enthaltenen Elemente zurück.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="maxDepth.xml">  
        /Emp  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Der für das Zuordnungsschema (maxDepth.xml) angegebene Verzeichnispfad bezieht sich auf das Verzeichnis, in dem die Vorlage gespeichert wird. Es kann auch ein absoluter Pfad angegeben werden. Beispiel:  
  
    ```  
    mapping-schema="C:\MyDir\maxDepth.xml"  
    ```  
  
5.  Erstellen und verwenden Sie das SQLXML 4.0-Testskript (Sqlxml4test.vbs), um die Vorlage auszuführen. Weitere Informationen finden Sie unter [Verwenden von ADO zum Ausführen von SQLXML 4,0-Abfragen](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Dies ist das Ergebnis:  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<root>  
  <Emp FirstName="Nancy" EmployeeID="1" LastName="Devolio">  
  <Emp FirstName="Andrew" EmployeeID="2" LastName="Fuller" />   
    <Emp FirstName="Janet" EmployeeID="3" LastName="Leverling">  
      <Emp FirstName="Margaret" EmployeeID="4" LastName="Peacock">  
        <Emp FirstName="Steven" EmployeeID="5" LastName="Devolio">  
          <Emp FirstName="Nancy" EmployeeID="6" LastName="Buchanan">  
            <Emp FirstName="Michael" EmployeeID="7" LastName="Suyama" />   
          </Emp>  
        </Emp>  
      </Emp>  
    </Emp>  
  </Emp>  
</root>  
```  
  
> [!NOTE]  
>  Um im Ergebnis Hierarchien mit einer unterschiedlichen Anzahl von Ebenen zu erzeugen, ändern Sie den Wert der `sql:max-depth`-Anmerkung im Schema und führen die Vorlage nach jeder Änderung erneut aus.  
  
 Im vorherigen Schema **\<Emp>** hatten alle Elemente genau denselben Attribut Satz (Mitarbeiter-ID, **FirstName**und **LastName**).**EmployeeID** Das folgende Schema wurde leicht geändert, um ein zusätzliches **ReportsTo** -Attribut für alle Elemente zurückzugeben **\<Emp>** , die einem Vorgesetzten Berichten.  
  
 Zum Beispiel zeigt dieses XML-Fragment die Untergebenen von Mitarbeiter 1 an:  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<root>  
<Emp FirstName="Nancy" EmployeeID="1" LastName="Devolio">  
  <Emp FirstName="Andrew" EmployeeID="2"   
       ReportsTo="1" LastName="Fuller" />   
  <Emp FirstName="Janet" EmployeeID="3"   
       ReportsTo="1" LastName="Leverling">  
...  
...  
```  
  
 Dies ist das überarbeitete Schema:  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:dt="urn:schemas-microsoft-com:datatypes"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:annotation>  
    <xsd:documentation>  
      Customer-Order-Order Details Schema  
      Copyright 2000 Microsoft. All rights reserved.  
    </xsd:documentation>  
    <xsd:appinfo>  
      <sql:relationship name="SupervisorSupervisee"   
                  parent="Emp"  
                  parent-key="EmployeeID"  
                  child="Emp"  
                  child-key="ReportsTo" />  
    </xsd:appinfo>  
  </xsd:annotation>  
  <xsd:element name="Emp"   
                   type="EmpType"   
                   sql:relation="Emp"   
                   sql:key-fields="EmployeeID"   
                   sql:limit-field="ReportsTo" />  
  <xsd:complexType name="EmpType">  
    <xsd:sequence>  
       <xsd:element name="Emp"   
                    type="EmpType"   
                    sql:relation="Emp"   
                    sql:key-fields="EmployeeID"  
                    sql:relationship="SupervisorSupervisee"  
                    sql:max-depth="6"/>  
    </xsd:sequence>   
    <xsd:attribute name="EmployeeID" type="xsd:int" />  
    <xsd:attribute name="FirstName" type="xsd:string"/>  
    <xsd:attribute name="LastName" type="xsd:string"/>  
    <xsd:attribute name="ReportsTo" type="xsd:int" />  
  </xsd:complexType>  
</xsd:schema>  
```  
  
## <a name="sqlmax-depth-annotation"></a>sql:max-depth-Anmerkung  
 In einem Schema, das aus rekursiven Beziehungen besteht, muss die Rekursionstiefe im Schema explizit angegeben werden. Dies ist erforderlich, um die entsprechende FOR XML EXPLICIT-Abfrage, die die gewünschten Ergebnisse zurückgibt, erfolgreich zu erzeugen.  
  
 Verwenden Sie die `sql:max-depth`-Anmerkung im Schema, um die Rekursionstiefe einer rekursiven Beziehung anzugeben, die im Schema beschrieben wird. Der Wert der `sql:max-depth`-Anmerkung ist eine positive ganze Zahl (1 bis 50), die die Anzahl der Rekursionen angibt: Durch die Angabe des Werts 1 wird die Rekursion bei dem Element angehalten, für das die `sql:max-depth`-Anmerkung angegeben wurde. Durch die Angabe des Werts 2 wird die Rekursion in der nächsten Ebene unter dem Element, für das `sql:max-depth` angegeben wurde, angehalten ; usw.  
  
> [!NOTE]  
>  In der zugrunde liegenden Implementierung wird eine XPath-Abfrage, die für ein Zuordnungsschema angegeben wird, in eine SELECT... FOR XML (explizite Abfrage). Bei dieser Abfrage ist es erforderlich, eine endliche Rekursionstiefe anzugeben. Je höher der Wert, der für `sql:max-depth` angegeben wird, desto umfangreicher ist die generierte FOR XML EXPLICIT-Abfrage. Dies könnte den Abrufvorgang verlangsamen.  
  
> [!NOTE]  
>  Bei Updategrams und beim XML-Massenladen wird die -Anmerkung ignoriert. Dies bedeutet, rekursive Updates oder Einfügungen werden unabhängig von dem Wert ausgeführt, der für  angegeben wird.  
  
## <a name="specifying-sqlmax-depth-on-complex-elements"></a>Angeben von 'sql:max-depth' für komplexe Elemente  
 Die `sql:max-depth`-Anmerkung kann für jedes komplexe Inhaltselement angegeben werden.  
  
### <a name="recursive-elements"></a>Rekursive Elemente  
 Wenn `sql:max-depth` sowohl für das übergeordnete als auch das untergeordnete Element einer rekursiven Beziehung angegeben wird, dann hat die `sql:max-depth`-Anmerkung Vorrang, die für das übergeordnete Element angegeben wurde. Beispielsweise wird die `sql:max-depth`-Anmerkung im folgenden Schema sowohl für das übergeordnete als auch das untergeordnete &lt;Emp&gt;-Element angegeben. In diesem Fall hat, `sql:max-depth=4` für das über **\<Emp>** geordnete Element angegeben (Rolle des Vorgesetzten), Vorrang. Der, der `sql:max-depth` für das untergeordnete **\<Emp>** Element (die Rolle "supervisee" spielt) angegeben wird, wird ignoriert.  
  
#### <a name="example-b"></a>Beispiel B  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:dt="urn:schemas-microsoft-com:datatypes"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:annotation>  
    <xsd:appinfo>  
      <sql:relationship name="SupervisorSupervisee"  
                                  parent="Emp"  
                                  parent-key="EmployeeID"  
                                  child="Emp"  
                                  child-key="ReportsTo" />  
    </xsd:appinfo>  
  </xsd:annotation>  
  <xsd:element name="Emp" type="EmployeeType"   
                          sql:relation="Emp"   
                          sql:key-fields="EmployeeID"   
                          sql:limit-field="ReportsTo"   
                          sql:max-depth="3" />  
  <xsd:complexType name="EmployeeType">  
    <xsd:sequence>  
      <xsd:element name="Emp" type="EmployeeType"   
                              sql:relation="Emp"   
                              sql:key-fields="EmployeeID"  
                              sql:relationship="SupervisorSupervisee"  
                              sql:max-depth="2" />  
    </xsd:sequence>   
    <xsd:attribute name="EmployeeID" type="xsd:ID" />  
    <xsd:attribute name="FirstName" type="xsd:string"/>  
    <xsd:attribute name="LastName" type="xsd:string"/>  
  </xsd:complexType>  
</xsd:schema>  
```  
  
 Um dieses Schema zu testen, führen Sie die Schritte für Beispiel A weiter oben in diesem Thema aus.  
  
### <a name="nonrecursive-elements"></a>Nicht rekursive Elemente  
 Wenn die `sql:max-depth`-Anmerkung für ein Element in dem Schema angegeben wird, das keine Rekursion bewirkt, dann wird sie ignoriert. Im folgenden Schema besteht ein-Element aus einem untergeordneten- **\<Emp>** **\<Constant>** Element, das wiederum über ein untergeordnetes-Element verfügt **\<Emp>** .  
  
 In diesem Schema wird die-Anmerkung, die `sql:max-depth` für das-Element angegeben ist, **\<Constant>** ignoriert, da es keine Rekursion zwischen dem über **\<Emp>** geordneten und dem untergeordneten- **\<Constant>** Element gibt. Es gibt jedoch eine Rekursion zwischen dem **\<Emp>** Vorgänger und dem untergeordneten Element **\<Emp>** . Das Schema gibt die `sql:max-depth`-Anmerkung für beide an. Daher hat die- `sql:max-depth` Anmerkung, die auf dem Vorgänger ( **\<Emp>** in der Rolle "Supervisor") angegeben ist, Vorrang.  
  
#### <a name="example-c"></a>Beispiel C  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:annotation>  
    <xsd:appinfo>  
      <sql:relationship name="SupervisorSupervisee"   
                  parent="Emp"   
                  child="Emp"   
                  parent-key="EmployeeID"   
                  child-key="ReportsTo"/>  
    </xsd:appinfo>  
  </xsd:annotation>  
  <xsd:element name="Emp"   
               sql:relation="Emp"   
               type="EmpType"  
               sql:limit-field="ReportsTo"  
               sql:max-depth="1" />  
    <xsd:complexType name="EmpType" >  
      <xsd:sequence>  
       <xsd:element name="Constant"   
                    sql:is-constant="1"   
                    sql:max-depth="20" >  
         <xsd:complexType >  
           <xsd:sequence>  
            <xsd:element name="Emp"   
                         sql:relation="Emp" type="EmpType"  
                         sql:relationship="SupervisorSupervisee"   
                         sql:max-depth="3" />  
         </xsd:sequence>  
         </xsd:complexType>  
         </xsd:element>  
      </xsd:sequence>  
      <xsd:attribute name="EmployeeID" type="xsd:int" />  
    </xsd:complexType>  
</xsd:schema>  
```  
  
 Um dieses Schema zu testen, führen Sie die für Beispiel A weiter oben in diesem Thema beschriebenen Schritte aus.  
  
## <a name="complex-types-derived-by-restriction"></a>Durch Einschränkungen abgeleitete komplexe Typen  
 Wenn eine Ableitung komplexer Typen von vorhanden **\<restriction>** ist, können Elemente des entsprechenden komplexen Basistyps die-Anmerkung nicht angeben `sql:max-depth` . In diesen Fällen kann die `sql:max-depth`-Anmerkung dem Element des abgeleiteten Typs hinzugefügt werden.  
  
 Wenn Sie hingegen eine Ableitung komplexer Typen durch haben **\<extension>** , können die Elemente des entsprechenden komplexen Basistyps die-Anmerkung angeben `sql:max-depth` .  
  
 Beispielsweise erzeugt das folgende XSD-Schema einen Fehler, weil die `sql:max-depth`-Anmerkung für den Basistyp angegeben wurde. Diese Anmerkung wird für einen Typ, der von einem anderen Typ abgeleitet ist, nicht unterstützt **\<restriction>** . Zur Behebung dieses Problems müssen Sie das Schema ändern und die `sql:max-depth`-Anmerkung für Elemente im abgeleiteten Typ angeben.  
  
#### <a name="example-d"></a>Beispiel D  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:dt="urn:schemas-microsoft-com:datatypes"  
            xmlns:msdata="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:complexType name="CustomerBaseType">   
    <xsd:sequence>  
       <xsd:element name="CID" msdata:field="CustomerID" />  
       <xsd:element name="CompanyName"/>  
       <xsd:element name="Customers" msdata:max-depth="3">  
         <xsd:annotation>  
           <xsd:appinfo>  
             <msdata:relationship  
                     parent="Customers"  
                     parent-key="CustomerID"  
                     child-key="CustomerID"  
                     child="Customers" />  
           </xsd:appinfo>  
         </xsd:annotation>  
       </xsd:element>  
    </xsd:sequence>  
  </xsd:complexType>  
  <xsd:element name="Customers" type="CustomerType"/>  
  <xsd:complexType name="CustomerType">  
    <xsd:complexContent>  
       <xsd:restriction base="CustomerBaseType">  
          <xsd:sequence>  
            <xsd:element name="CID"   
                         type="xsd:string"/>  
            <xsd:element name="CompanyName"   
                         type="xsd:string"  
                         msdata:field="CName" />  
            <xsd:element name="Customers"   
                         type="CustomerType" />  
          </xsd:sequence>  
       </xsd:restriction>  
    </xsd:complexContent>  
  </xsd:complexType>  
</xsd:schema>   
```  
  
 Im Schema wird `sql:max-depth` für ein Element des komplexen Typs `CustomerBaseType` angegeben. Das Schema gibt auch ein- **\<Customer>** Element vom Typ an `CustomerType` , das von abgeleitet wird `CustomerBaseType` . Eine mit diesem Schema ausgeführte XPath-Abfrage erzeugt einen Fehler, weil `sql:max-depth` nicht für Elemente unterstützt wird, die in einem einfachen Einschränkungstyp definiert sind.  
  
## <a name="schemas-with-a-deep-hierarchy"></a>Schemas mit einer tiefen Hierarchie  
 Möglicherweise liegt ein Schema vor, das eine tiefe Hierarchie umfasst, in der ein Element ein untergeordnetes Element enthält, das wiederum ein untergeordnetes Element enthalt usw. Wenn die in einem solchen Schema angegebene `sql:max-depth`-Anmerkung ein XML-Dokument erzeugt, das eine Hierarchie mit mehr als 500 Ebenen umfasst (wobei das oberste Element auf Ebene 1, das diesem untergeordnete Element auf Ebene 2 etc. angesiedelt ist), wird ein Fehler zurückgegeben.  
  
  
