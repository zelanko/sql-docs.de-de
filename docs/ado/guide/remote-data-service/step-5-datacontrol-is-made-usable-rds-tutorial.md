---
title: 'Schritt 5: DataControl wird nutzbar gemacht (RDS-Tutorial) | Microsoft-Dokumentation'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS tutorial [ADO], datacontrol made usable
ms.assetid: ed5c4a24-9804-4c85-817e-317652acb9b4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 01b7a1b7829ace46cac7be21d33d9837845db9a7
ms.sourcegitcommit: 1a5448747ccb2e13e8f3d9f04012ba5ae04bb0a3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/12/2018
ms.locfileid: "51559737"
---
# <a name="step-5-datacontrol-is-made-usable-rds-tutorial"></a>Schritt 5: DataControl wird nutzbar gemacht (RDS-Tutorial)
Das zurückgegebene **Recordset** Objekt für die Verwendung verfügbar ist. Sie können überprüfen, navigieren Sie oder bearbeiten Sie sie, wie jede andere **Recordset**. Was Sie tun können, mit der **Recordset** hängt von Ihrer Umgebung. Visual Basic und Visual C++, haben Sie visuelle Steuerelemente, mit dem eine **Recordset** direkt oder indirekt mit Hilfe des Steuerelements ein aktivieren.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Z. B. Wenn Sie eine Webseite in Microsoft Internet Explorer anzeigen, Sie möchten Anzeigen der **Recordset** Objektdaten in einem visual-Steuerelement. Visuelle Steuerelemente auf einer Webseite können nicht zugegriffen werden. eine **Recordset** direkt. Allerdings können Zugriff auf die **Recordset** -Objekt über die [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md). Die **RDS. DataControl** verwendet wird, indem Sie eine Visualisierung steuern, wann die [SourceRecordset](../../../ado/reference/rds-api/recordset-sourcerecordset-properties-rds.md) -Eigenschaftensatz auf die **Recordset** Objekt.  
  
 Visuellen Steuerelements müssen die **Typ** Parameter festgelegt wird, um die **RDS. DataControl**, und die zugehörige **DATAFLD** -Eigenschaftensatz auf eine **Recordset** Objekt-Feld (Spalte).  
  
 In diesem Tutorial legen die **SourceRecordset** Eigenschaft:  
  
```vb
Sub RDSTutorial5()  
   Dim DS as New RDS.DataSpace  
   Dim RS as ADODB.Recordset  
   Dim DC as New RDS.DataControl  
   Dim DF as Object  
   Set DF = DS.CreateObject("RDSServer.DataFactory", "https://yourServer")  
   Set RS = DF.Query ("DSN=Pubs", "SELECT * FROM Authors")  
   DC.SourceRecordset = RS         ' Visual controls can now bind to DC.  
...  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Schritt 6: Änderungen werden an den Server (RDS-Tutorial) gesendet.](../../../ado/guide/remote-data-service/step-6-changes-are-sent-to-the-server-rds-tutorial.md)   
 [RDS-Tutorial (VBScript)](../../../ado/guide/remote-data-service/rds-tutorial-vbscript.md)   
