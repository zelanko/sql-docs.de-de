---
description: Beibehaltungsszenario für XML-Recordsets
title: Persistenzszenario für XML-Recordsets | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- XML persistence [ADO], persistence scenario
ms.assetid: 353d569a-043a-4397-9ee6-564c4af8d5f6
author: rothja
ms.author: jroth
ms.openlocfilehash: 91066d8dd42d1bcd4a11aab093661a9061a7d7d1
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88978821"
---
# <a name="xml-recordset-persistence-scenario"></a>Beibehaltungsszenario für XML-Recordsets
In diesem Szenario erstellen Sie eine ASP-Anwendung (Active Server Pages), mit der der Inhalt eines Recordset-Objekts direkt in das ASP-Antwortobjekt gespeichert wird.  
  
> [!NOTE]
>  Für dieses Szenario ist es erforderlich, dass auf dem Server Internet Information Server 5,0 (IIS) oder höher installiert ist.  
  
 Das zurückgegebene Recordset wird in Internet Explorer unter Verwendung eines [DataControl-Objekts (RDS)](../../reference/rds-api/datacontrol-object-rds.md)angezeigt.  
  
 Zum Erstellen dieses Szenarios sind die folgenden Schritte erforderlich:  
  
-   Einrichten der Anwendung  
  
-   Daten erhalten  
  
-   Senden der Daten  
  
-   Empfangen und Anzeigen der Daten  
  
## <a name="step-1-set-up-the-application"></a>Schritt 1: Einrichten der Anwendung  
 Erstellen Sie ein virtuelles IIS-Verzeichnis mit dem Namen "xmlpersistent" und Skript Berechtigungen. Erstellen Sie zwei neue Textdateien in dem Ordner, in den das virtuelle Verzeichnis verweist, eine mit dem Namen "XMLResponse. asp", die andere mit dem Namen "Default.htm".  
  
## <a name="step-2-get-the-data"></a>Schritt 2: Daten erhalten  
 In diesem Schritt schreiben Sie den Code, um ein ADO-Recordset zu öffnen und darauf vorzubereiten, es an den Client zu senden. Öffnen Sie die Datei XMLResponse. ASP mit einem Text-Editor, z. b. Notepad, und fügen Sie den folgenden Code ein.  
  
```  
<%@ language="VBScript" %>  
  
<!-- #include file='adovbs.inc' -->  
  
<%  
  Dim strSQL, strCon  
  Dim adoRec   
  Dim adoCon   
  Dim xmlDoc   
  
  ' You will need to change "MySQLServer" below to the name of the SQL   
  ' server machine to which you want to connect.  
  strCon = "Provider=sqloledb;Data Source=MySQLServer;Initial Catalog=Pubs;Integrated Security=SSPI;"  
  Set adoCon = server.createObject("ADODB.Connection")  
  adoCon.Open strCon  
  
  strSQL = "SELECT Title, Price FROM Titles ORDER BY Price"  
  Set adoRec = Server.CreateObject("ADODB.Recordset")  
  adoRec.Open strSQL, adoCon, adOpenStatic, adLockOptimistic, adCmdText  
```  
  
 Stellen Sie sicher, dass Sie den Wert des `Data Source` Parameters in in `strCon` den Namen Ihres Microsoft SQL Server Computers ändern.  
  
 Lassen Sie die Datei geöffnet, und fahren Sie mit dem nächsten Schritt fort.  
  
## <a name="step-3-send-the-data"></a>Schritt 3: Senden der Daten  
 Nachdem Sie nun über ein Recordset verfügen, müssen Sie es an den Client senden, indem Sie es als XML im ASP-Antwortobjekt speichern. Fügen Sie den folgenden Code am Ende von "XMLResponse. asp" ein.  
  
```  
  Response.ContentType = "text/xml"  
  Response.Expires = 0  
  Response.Buffer = False  
  
  Response.Write "<?xml version='1.0'?>" & vbNewLine  
  adoRec.save Response, adPersistXML  
  adoRec.Close  
  Set adoRec=Nothing  
%>  
```  
  
 Beachten Sie, dass das ASP-Antwortobjekt als Ziel für die [Speichermethode](../../reference/ado-api/save-method.md)Recordset angegeben wird. Das Ziel der Save-Methode kann ein beliebiges Objekt sein, das die IStream-Schnittstelle unterstützt, z. b. ein ADO [(ADO)](../../reference/ado-api/stream-object-ado.md)-Objekt oder ein Dateiname, der den gesamten Pfad enthält, in dem das Recordset gespeichert werden soll.  
  
 Speichern und schließen Sie XMLResponse. ASP, bevor Sie mit dem nächsten Schritt fortfahren. Kopieren Sie außerdem die Datei "adovsb. Inc" aus dem Standard Installationsordner der ADO-Bibliothek in den Ordner, in dem Sie die Datei "XMLResponse. asp" gespeichert haben.  
  
## <a name="step-4-receive-and-display-the-data"></a>Schritt 4: empfangen und Anzeigen der Daten  
 In diesem Schritt erstellen Sie eine HTML-Datei mit einem eingebetteten Objekt des [DataControl-Objekts (RDS)](../../reference/rds-api/datacontrol-object-rds.md) , das auf die Datei XMLResponse. ASP zeigt, um das Recordset zu erhalten. Öffnen Sie default.htm mit einem Text-Editor, z. b. Notepad, und fügen Sie den folgenden Code hinzu. Ersetzen Sie "SQLServer" in der URL durch den Namen Ihres Servers.  
  
```  
<HTML>  
<HEAD><TITLE>ADO Recordset Persistence Sample</TITLE></HEAD>  
<BODY>  
  
<TABLE DATASRC="#RDC1" border="1">  
  <TR>  
<TD><SPAN DATAFLD="title"></SPAN></TD>  
<TD><SPAN DATAFLD="price"></SPAN></TD>  
  </TR>  
</TABLE>  
<OBJECT CLASSID="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33" ID="RDC1">  
   <PARAM NAME="URL" VALUE="XMLResponse.asp">  
</OBJECT>  
  
</BODY>  
</HTML>  
```  
  
 Schließen Sie die Datei default.htm, und speichern Sie Sie im selben Ordner, in dem Sie "XMLResponse. asp" gespeichert haben. Öffnen Sie in Internet Explorer 4,0 oder höher die URL https://*SQLServer*default.htm/XMLPersist/, und beobachten Sie die Ergebnisse. Die Daten werden in einer gebundenen DHTML-Tabelle angezeigt. Öffnen Sie nun die URL https:// *SQLServer* /XMLPersist/XMLResponse.ASP, und beobachten Sie die Ergebnisse. Der XML-Code wird angezeigt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Save-Methode](../../reference/ado-api/save-method.md)   
 [Beibehalten von Datensätzen im XML-Format](./persisting-records-in-xml-format.md)