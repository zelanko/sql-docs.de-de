---
title: Simulieren einer Fehlerausgabe für die Skriptkomponente | Microsoft-Dokumentation
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
- Script component [Integration Services], error output
- error outputs [Integration Services], Script component
ms.assetid: f8b6ecff-ac99-4231-a0e7-7ce4ad76bad0
caps.latest.revision: 27
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 0c09510a58c691f4db6b12c4613ff68c9642ffa1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36049942"
---
# <a name="simulating-an-error-output-for-the-script-component"></a>Simulieren einer Fehlerausgabe für die Skriptkomponente
  Zur automatischen Bearbeitung von Fehlerzeilen können Sie eine Ausgabe in der Skriptkomponente zwar nicht direkt als Fehlerausgabe konfigurieren, aber Sie können die Funktion einer integrierten Fehlerausgabe reproduzieren, indem Sie eine weitere Ausgabe erstellen und im Skript Bedingungslogik verwenden, um Zeilen gegebenenfalls an diese Ausgabe weiterzuleiten. Möglicherweise möchten Sie das Verhalten einer integrierten Fehlerausgabe imitieren, indem Sie zwei zusätzliche Ausgabespalten hinzufügen, sodass Sie die Fehlernummer und die ID der Spalte erhalten, in der der Fehler aufgetreten ist.  
  
 Wenn Sie die Fehlerbeschreibung hinzufügen möchten, die einem spezifischen vordefinierten [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Fehlercode entspricht, können Sie dazu die <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.GetErrorDescription%2A>-Methode der <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100>-Schnittstelle verwenden. Diese wird über die <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A>-Eigenschaft der Skriptkomponente bereitgestellt.  
  
## <a name="example"></a>Beispiel  
 Das hier dargestellte Beispiel verwendet eine Skriptkomponente, die als Transformation konfiguriert ist und über zwei synchrone Ausgaben verfügt. Der Zweck der Skriptkomponente besteht darin, Fehlerzeilen aus Adressdaten in der AdventureWorks-Beispieldatenbank herauszufiltern. Dieses fiktive Beispiel geht von der Annahme aus, dass wir eine Werbeaktion für Kunden in Nordamerika vorbereiten und dazu Adressen herausfiltern müssen, die sich nicht in Nordamerika befinden.  
  
#### <a name="to-configure-the-example"></a>So konfigurieren Sie das Beispiel  
  
1.  Erstellen Sie einen Verbindungs-Manager, bevor Sie die neue Skriptkomponente erzeugen, und konfigurieren Sie eine Datenflussquelle, die Adressdaten aus der AdventureWorks-Beispieldatenbank herausfiltert. Für dieses Beispiel hat nur die Spalte CountryRegionName Bedeutung. Sie können einfach die Ansicht Person.vStateCountryProvinceRegion verwenden, oder Sie können Daten auswählen, indem Sie die Tabellen Person.Address, Person.StateProvince und Person.CountryRegion miteinander verknüpfen.  
  
2.  Fügen Sie der Datenfluss-Designeroberfläche eine neue Skriptkomponente hinzu, und konfigurieren Sie sie als Transformation. Öffnen Sie den **Transformations-Editor für Skripterstellung**.  
  
3.  Legen Sie auf der Seite **Skript** die **ScriptLanguage**-Eigenschaft auf die Skriptsprache fest, die Sie zum Codieren des Skripts verwenden möchten.  
  
4.  Klicken Sie auf **Skript bearbeiten** , um [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) zu öffnen.  
  
5.  Geben Sie den unten dargestellten Beispielcode in die `Input0_ProcessInputRow`-Methode ein, oder fügen Sie ihn ein.  
  
6.  Schließen Sie VSTA.  
  
7.  Wählen Sie auf der Seite **Eingabespalten** die Spalten aus, die Sie in der Skripttransformation verarbeiten möchten. In diesem Beispiel wird nur die CountryRegionName-Spalte verwendet. Verfügbare Eingabespalten, die Sie nicht auswählen, werden einfach unverändert im Datenfluss durchlaufen.  
  
8.  Auf der **Eingaben und Ausgaben** Seite, fügen Sie einen neuen, zweite Ausgabe, und legen Sie dessen `SynchronousInputID` Wert, der die ID der Eingabe, das ebenfalls den Wert von der `SynchronousInputID` -Eigenschaft der Standardausgabe. Legen Sie die `ExclusionGroup`-Eigenschaft beider Ausgaben auf denselben Wert ungleich Null (z. B. 1) fest, um anzugeben, dass jede Zeile nur an eine der beiden Ausgaben weitergeleitet wird. Geben Sie der neuen Fehlerausgabe einen aussagekräftigen Namen, z. B. "MeineFehlerausgabe".  
  
9. Fügen Sie der neuen Fehlerausgabe zusätzliche Ausgabespalten hinzu, um die gewünschten Fehlerinformationen aufzuzeichnen, zu denen zum Beispiel der Fehlercode, die ID der Spalte mit dem Fehler und möglicherweise die Fehlerbeschreibung zählen können. In diesem Beispiel werden die neuen Spalten, ErrorColumn und ErrorMessage, erstellt. Wenn Sie vordefinierte [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Fehler in Ihren eigenen Implementierungen erkennen, stellen Sie sicher, dass Sie eine ErrorCode-Spalte für die Fehlernummer hinzufügen.  
  
10. Beachten Sie den ID-Wert der Eingabezeile oder -zeilen, die die Skriptkomponente auf Fehlerbedingungen untersucht. In diesem Beispiel wird dieser Spaltenbezeichner dazu verwendet, den ErrorColumn-Wert aufzufüllen.  
  
11. Schließen Sie den **Transformations-Editor für Skripterstellung**.  
  
12. Fügen Sie die Ausgaben der Skriptkomponente an geeignete Ziele an. Flatfileziele sind die einfachste Möglichkeit zur Konfiguration bei Ad-hoc-Tests.  
  
13. Führen Sie das Paket aus.  
  
```vb  
Public Overrides Sub Input0_ProcessInputRow(ByVal Row As Input0Buffer)  
  
  If Row.CountryRegionName <> "Canada" _  
      And Row.CountryRegionName <> "United States" Then  
  
    Row.ErrorColumn = 68 ' ID of CountryRegionName column  
    Row.ErrorMessage = "Address is not in North America."  
    Row.DirectRowToMyErrorOutput()  
  
  Else  
  
    Row.DirectRowToOutput0()  
  
  End If  
  
End Sub  
```  
  
```csharp  
public override void Input0_ProcessInputRow(Input0Buffer Row)  
{  
  
  if (Row.CountryRegionName!="Canada"&&Row.CountryRegionName!="United States")  
  
  {  
    Row.ErrorColumn = 68; // ID of CountryRegionName column  
    Row.ErrorMessage = "Address is not in North America.";  
    Row.DirectRowToMyErrorOutput();  
  
  }  
  else  
  {  
  
    Row.DirectRowToOutput0();  
  
  }  
  
}  
```  
  
![Integration Services (kleines Symbol)](../media/dts-16.gif "Integration Services (kleines Symbol)")**bleiben Sie mit Integration Services** <br /> Die neuesten Downloads, Artikel, Beispiele und Videos von Microsoft sowie ausgewählte Lösungen aus der Community finden Sie auf MSDN auf der [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Seite:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](http://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.  
  
## <a name="see-also"></a>Siehe auch  
 [Fehlerbehandlung in Daten](../data-flow/error-handling-in-data.md)   
 [Verwenden von Fehlerausgaben in einer Datenflusskomponente](../extending-packages-custom-objects/data-flow/using-error-outputs-in-a-data-flow-component.md)   
 [Erstellen einer synchronen Transformation mit der Skriptkomponente](../extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md) 
  
  