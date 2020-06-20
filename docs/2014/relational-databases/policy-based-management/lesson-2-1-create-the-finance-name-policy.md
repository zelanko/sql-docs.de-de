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
ms.openlocfilehash: 184865166da659ae00308eb1192e832989949da6
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85061628"
---
# <a name="create-the-finance-name-policy"></a>Erstellen der Richtlinie Finance Name
   In diesem Task erstellen Sie eine Datenbank mit dem Namen „Finanzen“. Anschließend erstellen Sie eine Bedingung, die vorschreibt, dass alle Tabellen mit den Buchstaben **fintbl** anfangen. Dann erstellen Sie eine Richtlinie und eine Richtlinienkategorie, um einen Namensstandard für Tabellen in der Datenbank Finanzen zu erzwingen.  
  
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
  
4.  Wählen Sie im Bereich **Ausdruck** im **Feld Feld** die Option ** \@ Name**aus, wählen Sie im Feld **Operator** die Option like aus, und geben Sie im Feld **Wert den Wert** **' fintbl anfangen% '** ein, um zu erzwingen, **dass**alle Tabellennamen mit den Buchstaben **fintbl anfangen**beginnen.  
  
5.  Geben Sie auf der Seite **Beschreibung** die Beschreibung **Finanz_Tabellen-Namen müssen mit fintbl beginnen**ein, und klicken Sie anschließend auf **OK** , um die Bedingung zu erstellen.  
  
### <a name="to-create-the-finance-name-policy"></a>So erstellen Sie die Richtlinie 'Finanz_Name'  
  
1.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf **Richtlinien**und anschließend auf **Neue Richtlinie**.  
  
2.  Geben Sie im Dialogfeld **Neue Richtlinie erstellen** im Feld **Name** den Namen **Finanz_Name**ein.  
  
3.  Wählen Sie in der Liste **Bedingung überprüfen** die Option **Finanz_Tabellen**aus. Diese befindet sich im Abschnitt **Mehrteiliger Name** .  
  
4.  Im Abschnitt **Für** wird eine Liste der Datenbankobjekte angezeigt, die diese Richtlinie anwenden könnten. Aktivieren Sie das Kontrollkästchen für **Jede Tabelle**.  
  
5.  Erweitern Sie im Abschnitt **Jede Datenbank** den Eintrag **Jede**, und klicken Sie anschließend auf **Neue Bedingung**.  
  
6.  Geben Sie im Dialogfeld **Neue Bedingung erstellen** im Feld **Name** den Namen **Finanz_Datenbank**ein.  
  
7.  Vervollständigen Sie im Feld **Ausdruck** den Ausdruck, um ** \@ Name = ' Finance '** einzuschließen, und klicken Sie dann auf **OK** , um die Seite Bedingung zu schließen.  
  
    > [!NOTE]  
    >  Sie müssen möglicherweise mit dem Cursor aus dem Feld **Wert** wechseln, um die Schaltfläche **OK** zu aktivieren.  
  
8.  Wählen Sie in der Liste **Auswertungsmodus** die Option **Bei Änderung: Verhindern**aus. Dadurch wird die Richtlinie erzwungen, indem ein Datenbanktrigger für die Datenbank Finanzen erstellt wird.  
  
9. Wählen Sie in der Liste **Aktiviert** aus. (Das Feld **Aktiviert** gilt nicht für **bedarfsgesteuerte** Richtlinien.)  
  
10. Wählen Sie in der Liste **Serverbeschränkung** die Option **Keine**aus.  
  
11. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-create-the-finance-policy-category"></a>So erstellen Sie die Richtlinienkategorie 'Finanzen'  
  
1.  Erweitern Sie im Objekt-Explorer **Verwaltung**, klicken Sie mit der rechten Maustaste auf **Richtlinienverwaltung**und anschließend auf **Kategorien verwalten**.  
  
2.  Geben Sie im Dialogfeld **Richtlinien Kategorien verwalten** unter **Name** `Finance` das leere Feld ein, und deaktivieren Sie dann **Daten Bank Abonnements beauftragen**. **Datenbankabonnements beauftragen** zwingt jede Datenbank in der Instanz, die zu dieser Richtlinienkategorie gehörenden Richtlinien zu abonnieren. Für diese Lektion darf nur die Datenbank Finanzen die Richtlinie Finanz_Name abonnieren.  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in der Lektion  
 [Abonnieren und Überprüfen der Richtlinie 'Finanz_Name'](lesson-2-2-subscribe-to-and-check-the-finance-name-policy.md)  
  
  
