---
title: Adressbuch-Navigations Schaltflächen | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS scenarios [ADO], navigation buttons
- address book application scenario [ADO], navigation buttons
ms.assetid: f0dd84c6-5c33-4ab9-82b4-4c42dfdd2277
author: rothja
ms.author: jroth
ms.openlocfilehash: fcb9ef043f27cd36c57b35605c8bf8257613af5d
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82764711"
---
# <a name="address-book-navigation-buttons"></a>Adress Book-Navigationsschaltflächen
Die Adressbuch Anwendung zeigt die Navigations Schaltflächen unten auf der Webseite an. Sie können die Navigations Schaltflächen verwenden, um durch die Daten in der HTML-Raster Anzeige zu navigieren, indem Sie entweder die erste oder letzte Daten Zeile oder Zeilen neben der aktuellen Auswahl auswählen.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
## <a name="navigation-sub-procedures"></a>Navigations unter Prozeduren  
 Die Adressbuch Anwendung enthält mehrere Prozeduren, mit denen Benutzer auf die Schaltflächen **erste**, **weiter**, zurück und **Letzter** klicken **können, um**die Daten zu verschieben.  
  
 Wenn Sie beispielsweise auf die **erste** Schaltfläche klicken, wird die VBScript-First_OnClick unter Prozedur aktiviert. Die Prozedur führt eine " [muvefirst](../../../ado/reference/rds-api/movefirst-movelast-movenext-and-moveprevious-methods-rds.md) "-Methode aus, die die erste Zeile der Daten zur aktuellen Auswahl macht. Durch Klicken auf die **Letzte** Schaltfläche wird die Last_OnClick unter Prozedur aktiviert, die die " [muvelast](../../../ado/reference/rds-api/movefirst-movelast-movenext-and-moveprevious-methods-rds.md) "-Methode aufruft und die letzte Daten Zeile zur aktuellen Auswahl macht. Die verbleibenden Navigations Schaltflächen funktionieren auf ähnliche Weise.  
  
```vb
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
  
## <a name="see-also"></a>Weitere Informationen  
 [DataControl-Objekt (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)   
 [MoveFirst-, MoveLast-, MoveNext- und MovePrevious-Methode (RDS)](../../../ado/reference/rds-api/movefirst-movelast-movenext-and-moveprevious-methods-rds.md)



