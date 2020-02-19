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
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: d1b5742d082fdb40b03663cf2db719399290a010
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "75247766"
---
# <a name="enumerating-instances-of-sql-server-adonet"></a>Auflisten von SQL Server-Instanzen (ADO.NET)

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[ADO.NET herunterladen](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

SQL Server ermöglicht es Anwendungen, SQL Server-Instanzen im aktuellen Netzwerk zu finden. Die <xref:System.Data.Sql.SqlDataSourceEnumerator>-Klasse stellt diese Informationen dem Anwendungsentwickler zur Verfügung, wobei eine <xref:System.Data.DataTable> Informationen zu allen sichtbaren Servern enthält. Diese zurückgegebene Tabelle enthält eine Liste der im Netzwerk verfügbaren Serverinstanzen. Diese Liste entspricht der Liste, die bereitgestellt wird, wenn ein Benutzer beim Erstellen einer neuen Verbindung im Dialogfeld **Verbindungseigenschaften** die Dropdownliste mit allen verfügbaren Servern erweitert. Die angezeigten Ergebnisse sind nicht immer vollständig.  
  
> [!NOTE]
>  Wie bei den meisten Windows-Diensten ist es am besten, den SQL-Browser-Dienst mit den geringstmöglichen Rechten auszuführen. Weitere Informationen zum SQL-Browserdienst und dessen Verwaltung finden Sie in der SQL Server-Onlinedokumentation.  
  
## <a name="retrieving-an-enumerator-instance"></a>Abrufen einer Enumeratorinstanz  
Damit Sie die Tabelle mit den Informationen zu den verfügbaren SQL Server-Instanzen abrufen können, müssen Sie zunächst einen Enumerator abrufen. Hierzu verwenden Sie die freigegebene/statische <xref:System.Data.Sql.SqlDataSourceEnumerator.Instance%2A>-Eigenschaft:  
  
```csharp  
System.Data.Sql.SqlDataSourceEnumerator instance =   
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
Sobald Sie die statische Instanz abgerufen haben, können Sie die <xref:System.Data.Sql.SqlDataSourceEnumerator.GetDataSources%2A>-Methode aufrufen, die eine <xref:System.Data.DataTable> mit Informationen zu den verfügbaren Servern zurückgibt:  
  
```csharp  
System.Data.DataTable dataTable = instance.GetDataSources();  
```  
  
Die vom Methodenaufruf zurückgegebene Tabelle enthält die folgenden Spalten, die allesamt `string`-Werte enthalten:  
  
|Column|Beschreibung|  
|------------|-----------------|  
|**ServerName**|Name des Servers.|  
|**InstanceName**|Name der Serverinstanz. Leer, wenn der Server als Standardinstanz ausgeführt wird.|  
|**IsClustered**|Gibt ab, ob die Serverinstanz zu einem Cluster gehört.|  
|**Version**|Die Version des Servers. Beispiel:<br /><br /> - 9.00.x (SQL Server 2005)<br />10.0.xx (SQL Server 2008)<br />- 10.50.x (SQL Server 2008 R2)<br />11.0.xx (SQL Server 2012)|  
  
## <a name="enumeration-limitations"></a>Enumerationseinschränkungen  
Alle verfügbaren Server werden möglicherweise aufgelistet oder nicht. Die Liste kann je nach Faktoren wie Zeitlimits und Netzwerkdatenverkehr variieren. Dies kann dazu führen, dass die Liste bei zwei aufeinander folgenden Aufrufen unterschiedlich ist. Nur Server im selben Netzwerk werden aufgelistet. Übertragungspakete durchlaufen normalerweise keine Router, weshalb ein Server zwar ggf. nicht aufgelistet wird, aber aufrufübergreifend stabil bleibt.  
  
Aufgelistete Server können zusätzliche Informationen wie `IsClustered` und die Version enthalten oder auch nicht. Dies hängt davon ab, wie die Liste abgerufen wurde. Es werden ausführlichere Informationen angezeigt, wenn die Server über den SQL Server-Browserdienst aufgelistet werden. Bei Servern, die über die Windows-Infrastruktur ermittelt werden, wird nur der Name aufgeführt.  
  
> [!NOTE]
>  Die Serverenumeration ist nur verfügbar, wenn sie im vollständig vertrauenswürdigen Modus ausgeführt wird. Assemblys, die in einer teilweise vertrauenswürdigen Umgebung ausgeführt werden, können sie nicht verwenden, selbst wenn sie die CAS-Berechtigung (Code Access Security, Codezugriffssicherheit) <xref:Microsoft.Data.SqlClient.SqlClientPermission> haben.  
  
SQL Server stellt Informationen für <xref:System.Data.Sql.SqlDataSourceEnumerator> mithilfe eines externen Windows-Diensts namens SQL-Browser bereit. Dieser Dienst ist standardmäßig aktiviert. Administratoren können ihn jedoch deaktivieren, sodass die Serverinstanz für diese Klasse nicht sichtbar ist.  
  
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
