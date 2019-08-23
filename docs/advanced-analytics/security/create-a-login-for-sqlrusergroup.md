---
title: Erstellen von Anmeldeinformationen für SQLRUserGroup
description: Erstellen Sie für Loopback Verbindungen mit implizierter Authentifizierung einen Anmelde Namen in SQL Server für sqlrusergroup, damit sich ein Workerkonto beim Server anmelden kann, um die Identitäts Konvertierung zurück in den aufrufenden Benutzer durchführen zu können.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/25/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: a5194f251b7ea47e0d9485446b8957e96037ded0
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/01/2019
ms.locfileid: "68714963"
---
# <a name="create-a-login-for-sqlrusergroup"></a>Erstellen von Anmeldeinformationen für SQLRUserGroup
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Erstellen Sie eine [Anmeldung in SQL Server](https://docs.microsoft.com/sql/relational-databases/security/authentication-access/create-a-login) für [sqlrusergroup](../concepts/security.md#sqlrusergroup) , wenn eine [Loopback Verbindung](../../advanced-analytics/concepts/security.md#implied-authentication) in Ihrem Skript eine *Vertrauenswürdige Verbindung*angibt und die Identität, die zum Ausführen eines Objekts verwendet wird, das Windows-Benutzerkonto ist.

Vertrauenswürdige Verbindungen sind `Trusted_Connection=True` die in der Verbindungs Zeichenfolge. Wenn SQL Server eine Anforderung empfängt, die eine vertrauenswürdige Verbindung angibt, wird überprüft, ob die Identität des aktuellen Windows-Benutzers über einen Anmelde Namen verfügt. Bei externen Prozessen, die als Workerkonto (z. b. MSSQLSERVER01 von **sqlrusergroup**) ausgeführt werden, schlägt die Anforderung fehl, da diese Konten nicht standardmäßig über einen Anmelde Namen verfügen.

Sie können den Verbindungsfehler umgehen, indem Sie einen Anmelde Namen für **sqlserverrusergroup**erstellen. Weitere Informationen zu Identitäten und externen Prozessen finden Sie unter [Übersicht über die Sicherheit für das Erweiterbarkeit Framework](../concepts/security.md).

> [!Note]
> Stellen Sie sicher, dass **sqlrusergroup** über die Berechtigung "Lokal anmelden zulassen" verfügt. Standardmäßig wird dieses Recht allen neuen lokalen Benutzern gewährt, aber einige Organisationen strengere Gruppenrichtlinien können dieses Recht deaktivieren.

## <a name="create-a-login"></a>Erstellen eines Anmeldenamens

1. Erweitern Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]im Objekt-Explorer den Knoten **Sicherheit**, klicken Sie mit der rechten Maustaste auf **Anmeldungen**, und wählen Sie anschließend **Neue Anmeldung**.

2. Klicken Sie im Dialogfeld **Anmeldung-neu** auf **Suchen**. (Geben Sie noch nichts in das Feld ein.)
    
     ![Klicken Sie zum Hinzufügen einer neuen Anmeldung für Machine Learning auf Suchen](media/implied-auth-login1.png "Klicken Sie zum Hinzufügen einer neuen Anmeldung für Machine Learning auf Suchen") .

3. Klicken Sie im Feld **Benutzer oder Gruppe auswählen** auf die Schaltfläche **Objekttypen** .

     ![Objekttypen durchsuchen, um einen neuen Anmelde Namen für Machine Learning hinzuzufügen](media/implied-auth-login2.png "Objekttypen durchsuchen, um einen neuen Anmelde Namen für Machine Learning hinzuzufügen")

4. Wählen Sie im Dialogfeld **Objekttypen** die Option **Gruppen**aus. Deaktivieren Sie alle anderen Kontrollkästchen.

     ![Dialogfeld "Gruppen in Objekttypen auswählen](media/implied-auth-login3.png "Dialogfeld \"Gruppen in Objekttypen auswählen") "

4. Klicken Sie auf **erweitert**, vergewissern Sie sich, dass der aktuelle Computer gesucht wird, und klicken Sie dann auf **jetzt**suchen.

     ![Klicken Sie auf Jetzt suchen, um die Liste der Gruppen](media/implied-auth-login4.png "Klicken Sie auf Jetzt suchen, um die Liste der Gruppen")

5. Führen Sie einen Bildlauf durch die Liste der Gruppenkonten auf dem Server durch, `SQLRUserGroup`bis Sie einen ab finden.
    
    + Der Name der Gruppe, die dem Launchpad-Dienst für die _Standard Instanz_ zugeordnet ist, lautet immer **sqlrusergroup**, unabhängig davon, ob Sie R oder python oder beides installiert haben. Wählen Sie dieses Konto nur für die Standard Instanz aus.
    + Wenn Sie eine _benannte Instanz_verwenden, wird der Instanzname an den Namen des standardmäßigen workergruppennamens `SQLRUserGroup`angehängt. Wenn Ihre Instanz z. b. den Namen "mltest" hat, lautet der Standardbenutzer Gruppenname für diese Instanz " **sqlrusergroupmltest**".
 
    ![Beispiel für Gruppen auf dem Server](media/implied-auth-login5.png "Beispiel für Gruppen auf dem Server")
   
5. Klicken Sie auf **OK** , um das Dialogfeld Erweiterte Suche zu schließen.

    > [!IMPORTANT]
    > Stellen Sie sicher, dass Sie das richtige Konto für die Instanz ausgewählt haben. Jede Instanz kann nur ihren eigenen Launchpad-Dienst und die für diesen Dienst erstellte Gruppe verwenden. Instanzen können keinen Launchpad-Dienst oder keine workerkonten freigeben.

6. Klicken Sie noch einmal auf **OK** , um das Dialogfeld **Benutzer oder Gruppe auswählen** zu schließen.

7. Klicken Sie im Dialogfeld **Anmeldung-neu** auf **OK**. In der Standardeinstellung ist die Anmeldung der **öffentlichen** Rolle zugewiesen und verfügt über die Berechtigung, eine Verbindung zur Datenbank-Engine herzustellen.

## <a name="next-steps"></a>Nächste Schritte

+ [Sicherheitsübersicht](../concepts/security.md)
+ [Erweiterbarkeits Framework](../concepts/extensibility-framework.md)
