---
title: Warnung zur Client seitigen Verwendung von Geometry, Geography und hierarchyid | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 500ee6b3-2154-45d2-a3cf-8760166d9413
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 524400e9c9420fb54447220215d4660874ec6d69
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66091090"
---
# <a name="warning-about-client-side-usage-of-geometry-geography-and-hierarchyid"></a>Warnung zur clientseitigen Verwendung von GEOMETRY, GEOGRAPHY und HIERARCHYID
  Die Assembly **Microsoft. SqlServer. types. dll**, die die räumlichen Datentypen enthält, wurde von Version 10,0 auf Version 11,0 aktualisiert. Benutzerdefinierte Anwendungen, die auf diese Assembly verweisen, schlagen möglicherweise fehl, wenn bestimmte Bedingungen den Wert "true" aufweisen.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>BESCHREIBUNG  
 Die Assembly **Microsoft. SqlServer. types. dll**, die die räumlichen Datentypen enthält, wurde von Version 10,0 auf Version 11,0 aktualisiert. Benutzerdefinierte Anwendungen, die auf diese Assembly verweisen, schlagen möglicherweise fehl, wenn die folgenden Bedingungen den Wert "true" aufweisen.  
  
-   Wenn Sie eine benutzerdefinierte Anwendung von einem Computer, auf [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] dem installiert wurde, auf einen Computer verschieben [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , auf dem nur installiert ist, schlägt die Anwendung fehl, da die referenzierte Version 10,0 der **SqlTypes** -Assembly nicht vorhanden ist. Möglicherweise wird folgende Fehlermeldung angezeigt: `"Could not load file or assembly 'Microsoft.SqlServer.Types, Version=10.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91' or one of its dependencies. The system cannot find the file specified."`  
  
-   Wenn Sie auf die Version 11,0 der **SqlTypes** -Assembly verweisen und Version 10,0 ebenfalls installiert ist, wird möglicherweise die folgende Fehlermeldung angezeigt:`"System.InvalidCastException: Unable to cast object of type 'Microsoft.SqlServer.Types.SqlGeometry' to type 'Microsoft.SqlServer.Types.SqlGeometry'."`  
  
-   Wenn Sie von einer benutzerdefinierten Anwendung, die auf .NET 3,5, 4 oder 4,5 ausgerichtet ist, auf die **SqlTypes** -Assemblyversion 11,0 verweisen, schlägt die Anwendung fehl, da SqlClient nach dem Entwurf Version 10,0 der Assembly lädt. Dieser Fehler tritt auf, wenn die Anwendung eine der folgenden Methoden aufruft:  
  
    -   
  `GetValue`-Methode der `SqlDataReader`-Klasse  
  
    -   
  `GetValues`-Methode der `SqlDataReader`-Klasse  
  
    -   Klammerindexoperator [] der `SqlDataReader`-Klasse  
  
    -   
  `ExecuteScalar`-Methode der `SqlCommand`-Klasse  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-Engine Upgradeprobleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neuen&#93;](sql-server-2014-upgrade-advisor.md
)  
  
  
