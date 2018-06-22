---
title: Verwenden von XML-Schemas mit | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- XML [SMO]
ms.assetid: 9d04de01-efeb-4b2d-8c28-3234bc7ff2f3
caps.latest.revision: 38
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f59dd029b5dc0311323efa85c852c611d787b894
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36060253"
---
# <a name="using-xml-schemas"></a>Verwenden von XML-Schemas
  Die XML-Programmierung in SMO ist auf die Bereitstellung von XML-Datentypen, XML-Namespaces und eine einfache Indizierung für XML-Datentypspalten beschränkt.  
  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Stellt systemeigenen Speicher für XML-Dokumentinstanzen bereit. Über XML-Schemas können Sie komplexe XML-Datentypen definieren, die für die Validierung von XML-Dokumenten verwendet werden können, um die Datenintegrität sicherzustellen. Das XML-Schema wird im <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection>-Objekt definiert.  
  
## <a name="example"></a>Beispiel  
 Zum Verwenden eines angegebenen Codebeispiels müssen Sie die Programmierumgebung, Programmiervorlage und die zu verwendende Programmiersprache auswählen, um Ihre Anwendung zu erstellen. Weitere Informationen finden Sie unter [Erstellen eines Visual Basic SMO-Projekts in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) oder [Erstellen eines Visual C&#35; SMO-Projekts in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="creating-an-xml-schema-in-visual-basic"></a>Erstellen eines XML-Schemas in Visual Basic  
 In diesem Codebeispiel wird veranschaulicht, wie zum Erstellen eines XML-Schemas mit der <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection> Objekt. Die <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection.Text%2A>-Eigenschaft, die die XML-Schemaauflistung definiert, enthält mehrere doppelte Anführungszeichen. Diese werden durch die `chr(34)` -Zeichenfolge ersetzt.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBXMLSchema1](SMO How to#SMO_VBXMLSchema1)]  -->  
  
## <a name="creating-an-xml-schema-in-visual-c"></a>Erstellen eines XML-Schemas in Visual C#  
 In diesem Codebeispiel wird veranschaulicht, wie zum Erstellen eines XML-Schemas mit der <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection> Objekt. Die <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection.Text%2A>-Eigenschaft, die die XML-Schemaauflistung definiert, enthält mehrere doppelte Anführungszeichen. Diese werden durch die `chr(34)` -Zeichenfolge ersetzt.  
  
```  
{  
            //Connect to the local, default instance of SQL Server.   
            Server srv = default(Server);  
            srv = new Server();  
            //Reference the AdventureWorks2012 database.   
            Database db = default(Database);  
            db = srv.Databases["AdventureWorks2012"];  
            //Define an XmlSchemaCollection object by supplying the parent  
            // database and name arguments in the constructor.   
            XmlSchemaCollection xsc = default(XmlSchemaCollection);  
            xsc = new XmlSchemaCollection(db, "MySampleCollection");  
            xsc.Text = "<schema xmlns=" + Strings.Chr(34) + "http://www.w3.org/2001/XMLSchema" + Strings.Chr(34) + " xmlns:ns=" + Strings.Chr(34) + "http://ns" + Strings.Chr(34) + "><element name=" + Strings.Chr(34) + "e" + Strings.Chr(34) + " type=" + Strings.Chr(34) + "dateTime" + Strings.Chr(34) + "/></schema>";  
            //Create the XML schema collection on the instance of SQL Server.   
            xsc.Create();  
        }  
```  
  
## <a name="creating-an-xml-schema-in-powershell"></a>Erstellen eines XML-Schemas in PowerShell  
 In diesem Codebeispiel wird veranschaulicht, wie zum Erstellen eines XML-Schemas mit der <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection> Objekt. Die <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection.Text%2A>-Eigenschaft, die die XML-Schemaauflistung definiert, enthält mehrere doppelte Anführungszeichen. Diese werden durch die `chr(34)` -Zeichenfolge ersetzt.  
  
```  
#Get a server object which corresponds to the default instance replace LocalMachine with the physical server  
cd \sql\LocalHost  
$srv = get-item default  
  
#Reference the AdventureWorks database.  
$db = $srv.Databases["AdventureWorks2012"]  
  
#Create a new schema collection  
$xsc = New-Object -TypeName Microsoft.SqlServer.Management.SMO.XmlSchemaCollection `  
-argumentlist $db,"MySampleCollection"  
  
#Add the xml  
$dq = '"' # the double quote character  
$xsc.Text = "<schema xmlns=" + $dq + "http://www.w3.org/2001/XMLSchema" + $dq + `  
"  xmlns:ns=" + $dq + "http://ns" + $dq + "><element name=" + $dq + "e" + $dq +`  
 " type=" + $dq + "dateTime" + $dq + "/></schema>"  
  
#Create the XML schema collection on the instance of SQL Server.  
$xsc.Create()  
```  
  
  