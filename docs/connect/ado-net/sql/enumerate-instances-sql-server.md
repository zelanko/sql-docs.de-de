---
title: Auflisten von SQL Server-Instanzen (ADO.NET)
description: Beschreibt das Auflisten aktiver Instanzen von SQL Server 2000.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: ddf1c83c-9d40-45e6-b04d-9828c6cbbfdc
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: d6c83ffd407a9b27a04b254fb3e9e5673a600417
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72452199"
---
# <a name="enumerating-instances-of-sql-server-adonet"></a>Auflisten von SQL Server-Instanzen (ADO.NET)

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[ADO.NET herunterladen](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

SQL Server ermöglicht es Anwendungen, SQL Server Instanzen im aktuellen Netzwerk zu finden. Die <xref:System.Data.Sql.SqlDataSourceEnumerator>-Klasse macht diese Informationen für den Anwendungsentwickler verfügbar und bietet eine <xref:System.Data.DataTable>, die Informationen über alle sichtbaren Server enthält. Diese zurückgegebene Tabelle enthält eine Liste der im Netzwerk verfügbaren Serverinstanzen. Diese Liste entspricht der Liste, die bereitgestellt wird, wenn ein Benutzer beim Erstellen einer neuen Verbindung im Dialogfeld **Verbindungseigenschaften** die Dropdownliste mit allen verfügbaren Servern erweitert. Die angezeigten Ergebnisse sind nicht immer erfüllt.  
  
> [!NOTE]
>  Wie bei den meisten Windows-Diensten ist es am besten, den SQL-Browser-Dienst mit den geringstmöglichen Berechtigungen auszuführen. Weitere Informationen zum SQL-Browserdienst und dessen Verwaltung finden Sie in der SQL Server-Onlinedokumentation.  
  
## <a name="retrieving-an-enumerator-instance"></a>Abrufen einer Enumeratorinstanz  
Damit Sie die Tabelle mit den Informationen zu den verfügbaren SQL Server-Instanzen abrufen können, müssen Sie zunächst einen Enumerator abrufen. Hierzu verwenden Sie die freigegebene/statische <xref:System.Data.Sql.SqlDataSourceEnumerator.Instance%2A>-Eigenschaft:  
  
```csharp  
System.Data.Sql.SqlDataSourceEnumerator instance =   
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
Nachdem Sie die statische Instanz abgerufen haben, können Sie die <xref:System.Data.Sql.SqlDataSourceEnumerator.GetDataSources%2A>-Methode abrufen, die eine <xref:System.Data.DataTable> mit Informationen zu den verfügbaren Servern zurückgibt:  
  
```csharp  
System.Data.DataTable dataTable = instance.GetDataSources();  
```  
  
Die vom Methoden Aufrufwert zurückgegebene Tabelle enthält die folgenden Spalten, die alle `string` Werte enthalten:  
  
|Spalte|und Beschreibung|  
|------------|-----------------|  
|**ServerName**|Name des Servers.|  
|**InstanceName**|Der Name der Serverinstanz. Leer, wenn der Server als Standard Instanz ausgeführt wird.|  
|**IsClustered**|Gibt an, ob der Serverteil eines Clusters ist.|  
|**Version**|Die Version des Servers. Beispiel:<br /><br /> - 9.00.x (SQL Server 2005)<br />-10.0. XX (SQL Server 2008)<br />- 10.50.x (SQL Server 2008 R2)<br />-11.0. XX (SQL Server 2012)|  
  
## <a name="enumeration-limitations"></a>Enumerationseinschränkungen  
Alle verfügbaren Server werden möglicherweise aufgelistet. Die Liste kann je nach Faktoren variieren, z. b. Timeouts und Netzwerk Datenverkehr. Dies kann dazu führen, dass die Liste bei zwei aufeinander folgenden Aufrufen unterschiedlich ist. Es werden nur Server im gleichen Netzwerk aufgelistet. Broadcast Pakete werden in der Regel keine Router durchlaufen. aus diesem Grund wird Ihnen möglicherweise kein Server angezeigt, Sie sind jedoch über mehrere Aufrufe hinweg stabil.  
  
Die aufgelisteten Server verfügen möglicherweise über zusätzliche Informationen, z. b. `IsClustered` und Version. Dies hängt davon ab, wie die Liste abgerufen wurde. Es werden ausführlichere Informationen angezeigt, wenn die Server über den SQL Server-Browserdienst aufgelistet werden. Bei Servern, die über die Windows-Infrastruktur ermittelt werden, wird nur der Name aufgeführt.  
  
> [!NOTE]
>  Die Server Enumeration ist nur verfügbar, wenn Sie mit voller Vertrauenswürdigkeit ausgeführt wird. Assemblys, die in einer teilweise vertrauenswürdigen Umgebung ausgeführt werden, können Sie nicht verwenden, auch wenn Sie über die Berechtigung zur <xref:Microsoft.Data.SqlClient.SqlClientPermission> Code Zugriffssicherheit (CAS) verfügen.  
  
SQL Server stellt Informationen für <xref:System.Data.Sql.SqlDataSourceEnumerator> mithilfe eines externen Windows-Diensts namens SQL-Browser bereit. Dieser Dienst ist standardmäßig aktiviert, kann aber von Administratoren ausgeschaltet oder deaktiviert werden, sodass die Serverinstanz für diese Klasse unsichtbar wird.  
  
## <a name="example"></a>Beispiel  
Die folgende Konsolenanwendung ruft Informationen zu allen sichtbaren SQL Server-Instanzen ab und zeigt die Informationen im Konsolenfenster an.  
  
```csharp  
using System.Data.Sql;  
  
class Program  
{  
  static void Main()  
  {  
    // Retrieve the enumerator instance and then the data.  
    SqlDataSourceEnumerator instance =  
      SqlDataSourceEnumerator.Instance;  
    System.Data.DataTable table = instance.GetDataSources();  
  
    // Display the contents of the table.  
    DisplayData(table);  
  
    Console.WriteLine("Press any key to continue.");  
    Console.ReadKey();  
  }  
  
  private static void DisplayData(System.Data.DataTable table)  
  {  
    foreach (System.Data.DataRow row in table.Rows)  
    {  
      foreach (System.Data.DataColumn col in table.Columns)  
      {  
        Console.WriteLine("{0} = {1}", col.ColumnName, row[col]);  
      }  
      Console.WriteLine("============================");  
    }  
  }  
}  
```  
  
## <a name="next-steps"></a>Nächste Schritte
- [SQL Server und ADO.NET](index.md)
