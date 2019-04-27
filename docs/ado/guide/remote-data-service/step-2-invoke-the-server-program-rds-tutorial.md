---
title: 'Schritt 2: Rufen Sie die Server-Anwendung (RDS-Tutorial) | Microsoft-Dokumentation'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS tutorial [ADO], invoking server program
ms.assetid: 5e74c2da-65ee-4de4-8b41-6eac45c3632e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a64e45f68003948f0d0f45d3932c1edf9b94972a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62675812"
---
# <a name="step-2-invoke-the-server-program-rds-tutorial"></a>Schritt 2: Aufrufen eines Serverprogramms (RDS-Tutorial)
Beim Aufruf einer Methode auf dem Client *Proxy*, das tatsächliche Programm auf dem Server führt die Methode. In diesem Schritt müssen Sie eine Abfrage auf dem Server ausführen.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 **Teil A** bei Verwendung von nicht waren [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) in diesem Tutorial wäre am einfachsten, diesen Schritt auszuführen, verwenden die [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) Objekt. Die **RDS. DataControl** verbindet den vorherigen Schritt erstellen Sie einen Proxy für den mit diesem Schritt die Ausgabe der Abfrage.  
  
 Legen Sie die **RDS. DataControl** Objekt [Server](../../../ado/reference/rds-api/server-property-rds.md) Eigenschaft identifizieren, in denen die Server-Anwendung instanziiert werden soll; die [Connect](../../../ado/reference/rds-api/connect-property-rds.md) Eigenschaft, um die Verbindungszeichenfolge für den Zugriff auf die Datenquelle anzugeben und die [SQL](../../../ado/reference/rds-api/sql-property.md) -Eigenschaft Befehlstext der Abfrage an. Geben Sie dann die [aktualisieren](../../../ado/reference/rds-api/refresh-method-rds.md) Methode bewirkt, dass der eine Verbindung mit der Datenquelle herstellen, Abrufen von Zeilen, die von der Abfrage angegebene Serverprogramm und Zurückgeben einer **Recordset** Objekt an den Client.  
  
 In diesem Tutorial verwendet nicht die **RDS. DataControl**, aber dies ist, wie es aussehen würde, wenn dies der Fall:  
  
```vb
Sub RDSTutorial2A()  
   Dim DC as New RDS.DataControl  
   DC.Server = "https://yourServer"  
   DC.Connect = "DSN=Pubs"  
   DC.SQL = "SELECT * FROM Authors"  
   DC.Refresh  
...  
```  
  
 Noch ist das Tutorial RDS mit ADO-Objekte aufrufen, dies ist jedoch wie es aussehen würde, wenn dies der Fall:  
  
```vb
Dim rs as New ADODB.Recordset  
rs.Open "SELECT * FROM Authors","Provider=MS Remote;Data Source=Pubs;" & _  
        "Remote Server=https://yourServer;Remote Provider=SQLOLEDB;"  
```  
  
 **Teil B** die allgemeine Methode zur Durchführung dieses Schrittes ist zum Aufrufen der **RDSServer.DataFactory** Objekt [Abfrage](../../../ado/reference/rds-api/query-method-rds.md) Methode. Diese Methode verwendet eine Verbindungszeichenfolge, die zum Herstellen einer Verbindung mit einer Datenquelle verwendet wird, und einen Befehlstext, die verwendet wird, zur Angabe der Zeilen aus der Datenquelle zurückgegeben werden.  
  
 Dieses Tutorial verwendet die **DataFactory** Objekt **Abfrage** Methode:  
  
```vb
Sub RDSTutorial2B()  
   Dim DS as New RDS.DataSpace  
   Dim DF  
   Dim RS as ADODB.Recordset  
   Set DF = DS.CreateObject("RDSServer.DataFactory", "https://yourServer")  
   Set RS = DF.Query ("DSN=Pubs", "SELECT * FROM Authors")  
...  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Schritt 3: Server erhält ein Recordset (RDS-Tutorial)](../../../ado/guide/remote-data-service/step-3-server-obtains-a-recordset-rds-tutorial.md)   
 [RDS-Tutorial (VBScript)](../../../ado/guide/remote-data-service/rds-tutorial-vbscript.md)   
