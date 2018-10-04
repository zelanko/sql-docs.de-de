---
title: Ausführen von XPath-Abfragen mit Namespaces (verwaltete SQLXML Klassen) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 03635a138874c010225174e854bd6e5e3c13d3ca
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48200910"
---
# <a name="executing-xpath-queries-with-namespaces-sqlxml-managed-classes"></a>Ausführen von XPath-Abfragen mit Namespaces (Verwaltete SQLXML-Klassen)
  XPath-Abfragen können Namespaces enthalten. Wenn die Schemaelemente mit Namespace angegeben wurden (einen Zielnamespace verwenden), dann müssen mit diesem Schema ausgeführte XPath-Abfragen diesen Namespace angeben.  
  
 Weil die Verwendung des Platzhalterzeichens (*) in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0 nicht unterstützt wird, müssen Sie die XPath-Abfrage mithilfe eines Namespacepräfixes angeben. Um das Präfix aufzulösen, verwenden Sie die Namespaces-Eigenschaft, die Namespacebindung an.  
  
 Im folgenden Beispiel gibt die XPath-Abfrage Namespaces mit dem Platzhalterzeichen (\*) und die local-name() and Namespace-URI()=' XPath-Funktionen. Diese XPath-Abfrage gibt alle Elemente zurück, bei denen der lokale Name `Employee` und der Namespace-URI `urn:myschema:Contacts` lautet:  
  
```  
/*[local-name() = 'Contact' and namespace-uri() = 'urn:myschema:Contacts']  
```  
  
 Geben Sie in SQLXML 4.0 diese XPath-Abfrage mit einem Namespacepräfix an. Ein Beispiel ist `x:Contact`, wobei `x` für das Namespacepräfix steht. Betrachten Sie folgendes XSD-Schema:  
  
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
  
 Da den Target Namespace dieses Schemas definiert wird, muss eine XPath-Abfrage (z. B. "Employee") mit diesem Schema den Namespace enthalten.  
  
 Die folgende C#-Beispielanwendung führt mit dem angegebenen XSD-Schema (MySchema.xml) eine XPath-Abfrage aus. Um das Präfix aufzulösen, geben Sie die Namespacebindung mithilfe der Namespaces-Eigenschaft des SqlXmlCommand-Objekt.  
  
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
  
2.  Speichern Sie die c#-Code (DocSample.cs), der bereitgestellt wird, in diesem Beispiel im selben Ordner, in dem das Schema gespeichert ist. (Wenn Sie die Dateien in einem anderen Ordner speichern, müssen Sie den Code bearbeiten und den entsprechenden Verzeichnispfad für das Zuordnungsschema angeben.)  
  
3.  Kompilieren Sie den Code. Verwenden Sie zur Kompilierung des Codes an der Eingabeaufforderung die folgende Zeichenfolge:  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DocSample.cs  
    ```  
  
     Dadurch wird eine ausführbare Datei (DocSample.exe) erstellt.  
  
4.  Führen Sie DocSample.exe an der Eingabeaufforderung aus.  
  
  
