---
title: Erstellen von Anmeldeinformationen für SQLRUserGroup
description: Erstellen Sie für Loopbackverbindungen mit implizierter Authentifizierung einen Anmeldeinformationen in SQL Server für SQLRUserGroup, damit sich ein Workerkonto zur Identitätskonvertierung zurück zum aufrufenden Benutzer beim Server anmelden kann.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/25/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: c57a62e954ae8cb0fc52c9a5ead22d418243c0b8
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/04/2020
ms.locfileid: "81117123"
---
# <a name="create-a-login-for-sqlrusergroup"></a>Erstellen von Anmeldeinformationen für SQLRUserGroup
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Erstellen Sie [Anmeldeinformationen in SQL Server](https://docs.microsoft.com/sql/relational-databases/security/authentication-access/create-a-login) für [SQLRUserGroup](../concepts/security.md#sqlrusergroup), wenn eine [Loopbackverbindung](../../machine-learning/concepts/security.md#implied-authentication) in Ihrem Skript eine *vertrauenswürdige Verbindung* angibt und die Identität, die zum Ausführen eines Objekts mit Ihrem Code verwendet wird, ein Windows-Benutzerkonto ist.

Bei vertrauenswürdigen Verbindungen ist in der Verbindungszeichenfolge `Trusted_Connection=True` enthalten. Wenn SQL Server eine Anforderung mit einer vertrauenswürdigen Verbindung empfängt, wird überprüft, ob die Identität des aktuellen Windows-Benutzers Anmeldeinformationen enthält. Bei externen Prozessen, die als Workerkonto ausgeführt werden (z. B. MSSQLSERVER01 aus **SQLRUserGroup**), schlägt die Anforderung fehl, da diese Konten standardmäßig keine Anmeldeinformationen enthalten.

Sie können den Verbindungsfehler umgehen, indem Sie für **SQLServerRUserGroup** Anmeldeinformationen erstellen. Weitere Informationen zu Identitäten und externen Prozessen finden Sie unter [Sicherheitsübersicht für das Erweiterbarkeitsframework](../concepts/security.md).

> [!Note]
> Stellen Sie sicher, dass **SQLRUserGroup** über die Berechtigung „Lokale Anmeldung zulassen“ verfügt. Diese Berechtigung wird standardmäßig allen neuen lokalen Benutzern gewährt. Sie kann jedoch durch die strengeren Gruppenrichtlinien einiger Organisationen deaktiviert werden.

## <a name="create-a-login"></a>Erstellen eines Anmeldenamens

1. Erweitern Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]im Objekt-Explorer den Knoten **Sicherheit**, klicken Sie mit der rechten Maustaste auf **Anmeldungen**, und wählen Sie anschließend **Neue Anmeldung**.

2. Wählen Sie im Dialogfeld **Anmeldung – Neu** die Option **Suchen** aus. (Geben Sie in das Feld noch nichts ein.)
    
     ![Klicken auf „Suchen“, um eine neue Anmeldung für das maschinelle Lernen hinzuzufügen](media/implied-auth-login1.png "Klicken auf „Suchen“, um eine neue Anmeldung für das maschinelle Lernen hinzuzufügen")

3. Klicken Sie im Feld **Benutzer oder Gruppe auswählen** auf die Schaltfläche **Objekttypen**.

     ![Suchen nach Objekttypen, um eine neue Anmeldung für das maschinelle Lernen hinzuzufügen](media/implied-auth-login2.png "Suchen nach Objekttypen, um eine neue Anmeldung für das maschinelle Lernen hinzuzufügen")

4. Wählen Sie im Dialogfeld **Objekttypen** die Option **Gruppen** aus. Deaktivieren Sie alle anderen Kontrollkästchen.

     ![Auswählen von Gruppen im Objekttypendialogfeld](media/implied-auth-login3.png "Auswählen von Gruppen im Objekttypendialogfeld")

4. Klicken Sie auf **Erweitert**. Vergewissern Sie sich, dass als der zu durchsuchende Speicherort der aktuelle Computer angezeigt wird, und klicken Sie auf **Suche starten**.

     ![Klicken auf „Suche starten“, um eine Liste von Gruppen abzurufen](media/implied-auth-login4.png "Klicken auf „Suche starten“, um eine Liste von Gruppen abzurufen")

5. Scrollen Sie durch die Liste der Gruppenkonten auf dem Server, bis Sie einen finden, der mit `SQLRUserGroup` beginnt.
    
    + Der Name der Gruppe, die dem Launchpad-Dienst für die _Standardinstanz_ zugeordnet ist, lautet immer **SQLRUserGroup**, ganz gleich, ob Sie R, Python oder beides installiert haben. Wählen Sie dieses Konto nur für die Standardinstanz aus.
    + Wenn Sie eine _benannte Instanz_ verwenden, wird der Instanzname an `SQLRUserGroup`, den Standardnamen der Workergruppe, angehängt. Wenn Ihre Instanz beispielsweise den Namen „MLTEST“ hat, lautet der Standardname der Benutzergruppe für diese Instanz **SQLRUserGroupMLTest**.
 
    ![Beispiel für Gruppen auf dem Server](media/implied-auth-login5.png "Beispiel für Gruppen auf dem Server")
   
5. Klicken Sie auf **OK**, um das Dialogfeld „Erweiterte Suche“ zu schließen.

    > [!IMPORTANT]
    > Vergewissern Sie sich, dass Sie das richtige Konto für die Instanz ausgewählt haben. Jede Instanz kann nur den eigenen Launchpad-Dienst und die für diesen Dienst erstellte Gruppe verwenden. Instanzen können Launchpad-Dienste oder Workerkonten nicht freigeben.

6. Klicken Sie erneut auf **OK**, um das Dialogfeld **Benutzer oder Gruppe auswählen** zu schließen.

7. Klicken Sie im Dialogfeld **Anmeldung - Neu** auf **OK**. In der Standardeinstellung ist die Anmeldung der **öffentlichen** Rolle zugewiesen und verfügt über die Berechtigung, eine Verbindung zur Datenbank-Engine herzustellen.

## <a name="next-steps"></a>Nächste Schritte

+ [Sicherheitsübersicht](../concepts/security.md)
+ [Erweiterbarkeitsframework](../concepts/extensibility-framework.md)
