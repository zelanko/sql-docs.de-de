---
title: 'Schritt 1: Geben Sie ein Serverprogramm (RDS-Lernprogramm) | Microsoft Docs'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS tutorial [ADO], specifying server program
ms.assetid: d8bb35b1-c02a-4231-8d55-016e56e53b95
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 68468c97d870f103260c8a5ee1b7914c2ecc378a
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "35274559"
---
# <a name="step-1-specify-a-server-program-rds-tutorial"></a>Schritt 1: Geben Sie ein Serverprogramm (RDS-Lernprogramm)
In den allgemeinsten Fall verwenden die [RDS. DataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md) Objekt [CreateObject](../../../ado/reference/rds-api/createobject-method-rds.md) Methode, um die Standardserverprogramm anzugeben [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md), oder eigene benutzerdefinierte Serverprogramm (Business-Objekt). Ein Serverprogramm auf dem Server und einem Verweis auf das Serverprogramm instanziiert wird oder *Proxy*, zurückgegeben.  
  
 Dieses Lernprogramm verwendet das Standardprogramm für den Server:  
  
```  
Sub RDSTutorial1()  
   Dim DS as New RDS.DataSpace  
   Dim DF as Object  
   Set DF = DS.("RDSServer.DataFactory", "http://yourServer")  
...  
```  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in Windows-Betriebssystems enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/en-us/download/details.aspx?id=27416) detailliertere). RDS-Clientkomponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden sollten migrieren [WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="see-also"></a>Siehe auch  
 [Schritt 2: Aufrufen des Programms (RDS-Lernprogramm)](../../../ado/guide/remote-data-service/step-2-invoke-the-server-program-rds-tutorial.md)   
 [RDS-Tutorial (VBScript)](../../../ado/guide/remote-data-service/rds-tutorial-vbscript.md)   
