---
title: Ausführen eines DiffGram-Codes mithilfe von verwalteten SQLXML-Klassen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- DiffGrams [SQLXML], Managed Classes
- SQLXML Managed Classes, DiffGrams
- Managed Classes [SQLXML], DiffGrams
- SQLXML, Managed Classes
ms.assetid: 81c687ca-8c9f-4f58-801f-8dabcc508a06
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3d8756bb3dc7b030541159c2aa127162907aa4b5
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66013048"
---
# <a name="executing-a-diffgram-by-using-sqlxml-managed-classes"></a>Ausführen eines DiffGram-Objekts mit verwalteten SQLXML-Klassen
  Dieses Beispiel zeigt, wie Sie eine DiffGram-Datei in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] der .NET Framework Umgebung ausführen, um Daten [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Aktualisierungen mithilfe von verwalteten SQLXML-Klassen (Microsoft. Data. SqlXml) auf Tabellen anzuwenden.  
  
 In diesem Beispiel aktualisiert das DiffGram Kundeninformationen (CompanyName und ContactName) für den Kunden ALFKI.  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql" sql:mapping-schema="DiffGramSchema.xml">  
  <diffgr:diffgram   
           xmlns:msdata="urn:schemas-microsoft-com:xml-msdata"   
           xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1">  
    <DataInstance>  
      <Customer diffgr:id="Customer1"   
                msdata:rowOrder="0" diffgr:hasChanges="modified"   
                CustomerID="ALFKI">  
          <CompanyName>Bottom Dollar Markets</CompanyName>  
          <ContactName>Antonio Moreno</ContactName>  
      </Customer>  
    </DataInstance>  
    <diffgr:before>  
     <Customer diffgr:id="Customer1"   
               msdata:rowOrder="0"   
               CustomerID="ALFKI">  
        <CompanyName>Alfreds Futterkiste</CompanyName>  
        <ContactName>Maria Anders</ContactName>  
      </Customer>  
    </diffgr:before>  
  </diffgr:diffgram>  
</ROOT>  
```  
  
 Der ** \<before>** -Block enthält ein ** \<Customer>** -Element (**diffgr: ID = "Customer1"**). Der ** \<DataInstance->** Block enthält das entsprechende ** \<Customer>** -Element mit derselben **ID**. Das ** \<Customer>** -Element in ** \<NewDataSet>** auch **diffgr: hasChanges = "modified"** angibt. Dadurch wird ein Updatevorgang angezeigt und der Kundendatensatz in der Cust-Tabelle entsprechend aktualisiert. Beachten Sie Folgendes: Wenn das **diffgr: hasChanges** -Attribut nicht angegeben ist, ignoriert die DiffGram-Verarbeitungslogik dieses Element, und es werden keine Updates durchgeführt.  
  
 Der folgende Code zeigt eine c#-Lernprogramm Anwendung, die veranschaulicht, wie die verwalteten SQLXML-Klassen verwendet werden, um das obige DiffGram auszuführen und zwei Tabellen (cust, Ord) zu aktualisieren, die Sie ebenfalls in der **tempdb** -Datenbank erstellen.  
  
```  
using System;  
using System.Data;  
using Microsoft.Data.SqlXml;  
using System.IO;  
class Test  
{  
   static string ConnString = "Provider=SQLOLEDB;Server=MyServer;database=tempdb;Integrated Security=SSPI;";  
   public static int testParams()  
   {  
      SqlXmlAdapter ad;  
      // Need a memory stream to hold diff gram temporarily  
      MemoryStream ms = new MemoryStream();  
      SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
      cmd.RootTag = "ROOT";  
      cmd.CommandStream = new FileStream("MyDiffgram.xml", FileMode.Open, FileAccess.Read);  
      cmd.CommandType = SqlXmlCommandType.DiffGram;  
      cmd.SchemaPath = "DiffGramSchema.xml";  
      // Load data set  
      DataSet ds = new DataSet();  
      ad = new SqlXmlAdapter(cmd);  
      ad.Fill(ds);  
      ad.Update(ds);  
      return 0;  
   }  
   public static int Main(String[] args)  
   {  
      testParams();  
      return 0;  
   }  
}  
```  
  
### <a name="to-test-the-application"></a>So testen Sie die Anwendung  
  
1.  Stellen Sie sicher, dass .NET Framework auf dem Computer installiert ist.  
  
2.  Speichern Sie das folgende XSD-Schema (DiffGramSchema.xml) in einem Ordner:  
  
    ```  
    <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
                xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
     <xsd:annotation>  
      <xsd:documentation>  
        Diffgram Customers/Orders Schema.  
      </xsd:documentation>  
      <xsd:appinfo>  
           <sql:relationship name="CustomersOrders"   
                      parent="Cust"  
                      parent-key="CustomerID"  
                      child-key="CustomerID"  
                      child="Ord"/>  
      </xsd:appinfo>  
     </xsd:annotation>  
     <xsd:element name="Customer" sql:relation="Cust">  
      <xsd:complexType>  
        <xsd:sequence>  
          <xsd:element name="CompanyName"    type="xsd:string"/>  
          <xsd:element name="ContactName"    type="xsd:string"/>  
           <xsd:element name="Order" sql:relation="Ord" sql:relationship="CustomersOrders">  
            <xsd:complexType>  
              <xsd:attribute name="OrderID" type="xsd:int" sql:field="OrderID"/>  
              <xsd:attribute name="CustomerID" type="xsd:string"/>  
            </xsd:complexType>  
          </xsd:element>  
        </xsd:sequence>  
        <xsd:attribute name="CustomerID" type="xsd:string" sql:field="CustomerID"/>  
      </xsd:complexType>  
     </xsd:element>  
    </xsd:schema>  
    ```  
  
3.  Erstellen Sie diese Tabellen in der **tempdb** -Datenbank.  
  
    ```  
    CREATE TABLE Cust(  
            CustomerID  nchar(5) Primary Key,  
            CompanyName nvarchar(40) NOT NULL ,  
            ContactName nvarchar(60) NULL)  
    GO  
  
    CREATE TABLE Ord(  
       OrderID    int Primary Key,  
       CustomerID nchar(5) Foreign Key REFERENCES Cust(CustomerID))  
    GO  
    ```  
  
4.  Fügen Sie diese Beispieldaten hinzu:  
  
    ```  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ALFKI', N'Alfreds Futterkiste', N'Maria Anders')  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ANATR', N'Ana Trujillo Emparedados y helados', N'Ana Trujillo')  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ANTON', N'Antonio Moreno Taquer??a', N'Antonio Moreno')  
  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(1, N'ALFKI')  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(2, N'ANATR')  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(3, N'ANTON')  
    ```  
  
5.  Kopieren Sie das oben stehende DiffGram, und fügen Sie es in eine Textdatei ein. Speichern Sie die Datei als MyDiffGram.xml in demselben Ordner, den Sie in Schritt 1 verwendet haben.  
  
6.  Speichern Sie den C#-Code (DiffgramSample.cs) aus dem Beispiel oben im selben Ordner, in dem DiffGramSchema.xml und MyDiffGram.xml aus den vorherigen Schritten gespeichert wurden.  
  
    > [!NOTE]  
    >  Sie müssen den Namen der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanz in der Verbindungszeichenfolge von '`MyServer`' in den tatsächlichen Namen Ihrer installierten Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ändern.  
  
     Wenn Sie die Dateien in einem anderen Ordner speichern, müssen Sie den Code bearbeiten und den entsprechenden Verzeichnispfad für das Zuordnungsschema angeben.  
  
7.  Kompilieren Sie den Code. Verwenden Sie zur Kompilierung des Codes an der Eingabeaufforderung die folgende Zeichenfolge:  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DiffgramSample.cs  
    ```  
  
     Dadurch wird eine ausführbare Datei (DiffgramSample.exe) erstellt.  
  
8.  Führen Sie DiffgramSample.exe an der Eingabeaufforderung aus.  
  
## <a name="see-also"></a>Weitere Informationen  
 [DiffGram-Beispiele &#40;SQLXML 4,0&#41;](diffgram-examples-sqlxml-4-0.md)  
  
  
