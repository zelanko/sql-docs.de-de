---
title: Implementieren externer Metadaten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- disconnected validation [Integration Services]
- connected validation [Integration Services]
- custom data flow components [Integration Services], validating
- validation [Integration Services], components
- metadata [Integration Services]
- data flow components [Integration Services], validating
- data flow components [Integration Services], external metadata
- custom data flow components [Integration Services], external metadata
- external metadata [Integration Services]
ms.assetid: 8f5bd3ed-3e79-43a4-b6c1-435e4c2cc8cc
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 838cbe74489ba0a9388eb8f2848722b78cf999b3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48052520"
---
# <a name="implementing-external-metadata"></a>Implementieren externer Metadaten
  Wenn die Verbindung einer Komponente mit einer Datenquelle getrennt ist, können Sie mithilfe der <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumnCollection100>-Schnittstelle die Spalten in den Eingabe- und Ausgabespaltenauflistungen anhand der Spalten der externen Datenquelle überprüfen. Mit dieser Schnittstelle können Sie eine Momentaufnahme der Spalten der externen Datenquelle verwalten und diese Spalten den Eingabe- und Ausgabespaltenauflistungen der Komponente zuordnen.  
  
 Die Implementierung externer Metadatenspalten erhöht den Verwaltungsaufwand und die Komplexität bei der Komponentenentwicklung, da Sie eine weitere Spaltenauflistung verwalten und überprüfen müssen. Diese Entwicklungsarbeit kann sich aber lohnen, da Sie teure Roundtrips zum Server zu Überprüfungszwecken vermeiden können.  
  
## <a name="populating-external-metadata-columns"></a>Auffüllen von externen Metadatenspalten  
 Externe Metadatenspalten werden der Auflistung meist bei der Erstellung der entsprechenden Eingabe- oder Ausgabespalten hinzugefügt. Neue Spalten werden durch Aufrufen der <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumnCollection100.New%2A>-Methode erstellt. Die Eigenschaften der Spalte werden anschließend entsprechend der externen Datenquelle festgelegt.  
  
 Die externe Metadatenspalte wird der entsprechenden Eingabe- oder Ausgabespalte durch Zuweisen der ID der externen Metadatenspalte zur <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.ExternalMetadataColumnID%2A>-Eigenschaft der Eingabe- oder Ausgabespalte zugeordnet. So können Sie die externe Metadatenspalte für eine spezifische Eingabe- oder Ausgabespalte leicht mithilfe der <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumnCollection100.GetObjectByID%2A>-Methode der Auflistung finden.  
  
 Im folgenden Beispiel werden die Erstellung einer externen Metadatenspalte und die anschließende Zuordnung der Spalte zu einer Ausgabespalte durch Festlegen der <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.ExternalMetadataColumnID%2A>-Eigenschaft veranschaulicht.  
  
```csharp  
public void CreateExternalMetaDataColumn(IDTSOutput100 output, int outputColumnID )  
{  
    IDTSOutputColumn100 oColumn = output.OutputColumnCollection.GetObjectByID(outputColumnID);  
    IDTSExternalMetadataColumn100 eColumn = output.ExternalMetadataColumnCollection.New();  
  
    eColumn.DataType = oColumn.DataType;  
    eColumn.Precision = oColumn.Precision;  
    eColumn.Scale = oColumn.Scale;  
    eColumn.Length = oColumn.Length;  
    eColumn.CodePage = oColumn.CodePage;  
  
    oColumn.ExternalMetadataColumnID = eColumn.ID;  
}  
```  
  
```vb  
Public Sub CreateExternalMetaDataColumn(ByVal output As IDTSOutput100, ByVal outputColumnID As Integer)   
 Dim oColumn As IDTSOutputColumn100 = output.OutputColumnCollection.GetObjectByID(outputColumnID)   
 Dim eColumn As IDTSExternalMetadataColumn100 = output.ExternalMetadataColumnCollection.New   
 eColumn.DataType = oColumn.DataType   
 eColumn.Precision = oColumn.Precision   
 eColumn.Scale = oColumn.Scale   
 eColumn.Length = oColumn.Length   
 eColumn.CodePage = oColumn.CodePage   
 oColumn.ExternalMetadataColumnID = eColumn.ID   
End Sub  
```  
  
