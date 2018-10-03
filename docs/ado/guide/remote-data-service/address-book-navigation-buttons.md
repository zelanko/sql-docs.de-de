---
title: Behandeln von Book-Navigationsschaltflächen | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS scenarios [ADO], navigation buttons
- address book application scenario [ADO], navigation buttons
ms.assetid: f0dd84c6-5c33-4ab9-82b4-4c42dfdd2277
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: be8020f5a9ce826fbe4f92864d8d580bbcb6ae5a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47696939"
---
# <a name="address-book-navigation-buttons"></a>Adress Book-Navigationsschaltflächen
Das Adressbuch-App zeigt die Navigationsschaltflächen am unteren Rand der Webseite an. Sie können die Navigationsschaltflächen verwenden, Navigieren durch die Daten in der HTML-Rasteransicht durch Auswählen von entweder die erste oder letzte Zeile der Daten oder Zeilen, die neben der aktuellen Auswahl.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/en-us/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="navigation-sub-procedures"></a>Navigation Sub-Prozeduren  
 Das Adressbuch-App enthält mehrere Verfahren, mit denen Benutzer auf die **erste**, **Weiter**, **zurück**, und **letzten** Schaltflächen, um die Daten zu verschieben.  
  
 Klicken Sie z. B. die **erste** Schaltfläche aktiviert wird, die VBScript First_OnClick Sub-Prozedur. Die Prozedur führt eine [MoveFirst](../../../ado/reference/rds-api/movefirst-movelast-movenext-and-moveprevious-methods-rds.md) -Methode, die der erste Zeile der Daten aufgrund der aktuelle Auswahl ist. Klicken auf die **letzten** Schaltfläche wird der Unterprozedur Last_OnClick aktiviert, die [MoveLast](../../../ado/reference/rds-api/movefirst-movelast-movenext-and-moveprevious-methods-rds.md) -Methode, sodass der letzten Zeile der Daten der aktuellen Auswahl. Die verbleibenden Navigationsschaltflächen funktionieren auf ähnliche Weise.  
  
```  
' Move to the first record in the bound Recordset.  
Sub First_OnClick  
   DC1.Recordset.MoveFirst  
End Sub  
  
' Move to the next record from the current position   
' in the bound Recordset.  
Sub Next_OnClick  
   If Not DC1.Recordset.EOF Then    ' Cannot move beyond bottom record.  
      DC1.Recordset.MoveNext  
      Exit Sub  
   End If     
End Sub  
  
' Move to the previous record from the current position in the bound   
' Recordset.  
Sub Prev_OnClick  
   If Not DC1.Recordset.BOF Then    ' Cannot move beyond top record.  
      DC1.Recordset.MovePrevious  
      Exit Sub  
   End If  
End Sub  
  
' Move to the last record in the bound Recordset.  
Sub Last_OnClick  
   DC1.Recordset.MoveLast  
End Sub  
```  
  
## <a name="see-also"></a>Siehe auch  
 [DataControl-Objekt (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)   
 [MoveFirst-, MoveLast-, MoveNext- und MovePrevious-Methode (RDS)](../../../ado/reference/rds-api/movefirst-movelast-movenext-and-moveprevious-methods-rds.md)



