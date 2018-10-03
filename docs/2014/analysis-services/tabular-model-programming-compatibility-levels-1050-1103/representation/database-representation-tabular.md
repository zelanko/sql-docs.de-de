---
title: Datenbankdarstellung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: 16a233fb-f83b-4ca1-acb5-6186eca0a62c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 02fd33d8adf1ccee042f09c8b102401d5ba94435
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48116281"
---
# <a name="database-representationtabular"></a>Datenbankdarstellung (tabellarisch)
  Im tabellarischen Modus ist die Datenbank der Container für alle Objekte im tabellarischen Modell.  
  
## <a name="database-representation"></a>Datenbankdarstellung  
 Die Datenbank ist die Stelle, an der sich alle Objekte befinden, die ein tabellarisches Modell bilden. In der Datenbank findet der Entwickler Objekte wie Verbindungen, Tabellen, Rollen u.v.m. vor.  
  
### <a name="database-in-amo"></a>Datenbank in AMO  
 Wenn eine tabellarische Modelldatenbank mithilfe von AMO verwaltet wird, entspricht das <xref:Microsoft.AnalysisServices.Database>-Objekt in AMO 1:1 dem logischen Datenbankobjekt in einem tabellarischen Modell.  
  
> [!NOTE]  
>  Um Zugriff auf ein Datenbankobjekt in AMO zu erhalten, benötigt der Benutzer Zugriff auf ein Serverobjekt und muss eine Verbindung damit herstellen.  
  
### <a name="database-in-adomdnet"></a>Datenbank in ADOMD.Net  
 Wenn ADOMD verwendet wird, um eine tabellarische Modelldatenbank abzufragen, wird die Verbindung mit einer bestimmten Datenbank durch das <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>-Objekt erreicht.  
  
 Mit dem folgenden Codeabschnitt können Sie direkt eine Verbindung zu einer bestimmten Datenbank herstellen:  
  
```csharp  
using ADOMD = Microsoft.AnalysisServices.AdomdClient;  
…  
   ADOMD.AdomdConnection currrentCnx = new ADOMD.AdomdConnection("Data Source=<<server\instance>>;Catalog=<<database>>");  
   currrentCnx.Open();  
…  
  
```  
  
 Über ein vorhandenes Verbindungsobjekt (das nicht geschlossen wurde) können Sie auch von der aktuellen Datenbank zu einer anderen Datenbank wechseln, wie im folgenden Codeausschnitt gezeigt:  
  
```csharp  
currentCnx.ChangeDatabase("myOtherDatabase");  
  
```  
  
## <a name="database-in-amo"></a>Datenbank in AMO  
 Wenn Sie AMO verwenden, um ein Datenbankobjekt zu verwalten, beginnen Sie mit einem <xref:Microsoft.AnalysisServices.Server>-Objekt. Suchen Sie dann Ihre Datenbank in der Datenbankauflistung, oder erstellen Sie eine neue Datenbank, indem Sie sie der Auflistung hinzufügen.  
  
 Der folgende Codeausschnitt veranschaulicht die Schritte, mit denen eine Verbindung mit einem Server hergestellt und eine leere Datenbank erstellt wird, nachdem überprüft wurde, dass die Datenbank noch nicht vorhanden ist:  
  
```  
  
AMO.Server CurrentServer = new AMO.Server();  
try  
{  
    CurrentServer.Connect(currentServerName);  
}  
catch (Exception cnxException)  
{  
    MessageBox.Show(string.Format("Error while trying to connect to server: [{0}]\nError message: {1}", currentServerName, cnxException.Message), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Error);  
    return;  
}  
newDatabaseName = DatabaseName.Text;  
if (CurrentServer.Databases.Contains(newDatabaseName))  
{  
    return;  
}  
try  
{  
    AMO.Database newDatabase = CurrentServer.Databases.Add(newDatabaseName);  
  
    CurrentServer.Update();  
}  
catch (Exception createDBxc)  
{  
    MessageBox.Show(String.Format("Database [{0}] couldn't be created.\n{1}", newDatabaseName, createDBxc.Message), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Error);  
    newDatabaseAvailable = false;  
}  
  
```  
  
 Ein praktisches Verständnis für die Verwendung von AMO zur Erstellung und Bearbeitung von datenbankdarstellungen, dazu finden Sie Quellcode im Tabular AMO 2012-Beispiel. Prüfen Sie insbesondere die Quelldatei: Database.cs. Beispielcode wird nur zur Verdeutlichung der hier erläuterten logischen Konzepte bereitgestellt und sollte nicht in einer Produktionsumgebung verwendet werden.  
  
  
