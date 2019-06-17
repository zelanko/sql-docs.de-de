---
title: Visual Basic-Beispiel der Datenstrukturierung | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic example of data shaping[ADO], about data shaping
ms.assetid: d95dd499-19e2-4ce7-b16e-f56a04a9519c
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 8af816b36ee3138c7742447ccba6b20c14860dff
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66704587"
---
# <a name="visual-basic-example-of-data-shaping"></a>Visual Basic-Beispiel der Datenstrukturierung
```  
' This application makes use of Microsoft Hierarchical FlexGrid  
' Control, which is named as MSHFLexGrid.  
Const SHAPER = "MSDataShape"  
Const DP = "SQLOLEDB"  
Const DS = "MySQLServer"  
Const DB = "Northwind"  
  
Private Sub Form_Load()  
    FirstExample  
End Sub  
  
Private Sub Form_Resize()  
    MSHFlexGrid.Top = 0  
    MSHFlexGrid.Left = 0  
    MSHFlexGrid.Width = Me.ScaleWidth  
    MSHFlexGrid.Height = Me.ScaleHeight  
End Sub  
  
Private Sub FirstExample()  
    Dim con As ADODB.Connection  
    Dim rst As ADODB.Recordset  
    Dim sCmd As String  
  
    Set con = New ADODB.Connection  
    Set rst = New ADODB.Recordset  
  
    con.ConnectionString = ConnectionString(SHAPER, DP, DS, DB)  
    con.Open  
  
    sCmd = "SHAPE {SELECT CustomerID, ContactName FROM Customers} " _  
        & "APPEND ({SELECT OrderID, OrderDate, CustomerID FROM Orders} " _  
        & "AS chapOrders " _  
        & "RELATE customerID TO customerID)"  
  
    rst.Open sCmd, con, adOpenStatic, 2  
    Set MSHFlexGrid.Recordset = rst  
  
    rst.Close  
    Set rst = Nothing  
  
    con.Close  
    Set con = Nothing  
  
End Sub  
  
Private Function ConnectionString(pr As String, _  
                                  dpr As String, _  
                                  dsr As String, _  
                                  dbs As String)  
    Dim s As String  
    If pr = "" Then  
        s = "Provider=" & dpr & _  
          ";Data Source=" & dsr & _  
          ";Initial Catalog=" & dbs & _  
          ";Integrated Security=SSPI;"  
    Else  
        s = "Provider=" & pr & _  
          ";Data Provider=" & dpr & _  
          ";Data Source=" & dsr & _  
          ";Initial Catalog=" & dbs & _  
          ";Integrated Security=SSPI;"  
    End If  
    ConnectionString = s  
End Function  
  
```  
  
#### <a name="try-it"></a>Versuch es!  
  
1.  Erstellen eines Visual Basic-Standard-EXE-Anwendungsprojekts  
  
2.  Wählen Sie **Komponenten** aus der **Projekt** Menü in Visual Studio  
  
3.  Wählen Sie "Microsoft hierarchische Flex-Tabelle Steuerelement 6.0 (OLEDB)" aus der **Komponenten** Popup-Fenster, und klicken Sie dann auf **speichern**.  
  
4.  Doppelklicken Sie auf das Steuerelement Flex-Tabelle, aus dem Bereich "ToolBox" in Visual Basic-Arbeitsbereichs. Ändern Sie den Namen dieser Instanz, um MSHFLEXGRID.  
  
5.  Kopieren Sie den vorherigen Code, und fügen Sie ihn in das **Code** Seite, um alle vorhandenen Code zu ersetzen.  
  
6.  Wählen Sie **starten** aus der **ausführen** Menü, um die Anwendung auszuführen.
