---
description: 'Schritt 3: Server ruft ein Recordset ab (RDS-Tutorial)'
title: 'Schritt 3: Server erhält ein Recordset (RDS-Tutorial) | Microsoft-Dokumentation'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS tutorial [ADO], server obtains Recordset
ms.assetid: 9c6779c9-1208-4696-ac51-c39f3a6d9240
author: rothja
ms.author: jroth
ms.openlocfilehash: 494cf7a3be5206f5fd4f89d3f575989ce51002b9
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88977541"
---
# <a name="step-3-server-obtains-a-recordset-rds-tutorial"></a>Schritt 3: Server ruft ein Recordset ab (RDS-Tutorial)
Das Serverprogramm verwendet die Verbindungs Zeichenfolge und den Befehls Text, um die Datenquelle nach den gewünschten Zeilen abzufragen. ADO wird in der Regel zum Abrufen dieses **Recordsets**verwendet, obwohl andere Microsoft-Datenzugriffs Schnittstellen (z. b. OLE DB) verwendet werden können.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
 Ein benutzerdefiniertes Serverprogramm könnte wie folgt aussehen:  
  
```vb
Public Function ServerProgram(cn as String, qry as String) as Object  
Dim rs as New ADODB.Recordset  
   rs.CursorLocation = adUseClient  
   rs.Open qry, cn   
   rs.ActiveConnection = Nothing  
   Set ServerProgram = rs  
End Function  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Schritt 4: Server gibt das Recordset zurück (RDS-Tutorial)](./step-4-server-returns-the-recordset-rds-tutorial.md)   
 [RDS-Tutorial (VBScript)](./rds-tutorial-vbscript.md)