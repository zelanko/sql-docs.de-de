---
title: Herstellen einer Verbindung mit Datenquellen in der Skriptkomponente | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Script component [Integration Services], connecting to data sources
ms.assetid: 96de63ab-ff48-4e7e-89e0-ffd6a89c63b6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 4af1e5e1aedcd9916c1d4f6a13d0c4f63922b8b7
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/13/2018
ms.locfileid: "53375462"
---
# <a name="connecting-to-data-sources-in-the-script-component"></a>Herstellen einer Verbindung zu Datenquellen in der Skriptkomponente 
  Ein Verbindungs-Manager ist eine praktische Einheit, die die Informationen kapselt und speichert, die benötigt werden, um eine Verbindung mit einem bestimmten Datenquellentyp herzustellen. Weitere Informationen finden Sie unter [Integration Services-Verbindungen &#40;SSIS&#41;](../../connection-manager/integration-services-ssis-connections.md).  
  
 Sie können vorhandene Verbindungs-Manager über das benutzerdefinierte Skript in der Quell- oder Zielkomponente zum Zugriff freigeben, indem Sie auf der Seite **Verbindungs-Manager** des **Transformations-Editors für Skripterstellung** auf die Schaltfläche **Hinzufügen** oder **Entfernen** klicken. Um Daten zu laden und zu speichern und möglicherweise auch eine Verbindung mit der Datenquelle herzustellen und diese zu beenden, müssen Sie jedoch Ihren eigenen benutzerdefinierten Code schreiben. Weitere Informationen über die Seite **Verbindungs-Manager** im **Transformations-Editor für Skripterstellung** finden Sie unter [Configuring the Script Component in the Script Component Editor (Konfigurieren der Skriptkomponente im Skriptkomponenten-Editor)](configuring-the-script-component-in-the-script-component-editor.md) oder [Script Transformation Editor (Connection Managers Page) (Transformations-Editor für Skripterstellung (Seite „Verbindungs-Manager“))](../../script-transformation-editor-connection-managers-page.md).  
  
 Die Skriptkomponente erstellt eine `Connections`-Auflistungsklasse im `ComponentWrapper`-Projektelement, die einen Accessor mit starker Typbindung für jeden Verbindungs-Manager enthält, der denselben Namen wie der Verbindungs-Manager trägt. Diese Auflistung wird von der `Connections`-Eigenschaft der `ScriptMain`-Klasse verfügbar gemacht. Die Accessoreigenschaft gibt einen Verweis auf den Verbindungs-Manager als Instanz von <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.IDTSConnectionManager100> zurück. Wenn Sie beispielsweise auf der Seite Verbindungs-Manager des Dialogfelds den Verbindungs-Manager `MyADONETConnection` hinzugefügt haben, können Sie mit dem folgenden Code im Skript einen Verweis darauf hinzufügen:  
  
 `Dim myADONETConnectionManager As IDTSConnectionManager100 = _`  
  
 `Me.Connections.MyADONETConnection`  
  
> [!NOTE]  
>  Sie müssen den Typ der Verbindung wissen, der vom Verbindungs-Manager zurückgegeben wird, bevor Sie `AcquireConnection` aufrufen. Da für den Skripttask `Option Strict` aktiviert ist, müssen Sie die Verbindung, die als `Object`-Typ zurückgegeben wird, vor ihrer Verwendung in den richtigen Verbindungstyp umwandeln.  
  
 Anschließend rufen Sie die `AcquireConnection`-Methode des jeweiligen Verbindungs-Managers auf, um entweder die zugrunde liegende Verbindung oder die für die Verbindung zur Datenquelle erforderlichen Informationen zu erhalten. Mit folgendem Code erhalten Sie beispielsweise einen Verweis auf ein **System.Data.SqlConnection**-Objekt, das von einem ADO.NET-Verbindungs-Manager umschlossen wird:  
  
 `Dim myADOConnection As SqlConnection = _`  
  
 `CType(MyADONETConnectionManager.AcquireConnection(Nothing), SqlConnection)`  
  
 Wenn Sie im Gegensatz dazu einen Verbindungs-Manager für Flatfiles aufrufen, wird nur der Pfad und der Dateiname der Dateidatenquelle zurückgegeben.  
  
 `Dim myFlatFile As String = _`  
  
 `CType(MyFlatFileConnectionManager.AcquireConnection(Nothing), String)`  
  
 Übergeben Sie dann diesen Pfad und den Dateinamen an einen `System.IO.StreamReader` oder `Streamwriter`, um die Daten in der Flatfile zu lesen oder zu schreiben.  
  
> [!IMPORTANT]  
>  Wenn Sie in einer Skriptkomponente verwalteten Code schreiben, können Sie die AcquireConnection-Methode nicht für Verbindungs-Manager wie den OLEDB- oder den Excel-Verbindungs-Manager aufrufen, die nicht verwaltete Objekte zurückgeben. Sie können jedoch die ConnectionString-Eigenschaft dieser Verbindungs-Manager lesen und mithilfe der Verbindungszeichenfolge einer OLEDB-**Verbindung** aus dem **System.Data.OleDb**-Namespace direkt im Code eine Verbindung mit der Datenquelle herstellen.  
>   
>  Wenn Sie die AcquireConnection-Methode eines Verbindungs-Managers aufrufen müssen, der nicht verwaltete Objekte zurückgibt, verwenden Sie einen ADO.NET-Verbindungs-Manager. Wenn Sie den ADO.NET-Verbindungs-Manager zur Verwendung eines OLE DB-Anbieters konfigurieren, stellt er über den .NET Framework-Datenanbieter für OLE DB eine Verbindung her. In diesem Fall die AcquireConnection-Methode gibt eine `System.Data.OleDb.OleDbConnection` anstelle eines nicht verwalteten Objekts. Zur Konfiguration eines ADO.NET-Verbindungs-Managers zur Verwendung mit einer Excel-Datenquelle wählen Sie den Microsoft OLEDB-Anbieter für Jet aus, geben eine Excel-Arbeitsmappe an und geben dann `Excel 8.0` (für Excel 97 und höher) als Wert für **Erweiterte Eigenschaften** auf der Seite **Alle** des Dialogfelds **Verbindungs-Manager** ein.  
  
 Weitere Informationen zur Verwendung von Verbindungs-Managern mit der Skriptkomponente finden Sie unter [Creating a Source with the Script Component (Erstellen einer Quelle mit der Skriptkomponente)](../../extending-packages-scripting-data-flow-script-component-types/creating-a-source-with-the-script-component.md) und [Creating a Destination with the Script Component (Erstellen eines Ziels mit der Skriptkomponente)](../../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md).  
  
![Integration Services (kleines Symbol)](../../media/dts-16.gif "Integration Services (kleines Symbol)")**bleiben oben, um das Datum mit Integration Services**<br /> Die neuesten Downloads, Artikel, Beispiele und Videos von Microsoft sowie ausgewählte Lösungen aus der Community finden Sie auf MSDN auf der [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] -Seite:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.  
  
## <a name="see-also"></a>Siehe auch  
 [Integration Services (SSIS) Connections (Integration Services-Verbindungen (SSIS))](../../connection-manager/integration-services-ssis-connections.md)   
 [Erstellen von Verbindungs-Managern](../../create-connection-managers.md)  
  
  
