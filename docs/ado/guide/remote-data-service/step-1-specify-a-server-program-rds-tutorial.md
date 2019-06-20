---
title: 'Schritt 1: Geben Sie eine Serverprogramm (RDS-Tutorial) | Microsoft-Dokumentation'
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
manager: jroth
ms.openlocfilehash: 03d60a00a116f771e3854a4fe1b6b5ec512c0708
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66704176"
---
# <a name="step-1-specify-a-server-program-rds-tutorial"></a>Schritt 1: Angeben eines Serverprogramms (RDS-Tutorial)
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
