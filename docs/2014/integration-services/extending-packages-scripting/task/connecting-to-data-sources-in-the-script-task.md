---
title: Herstellen einer Verbindung mit Datenquellen im Skripttask | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- integration-services
ms.tgt_pltfrm: ''
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- connections [Integration Services], scripts
- Integration Services packages, connections
- connection managers [Integration Services], scripts
- scripts [Integration Services], connections
- SSIS packages, connections
- packages [Integration Services], connections
- Script task [Integration Services], connections
- Connections property
- SQL Server Integration Services packages, connections
- SSIS Script task, connections
ms.assetid: 9c008380-715b-455b-9da7-22572d67c388
caps.latest.revision: 58
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 0266f6683e354f87edb6423bab638436447fcc5d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37285646"
---
# <a name="connecting-to-data-sources-in-the-script-task"></a>Herstellen einer Verbindung zu Datenquellen im Skripttask 
  Verbindungs-Manager bieten Zugriff auf Datenquellen, die im Paket konfiguriert wurden. Weitere Informationen finden Sie unter [Integration Services-Verbindungen &#40;SSIS&#41;](../../connection-manager/integration-services-ssis-connections.md).  
  
 Der Skripttask kann auf diese Verbindungs-Manager über die <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Connections%2A>-Eigenschaft des **Dts**-Objekts zugreifen. Jeder Verbindungs-Manager in der <xref:Microsoft.SqlServer.Dts.Runtime.Connections>-Auflistung speichert Informationen darüber, wie eine Verbindung mit der zugrunde liegenden Datenquelle hergestellt werden kann.  
  
 Wenn Sie die <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A>-Methode eines Verbindungs-Managers aufrufen, stellt der Verbindungs-Manager eine Verbindung zur Datenquelle her (falls diese nicht bereits besteht), und gibt die entsprechenden Verbindungsinformationen zur Verwendung im Skripttaskcode zurück.  
  
> [!NOTE]  
>  Benötigen Sie die Art der Verbindung, die von den Verbindungs-Manager vor dem Aufruf zurückgegebenen `AcquireConnection`. Da für den Skripttask `Option Strict` aktiviert ist, müssen Sie die Verbindung, die als `Object`-Typ zurückgegeben wird, vor ihrer Verwendung in den richtigen Verbindungstyp umwandeln.  
  
 Sie können die <xref:Microsoft.SqlServer.Dts.Runtime.Connections.Contains%2A>-Methode der <xref:Microsoft.SqlServer.Dts.Runtime.Connections>-Auflistung verwenden, die von der <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Connections%2A>-Eigenschaft zurückgegeben wird, um nach einer vorhandenen Verbindung zu suchen, bevor Sie diese Verbindung im Code verwenden.  
  
> [!IMPORTANT]  
>  Sie können die AcquireConnection-Methode von Verbindungs-Managern, die nicht verwaltete Objekte zurückgeben (z.B. der OLE DB-Verbindungs-Manager und der Excel-Verbindungs-Manager) nicht im verwalteten Code eines Skripttasks aufrufen. Allerdings Sie lesen die ConnectionString-Eigenschaft dieser Verbindungs-Manager und Herstellen einer Verbindung mit der Datenquelle direkt in Ihrem Code mithilfe der Verbindungszeichenfolge mit einem `OledbConnection` aus der **"System.Data.OleDb"** Namespace.  
>   
>  Wenn Sie die AcquireConnection-Methode eines Verbindungs-Managers aufrufen müssen, der nicht verwaltete Objekte zurückgibt, verwenden Sie einen [!INCLUDE[vstecado](../../../includes/vstecado-md.md)]-Verbindungs-Manager. Wenn Sie den [!INCLUDE[vstecado](../../../includes/vstecado-md.md)]-Verbindungs-Manager zur Verwendung eines OLE DB-Anbieters konfigurieren, stellt er über den [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]-Datenanbieter für OLE DB eine Verbindung her. In diesem Fall die AcquireConnection-Methode gibt eine `System.Data.OleDb.OleDbConnection` anstelle eines nicht verwalteten Objekts. Zur Konfiguration eines [!INCLUDE[vstecado](../../../includes/vstecado-md.md)]-Verbindungs-Managers zur Verwendung mit einer Excel-Datenquelle wählen Sie den [!INCLUDE[msCoName](../../../includes/msconame-md.md)] OLE DB-Anbieter für Jet aus, geben eine Excel-Datei an und geben dann `Excel 8.0` (für Excel 97 und höher) als Wert für **Erweiterte Eigenschaften** auf der Seite **Alle** des Dialogfelds **Verbindungs-Manager** ein.  
  
## <a name="connections-example"></a>Verbindungsbeispiel  
 Im folgenden Beispiel wird veranschaulicht, wie Verbindungs-Manager innerhalb des Skripttasks aufgerufen werden können. In diesem Beispiel wird davon ausgegangen, dass Sie einen [!INCLUDE[vstecado](../../../includes/vstecado-md.md)]-Verbindungs-Manager namens **Test ADO.NET Connection** und einen Verbindungs-Manager für Flatfiles namens **Test Flat File Connection** erstellt und konfiguriert haben. Beachten Sie, dass der [!INCLUDE[vstecado](../../../includes/vstecado-md.md)]-Verbindungs-Manager ein `SqlConnection`-Objekt zurückgibt, das Sie sofort zur Verbindung mit der Datenquelle verwenden können. Der Verbindungs-Manager für Flatfiles gibt im Gegensatz dazu nur eine Zeichenfolge mit Pfad und Dateinamen zurück. Sie müssen Methoden aus dem `System.IO`-Namespace verwenden, um die Flatfile zu öffnen und mit ihr zu arbeiten.  
  
```vb  
Public Sub Main()  
  
    Dim myADONETConnection As SqlClient.SqlConnection  
    myADONETConnection = _  
        DirectCast(Dts.Connections("Test ADO.NET Connection").AcquireConnection(Dts.Transaction), _  
        SqlClient.SqlConnection)  
    MsgBox(myADONETConnection.ConnectionString, _  
        MsgBoxStyle.Information, "ADO.NET Connection")  
  
    Dim myFlatFileConnection As String  
    myFlatFileConnection = _  
        DirectCast(Dts.Connections("Test Flat File Connection").AcquireConnection(Dts.Transaction), _  
        String)  
    MsgBox(myFlatFileConnection, MsgBoxStyle.Information, "Flat File Connection")  
  
    Dts.TaskResult = ScriptResults.Success  
  
End Sub  
```  
  
```csharp  
using System;  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Dts.Runtime;  
using System.Windows.Forms;  
  
public class ScriptMain  
{  
  
        public void Main()  
        {  
            SqlConnection myADONETConnection = new SqlConnection();  
            myADONETConnection = (SqlConnection)(Dts.Connections["Test ADO.NET Connection"].AcquireConnection(Dts.Transaction)as SqlConnection);  
            MessageBox.Show(myADONETConnection.ConnectionString, "ADO.NET Connection");  
  
            string myFlatFileConnection;  
            myFlatFileConnection = (string)(Dts.Connections["Test Flat File Connection"].AcquireConnection(Dts.Transaction) as String);  
            MessageBox.Show(myFlatFileConnection, "Flat File Connection");  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
  
        }  
  
}  
  
```  
  
![Integration Services (kleines Symbol)](../../media/dts-16.gif "Integration Services (kleines Symbol)")**bleiben oben, um das Datum mit Integration Services  **<br /> Die neuesten Downloads, Artikel, Beispiele und Videos von Microsoft sowie ausgewählte Lösungen aus der Community finden Sie auf MSDN auf der [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] -Seite:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](http://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.  
  
## <a name="see-also"></a>Siehe auch  
 [Integration Services (SSIS) Connections (Integration Services-Verbindungen (SSIS))](../../connection-manager/integration-services-ssis-connections.md)   
 [Erstellen von Verbindungs-Managern](../../create-connection-managers.md)  
  
  
