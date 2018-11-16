---
title: 'Schritt 1: Angeben ein Serverprogramms (RDS-Tutorial) | Microsoft-Dokumentation'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS tutorial [ADO], specifying server program
ms.assetid: d8bb35b1-c02a-4231-8d55-016e56e53b95
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5583f9b2c5093859e9bb5d3fd0eb9444828cb4bc
ms.sourcegitcommit: 1a5448747ccb2e13e8f3d9f04012ba5ae04bb0a3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/12/2018
ms.locfileid: "51558297"
---
# <a name="step-1-specify-a-server-program-rds-tutorial"></a>Schritt 1: Serverprogramm angeben (RDS-Tutorial)
Im allgemeinsten Fall verwenden die [RDS. DataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md) Objekt [CreateObject](../../../ado/reference/rds-api/createobject-method-rds.md) -Methode zur Angabe der Standardserverprogramm [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md), oder Ihre eigenen benutzerdefinierten Server-Programm (Business-Objekt). Ein Server-Programm wird auf dem Server und einen Verweis auf die Server-Anwendung instanziiert oder *Proxy*, zurückgegeben wird.  
  
 In diesem Tutorial verwendet das Standardprogramm für den Server:  
  
```vb
Sub RDSTutorial1()  
   Dim DS as New RDS.DataSpace  
   Dim DF as Object  
   Set DF = DS.("RDSServer.DataFactory", "https://yourServer")  
...  
```  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="see-also"></a>Siehe auch  
 [Schritt 2: Rufen Sie die Server-Anwendung (RDS-Tutorial)](../../../ado/guide/remote-data-service/step-2-invoke-the-server-program-rds-tutorial.md)   
 [RDS-Tutorial (VBScript)](../../../ado/guide/remote-data-service/rds-tutorial-vbscript.md)   
