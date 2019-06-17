---
title: Verwenden von XML-Schemas mit | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- XML [SMO]
ms.assetid: 9d04de01-efeb-4b2d-8c28-3234bc7ff2f3
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f65643152bb069c703fe3a63e58ad669f3d3e322
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62626863"
---
# <a name="using-xml-schemas"></a>Verwenden von XML-Schemas
  Die XML-Programmierung in SMO ist auf die Bereitstellung von XML-Datentypen, XML-Namespaces und eine einfache Indizierung für XML-Datentypspalten beschränkt.  
  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Stellt systemeigenen Speicher für XML-Dokumentinstanzen bereit. Über XML-Schemas können Sie komplexe XML-Datentypen definieren, die für die Validierung von XML-Dokumenten verwendet werden können, um die Datenintegrität sicherzustellen. Das XML-Schema wird im <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection>-Objekt definiert.  
  
## <a name="example"></a>Beispiel  
 Zum Verwenden eines angegebenen Codebeispiels müssen Sie die Programmierumgebung, Programmiervorlage und die zu verwendende Programmiersprache auswählen, um Ihre Anwendung zu erstellen. Weitere Informationen finden Sie unter [erstellen Sie eine Visual Basic-SMO-Projekts in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) oder [Erstellen eines Visual C&#35; SMO-Projekts in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="creating-an-xml-schema-in-visual-basic"></a>Erstellen eines XML-Schemas in Visual Basic  
 Dieses Codebeispiel zeigt, wie ein XML-Schema mithilfe des <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection>-Objekts erstellt wird. Die <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection.Text%2A>-Eigenschaft, die die XML-Schemaauflistung definiert, enthält mehrere doppelte Anführungszeichen. Diese werden durch die `chr(34)` -Zeichenfolge ersetzt.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBXMLSchema1](SMO How to#SMO_VBXMLSchema1)]  -->  
  
## <a name="creating-an-xml-schema-in-visual-c"></a>Erstellen eines XML-Schemas in Visual C#  
 Dieses Codebeispiel zeigt, wie ein XML-Schema mithilfe des <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection>-Objekts erstellt wird. Die <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection.Text%2A>-Eigenschaft, die die XML-Schemaauflistung definiert, enthält mehrere doppelte Anführungszeichen. Diese werden durch die `chr(34)` -Zeichenfolge ersetzt.  
  
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
 Dieses Codebeispiel zeigt, wie ein XML-Schema mithilfe des <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection>-Objekts erstellt wird. Die <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection.Text%2A>-Eigenschaft, die die XML-Schemaauflistung definiert, enthält mehrere doppelte Anführungszeichen. Diese werden durch die `chr(34)` -Zeichenfolge ersetzt.  
  
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
  
  
