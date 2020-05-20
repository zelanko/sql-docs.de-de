---
title: 'Schritt 4: der Server gibt das Recordset zurück (RDS-Tutorial) | Microsoft-Dokumentation'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS tutorial [ADO], server returns Recordset
ms.assetid: 3d1855c4-419c-4810-b5ea-6c874b5e2905
author: rothja
ms.author: jroth
ms.openlocfilehash: ce53c987a43ed208a4d7120fb3655b3a3acd5083
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82764661"
---
# <a name="step-4-server-returns-the-recordset-rds-tutorial"></a>Schritt 4: Server gibt das Recordset zurück (RDS-Tutorial)
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
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
 [Schritt 5: DataControl ist verwendbar (RDS-Tutorial)](../../../ado/guide/remote-data-service/step-5-datacontrol-is-made-usable-rds-tutorial.md)   
 [RDS-Tutorial (VBScript)](../../../ado/guide/remote-data-service/rds-tutorial-vbscript.md)   
