---
description: Adress Book-Befehlsschaltflächen
title: Adressbuch-Befehls Schaltflächen | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- address book application scenario [ADO], command buttons
- RDS scenarios [ADO], command buttons
ms.assetid: 80676831-6488-4dad-a558-c47c52256a22
author: rothja
ms.author: jroth
ms.openlocfilehash: d234732b90fdd89b6f0e41efe1762bb3a99ddde2
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/05/2020
ms.locfileid: "91724851"
---
# <a name="address-book-command-buttons"></a>Adress Book-Befehlsschaltflächen
Die Adressbuch Anwendung enthält die folgenden Befehls Schaltflächen:  
  
-   Eine Schaltfläche **Suchen** , um eine Abfrage an die Datenbank zu übermitteln.  
  
-   Eine Schaltfläche **Löschen** , um die Textfelder vor dem Starten einer neuen Suche zu löschen.  
  
-   Eine Schaltfläche zum **Aktualisieren des Profils** , um Änderungen an einem Mitarbeiterdaten Satz zu speichern.  
  
-   Eine Schaltfläche zum **Abbrechen von Änderungen** zum Verwerfen von Änderungen.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](/dotnet/framework/wcf/)migriert werden.  
  
## <a name="find-button"></a>Schaltfläche Suchen  
 Wenn Sie auf die Schaltfläche **Suchen** klicken, wird die VBScript-Find_OnClick unter Prozedur aktiviert, die die SQL-Abfrage erstellt und sendet. Durch Klicken auf diese Schaltfläche wird das Datenraster aufgefüllt.  
  
## <a name="building-the-sql-query"></a>SQL-Abfrage wird aufgebaut  
 Der erste Teil der Find_OnClick unter Prozedur erstellt die SQL-Abfrage, jeweils einen Ausdruck, indem Text Zeichenfolgen an eine globale SQL SELECT-Anweisung angehängt werden. Zuerst wird die-Variable `myQuery` auf eine SQL SELECT-Anweisung festgelegt, die alle Daten Zeilen aus der Datenquellen Tabelle anfordert. Als nächstes scannt die unter Prozedur alle vier Eingabefelder auf der Seite.  
  
 Da das Programm das Wort zum entwickeln `like` der SQL-Anweisungen verwendet, sind die Abfragen Teil Zeichenfolgen-suchen anstelle von exakten Übereinstimmungen.  
  
 Wenn beispielsweise das Feld **Nachname** den Eintrag "Berge" enthielt und im Feld " **Titel** " der Eintrag "Programm-Manager" enthalten ist, wird in der SQL-Anweisung (Wert von `myQuery` ) Folgendes gelesen:  
  
```sql
Select FirstName, LastName, Title, Email, Building, Room, Phone from Employee where lastname like 'Berge%' and title like 'Program Manager%'  
```  
  
 Wenn die Abfrage erfolgreich war, werden alle Personen mit einem Nachnamen, der den Text "Berge" enthält (z. b. "Berge" und "Berger"), und mit einem Titel, der die Wörter "Program Manager" enthält (z. b. Programm-Manager, erweiterte Technologien), im HTML-Datenraster angezeigt.  
  
## <a name="preparing-and-sending-the-query"></a>Vorbereiten und Senden der Abfrage  
 Der letzte Teil der Find_OnClick unter Prozedur besteht aus zwei-Anweisungen. Mit der ersten Anweisung wird die [SQL](../../reference/rds-api/sql-property.md) -Eigenschaft des [RDS zugewiesen. DataControl](../../reference/rds-api/datacontrol-object-rds.md) -Objekt, das der dynamisch erstellten SQL-Abfrage entspricht. Die zweite Anweisung bewirkt, dass **RDS. DataControl** -Objekt ( `DC1` ) zum Abfragen der Datenbank und anschließendes Anzeigen der neuen Ergebnisse der Abfrage im Raster.  
  
```vb
Sub Find_OnClick  
   '...  
   DC1.SQL = myQuery  
   DC1.Refresh  
End Sub  
```  
  
## <a name="update-profile-button"></a>Schaltfläche Profil aktualisieren  
 Wenn Sie auf die Schaltfläche " **Profil aktualisieren** " klicken, wird die VBScript-Update_OnClick unter Prozedur aktiviert, die [RDS ausführt. ](../../reference/rds-api/datacontrol-object-rds.md) `DC1` [SubmitChanges](../../reference/rds-api/submitchanges-method-rds.md) und [Aktualisierungs](../../reference/rds-api/refresh-method-rds.md) Methoden des DataControl-Objekts.  
  
```vb
Sub Update_OnClick  
   DC1.SubmitChanges  
   DC1.Refresh  
End Sub  
```  
  
 Wenn `DC1.SubmitChanges` ausgeführt wird, verpackt der Remote Datendienst alle Update Informationen und sendet Sie über HTTP an den Server. Das Update ist alles-oder-nichts. Wenn ein Teil des Updates nicht erfolgreich ist, wird keine der Änderungen vorgenommen, und eine Statusmeldung wird zurückgegeben. `DC1.Refresh` ist nach **SubmitChanges** mit dem Remote Datendienst nicht erforderlich, stellt jedoch neue Daten sicher.  
  
## <a name="cancel-changes-button"></a>Schaltfläche "Änderungen abbrechen  
 Wenn Sie auf **Änderungen abbrechen** klicken, wird die VBScript-Cancel_OnClick unter Prozedur aktiviert, die das [RDS ausführt. DataControl](../../reference/rds-api/datacontrol-object-rds.md) -Objekt ( `DC1)` [CancelUpdate](../../reference/rds-api/cancelupdate-method-rds.md) -Methode.  
  
```vb
Sub Cancel_OnClick  
   DC1.CancelUpdate  
End Sub  
```  
  
 Wenn `DC1.CancelUpdate` ausgeführt wird, werden alle Änderungen verworfen, die ein Benutzer seit der letzten Abfrage oder Aktualisierung an einem Mitarbeiterdaten Satz im Datenraster vorgenommen hat. Die ursprünglichen Werte werden wieder hergestellt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Adressbuch-Navigations Schaltflächen](./address-book-navigation-buttons.md)   
 [DataControl-Objekt (RDS)](../../reference/rds-api/datacontrol-object-rds.md)