## <a name="validating-with-external-metadata-columns"></a>Überprüfen anhand externer Metadatenspalten  
 Die Überprüfung erfordert weitere Schritte für Komponenten, die eine externe Metadatenspaltenauflistung verwalten, denn Sie müssen die Überprüfung anhand einer weiteren Spaltenauflistung vornehmen. Bei der Überprüfung kann zwischen einer verbundenen und einer getrennten Überprüfung unterschieden werden.  
  
### <a name="connected-validation"></a>Verbundene Überprüfung  
 Besteht eine Verbindung einer Komponente mit einer externen Datenquelle, werden die Spalten in den Eingabe- oder Ausgabeauflistungen direkt anhand der externen Datenquelle überprüft. Darüber hinaus müssen die Spalten in der externen Metadatensammlung überprüft werden. Dies ist erforderlich, da die externe Metadatensammlung unter **Erweiterter Editor** in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] verändert werden kann, und Änderungen, die an der Sammlung vorgenommen werden, nicht erkennbar sind. Daher müssen die Komponenten, wenn eine Verbindung besteht, sicherstellen, dass die Spalten in der externen Metadatensammlung weiterhin den Spalten der externen Datenquelle entsprechen.  
  
 Sie können auch die externe Metadatensammlung Ausblenden der **Erweiterter Editor** durch Festlegen der <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumnCollection100.IsUsed%2A> -Eigenschaft der Auflistung zu `false`. Dadurch wird jedoch auch die Registerkarte **Spaltenzuordnung** des Editors ausgeblendet, über die Benutzer Spalten der Eingabe- und Ausgabeauflistungen den Spalten in der externen Metadatenspaltenauflistung zuordnen können. Ein Festlegen dieser Eigenschaft auf den Wert `false` verhindert nicht, dass Entwickler die Auflistung programmgesteuert verändern, bietet jedoch Schutz für die externe Metadatenspaltenauflistung einer Komponente, die ausschließlich in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] verwendet wird.  
  
### <a name="disconnected-validation"></a>Getrennte Überprüfung  
 Ist die Verbindung einer Komponente mit einer externen Datenquelle getrennt, ist die Überprüfung einfacher, da die Spalten in der Eingabe- oder Ausgabeauflistung direkt anhand der Spalten der externen Metadatensammlung und nicht anhand der externen Datenquelle überprüft werden. Eine Komponente sollte eine getrennte Überprüfung ausführen, wenn keine Verbindung mit der externen Datenquelle besteht oder die <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ValidateExternalMetadata%2A>-Eigenschaft den Wert `false` aufweist.  
  
 Im folgenden Codebeispiel wird die Implementierung einer Komponente, die eine Überprüfung anhand der externen Metadatenspaltenauflistung vornimmt, gezeigt.  
  
```csharp  
public override DTSValidationStatus Validate()  
{  
    if( this.isConnected && ComponentMetaData.ValidateExternalMetaData )  
    {  
        // TODO: Perform connected validation.  
    }  
    else  
    {  
        // TODO: Perform disconnected validation.  
    }  
}  
```  
  
```vb  
Public  Overrides Function Validate() As DTSValidationStatus   
 If Me.isConnected AndAlso ComponentMetaData.ValidateExternalMetaData Then   
  ' TODO: Perform connected validation.  
 Else   
  ' TODO: Perform disconnected validation.  
 End If   
End Function  
```  
  
![Integration Services (kleines Symbol)](../../media/dts-16.gif "Integration Services (kleines Symbol)")**bleiben oben, um das Datum mit Integration Services** <br /> Die neuesten Downloads, Artikel, Beispiele und Videos von Microsoft sowie ausgewählte Lösungen aus der Community finden Sie auf MSDN auf der [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] -Seite:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](http://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenfluss](../../data-flow/data-flow.md)  
  
  
