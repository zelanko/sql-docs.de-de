---
title: 'Aufgabe 1: Erstellen einer Wissensdatenbank und von Domänen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 7d74a60b-8933-4038-bcbb-4e9dcc4f70e9
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 79edd8566f2b3c9b586bc8c8815e1d9bc586fb05
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "65481244"
---
# <a name="task-1-creating-a-knowledge-base-and-domains"></a>Aufgabe 1: Erstellen einer Wissensdatenbank und von Domänen
  In dieser Aufgabe erstellen Sie die Wissensdatenbank **Suppliers** und erstellen Domänen, die zum Bereinigen von Daten und zum Abgleichen von Daten verwendet werden, um Duplikate zu entfernen.  
  
1.  Starten Sie **Data Quality-Client**. Klicken Sie auf **Start**, zeigen Sie auf **Alle Programme**, klicken Sie auf **Microsoft SQL Server 2012**und dann auf **Data Quality Services**, und klicken Sie dann auf **Data Quality-Client**.  
  
2.  Wählen Sie im Dialogfeld **Verbindung mit Server herstellen** die Daten Bank Server Instanz aus, auf der DQS installiert ist, und klicken Sie auf **verbinden**.  
  
     ![Dialog Feld "Verbindung mit Server herstellen"](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-01.jpg "Verbindung mit Server herstellen (Dialogfeld)")  
  
3.  Klicken Sie auf der Startseite Data Quality-Client im Bereich **Wissensdatenbank-Verwaltung** auf **neue Wissensdatenbank**.  
  
     ![Wissensdatenbank-Verwaltung – Neu (KB)](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-02.jpg "Wissensdatenbank-Verwaltung – Neu (KB)")  
  
4.  Geben Sie **Suppliers** als **Name** der Wissensdatenbank ein.  
  
     ![Neue Wissensdatenbank – Domänenverwaltung](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-03.jpg "Neue Wissensdatenbank – Domänenverwaltung")  
  
5.  Vergewissern Sie sich, dass das Feld **Wissensdatenbank aus Feld erstellen** auf **keine** festgelegt ist, da Sie die Wissensdatenbank **Suppliers** von Grund auf neu erstellen.  
  
6.  Vergewissern Sie sich, dass für die **Aktivität** **Domänen Verwaltung** ausgewählt ist, und klicken Sie auf **weiter** Mit der Domänenverwaltungsaktivität können Sie Domänen in der Wissensdatenbank erstellen und verwalten.  
  
7.  Klicken Sie im Fenster **Domänen Verwaltung** auf **Domänen** Symbolleisten-Schaltfläche erstellen, um eine Domäne zu erstellen.  
  
     ![Domäne erstellen (Symbolleistenschaltfläche)](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-04.jpg "Domäne erstellen (Symbolleistenschaltfläche)")  
  
8.  Geben Sie im Dialogfeld **Domäne erstellen** den Namen **Lieferanten-ID** für den **Domänen Namen**ein, und klicken Sie auf **OK**.  
  
     ![Domäne erstellen (Dialogfeld)](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-05.jpg "Domäne erstellen (Dialogfeld)")  
  
9. Wiederholen Sie den vorherigen Schritt, um folgenden Domänen mit allen Standardeinstellungen zu erstellen. Um das Tutorial einfach zu halten, legen Sie den **Datentyp** aller Domänen als **Zeichenfolge**fest. Die anderen zulässigen Datentypen sind: Ganze Zahl, Dezimalzahl und Datum. Wenn die Option **führende Werte verwenden** ausgewählt ist (Standard), werden alle Synonyme durch den führenden Wert der Synonym Gruppe in der Ausgabe ersetzt. Durch Festlegen der Option " **normalize String** " (Standard) werden alle Sonderzeichen in den Domänen Werten entfernt. Mit der Option **Format Output to** können Sie die Formatierung auswählen, die angewendet wird, wenn die Datenwerte in der Domäne ausgegeben werden. Wählen Sie Rechtschreibprüfung **aktivieren** (Standard) aus, um die Rechtschreibprüfung beim Auffüllen der Domäne für alle Zeichen folgen Werte auszuführen. Die **sprach** Einstellung gibt die Sprachversion der Rechtschreibprüfung an, **die Sie anwenden** möchten. Aktivieren Sie **Syntax Fehler Algorithmen deaktivieren** , um die Domäne aufzufüllen, ohne die Zeichen folgen Werte auf Syntax Fehler zu überprüfen. Weitere Informationen finden Sie unter [Erstellen eines Domänen](https://msdn.microsoft.com/library/hh510401.aspx) Themas in der MSDN Library.  
  
    -   Supplier Name  
  
    -   Kontakt-E-Mail  
  
    -   Adresszeile  
  
    -   City  
  
    -   State  
  
    -   Country  
  
    -   Zip  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 2: Manuelles Hinzufügen von Domänenwerten](../../2014/tutorials/task-2-adding-domain-values-manually.md)  
  
  
