---
description: 'Schritt 6: Änderungen werden an den Server gesendet (RDS-Tutorial)'
title: 'Schritt 6: Änderungen werden an den Server gesendet (RDS-Tutorial) | Microsoft-Dokumentation'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS tutorial [ADO], changes sent to server
ms.assetid: b1e927d6-7d50-4978-9eef-045043cdce7a
author: rothja
ms.author: jroth
ms.openlocfilehash: 33a80f1cf59ff314236e69085c7625521d6f721f
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88977471"
---
# <a name="step-6-changes-are-sent-to-the-server-rds-tutorial"></a>Schritt 6: Änderungen werden an den Server gesendet (RDS-Tutorial)
Wenn das **Recordset** -Objekt bearbeitet wird, können alle Änderungen (d. h. hinzugefügte, geänderte oder gelöschte Zeilen) an den Server zurückgesendet werden.  
  
> [!NOTE]
>  Das Standardverhalten von RDS kann implizit mit ADO-Objekten und dem Microsoft OLE DB Remoting-Anbieter aufgerufen werden. Abfragen können **Recordsets**zurückgeben, und bearbeitete **Recordsets**können die Datenquelle aktualisieren. In diesem Lernprogramm wird RDS nicht mit ADO-Objekten aufgerufen, aber dies sieht wie folgt aus:  
  
```vb
Dim rs as New ADODB.Recordset  
rs. "SELECT * FROM Authors","=MS Remote;=Pubs;" & _  
=https://yourServer;=SQLOLEDB;"  
...              ' Edit the Recordset.  
rs.   ' The equivalent of   
...  
```  
  
 **Teil A** Angenommen, Sie haben nur [RDS verwendet. DataControl](../../reference/rds-api/datacontrol-object-rds.md) und ein **Recordset** -Objekt sind nun dem RDS zugeordnet **. DataControl**. Die [SubmitChanges](../../reference/rds-api/submitchanges-method-rds.md) -Methode aktualisiert die Datenquelle mit allen Änderungen am **Recordset** -Objekt, wenn die [Server](../../reference/rds-api/server-property-rds.md) -und [Verbindungs](../../reference/rds-api/connect-property-rds.md) Eigenschaften noch festgelegt sind.  
  
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
  
 **Teil B** Alternativ können Sie den Server mit dem [RDSServer. DataFactory](../../reference/rds-api/datafactory-object-rdsserver.md) -Objekt aktualisieren, indem Sie eine Verbindung und ein **Recordset** -Objekt angeben.  
  
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
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Microsoft OLE DB Remoting Provider (ADO-Dienstanbieter)](../appendixes/microsoft-ole-db-remoting-provider-ado-service-provider.md)   
 [RDS-Tutorial](./rds-tutorial.md)   
 [RDS-Tutorial (VBScript)](./rds-tutorial-vbscript.md)