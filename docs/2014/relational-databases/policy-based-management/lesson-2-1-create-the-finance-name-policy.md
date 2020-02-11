---
title: Erstellen der Richtlinie „Finance Name“ | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 56b2c852-fd69-4cd2-9b5d-977467b94fd9
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: a4484f9ccb76ea31c95a5392570e18df2c4b0ff5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67792911"
---
# <a name="create-the-finance-name-policy"></a>Erstellen der Richtlinie Finance Name
  In dieser Aufgabe erstellen Sie eine Datenbank mit dem Namen Finance und erstellen dann eine Bedingung, die erfordert, dass alle Tabellen mit den Buchstaben **fintbl anfangen**beginnen. Dann erstellen Sie eine Richtlinie und eine Richtlinienkategorie, um einen Namensstandard für Tabellen in der Datenbank Finanzen zu erzwingen.  
  
### <a name="to-create-the-finance-database"></a>So erstellen Sie die Datenbank "Finance"  
  
1.  Öffnen Sie ein Abfragefenster in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], und führen Sie die folgende Anweisung aus:  
  
    ```  
    CREATE DATABASE Finance ;  
    GO  
    ```  
  
2.  Klicken Sie im Objekt-Explorer auf **Datenbanken**, und drücken Sie anschließend F5, um die Liste der Datenbanken zu aktualisieren.  
  
### <a name="to-create-the-finance-tables-condition"></a>So erstellen Sie die Bedingung 'Finanz_Tabellen'  
  
1.  Erweitern Sie im Objekt-Explorer **Verwaltung**, erweitern Sie **Richtlinienverwaltung**, klicken Sie mit der rechten Maustaste auf **Bedingungen**und anschließend auf **Neue Bedingung**.  
  
2.  Geben Sie im Dialogfeld **Neue Bedingung erstellen** im Feld **Name** den Namen **Finanz_Tabellen**ein.  
  
3.  Wählen Sie in der Liste **Facet** die Option **Mehrteiliger Name**aus.  
  
4.  Wählen Sie **** ** \@** im Bereich Ausdruck im **Feld Feld** die Option Name aus. Wählen Sie im Feld **Operator** die Option **like**aus. Geben Sie im Feld **Wert** den Wert **' fintbl anfangen% '** ein, um zu erzwingen, dass alle Tabellennamen mit den Buchstaben **fintbl anfangen**beginnen.  
  
5.  Geben Sie auf der Seite **Beschreibung** die Beschreibung **Finanz_Tabellen-Namen müssen mit fintbl beginnen**ein, und klicken Sie anschließend auf **OK** , um die Bedingung zu erstellen.  
  
### <a name="to-create-the-finance-name-policy"></a>So erstellen Sie die Richtlinie 'Finanz_Name'  
  
1.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf **Richtlinien**und anschließend auf **Neue Richtlinie**.  
  
2.  Geben Sie im Dialogfeld **Neue Richtlinie erstellen** im Feld **Name** den Namen **Finanz_Name**ein.  
  
3.  Wählen Sie in der Liste **Bedingung überprüfen** die Option **Finanz_Tabellen**aus. Diese befindet sich im Abschnitt **Mehrteiliger Name** .  
  
4.  Im Abschnitt **Für** wird eine Liste der Datenbankobjekte angezeigt, die diese Richtlinie anwenden könnten. Aktivieren Sie das Kontrollkästchen für **Jede Tabelle**.  
  
5.  Erweitern Sie im Abschnitt **Jede Datenbank** den Eintrag **Jede**, und klicken Sie anschließend auf **Neue Bedingung**.  
  
6.  Geben Sie im Dialogfeld **Neue Bedingung erstellen** im Feld **Name** den Namen **Finanz_Datenbank**ein.  
  
7.  Vervollständigen Sie im Feld **Ausdruck** den Ausdruck, um ** \@Name = ' Finance '** einzuschließen, und klicken Sie dann auf **OK** , um die Seite Bedingung zu schließen.  
  
    > [!NOTE]  
    >  Sie müssen möglicherweise mit dem Cursor aus dem Feld **Wert** wechseln, um die Schaltfläche **OK** zu aktivieren.  
  
8.  Wählen Sie in der Liste **Auswertungsmodus** die Option **Bei Änderung: Verhindern**aus. Dadurch wird die Richtlinie erzwungen, indem ein Datenbanktrigger für die Datenbank Finanzen erstellt wird.  
  
9. Wählen Sie in der Liste **Aktiviert** aus. (Das Feld **Aktiviert** gilt nicht für **bedarfsgesteuerte** Richtlinien.)  
  
10. Wählen Sie in der Liste **Serverbeschränkung** die Option **Keine**aus.  
  
11. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-create-the-finance-policy-category"></a>So erstellen Sie die Richtlinienkategorie 'Finanzen'  
  
1.  Erweitern Sie im Objekt-Explorer **Verwaltung**, klicken Sie mit der rechten Maustaste auf **Richtlinienverwaltung**und anschließend auf **Kategorien verwalten**.  
  
2.  Geben `Finance` Sie im Dialogfeld **Richtlinien Kategorien verwalten** unter **Name**das leere Feld ein, und deaktivieren Sie dann **Daten Bank Abonnements beauftragen**. Durch das **beauftragen von Daten Bank Abonnements** wird erzwungen, dass jede Datenbank in der Instanz die Richtlinien abonniert, die zu dieser Richtlinien Kategorie gehören. Für diese Lektion darf nur die Datenbank Finanzen die Richtlinie Finanz_Name abonnieren.  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in der Lektion  
 [Abonnieren und Überprüfen der Richtlinie 'Finanz_Name'](lesson-2-2-subscribe-to-and-check-the-finance-name-policy.md)  
  
  
