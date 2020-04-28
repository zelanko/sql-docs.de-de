---
title: 'Festlegen von rekursiven tiefen Beziehungen mit SQL: Max-Tiefe'
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
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
author: MightyPen
ms.author: genemi
ms.reviewer: ''
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: aaeeae8c0adfc34c80b986898c5209b744d7efc4
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "75257356"
---
# <a name="specifying-depth-in-recursive-relationships-by-using-sqlmax-depth"></a>Angeben der Tiefe von rekursiven Beziehungen mit 'sql:max-depth'
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
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
  
 Sie können das folgende XSD-Schema verwenden und eine XPath-Abfrage damit ausführen, um dieses Ergebnis zu erhalten. Das Schema beschreibt ein ** \<EMP->** Element vom Typ Mitarbeiter Type, das aus einem ** \<EMP->** untergeordneten Element desselben Typs, Mitarbeiter Type, besteht. Dies ist eine rekursive Beziehung (das Element und sein Vorgänger sind vom gleichen Typ). Außerdem verwendet das Schema eine ** \<SQL: Relationship->** , um die über-/Unterordnungsbeziehung zwischen dem Supervisor und der Aufsicht zu beschreiben. Beachten Sie, dass in dieser ** \<SQL: Relationship->** EMP sowohl die übergeordnete als auch die untergeordnete Tabelle ist.  
  
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
  
 Weil die Beziehung rekursiv ist, müssen Sie auf irgendeine Weise die Rekursionstiefe im Schema angeben können. Andernfalls enthält das Ergebnis eine endlose Rekursion (ein Mitarbeiter berichtet an den Mitarbeiter, der an den Mitarbeiter berichtet usw.). Mit der **SQL: Max-Deep-** Anmerkung können Sie angeben, wie tief die Rekursion wechseln soll. Wenn Sie in diesem speziellen Beispiel einen Wert für " **SQL: Max-** Deep" angeben möchten, müssen Sie wissen, wie tief die Verwaltungshierarchie in das Unternehmen wechselt.  
  
> [!NOTE]  
>  Das Schema gibt die **SQL: limit-field-** Anmerkung an, aber nicht die **SQL: limit-value-** Anmerkung. Dadurch wird der oberste Knoten der resultierenden Hierarchie lediglich auf diejenigen Mitarbeiter beschränkt, die niemandem unterstellt sind. (ReportsTo ist NULL.) Durch Angeben von " **SQL: limit-field** " und ohne Angabe von " **SQL: limit-value** " (standardmäßig NULL) wird dies erreicht. Wenn Sie möchten, dass die resultierende XML-Datei jede mögliche Berichtsstruktur (die Berichtsstruktur für jeden Mitarbeiter in der Tabelle) einschließt, entfernen Sie die **SQL: limit-field-** Anmerkung aus dem Schema.  
  
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
  
