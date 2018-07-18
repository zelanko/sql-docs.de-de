---
title: 'Aufgabe 1: Erstellen einer Wissensdatenbank und Domänen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 7d74a60b-8933-4038-bcbb-4e9dcc4f70e9
caps.latest.revision: 8
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 9114289ed2a4e09a5f7b59ed016c553c1d225dfc
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37226580"
---
# <a name="task-1-creating-a-knowledge-base-and-domains"></a>Aufgabe 1: Erstellen einer Wissensdatenbank und von Domänen
  In dieser Aufgabe erstellen Sie die **Lieferanten** Wissensdatenbank und Domänen, die für die Bereinigung und Abgleich von Daten verwendet wird, um Duplikate zu entfernen.  
  
1.  Starten Sie **Data Quality-Client**. Klicken Sie auf **starten**, zeigen Sie auf **Programme**, klicken Sie auf **Microsoft SQL Server 2012**, klicken Sie auf **Data Quality Services**, und klicken Sie dann auf  **Data Quality-Client**.  
  
2.  In der **Herstellen einer Verbindung mit Server** Dialogfeld wählen die Datenbank-Server-Instanz auf dem der DQS installiert ist, und klicken Sie auf **Connect**.  
  
     ![Herstellen einer Verbindung im Dialogfeld mit](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-01.jpg "im Dialogfeld mit Server verbinden")  
  
3.  In Data Quality-Client-Startseite im der **Wissensdatenbank-Verwaltung** Bereich, klicken Sie auf **neue Wissensdatenbank**.  
  
     ![Wissensdatenbank-Verwaltung – neu (KB)](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-02.jpg "Wissensdatenbank-Verwaltung – neu (KB)")  
  
4.  Geben Sie **Lieferanten** für **Namen** der Wissensdatenbank.  
  
     ![Neue Wissensdatenbank – Domänenverwaltung](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-03.jpg "neue Wissensdatenbank – Domänenverwaltung")  
  
5.  Überprüfen Sie, ob **Wissensdatenbank erstellen** Feld nastaven NA hodnotu **keine** seit Erstellung der **Lieferanten** Wissensdatenbank von Grund auf neu.  
  
6.  Überprüfen Sie, ob **Domänenverwaltung** ausgewählt ist, für die **Aktivität** , und klicken Sie auf **Weiter**. Mit der Domänenverwaltungsaktivität können Sie Domänen in der Wissensdatenbank erstellen und verwalten.  
  
7.  In der **Domänenverwaltung** Fenster, klicken Sie auf **erstellen Sie eine Domäne** Symbolleisten-Schaltfläche, um eine Domäne zu erstellen.  
  
     ![Erstellen Sie Domain Symbolleisten-Schaltfläche](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-04.jpg "Domain Symbolleisten-Schaltfläche erstellen")  
  
8.  In der **Domäne erstellen** (Dialogfeld), Typ **Supplier ID** für die **Domänennamen**, und klicken Sie auf **OK**.  
  
     ![Erstellen Sie im Dialogfeld Domäne](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-05.jpg "erstellen Domäne (Dialogfeld)")  
  
9. Wiederholen Sie den vorherigen Schritt, um folgenden Domänen mit allen Standardeinstellungen zu erstellen. Um das Tutorial einfach zu halten, Sie legen die **Datentyp** aller Domänen als **Zeichenfolge**. Die anderen zulässigen Datentypen sind: Ganze Zahl, Dezimalzahl und Datum. Wenn die **führende Werte** Option ist aktiviert (Standardeinstellung), die alle Synonyme durch den führenden Wert der synonymgruppe in der Ausgabe ersetzt werden. Festlegen von **Zeichenfolge normalisieren** Option (Standard) wird keine Sonderzeichen in den domänenwerten entfernt. Die **Formatausgabe** Option können Sie die Formatierung auswählen, die angewendet wird, wenn die Datenwerte in der Domäne ausgegeben werden. Wählen Sie **Rechtschreibprüfung aktivieren** (Standard), um die Rechtschreibprüfung beim Auffüllen der Domäne für alle Zeichenfolgenwerte auszuführen. Die **Sprache** Einstellung gibt an, welche Sprachversion des der **Rechtschreibprüfung** angewendet werden soll. Wählen Sie **Syntaxfehleralgorithmen deaktivieren** um die Domäne aufzufüllen, ohne die Zeichenfolgenwerte auf Syntaxfehler zu überprüfen. Finden Sie unter [erstellen Sie eine Domäne](http://msdn.microsoft.com/library/hh510401.aspx) in der MSDN Library Weitere Informationen.  
  
    -   Supplier Name  
  
    -   Contact Email  
  
    -   Adresszeile  
  
    -   Ort  
  
    -   Status  
  
    -   Country  
  
    -   PLZ  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 2: Manuelles Hinzufügen von Domänenwerten](../../2014/tutorials/task-2-adding-domain-values-manually.md)  
  
  
