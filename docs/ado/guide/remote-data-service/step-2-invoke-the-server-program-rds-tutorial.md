---
description: 'Schritt 2: Serverprogramm aufrufen (RDS-Tutorial)'
title: 'Schritt 2: Aufrufen des Server Programms (RDS-Tutorial) | Microsoft-Dokumentation'
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 19f16da3e3501a179bfb28529a9b1a14486aad20
ms.sourcegitcommit: c4d564435c008e2c92035efd2658172f20f07b2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88759150"
---
# <a name="step-2-invoke-the-server-program-rds-tutorial"></a>Schritt 2: Serverprogramm aufrufen (RDS-Tutorial)
Wenn Sie eine Methode auf dem Client *Proxy*aufrufen, führt das eigentliche Programm auf dem Server die-Methode aus. In diesem Schritt führen Sie eine Abfrage auf dem Server aus.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
 **Teil A** Wenn Sie in diesem Tutorial [RDSServer. DataFactory](../../reference/rds-api/datafactory-object-rdsserver.md) nicht verwendet haben, ist die Verwendung des RDS die einfachste Möglichkeit, diesen Schritt auszuführen [. DataControl](../../reference/rds-api/datacontrol-object-rds.md) -Objekt. Das **RDS. DataControl** kombiniert den vorherigen Schritt der Erstellung eines Proxys mit diesem Schritt und der Ausgabe der Abfrage.  
  
 Legen Sie **RDS fest. DataControl** -Objekt [Server](../../reference/rds-api/server-property-rds.md) Eigenschaft, um zu identifizieren, wo das Server Programm instanziiert werden soll. die [Connect](../../reference/rds-api/connect-property-rds.md) -Eigenschaft zum Angeben der Verbindungs Zeichenfolge für den Zugriff auf die Datenquelle. und die [SQL](../../reference/rds-api/sql-property.md) -Eigenschaft, um den Abfrage Befehls Text anzugeben. Geben Sie dann die [Aktualisierungs](../../reference/rds-api/refresh-method-rds.md) Methode aus, damit das Serverprogramm eine Verbindung mit der Datenquelle herstellt, von der Abfrage angegebene Zeilen abruft und ein **Recordset** -Objekt an den Client zurückgibt.  
  
 In diesem Tutorial wird RDS nicht verwendet **. DataControl**, aber auf diese Weise wird folgendes Aussehen:  
  
```vb
Sub RDSTutorial2A()  
   Dim DC as New RDS.DataControl  
   DC.Server = "https://yourServer"  
   DC.Connect = "DSN=Pubs"  
   DC.SQL = "SELECT * FROM Authors"  
   DC.Refresh  
...  
```  
  
 Außerdem wird das Lernprogramm RDS nicht mit ADO-Objekten aufrufen, aber dies sieht wie folgt aus:  
  
```vb
Dim rs as New ADODB.Recordset  
rs.Open "SELECT * FROM Authors","Provider=MS Remote;Data Source=Pubs;" & _  
        "Remote Server=https://yourServer;Remote Provider=SQLOLEDB;"  
```  
  
 **Teil B** Die allgemeine Methode, diesen Schritt auszuführen, ist das Aufrufen der [Abfrage](../../reference/rds-api/query-method-rds.md) Methode **RDSServer. DataFactory.** Diese Methode verwendet eine Verbindungs Zeichenfolge, die zum Herstellen einer Verbindung mit einer Datenquelle verwendet wird, sowie einen Befehls Text, der verwendet wird, um die Zeilen anzugeben, die von der Datenquelle zurückgegeben werden sollen.  
  
 In diesem Tutorial wird die **DataFactory** -Objekt **Abfrage** Methode verwendet:  
  
```vb
Sub RDSTutorial2B()  
   Dim DS as New RDS.DataSpace  
   Dim DF  
   Dim RS as ADODB.Recordset  
   Set DF = DS.CreateObject("RDSServer.DataFactory", "https://yourServer")  
   Set RS = DF.Query ("DSN=Pubs", "SELECT * FROM Authors")  
...  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Schritt 3: Server erhält ein Recordset (RDS-Tutorial)](./step-3-server-obtains-a-recordset-rds-tutorial.md)   
 [RDS-Tutorial (VBScript)](./rds-tutorial-vbscript.md)