---
title: Hinzufügen der SQLRUserGroup als Datenbankbenutzer (SQL Server-Machine Learning) | Microsoft-Dokumentation
description: Informationen zum Hinzufügen der SQLRUserGroup als Datenbankbenutzer für SQL Server-Machine Learning-Dienste.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/10/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: fc5294453def64d13cc43a74a8a5fb299c3e23e3
ms.sourcegitcommit: 485e4e05d88813d2a8bb8e7296dbd721d125f940
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/11/2018
ms.locfileid: "49100321"
---
# <a name="add-sqlrusergroup-as-a-database-user"></a>Hinzufügen von SQLRUserGroup als Datenbankbenutzer
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Erstellen eines datenbankanmeldenamens für das [SQLRUserGroup](../concepts/security.md#sqlrusergroup) um vertrauenswürdige Verbindungen über R und Python-Skripts, stammen, wenn das Ziel, Daten oder Vorgänge für SQL Server-Instanz ist zu ermöglichen. 

Für Skripts, die Verbindungszeichenfolgen mit SQL Server-Anmeldungen oder einen vollständig angegebenen Benutzernamen und ein Kennwort enthält ist das Erstellen einer Anmeldung nicht erforderlich.

## <a name="when-a-login-is-required"></a>Wenn eine Anmeldung erforderlich ist.

Wenn R oder Python-Skript eine Verbindungszeichenfolge, die eine vertrauenswürdige Verbindung angeben enthält (z. B. "Trusted_Connection = True"), ist zusätzliche Konfiguration für die richtige Darstellung der Identität des Benutzers mit SQL Server erforderlich. Für externe Prozesse, die unter einem **SQLRUserGroup** workerkonto, z. B. MSSQLSERVER01, den vertrauenswürdigen Benutzer als die Worker-Identität dargestellt wird. Da diese Identität kein Anmelderechte für SQL Server verfügt, vertrauenswürdige Verbindungen schlagen fehl, es sei denn, Sie fügen **SQLRUserGroup** als Datenbankbenutzer. Weitere Informationen finden Sie unter [ *implizite Authentifizierung*](../../advanced-analytics/concepts/security.md#implied-authentication).

Denken Sie daran, dass Launchpad eine Zuordnung des ursprünglichen Benutzers beibehalten, die das Skript und das workerkonto Ausführen des Prozesses aufgerufen. Wenn die vertrauenswürdige Verbindung für das workerkonto erfolgreich war, wird die Identität des ursprünglichen aufrufenden Benutzers übernimmt und wird verwendet, um die Daten abzurufen. Sie müssen nicht gewähren der Db_datareader-Berechtigungen für **SQLRUserGroup**.

> [!Note]
>  Stellen Sie sicher, dass **SQLRUserGroup** "Lokal anmelden zulassen" berechtigt. Klicken Sie in der Standardeinstellung dieses Recht allen neuen lokalen Benutzern erteilt, aber in einigen Organisationen möglicherweise strengere Gruppenrichtlinien erzwungen werden.

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
    + Bei Verwendung einer _benannte Instanz_, den Namen der Instanz wird auf den Namen des den Worker-Gruppe Standardnamen angefügt `SQLRUserGroup`. Daher, wenn die Instanz "MLTEST" heißt, der Standardnamen für die Gruppe von Benutzer für diese Instanz wäre **SQLRUserGroupMLTest**.
 
     ![Beispiel für die Gruppen auf Server](media/implied-auth-login5.png "Beispiel für die Gruppen auf Server")
   
5. Klicken Sie auf **OK** um das Dialogfeld "Erweiterte Suche" zu schließen.

    > [!IMPORTANT]
    > Achten Sie darauf, dass Sie das richtige Konto für die Instanz ausgewählt haben. Jede Instanz kann nur einen eigenen Launchpad-Dienst und die Gruppe erstellt, die für diesen Dienst verwenden. Instanzen können kein Launchpad-Konten oder eine workerrolle verwenden.

6. Klicken Sie auf **OK** um schließen die **Benutzer oder Gruppe auswählen** Dialogfeld.

7. In der **Anmeldung – neu** Dialogfeld klicken Sie auf **OK**. In der Standardeinstellung ist die Anmeldung der **öffentlichen** Rolle zugewiesen und verfügt über die Berechtigung, eine Verbindung zur Datenbank-Engine herzustellen.