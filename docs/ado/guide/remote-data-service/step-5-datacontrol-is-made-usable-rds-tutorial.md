---
description: 'Schritt 5: DataControl wird nutzbar gemacht (RDS-Tutorial)'
title: 'Schritt 5: DataControl ist verwendbar (RDS-Tutorial) | Microsoft-Dokumentation'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS tutorial [ADO], datacontrol made usable
ms.assetid: ed5c4a24-9804-4c85-817e-317652acb9b4
author: rothja
ms.author: jroth
ms.openlocfilehash: 560c5968b3343f2553bc117ebbbdcf06938cc49f
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/05/2020
ms.locfileid: "91722951"
---
# <a name="step-5-datacontrol-is-made-usable-rds-tutorial"></a>Schritt 5: DataControl wird nutzbar gemacht (RDS-Tutorial)
Das zurückgegebene **Recordset** -Objekt ist zur Verwendung verfügbar. Sie können Sie wie jedes andere **Recordset**überprüfen, navigieren oder bearbeiten. Was Sie mit dem **Recordset** tun können, hängt von Ihrer Umgebung ab. Visual Basic und Visual C++ über visuelle Steuerelemente verfügen, die ein **Recordset** direkt oder indirekt mit der Unterstützung eines aktivierenden Daten Steuer Elements verwenden können.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](/dotnet/framework/wcf/)migriert werden.  
  
 Wenn Sie z. b. eine Webseite in Microsoft Internet Explorer anzeigen, möchten Sie möglicherweise die Daten des **Recordset** -Objekts in einem visuellen Steuerelement anzeigen. Visuelle Steuerelemente auf einer Webseite können nicht direkt auf ein **Recordset** -Objekt zugreifen. Allerdings können Sie über das RDS auf das **Recordset** -Objekt zugreifen [. DataControl](../../reference/rds-api/datacontrol-object-rds.md). Das **RDS. DataControl** kann von einem visuellen Steuerelement verwendet werden, wenn die [SourceRecordset](../../reference/rds-api/recordset-sourcerecordset-properties-rds.md) -Eigenschaft auf das **Recordset** -Objekt festgelegt ist.  
  
 Für das visuelle Steuerelement Objekt muss sein **dataSrc** -Parameter auf RDS festgelegt sein **. DataControl**und die zugehörige **Datafld** -Eigenschaft sind auf ein **Recordset** -Objektfeld (Spalte) festgelegt.  
  
 Legen Sie in diesem Tutorial die **SourceRecordset** -Eigenschaft fest:  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Schritt 6: Änderungen werden an den Server gesendet (RDS-Tutorial)](./step-6-changes-are-sent-to-the-server-rds-tutorial.md)   
 [RDS-Tutorial (VBScript)](./rds-tutorial-vbscript.md)