5.  Erstellen und verwenden Sie das SQLXML 4.0-Testskript (Sqlxml4test.vbs), um die Vorlage auszuführen. Weitere Informationen finden Sie unter [Verwenden von ADO zum Ausführen von SQLXML 4,0-Abfragen](../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  

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
>  Um verschiedene Tiefen der Hierarchien im Ergebnis zu erstellen, ändern Sie den Wert der Anmerkung " **SQL: Max-Tiefe** " im Schema, und führen Sie die Vorlage nach jeder Änderung erneut aus.  
  
 Im vorherigen Schema besaßen alle ** \<EMP->** Elemente genau denselben Satz von**Attributen (Mitarbeiter**-ID, **FirstName**und **LastName**). Das folgende Schema wurde leicht geändert, um ein zusätzliches **ReportsTo** -Attribut für alle ** \<EMP->** Elemente zurückzugeben, die einem Vorgesetzten Berichten.  
  
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
  
 Verwenden Sie die " **SQL: Max-Tiefe"-** Anmerkung im Schema, um die Tiefe der Rekursion in einer rekursiven Beziehung anzugeben, die im Schema beschrieben wird. Der Wert der " **SQL: Max-tiefen"-** Anmerkung ist eine positive ganze Zahl (1 bis 50), die die Anzahl der Rekursionen angibt: bei einem Wert von 1 wird die Rekursion an dem Element angehalten, für das die **SQL: Max-tiefen** Anmerkung angegeben ist. der Wert 2 beendet die Rekursion auf der nächsten Ebene des Elements, bei dem **SQL: Max-Tiefe** angegeben ist. Und so weiter.  
  
> [!NOTE]  
>  In der zugrunde liegenden Implementierung wird eine XPath-Abfrage, die für ein Zuordnungsschema angegeben wird, in eine SELECT... FOR XML (explizite Abfrage). Bei dieser Abfrage ist es erforderlich, eine endliche Rekursionstiefe anzugeben. Je höher der Wert ist, den Sie für " **SQL: Max-Tiefe**" angeben, desto größer ist die generierte for XML-Abfrage. Dies könnte den Abrufvorgang verlangsamen.  
  
> [!NOTE]  
>  Bei Updategrams und beim XML-Massenladen wird die -Anmerkung ignoriert. Dies bedeutet, rekursive Updates oder Einfügungen werden unabhängig von dem Wert ausgeführt, der für  angegeben wird.  
  
## <a name="specifying-sqlmax-depth-on-complex-elements"></a>Angeben von 'sql:max-depth' für komplexe Elemente  
 Die **SQL: Max-Tiefe-** Anmerkung kann für jedes beliebige komplexe Inhalts Element angegeben werden.  
  
### <a name="recursive-elements"></a>Rekursive Elemente  
 Wenn **SQL: Max-Tiefe** sowohl für das übergeordnete Element als auch für das untergeordnete Element in einer rekursiven Beziehung angegeben ist, hat die für das übergeordnete Element angegebene **SQL: Max-tiefen** Anmerkung Vorrang. Im folgenden Schema wird z. b. die **SQL: Max-Tiefe-** Anmerkung sowohl für das übergeordnete als auch das untergeordnete Employee-Element angegeben. In diesem Fall hat **SQL: Max-Tiefe = 4**, das für das ** \<EMP->** übergeordnete Element angegeben wird (Rolle des Vorgesetzten), Vorrang. Die für das untergeordnete ** \<EMP->** Element angegebene **SQL: Max-Tiefe** (Rolle von "supervisee") wird ignoriert.  
  
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
 Wenn die **SQL: Max-Tiefe-** Anmerkung für ein Element im Schema angegeben ist, das keine Rekursion auslöst, wird Sie ignoriert. Im folgenden Schema besteht ein ** \<EMP->** Element aus einem ** \<Konstanten>** untergeordneten Element, das wiederum über ein ** \<EMP->** untergeordnetes Element verfügt.  
  
 In diesem Schema wird die für das ** \<Konstante>** Element angegebene **SQL: Max-tiefen** Anmerkung ignoriert, da keine Rekursion zwischen dem ** \<EMP>** Parent und dem ** \<Konstanten>** untergeordneten Element vorhanden ist. Es gibt jedoch eine Rekursion zwischen dem ** \<EMP->** Vorgänger und dem ** \<EMP>** untergeordneten Element. Das Schema gibt die " **SQL: Max-Tiefe"-** Anmerkung für beide an. Daher hat die auf dem Vorgänger (**\<EMP>** in der Rolle "Supervisor" angegebene **SQL: Max-tiefen** Anmerkung Vorrang.  
  
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
 Wenn Sie eine komplexe Typableitung durch ** \<Einschränkung>** haben, können Elemente des entsprechenden komplexen Basistyps die **SQL: Max-Tiefe-** Anmerkung nicht angeben. In diesen Fällen kann die **SQL: Max-tiefen** Anmerkung dem-Element des abgeleiteten Typs hinzugefügt werden.  
  
 Wenn Sie dagegen eine komplexe Typableitung durch ** \<Erweiterung>** haben, können die Elemente des entsprechenden komplexen Basistyps die **SQL: Max-Tiefe-** Anmerkung angeben.  
  
 Das folgende XSD-Schema generiert beispielsweise einen Fehler, weil die **SQL: Max-tiefen-** Anmerkung für den Basistyp angegeben wird. Diese Anmerkung wird nicht für einen Typ unterstützt, der von ** \<Einschränkungs>** von einem anderen Typ abgeleitet wird. Um dieses Problem zu beheben, müssen Sie das Schema ändern und die " **SQL: Max-tiefen"-** Anmerkung für ein Element im abgeleiteten Typ angeben.  
  
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
  
 Im Schema ist **SQL: Max-Tiefe** für einen komplexen **CustomerBaseType** -Typ angegeben. Das Schema gibt auch ein ** \<Customer->** Element vom Typ **CustomerType**an, das von **CustomerBaseType**abgeleitet ist. Eine für ein solches Schema angegebene XPath-Abfrage generiert einen Fehler, da **SQL: Max-Tiefe** für ein Element, das in einem Einschränkungs Basistyp definiert ist, nicht unterstützt wird.  
  
## <a name="schemas-with-a-deep-hierarchy"></a>Schemas mit einer tiefen Hierarchie  
 Möglicherweise liegt ein Schema vor, das eine tiefe Hierarchie umfasst, in der ein Element ein untergeordnetes Element enthält, das wiederum ein untergeordnetes Element enthalt usw. Wenn die in einem solchen Schema angegebene **SQL: Max-tiefen** Anmerkung ein XML-Dokument generiert, das eine Hierarchie mit mehr als 500 Ebenen enthält (mit dem Element der obersten Ebene auf Ebene 1, dem untergeordneten Element auf der Ebene 2 usw.), wird ein Fehler zurückgegeben.  
  
  
