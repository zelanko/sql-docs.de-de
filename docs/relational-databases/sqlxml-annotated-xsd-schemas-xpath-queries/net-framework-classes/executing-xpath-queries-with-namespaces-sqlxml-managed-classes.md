---
title: Ausführen von XPath-Abfragen mit Namespaces (verwaltete SQLXML-Klassen) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- namespaces property
- XPath queries [SQLXML], SQLXML Managed Classes
- queries [SQLXML], SQLXML Managed Classes
- XPath queries [SQLXML], namespaces
- Managed Classes [SQLXML], executing XPath queries
- SQLXML Managed Classes, executing XPath queries
- namespaces [SQLXML], XPath queries
ms.assetid: c6fc46d8-6b42-4992-a8f1-a8d4b8886e6e
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 884ea584ec54425d6d0ed2d134e9181cd4d56678
ms.sourcegitcommit: 2a06c87aa195bc6743ebdc14b91eb71ab6b91298
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2019
ms.locfileid: "72909221"
---
# <a name="executing-xpath-queries-with-namespaces-sqlxml-managed-classes"></a>Ausführen von XPath-Abfragen mit Namespaces (Verwaltete SQLXML-Klassen)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  XPath-Abfragen können Namespaces enthalten. Wenn die Schemaelemente mit Namespace angegeben wurden (einen Zielnamespace verwenden), dann müssen mit diesem Schema ausgeführte XPath-Abfragen diesen Namespace angeben.  
  
 Weil die Verwendung des Platzhalterzeichens (*) in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0 nicht unterstützt wird, müssen Sie die XPath-Abfrage mithilfe eines Namespacepräfixes angeben. Um das Präfix aufzulösen, geben Sie mit der Namespace-Eigenschaft die Namespace Bindung an.  
  
 Im folgenden Beispiel gibt die XPath-Abfrage Namespaces mit dem Platzhalter Zeichen (\*) und den XPath-Funktionen local-Name () und Namespace-URI () an. Diese XPath-Abfrage gibt alle Elemente zurück, bei denen der lokale Name **Employee** ist, und der Namespace-URI ist **urn: MySchema: Contacts**:  
  
```  
/*[local-name() = 'Contact' and namespace-uri() = 'urn:myschema:Contacts']  
```  
  
 Geben Sie in SQLXML 4.0 diese XPath-Abfrage mit einem Namespacepräfix an. Ein Beispiel ist " **x:Contact**", wobei " **x** " das Namespace Präfix ist. Betrachten Sie folgendes XSD-Schema:  
  
```  
<schema xmlns="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema"  
            xmlns:con="urn:myschema:Contacts"  
            targetNamespace="urn:myschema:Contacts">  
<complexType name="ContactType">  
  <attribute name="CID" sql:field="ContactID" type="ID"/>  
  <attribute name="FName" sql:field="FirstName" type="string"/>  
  <attribute name="LName" sql:field="LastName"/>   
</complexType>  
<element name="Contact" type="con:ContactType" sql:relation="Person.Contact"/>  
</schema>  
```  
  
 Da dieses Schema den Ziel Namespace definiert, muss eine XPath-Abfrage (z. b. "Employee") für dieses Schema den Namespace enthalten.  
  
 Die folgende C#-Beispielanwendung führt mit dem angegebenen XSD-Schema (MySchema.xml) eine XPath-Abfrage aus. Um das Präfix aufzulösen, geben Sie die Namespace Bindung mithilfe der Namespaces-Eigenschaft des SqlXmlCommand-Objekts an.  
  
> [!NOTE]  
>  Im Code müssen Sie den Namen der Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in der Verbindungszeichenfolge bereitstellen.  
  
```  
using System;  
using Microsoft.Data.SqlXml;  
using System.IO;  
class Test  
{  
      static string ConnString = "Provider=SQLOLEDB;Server=(local);database=AdventureWorks;Integrated Security=SSPI";  
      public static int testXPath()  
      {  
         //Stream strm;  
         SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
         cmd.CommandText = "x:Contact[@CID='1']";  
         cmd.CommandType = SqlXmlCommandType.XPath;  
         cmd.RootTag = "ROOT";  
         cmd.Namespaces = "xmlns:x='urn:myschema:Contacts'";  
         cmd.SchemaPath = "MySchema.xml";  
         using (Stream strm = cmd.ExecuteStream()){  
            using (StreamReader sr = new StreamReader(strm)){  
               Console.WriteLine(sr.ReadToEnd());  
            }  
         }  
         return 0;  
      }  
      public static int Main(String[] args)  
      {  
         testXPath();  
         return 0;  
      }  
   }  
```  
  
 Um das Beispiel zu testen, muss auf dem Computer [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework installiert sein.  
  
### <a name="to-test-the-application"></a>So testen Sie die Anwendung  
  
1.  Speichern Sie das oben in diesem Beispiel bereitgestellte XSD-Schema (MySchema.xml) in einem Ordner.  
  
2.  Speichern Sie C# den Code (DocSample.cs), der in diesem Beispiel bereitgestellt wird, im selben Ordner, in dem das Schema gespeichert ist. (Wenn Sie die Dateien in einem anderen Ordner speichern, müssen Sie den Code bearbeiten und den entsprechenden Verzeichnispfad für das Zuordnungsschema angeben.)  
  
3.  Kompilieren Sie den Code. Verwenden Sie zur Kompilierung des Codes an der Eingabeaufforderung die folgende Zeichenfolge:  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DocSample.cs  
    ```  
  
     Dadurch wird eine ausführbare Datei (DocSample.exe) erstellt.  
  
4.  Führen Sie DocSample.exe an der Eingabeaufforderung aus.  

