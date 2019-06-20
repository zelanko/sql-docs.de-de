---
title: Behandeln von Book-Befehlsschaltflächen | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- address book application scenario [ADO], command buttons
- RDS scenarios [ADO], command buttons
ms.assetid: 80676831-6488-4dad-a558-c47c52256a22
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 731189838918a04ec211ec0bcac3f66843658177
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66699636"
---
# <a name="address-book-command-buttons"></a>Adress Book-Befehlsschaltflächen
Das Adressbuch-App umfasst die folgenden Schaltflächen:  
  
-   Ein **finden** Schaltfläche, um eine Abfrage an die Datenbank übermitteln.  
  
-   Ein **löschen** Schaltfläche, um den Inhalt der Textfelder zu löschen, bevor Sie eine neue Suche ab.  
  
-   Ein **Profil aktualisieren** Schaltfläche, um die Änderungen in einem Mitarbeiterdatensatz zu speichern.  
  
-   Ein **Änderungen Abbrechen** Schaltfläche, um die Änderungen zu verwerfen.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="find-button"></a>Schaltfläche "Suchen"  
 Klicken auf die **finden** Schaltfläche aktiviert wird, die VBScript-Find_OnClick-Sub-Prozedur, die erstellt und sendet die SQL-Abfrage. Auf diese Schaltfläche klicken, füllt das Datenraster.  
  
## <a name="building-the-sql-query"></a>Erstellen der SQL-Abfrage  
 Der erste Teil der Find_OnClick Sub-Prozedur erstellt die SQL-Abfrage, einen Ausdruck zu einem Zeitpunkt durch Anfügen von Zeichenfolgen, die an eine globale SQL SELECT-Anweisung. Zunächst wird die Variable `myQuery` auf eine SQL SELECT-Anweisung, die alle Zeilen mit Daten aus der Quelltabelle für die Daten anfordert. Als Nächstes durchsucht die Sub-Prozedur jedes der vier Eingabefelder auf der Seite.  
  
 Da das Programm das Wort verwendet `like` bei der Erstellung der SQL-Anweisungen, die Abfragen sind Teilzeichenfolge suchen, anstatt genaue Übereinstimmungen.  
  
 Z. B. wenn die **Nachname** Feld enthalten den Eintrag "Berge" und die **Titel** Feld enthalten den Eintrag "Programm-Manager" der SQL-Anweisung (Wert des `myQuery`) liest:  
  
```sql
Select FirstName, LastName, Title, Email, Building, Room, Phone from Employee where lastname like 'Berge%' and title like 'Program Manager%'  
```  
  
 Wenn die Abfrage erfolgreich war, werden alle Personen, die mit einem Nachnamen, die mit dem Text "Berge" (z. B. Berge und Berger) und mit einem Titel, die die Wörter "Programm-Manager" (z. B. Programmmanager, erweiterte Technologien) im HTML-Datenraster angezeigt.  
  
## <a name="preparing-and-sending-the-query"></a>Vorbereiten und das Senden der Abfrage  
 Der letzte Teil der Find_OnClick Sub-Prozedur besteht aus zwei Anweisungen. Die erste Anweisung weist die [SQL](../../../ado/reference/rds-api/sql-property.md) Eigenschaft der [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) Objekt gleich der dynamisch erstellten SQL-Abfrage. Die zweite Anweisung bewirkt, dass die **RDS. DataControl** Objekt (`DC1`) auf die Datenbank abzufragen, und klicken Sie dann die neuen Ergebnisse der Abfrage im Raster angezeigt.  
  
```vb
Sub Find_OnClick  
   '...  
   DC1.SQL = myQuery  
   DC1.Refresh  
End Sub  
```  
  
## <a name="update-profile-button"></a>Aktualisieren Sie die Schaltfläche "Profil"  
 Klicken auf die **Profil aktualisieren** Schaltfläche aktiviert wird, die VBScript Update_OnClick Sub-Prozedur, führt die [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) des Objekts (`DC1`) [SubmitChanges](../../../ado/reference/rds-api/submitchanges-method-rds.md) und [aktualisieren](../../../ado/reference/rds-api/refresh-method-rds.md) Methoden.  
  
```vb
Sub Update_OnClick  
   DC1.SubmitChanges  
   DC1.Refresh  
End Sub  
```  
  
 Wenn `DC1.SubmitChanges` ausgeführt wird, Remote Data Service Packt die Updateinformationen und sendet sie an den Server über HTTP. Das Update ist nichts. Wenn ein Teil des Updates nicht erfolgreich ist, erfolgt keine der Änderungen und eine Statusmeldung wird zurückgegeben. `DC1.Refresh` ist nicht erforderlich, nach dem **SubmitChanges** mit Remote Data Service stellt jedoch sicher neue Daten.  
  
## <a name="cancel-changes-button"></a>Abbrechen-Schaltfläche "Änderungen"  
 Auf **Änderungen Abbrechen** aktiviert die VBScript Cancel_OnClick Sub-Prozedur, führt die [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) des Objekts (`DC1)` [CancelUpdate](../../../ado/reference/rds-api/cancelupdate-method-rds.md) Methode.  
  
```vb
Sub Cancel_OnClick  
   DC1.CancelUpdate  
End Sub  
```  
  
 Wenn `DC1.CancelUpdate` ausgeführt wird, es verwirft alle Änderungen, die ein Benutzer auf das Datenraster Mitarbeiterdatensatz seit der letzten Abfrage oder Aktualisierung vorgenommen hat. Die ursprünglichen Werte wiederhergestellt.  
  
## <a name="see-also"></a>Siehe auch  
 [Behandeln von Book-Navigationsschaltflächen](../../../ado/guide/remote-data-service/address-book-navigation-buttons.md)   
 [DataControl-Objekt (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)


