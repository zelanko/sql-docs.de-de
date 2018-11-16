---
title: 'Schritt 6: Änderungen werden an den Server gesendet (RDS-Tutorial) | Microsoft-Dokumentation'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS tutorial [ADO], changes sent to server
ms.assetid: b1e927d6-7d50-4978-9eef-045043cdce7a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8bfeb9ad607fc35c055e025fcc67435323d3143e
ms.sourcegitcommit: 1a5448747ccb2e13e8f3d9f04012ba5ae04bb0a3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/12/2018
ms.locfileid: "51559967"
---
# <a name="step-6-changes-are-sent-to-the-server-rds-tutorial"></a>Schritt 6: Änderungen werden an den Server gesendet (RDS-Tutorial)
Wenn die **Recordset** Objekt bearbeitet wird, können alle Änderungen (d. h. Zeilen, die hinzugefügt, geändert oder gelöscht werden) an den Server gesendet werden.  
  
> [!NOTE]
>  Das Standardverhalten von RDS kann implizit mit ADO-Objekte und der Microsoft OLE DB-Anbieter für Remoting aufgerufen werden. Abfragen können zurückgeben **Recordset**s, und bearbeitete **Recordset**s kann die Datenquelle aktualisieren. In diesem Tutorial RDS mit ADO-Objekten nicht aufgerufen, aber dies ist, wie es aussehen würde, wenn dies der Fall:  
  
```vb
Dim rs as New ADODB.Recordset  
rs. "SELECT * FROM Authors","=MS Remote;=Pubs;" & _  
=https://yourServer;=SQLOLEDB;"  
...              ' Edit the Recordset.  
rs.   ' The equivalent of   
...  
```  
  
 **Teil A** annehmen, dass für diesen Fall an, die Sie, nur verwendet haben die [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) und eine **Recordset** Objekt jetzt zugeordnet ist die **RDS. DataControl**. Die [SubmitChanges](../../../ado/reference/rds-api/submitchanges-method-rds.md) Methode aktualisiert die Datenquelle mit Änderungen an der **Recordset** Objekt, wenn die [Server](../../../ado/reference/rds-api/server-property-rds.md) und [Connect](../../../ado/reference/rds-api/connect-property-rds.md) Eigenschaften werden immer noch festgelegt werden.  
  
```vb
Sub RDSTutorial6A()  
Dim DC as New RDS.DataControl  
Dim RS as ADODB.Recordset  
DC. = "https://yourServer"  
DC. = "DSN=Pubs"  
DC. = "SELECT * FROM Authors"  
DC.  
...  
Set RS = DC.  
   ' Edit the Recordset.  
...  
DC.  
...  
```  
  
 **Teil B** Alternativ könnten Sie den Server mit aktualisieren die [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) Objekt, das Angeben einer Verbindung und eine **Recordset** Objekt.  
  
```vb
Sub RDSTutorial6B()  
Dim DS As New RDS.DataSpace  
Dim RS As ADODB.Recordset  
Dim DC As New RDS.DataControl  
Dim DF As Object  
Dim blnStatus As Boolean  
Set DF = DS.("RDSServer.DataFactory", "https://yourServer")  
Set RS = DF. ("DSN=Pubs", "SELECT * FROM Authors")  
DC. = RS    ' Visual controls can now bind to DC.  
    ' Edit the Recordset.  
blnStatus = DF."DSN=Pubs", RS  
End Sub  
```  
  
 **Dies ist das Ende des Tutorials.**  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="see-also"></a>Siehe auch  
 [Microsoft OLE DB Remoting-Anbieter (ADO-Dienstanbieter)](../../../ado/guide/appendixes/microsoft-ole-db-remoting-provider-ado-service-provider.md)   
 [RDS-Tutorial](../../../ado/guide/remote-data-service/rds-tutorial.md)   
 [RDS-Tutorial (VBScript)](../../../ado/guide/remote-data-service/rds-tutorial-vbscript.md)   
