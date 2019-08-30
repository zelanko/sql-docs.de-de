---
title: Verwenden von XML-Schemas | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/11/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- XML [SMO]
ms.assetid: 9d04de01-efeb-4b2d-8c28-3234bc7ff2f3
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: e15ac5d5a028657a8f5ee30c8577d2990b1e31c6
ms.sourcegitcommit: f3f83ef95399d1570851cd1360dc2f072736bef6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2019
ms.locfileid: "70148375"
---
# <a name="using-xml-schemas"></a>Verwenden von XML-Schemas

[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  Die XML-Programmierung in SMO ist auf die Bereitstellung von XML-Datentypen, XML-Namespaces und eine einfache Indizierung für XML-Datentypspalten beschränkt.  
  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] stellt systemeigenen Speicher für XML-Dokument Instanzen bereit. Über XML-Schemas können Sie komplexe XML-Datentypen definieren, die für die Validierung von XML-Dokumenten verwendet werden können, um die Datenintegrität sicherzustellen. Das XML-Schema wird im <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection>-Objekt definiert.  
  
## <a name="example"></a>Beispiel  
 Zum Verwenden eines angegebenen Codebeispiels müssen Sie die Programmierumgebung, Programmiervorlage und die zu verwendende Programmiersprache auswählen, um Ihre Anwendung zu erstellen. Weitere Informationen finden Sie unter [Erstellen eines Visual C&#35; SMO-Projekts in Visual Studio .net](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="creating-an-xml-schema-in-visual-basic"></a>Erstellen eines XML-Schemas in Visual Basic  
 Dieses Codebeispiel zeigt, wie ein XML-Schema mithilfe des <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection>-Objekts erstellt wird. Die <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection.Text%2A>-Eigenschaft, die die XML-Schemaauflistung definiert, enthält mehrere doppelte Anführungszeichen. Diese werden durch die `chr(34)` -Zeichenfolge ersetzt.  
  
```VBNET
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server()
'Reference the AdventureWorks2012 2008R2 database.
Dim db As Database
db = srv.Databases("AdventureWorks2012")
'Define an XmlSchemaCollection object by supplying the parent database and name arguments in the constructor.
Dim xsc As XmlSchemaCollection
xsc = New XmlSchemaCollection(db, "MySampleCollection")
xsc.Text = "\<schema xmlns=" + Chr(34) + "http://www.w3.org/2001/XMLSchema" + Chr(34) + "  xmlns:ns=" + Chr(34) + "http://ns" + Chr(34) + ">\<element name=" + Chr(34) + "e" + Chr(34) + " type=" + Chr(34) + "dateTime" + Chr(34) + "/></schema>"
'Create the XML schema collection on the instance of SQL Server.
xsc.Create()
```
  
## <a name="creating-an-xml-schema-in-visual-c"></a>Erstellen eines XML-Schemas in Visual C#  
 Dieses Codebeispiel zeigt, wie ein XML-Schema mithilfe des <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection>-Objekts erstellt wird. Die <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection.Text%2A>-Eigenschaft, die die XML-Schemaauflistung definiert, enthält mehrere doppelte Anführungszeichen. Diese werden durch die `chr(34)` -Zeichenfolge ersetzt.  
  
```csharp  
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
            xsc.Text = "\<schema xmlns=" + Strings.Chr(34) + "http://www.w3.org/2001/XMLSchema" + Strings.Chr(34) + " xmlns:ns=" + Strings.Chr(34) + "http://ns" + Strings.Chr(34) + ">\<element name=" + Strings.Chr(34) + "e" + Strings.Chr(34) + " type=" + Strings.Chr(34) + "dateTime" + Strings.Chr(34) + "/></schema>";  
            //Create the XML schema collection on the instance of SQL Server.   
            xsc.Create();  
        }  
```  
  
## <a name="creating-an-xml-schema-in-powershell"></a>Erstellen eines XML-Schemas in PowerShell  
 Dieses Codebeispiel zeigt, wie ein XML-Schema mithilfe des <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection>-Objekts erstellt wird. Die <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection.Text%2A>-Eigenschaft, die die XML-Schemaauflistung definiert, enthält mehrere doppelte Anführungszeichen. Diese werden durch die `chr(34)` -Zeichenfolge ersetzt.  
  
```powershell   
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
  
  
