---
title: 'Aufgabe 1: Erstellen einer Wissensdatenbank und Domänen | Microsoft Docs'
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
ms.topic: article
ms.assetid: 7d74a60b-8933-4038-bcbb-4e9dcc4f70e9
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: beec636f9137802c6651f0c08889acf73000b063
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36150226"
---
# <a name="task-1-creating-a-knowledge-base-and-domains"></a>Aufgabe 1: Erstellen einer Wissensdatenbank und von Domänen
  In dieser Aufgabe erstellen Sie die **Lieferanten** Wissensdatenbank und Domänen, die für die Bereinigung und Abgleich von Daten verwendet wird, um Duplikate zu entfernen.  
  
1.  Starten Sie **Data Quality-Client**. Klicken Sie auf **starten**, zeigen Sie auf **Programme**, klicken Sie auf **Microsoft SQL Server 2012**, klicken Sie auf **Data Quality Services**, und klicken Sie dann auf  **Data Quality-Client**.  
  
2.  In der **Verbindung mit Server herstellen** Dialogfeld wählen die Datenbankserverinstanz, auf dem der DQS installiert ist, und klicken Sie auf **verbinden**.  
  
     ![Herstellen einer Verbindung mit Server-Dialogfeld](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-01.jpg "Herstellen einer Verbindung mit Server (Dialogfeld)")  
  
3.  In Data Quality-Client-Startseite im die **Wissensdatenbank-Verwaltung** Bereich, klicken Sie auf **neue Wissensdatenbank**.  
  
     ![Wissensdatenbank-Verwaltung – neu (KB)](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-02.jpg "Wissensdatenbank-Verwaltung – neu (KB)")  
  
4.  Geben Sie **Lieferanten** für **Namen** der Wissensdatenbank.  
  
     ![Neue Wissensdatenbank – Domänenverwaltung](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-03.jpg "neue Wissensdatenbank – Domänenverwaltung")  
  
5.  Überprüfen Sie, ob **Wissensdatenbank erstellen** Feld **keine** seit Erstellung der **Lieferanten** Wissensdatenbank von Grund auf neu.  
  
6.  Überprüfen Sie, ob **Domänenverwaltung** ausgewählt ist, für die **Aktivität** , und klicken Sie auf **Weiter**. Mit der Domänenverwaltungsaktivität können Sie Domänen in der Wissensdatenbank erstellen und verwalten.  
  
7.  In der **Domänenverwaltung** Fenster, klicken Sie auf **erstellen Sie eine Domäne** Symbolleisten-Schaltfläche, um eine Domäne zu erstellen.  
  
     ![Erstellen von Symbolleisten-Schaltfläche Domäne](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-04.jpg "Domäne Symbolleisten-Schaltfläche \"erstellen\"")  
  
8.  In der **Domäne erstellen** Geben Sie im Dialogfeld **Supplier ID** für die **Domänennamen**, und klicken Sie auf **OK**.  
  
     ![Erstellen Sie im Dialogfeld Domäne](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-05.jpg "erstellen Domäne (Dialogfeld)")  
  
9. Wiederholen Sie den vorherigen Schritt, um folgenden Domänen mit allen Standardeinstellungen zu erstellen. Um das Lernprogramm einfach zu halten, legen Sie die **Datentyp** aller Domänen als **Zeichenfolge**. Die anderen zulässigen Datentypen sind: Ganze Zahl, Dezimalzahl und Datum. Wenn die **führende Werte** Option (Standard) ausgewählt ist, werden alle Synonyme durch den führenden Wert der synonymgruppe in der Ausgabe ersetzt. Festlegen von **Zeichenfolge normalisieren** Option (Standardeinstellung) keine Sonderzeichen in den domänenwerten entfernt. Die **Formatausgabe** Option können Sie auswählen, die Formatierung angewendet wird, wenn die Datenwerte in der Domäne ausgegeben werden. Wählen Sie **Rechtschreibprüfung aktivieren** (Standard), um die Rechtschreibprüfung beim Auffüllen der Domäne für alle Zeichenfolgenwerte auszuführen. Die **Sprache** Einstellung gibt an, welche Sprachversion der **Rechtschreibprüfung** anwenden möchten. Wählen Sie **Syntaxfehleralgorithmen deaktivieren** um die Domäne aufzufüllen, ohne die Zeichenfolgenwerte auf Syntaxfehler überprüft. Finden Sie unter [erstellen Sie eine Domäne](http://msdn.microsoft.com/library/hh510401.aspx) Thema in der MSDN Library für weitere Details.  
  
    -   Supplier Name  
  
    -   Contact Email  
  
    -   Adresszeile  
  
    -   Ort  
  
    -   Status  
  
    -   Country  
  
    -   PLZ  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 2: Manuelles Hinzufügen von Domänenwerten](../../2014/tutorials/task-2-adding-domain-values-manually.md)  
  
  