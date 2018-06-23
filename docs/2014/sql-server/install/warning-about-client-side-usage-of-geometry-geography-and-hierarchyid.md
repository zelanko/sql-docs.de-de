---
title: Warnung zur clientseitigen Verwendung von GEOMETRY, GEOGRAPHY und HIERARCHYID | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 500ee6b3-2154-45d2-a3cf-8760166d9413
caps.latest.revision: 8
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 02748f9dca8e4f9f29c7c94658d2a4068b1ba65e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36161264"
---
# <a name="warning-about-client-side-usage-of-geometry-geography-and-hierarchyid"></a>Warnung zur clientseitigen Verwendung von GEOMETRY, GEOGRAPHY und HIERARCHYID
  Die Assembly **Microsoft.SqlServer.Types.dll**, die die räumlichen Datentypen enthält, wurde aktualisiert von Version 10.0 auf Version 11.0. Benutzerdefinierte Anwendungen, die auf diese Assembly verweisen, schlagen möglicherweise fehl, wenn bestimmte Bedingungen den Wert "true" aufweisen.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Die Assembly **Microsoft.SqlServer.Types.dll**, die die räumlichen Datentypen enthält, wurde aktualisiert von Version 10.0 auf Version 11.0. Benutzerdefinierte Anwendungen, die auf diese Assembly verweisen, schlagen möglicherweise fehl, wenn die folgenden Bedingungen den Wert "true" aufweisen.  
  
-   Wenn Sie verschieben eine benutzerdefinierte Anwendung von einem Computer auf dem [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] installiert wurde, um einen Computer, auf dem nur [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ist installiert, die Anwendung fehl, weil die referenzierte Version 10.0 der der **SqlTypes** Assembly ist nicht vorhanden. Möglicherweise wird folgende Fehlermeldung angezeigt: `“Could not load file or assembly 'Microsoft.SqlServer.Types, Version=10.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91' or one of its dependencies. The system cannot find the file specified.”`  
  
-   Wenn Sie verweisen auf die **SqlTypes** Version 11.0 der Assembly und Version 10.0 ebenfalls installiert ist, können Sie die folgende Fehlermeldung angezeigt: `“System.InvalidCastException: Unable to cast object of type 'Microsoft.SqlServer.Types.SqlGeometry' to type 'Microsoft.SqlServer.Types.SqlGeometry'.”`  
  
-   Wenn Sie verweisen auf die **SqlTypes** Version 11.0 der Assembly mit einer benutzerdefinierten Anwendung, die auf .NET 3.5, 4 oder 4.5 abzielen, da SqlClient entwurfsbedingt Version 10.0 der Assembly geladen, kann die Anwendung fehl. Dieser Fehler tritt auf, wenn die Anwendung eine der folgenden Methoden aufruft:  
  
    -   `GetValue`-Methode der `SqlDataReader`-Klasse  
  
    -   `GetValues`-Methode der `SqlDataReader`-Klasse  
  
    -   Klammerindexoperator [] der `SqlDataReader`-Klasse  
  
    -   `ExecuteScalar`-Methode der `SqlCommand`-Klasse  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Sie können dieses Problem mithilfe einer der folgenden Methoden umgehen:  
  
-   Sie können dieses Problem im Code umgehen, indem Sie anstelle der oben aufgeführten Get-Methoden die `GetSqlBytes`-Methode aufrufen, um CLR-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Systemtypen abzurufen. Hierzu ein Beispiel:  
  
    ```csharp  
    string query = "SELECT [SpatialColumn] FROM [SpatialTable]";  
          using (SqlConnection conn = new SqlConnection("..."))  
          {  
                SqlCommand cmd = new SqlCommand(query, conn);  
  
                conn.Open();  
                SqlDataReader reader = cmd.ExecuteReader();  
  
                while (reader.Read())  
                {  
                      // In version 11.0 only  
                      SqlGeometry g =   
    SqlGeometry.Deserialize(reader.GetSqlBytes(0));  
  
                      // In version 10.0 or 11.0  
                      SqlGeometry g2 = new SqlGeometry();  
                      g.Read(new BinaryReader(reader.GetSqlBytes(0).Stream));  
                }  
          }  
    ```  
  
-   Sie können dieses Problem umgehen, indem Sie eine Assemblyumleitung in der Anwendungskonfigurationsdatei verwenden. Siehe folgendes Beispiel:  
  
    ```xml  
    <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
        ...  
        <dependentAssembly>  
            <assemblyIdentity name="Microsoft.SqlServer.Types" publicKeyToken="89845dcd8080cc91" culture="neutral" />  
            <bindingRedirect oldVersion="10.0.0.0" newVersion="11.0.0.0" />  
        </dependentAssembly>  
        ...  
    </assemblyBinding>  
    ```  
  
-   Sie können dieses Problem in der Verbindungszeichenfolge umgehen, indem Sie den Wert "SQL Server 2012" für das Attribut "Typsystemversion" angeben, um SqlClient zu zwingen, Version 11.0 der Assembly zu laden. Dieses Verbindungszeichenfolgenattribut ist erst ab .NET 4.5 verfügbar.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-Engine-Upgradeprobleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neu&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
