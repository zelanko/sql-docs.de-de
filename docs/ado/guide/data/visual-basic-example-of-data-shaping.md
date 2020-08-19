---
description: Visual Basic-Beispiel der Datenstrukturierung
title: Visual Basic Beispiel für die Daten Strukturierung | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
ms.openlocfilehash: da0fc3bcc0af5aa4c4477c91f66e2ce1f2b2d7e0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88452562"
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
  
#### <a name="try-it"></a>Probieren Sie es aus!  
  
1.  Erstellen eines Visual Basic Standard-exe-Anwendungs Projekts  
  
2.  Auswählen von **Komponenten** aus dem Menü " **Projekt** " in Visual Studio  
  
3.  Wählen Sie im Popup Fenster **Komponenten** "Microsoft hierarchisches FlexGrid-Steuerelement 6,0 (OleDb)" aus, und klicken Sie dann auf **Speichern**.  
  
4.  Doppelklicken Sie im Bereich Toolbox im Arbeitsbereich Visual Basic auf das Steuerelement FlexGrid. Ändern Sie den Namen dieser Instanz in MSHFlexGrid.  
  
5.  Kopieren Sie den vorangehenden Code, und fügen Sie ihn in die **Codepage** ein, um vorhandenen Code zu ersetzen.  
  
6.  Wählen Sie im Menü **Ausführen** die Option **starten** aus, um die Anwendung auszuführen.
