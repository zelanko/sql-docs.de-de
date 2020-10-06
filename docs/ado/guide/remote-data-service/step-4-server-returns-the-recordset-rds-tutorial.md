---
description: 'Schritt 4: Server gibt das Recordset zurück (RDS-Tutorial)'
title: 'Schritt 4: der Server gibt das Recordset zurück (RDS-Tutorial) | Microsoft-Dokumentation'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS tutorial [ADO], server returns Recordset
ms.assetid: 3d1855c4-419c-4810-b5ea-6c874b5e2905
author: rothja
ms.author: jroth
ms.openlocfilehash: 031681460a9f5b958bc08f2b39cec6b3ec794623
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/05/2020
ms.locfileid: "91722961"
---
# <a name="step-4-server-returns-the-recordset-rds-tutorial"></a>Schritt 4: Server gibt das Recordset zurück (RDS-Tutorial)
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](/dotnet/framework/wcf/)migriert werden.  
  
 RDS konvertiert das abgerufene **Recordset** -Objekt in ein Formular, das an den Client zurückgesendet werden kann (d. h., er *Marshalls* das **Recordset**). Die genaue Form der Konvertierung und die Art der Übermittlung hängt davon ab, ob der Server sich im Internet oder in einem Intranet oder in einem lokalen Netzwerk befindet oder ob es sich um eine Dynamic Link Library handelt. Dieses Detail ist jedoch nicht kritisch. alles, was wichtig ist, ist, dass RDS das **Recordset** an den Client zurücksendet.  
  
 Auf der Clientseite wird ein **Recordset** -Objekt zurückgegeben und einer lokalen Variablen zugewiesen.  
  
```vb
Sub RDSTutorial4()  
   Dim DS as New RDS.DataSpace  
   Dim RS as ADODB.Recordset  
   Dim DF as Object  
   Set DF = DS.CreateObject("RDSServer.DataFactory", "https://yourServer")  
   Set RS = DF.Query("DSN=Pubs", "SELECT * FROM Authors")  
...  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Schritt 5: DataControl ist verwendbar (RDS-Tutorial)](./step-5-datacontrol-is-made-usable-rds-tutorial.md)   
 [RDS-Tutorial (VBScript)](./rds-tutorial-vbscript.md)