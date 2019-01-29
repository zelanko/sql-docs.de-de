---
title: Erstellen eines Anmeldenamens für SQLRUserGroup – SQL Server Machine Learning Services
description: Erstellen Sie für die Loopback-Verbindungen, die über die implizite Authentifizierung eine Anmeldung in SQL Server für SQLRUserGroup, sodass ein workerkonto an den Server für die identitätskonvertierung zurück an den aufrufenden Benutzer anmelden kann.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/25/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 62dd1ddf61c3cc2e1340619566ad9f4dcce062b7
ms.sourcegitcommit: 32a55df1275ad169bb1457243dc8caa8b48b206f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/28/2019
ms.locfileid: "55147041"
---
# <a name="create-a-login-for-sqlrusergroup"></a>Erstellen eines Anmeldenamens für SQLRUserGroup
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Erstellen einer [Anmeldung in SQL Server](https://docs.microsoft.com/sql/relational-databases/security/authentication-access/create-a-login) für [SQLRUserGroup](../concepts/security.md#sqlrusergroup) beim eine [Back Verbindung eine Schleife](../../advanced-analytics/concepts/security.md#implied-authentication) in Ihrem Skript gibt eine *vertrauenswürdige Verbindung*, und Ihr Code enthält, die Identität verwendet, um ein Objekt auszuführen ist ein Windows-Benutzerkonto.

Vertrauenswürdige Verbindungen sind diejenigen mit `Trusted_Connection=True` in der Verbindungszeichenfolge. Wenn SQL Server eine Anforderung, die das Angeben einer vertrauenswürdigen Verbindung empfängt, wird überprüft, ob die Identität des die aktuelle Windows-Benutzer eine Anmeldung vorhanden ist. Für externe Prozesse, die als ein workerkonto ausführen (z. B. MSSQLSERVER01 aus **SQLRUserGroup**), die Anforderung schlägt fehl, da diese Konten nicht über eine Anmeldung in der Standardeinstellung verfügen.

Sie können einen Verbindungsfehler umgehen, erstellen Sie eine Anmeldung für **SQLServerRUserGroup**. Weitere Informationen über Identitäten und externer Prozesse finden Sie unter [Sicherheit: Übersicht für das Extensibility Framework](../concepts/security.md).

> [!Note]
> Stellen Sie sicher, dass **SQLRUserGroup** "Lokal anmelden zulassen" berechtigt. Standardmäßig dieses Recht allen neuen lokalen Benutzern erteilt, aber einige strengeren Gruppenrichtlinien von Organisationen diese Berechtigung können deaktiviert werden.

## <a name="create-a-login"></a>Erstellen eines Anmeldenamens

1. Erweitern Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]im Objekt-Explorer den Knoten **Sicherheit**, klicken Sie mit der rechten Maustaste auf **Anmeldungen**, und wählen Sie anschließend **Neue Anmeldung**.

2. In der **Anmeldung – neu** wählen Sie im Dialogfeld **Suche**. (Geben Sie nichts in das Feld noch.)
    
     ![Klicken Sie auf Suchen, die zum Hinzufügen von neuen Anmeldenamen für Machine Learning](media/implied-auth-login1.png "klicken Sie auf Suchen, Hinzufügen von neuen Anmeldenamen für Machine Learning")

3. In der **Benutzer oder Gruppe auswählen** klicken Sie auf die **Objekttypen** Schaltfläche.

     ![Suchen Sie die Objekttypen, Hinzufügen von neuen Anmeldenamen für Machine Learning](media/implied-auth-login2.png "Suchen von Objekttypen, die neue Anmeldung für Machine Learning hinzufügen")

4. In der **Objekttypen** wählen Sie im Dialogfeld **Gruppen**. Deaktivieren Sie alle anderen Kontrollkästchen.

     ![Wählen Sie im Dialogfeld "Objekttypen" Gruppen](media/implied-auth-login3.png "Gruppen auswählen, im Dialogfeld \"Objekttypen\"")

4. Klicken Sie auf **erweitert**, stellen Sie sicher, dass zu suchenden Position der aktuellen Computer, und klicken Sie dann auf **Jetzt suchen**.

     ![Klicken Sie auf Jetzt suchen, um die Liste der Gruppen abzurufen](media/implied-auth-login4.png "klicken Sie auf Jetzt suchen zum Abrufen der Liste der Gruppen")

5. Scrollen Sie durch die Liste der Gruppenkonten auf dem Server, bis Sie beginnt mit gefunden `SQLRUserGroup`.
    
    + Der Name der Gruppe, die für den Launchpad-Dienst zugeordnet ist die _Standardinstanz_ ist immer **SQLRUserGroup**, unabhängig davon, ob Sie R, Python oder beides installiert. Wählen Sie dieses Konto für die Standardinstanz.
    + Bei Verwendung einer _benannte Instanz_, den Namen der Instanz wird auf den Namen des den Worker-Gruppe Standardnamen angefügt `SQLRUserGroup`. Z. B. wenn die Instanz "MLTEST" heißt, der Standardnamen für die Gruppe von Benutzer für diese Instanz wäre **SQLRUserGroupMLTest**.
 
    ![Beispiel für die Gruppen auf Server](media/implied-auth-login5.png "Beispiel für die Gruppen auf Server")
   
5. Klicken Sie auf **OK** um das Dialogfeld "Erweiterte Suche" zu schließen.

    > [!IMPORTANT]
    > Achten Sie darauf, dass Sie das richtige Konto für die Instanz ausgewählt haben. Jede Instanz kann nur einen eigenen Launchpad-Dienst und die Gruppe erstellt, die für diesen Dienst verwenden. Instanzen können kein Launchpad-Konten oder eine workerrolle verwenden.

6. Klicken Sie auf **OK** um schließen die **Benutzer oder Gruppe auswählen** Dialogfeld.

7. In der **Anmeldung – neu** Dialogfeld klicken Sie auf **OK**. In der Standardeinstellung ist die Anmeldung der **öffentlichen** Rolle zugewiesen und verfügt über die Berechtigung, eine Verbindung zur Datenbank-Engine herzustellen.

## <a name="next-steps"></a>Nächste Schritte

+ [Sicherheitsübersicht](../concepts/security.md)
+ [Erweiterungsframework](../concepts/extensibility-framework.md)
