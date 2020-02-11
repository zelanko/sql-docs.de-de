---
title: Konfigurieren gespeicherter Anmelde Informationen für die Power Pivot-Datenaktualisierung (PowerPivot für SharePoint) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 987eff0f-bcfe-4bbd-81e0-9aca993a2a75
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 23f35c8998b204182f25f85f8f7694fb60d042b4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66087456"
---
# <a name="configure-stored-credentials-for-powerpivot-data-refresh-powerpivot-for-sharepoint"></a>Konfigurieren gespeicherter Anmeldeinformationen für die PowerPivot-Datenaktualisierung (PowerPivot für SharePoint)
  PowerPivot-Datenaktualisierungsaufträge können mit jedem Windows-Benutzerkonto ausgeführt werden, sofern Sie eine Zielanwendung in Secure Store Service erstellen, um die Anmeldeinformationen zu speichern, die Sie verwenden möchten. Auf dieselbe Weise können Sie die Anmeldeinformationen einer Secure Store Service-Zielanwendung zuordnen und die Zielanwendung in einem Datenaktualisierungszeitplan angeben, wenn Sie eine andere Datenbankanmeldung als die zum Importieren der Daten in PowerPivot für Excel verwendete bereitstellen möchten.  
  
 **[!INCLUDE[applies](../includes/applies-md.md)]** SharePoint 2010  
  
 Nachdem Sie die Anweisungen in diesem Thema befolgt haben, können Sie die folgende Anmeldeinformationsoption auf der Seite mit dem PowerPivot-Datenaktualisierungszeitplan verwenden:  
  
 ![SSAS_PowerPivotDataRefreshCreds_Stored](media/ssas-powerpivotdatarefreshcreds-stored.gif "SSAS_PowerPivotDataRefreshCreds_Stored")  
  
 In diesem Thema wird erläutert, wie die Benutzernamen und Kennwörter für PowerPivot-Datenaktualisierung in einer SharePoint 2010-Farm eingerichtet werden. Bevor Sie diese Schritte verwenden können, müssen Sie Secure Store Service aktivieren und einen Hauptschlüssel generieren. Weitere Informationen finden Sie unter [Power Pivot-Datenaktualisierung mit SharePoint 2010](powerpivot-data-refresh-with-sharepoint-2010.md) .  
  
 Dieses Thema enthält folgende Abschnitte:  
  
 [Konfigurieren eines beliebigen Windows-Kontos für die Datenaktualisierung](#configAny)  
  
 [Konfigurieren eines vordefinierten Kontos für den Zugriff auf externe Datenquellen oder Datenquellen von Drittanbietern](#config3rd)  
  
 Wenn beim Konfigurieren oder verwenden der Datenaktualisierung Probleme auftreten, finden Sie im TechNet wiki auf der Seite Problembehandlung bei der [Power Pivot-Datenaktualisierung](https://go.microsoft.com/fwlink/?LinkID=223279) Informationen zu möglichen Lösungen.  
  
##  <a name="configAny"></a>Konfigurieren eines Windows-Kontos für die Datenaktualisierung  
 Wenn ein SharePoint-Benutzer einen Datenaktualisierungszeitplan definiert, muss die Benutzeridentität angegeben werden, unter der die Datenaktualisierung durchgeführt wird. Zu den Optionen gehören das Eingeben des Windows-Domänenbenutzerkontos, das Auswählen des unbeaufsichtigten Datenaktualisierungskontos für PowerPivot oder das Eingeben eines anderen Windows-Benutzerkontos für Datenaktualisierungszwecke. Die Schritte in diesem Abschnitt sind für die letzte Option: Angeben eines anderen Windows-Kontos.  
  
 Sie können diesen Ansatz wählen, wenn Sie eine Alternative zum Konto für unbeaufsichtigte PowerPivot-Datenaktualisierungen (verfügbar für alle PowerPivot-Benutzer auf SharePoint) oder der Anmeldeinformationen des Arbeitsmappenbesitzers verwenden möchten. Sie möchten z. B. anderen Arbeitsgruppen eine Reihe von Datenaktualisierungskonten verfügbar machen, um die Protokollierung und Verwaltung von Datenaktualisierungsaktivität auf organisatorischer Ebene zu vereinfachen.  
  
> [!IMPORTANT]  
>  Personen und Anwendungen, die diese Zielanwendung verwenden (und die Anmeldeinformationen, die sie speichert), müssen als Elemente der Anwendung aufgeführt sein. Sie müssen die Identität jeder PowerPivot-Dienstanwendung hinzufügen, die die Zielanwendung, Ihr Windows-Konto und die Gruppe oder die Benutzerkonten von Personen verwendet, die diese Zielanwendung in ihren Datenaktualisierungzeitplänen angeben werden. Sie können bei der Erstellung der Zielanwendung alle Konten angeben. Wenn Sie nicht alle Benutzer- und Gruppenkonten kennen, die Zugriff auf diese Anwendung erfordern, können Sie sie später hinzufügen, nachdem die Zielanwendung erstellt wurde.  
  
 Das Konfigurieren der gespeicherten Anmeldeinformationen für die Datenaktualisierung umfasst vier Schritte:  
  
-   Erstellen der Zielanwendung, in der die Anmeldeinformationen gespeichert werden  
  
-   Erteilen Sie dem Konto Teilnahmeberechtigungen.  
  
-   Erteilen Sie dem Konto Leseberechtigungen, um während der Datenaktualisierung auf externe Datenquellen zuzugreifen.  
  
-   Überprüfen Sie, ob die Datenaktualisierung funktioniert, wenn diese Zielanwendung in einem Datenaktualisierungszeitplan angegeben wird.  
  
### <a name="step-1-create-a-target-application"></a>Schritt 1: Erstellen einer Zielanwendung  
  
1.  Klicken Sie in der zentral Administration unter Anwendungs Verwaltung auf **Dienst Anwendungen verwalten**.  
  
2.  Klicken Sie auf **einmaliges Anmelden**.  
  
3.  Klicken Sie unter Zielanwendungen verwalten auf **neu**.  
  
4.  Geben Sie unter "Zielanwendungs-ID" eine Textzeichenfolge ein. Die Zeichenfolge muss eindeutig aber ebenfalls leicht einzuprägen sein. Benutzer geben diese Zeichenfolge auf Planungsseiten für die Datenaktualisierung an, wenn sie die in dieser Anwendung gespeicherten Anmeldeinformationen verwenden möchten.  
  
5.  Geben Sie unter Anzeigename einen aussagekräftigen Namen ein. Dieser Name wird nur zu Anzeigezwecken verwendet. Er wird nicht verwendet, um die Zielanwendung in einem Datenaktualisierungsplan anzugeben.  
  
6.  Geben Sie unter E-Mail des Kontakts Ihre E-Mail-Adresse ein.  
  
7.  Wählen Sie unter Ziel Anwendungstyp die Option **Gruppe**aus.  
  
    > [!IMPORTANT]  
    >  Der Kontotyp Gruppe muss ausgewählt werden, damit alle Benutzer- und Dienstkonten angegeben werden können, die Zugriff auf die Anmeldeinformationen erfordern. Bei jeder Anforderung überprüft der PowerPivot-Systemdienst, ob der Anforderer ein Element der Zielanwendung ist.  
  
8.  Überspringen Sie die Zielanwendungsseiten-URL. Von der PowerPivot-Datenaktualisierung wird dies nicht verwendet.  
  
9. Klicken Sie auf **Weiter**.  
  
10. Übernehmen Sie auf der Seite **Anmelde Informationen für die Secure Store-Zielanwendung angeben** die Standardwerte. Feldnamen und-Typen sollten Windows-Benutzer Name und Windows-Kennwort sein.  
  
11. Klicken Sie auf Weiter.  
  
12. Geben Sie unter Administratoren der Zielanwendung die Windows-Domänenbenutzerkonten der SharePoint-Benutzer ein, die über Administratorzugriff auf die Zielanwendungseinstellungen verfügen sollen (um beispielsweise der Mitgliederliste Konten hinzuzufügen oder Konten aus der Liste zu entfernen).  
  
13. Fügen Sie unter "Elemente" die folgenden Benutzer- und Gruppenkonten hinzu:  
  
    1.  Fügen Sie als die Person, die die Anwendung erstellt, Ihr Windows-Benutzerkonto der Elementenliste hinzu.  
  
    2.  Fügen Sie die Anwendungspoolidentität der PowerPivot-Dienstanwendung hinzu, damit bei geplanter Datenaktualisierung die Anmeldeinformationen abgerufen werden können. Um die Anwendungs Pool Identität anzuzeigen, wechseln Sie zu **Dienst Anwendungen verwalten**, wählen Sie die Power Pivot-Dienst Anwendung aus, indem Sie auf den leeren Bereich neben dem Namen klicken (Hierdurch wird die Zeile ausgewählt), und klicken Sie dann auf **Eigenschaften**. Das Sicherheitskonto, das auf dieser Seite angezeigt wird, ist das Konto, das der Zielanwendung als Element hinzugefügt werden soll.  
  
    3.  Fügen Sie Windows-Benutzer- und Gruppenkonten hinzu, die diese Zielanwendung in Datenaktualisierungszeitplänen eingeben.  
  
14. Klicken Sie auf **OK**.  
  
15. Wählen Sie die soeben erstellte Zielanwendung aus, klicken Sie auf den Pfeil nach unten, und wählen Sie **Anmelde Informationen festlegen.**  
  
16. Beachten Sie, dass die Liste der Besitzer der Anmeldeinformationen unter Besitzer der Anmeldeinformationen schreibgeschützt ist. Die Konten, die im Besitz der Anmeldeinformationen sind, sind Elemente der Zielanwendung. Zum Hinzufügen oder Entfernen eines Anmeldeinformationsbesitzers müssen Sie der Elementliste der Zielanwendung Konten hinzufügen oder Konten aus der Liste entfernen.  
  
     Geben Sie in Windows-Benutzername und Windows-Kennwort die Anmeldeinformationen des Windows-Benutzerkontos ein, das zum Ausführen der Datenaktualisierung verwendet wird.  
  
17. Klicken Sie auf **OK**.  
  
###  <a name="bkmk_grant"></a>Schritt 2: Erteilen von Teilnahme Berechtigungen für das Konto  
 Bevor die gespeicherten Anmeldeinformationen verwendet werden können, müssen allen PowerPivot-Arbeitsmappen, für die sie verwendet werden sollen, Teilnahmeberechtigungen zugewiesen werden. Die Berechtigungsebene ist erforderlich, um die Arbeitsmappe von einer Bibliothek zu öffnen und anschließend nach der Aktualisierung der Daten erneut in der Bibliothek zu speichern.  
  
 Das Zuweisen von Berechtigungen ist ein Schritt, der vom Websitesammlungsadministrator durchgeführt werden muss. SharePoint-Berechtigungen können an der Stammwebsitesammlung oder einer beliebigen darunterliegenden Ebene zugewiesen werden, einschließlich individueller Dokumente und Elemente. Die Art der Festlegung von Berechtigungen variiert je nach erforderlichem Genauigkeitsgrad. Die folgenden Schritte stellen eine Art der Erteilung von Berechtigungen dar.  
  
1.  Klicken Sie auf einer SharePoint-Website unter Website Aktionen auf **Website Berechtigungen**.  
  
2.  Klicken Sie auf **Berechtigungen erteilen**.  
  
3.  Geben Sie im Bereich für die Benutzerauswahl den Namen des Windows-Domänenbenutzerkontos ein, das Sie in der Zielanwendung angegeben haben.  
  
4.  Wählen Sie unter Berechtigungen erteilen die Option **Benutzern die Berechtigung direkt erteilen**aus.  
  
5.  Wählen Sie **mitwirken**aus, und klicken Sie dann auf **OK**.  
  
###  <a name="bkmk_dbread"></a>Schritt 3: Erteilen von Leseberechtigungen für den Zugriff auf externe Datenquellen, die bei der Datenaktualisierung verwendet werden  
 Wenn sie Daten in eine PowerPivot-Arbeitsmappe importieren, basieren Verbindungen zu externen Daten häufig auf vertrauenswürdigen oder personifizierten Verbindungen, die die Identität des aktuellen Benutzers verwenden, um eine Verbindung mit der Datenquelle herzustellen. Diese Typen von Verbindungen funktionieren nur, wenn der aktuelle Benutzer über die Berechtigung verfügt, die Daten zu lesen, die er importiert.  
  
 In einem Datenaktualisierungsszenario wird die gleiche Verbindungszeichenfolge, die zum Importieren von Daten verwendet wurde, jetzt erneut verwendet, um die Daten zu aktualisieren. Wenn die Verbindungszeichenfolge den aktuellen Benutzer voraussetzt (z. B. eine Zeichenfolge, die Integrated_Security=SSPI einschließt), dann übergibt der PowerPivot-Systemdienst die in der Zielanwendung angegebene Benutzeridentität als den aktuellen Benutzer. Diese Verbindung ist nur erfolgreich, wenn das Konto über Leseberechtigungen für die externe Datenquelle verfügt.  
  
 Daher müssen Sie dem Konto Leseberechtigungen für alle externen Datenquellen erteilen, die bei der Datenaktualisierung verwendet werden.  
  
 Wenn Sie Administrator für die in der Organisation verwendeten Datenquellen sind, können Sie eine Anmeldung erstellen und die erforderlichen Berechtigungen zuweisen. Andernfalls müssen Sie sich an die Besitzer der Daten wenden und die Kontoinformationen angeben. Sie müssen das Windows-Domänenbenutzerkonto angeben, das der Zielanwendung zugeordnet wird. Dies ist das Konto, das Sie in "Schritt 1: Erstellen einer Zielanwendung" in diesem Thema angegeben haben.  
  
###  <a name="bkmk_verify"></a>Schritt 4: Überprüfen der Konto Verfügbarkeit in den Daten Aktualisierungs Konfigurationsseiten  
  
1.  Öffnen Sie die Seite zum Konfigurieren der Datenaktualisierung für eine veröffentlichte Arbeitsmappe, die PowerPivot-Daten enthält. Anweisungen zum Öffnen der Seite finden Sie unter [Planen einer Datenaktualisierung &#40;PowerPivot für SharePoint&#41;](schedule-a-data-refresh-powerpivot-for-sharepoint.md).  
  
2.  Vergewissern Sie sich, dass die Option **mithilfe der in einmaliges Anmelden (SSS) gespeicherten Anmelde Informationen für die Anmeldung bei der Datenquelle verbinden** auf der Seite Daten Aktualisierungs Konfiguration aktiviert ist, und geben Sie dann den Namen der Zielanwendung ein.  
  
3.  Aktivieren Sie das Kontrollkästchen **auch so bald wie möglich aktualisieren** , und klicken Sie dann auf **OK**.  
  
4.  Wählen Sie in der Bibliothek, die die Arbeitsmappe enthält, die Arbeitsmappe aus, klicken Sie auf den rechts angezeigten Pfeil nach unten, und wählen Sie dann **Power Pivot-Datenaktualisierung verwalten**aus. Möglicherweise müssen Sie einige Minuten warten, wenn der Datenaktualisierungsauftrag eine große Datenmenge zurückgibt.  
  
 Wenn ein Fehler auftritt, können Sie auf der Seite Daten Aktualisierungs Verlauf auf **Zeitplan konfigurieren** klicken, um andere Anmelde Informationen zu verwenden. Sie müssen ggf. auch die Anmeldeinformationen der Datenquelle in der ursprünglichen Arbeitsmappe prüfen, um die Verbindungszeichenfolge anzuzeigen, die bei der Datenaktualisierung verwendet wird. Die Verbindungszeichenfolge enthält Informationen zum Serverstandort und der Datenbank, die Sie zur Problembehandlung verwenden können.  
  
 Weitere Informationen zur Problembehandlung finden Sie unter Problembehandlung bei der [Power Pivot-Datenaktualisierung](https://go.microsoft.com/fwlink/p/?LinkID=223279) im TechNet-wiki.  
  
##  <a name="config3rd"></a>Konfigurieren eines vordefinierten Kontos für den Zugriff auf externe Datenquellen oder Datenquellen von Drittanbietern  
 Datenbankserver werden oft mit eigenen Authentifizierungsmethoden ausgeliefert. Wenn Sie über eine PowerPivot-Arbeitsmappe verfügen, die für den Zugriff auf eine externe Datenquelle während der Datenaktualisierung Datenbank-Anmeldeinformationen erfordert, können Sie eine Zielanwendungs-ID für die Anmeldeinformationen erstellen und dieser Zielanwendung dann Datenbank-Anmeldeinformationen zuordnen.   
  
 Dieser Schritt ist nur notwendig, wenn Sie Benutzer mit einer Option zur Überschreibung der Datenbank-Anmeldeinformationen, die bereits in die Arbeitsmappe PowerPivot eingebettet sind, versehen möchten.  
  
 Dieser Schritt funktioniert nur, wenn die Verbindungszeichenfolge bereits einen Benutzernamen und ein Kennwort enthält. Beachten Sie, dass die Verbindungszeichenfolge relativ selten Anmeldeinformationen enthält. Daher ist die Verwendung dieser Option eingeschränkt. In den meisten Fällen enthält die Verbindungszeichenfolge nur eine Benutzer-ID und ein Kennwort, wenn eine Datenbankauthentifizierung zum Verbinden mit der Datenquelle verwendet wird. Weitere Informationen zum Überprüfen der Verbindungs Zeichenfolge, um festzustellen, ob Sie eine Benutzer-ID und ein Kennwort enthält, finden Sie im Abschnitt "erteilen von Berechtigungen zum Erstellen von Zeitplänen und Zugreifen auf externe Daten" in [Power Pivot-Datenaktualisierung mit SharePoint 2010](powerpivot-data-refresh-with-sharepoint-2010.md).  
  
1.  Klicken Sie in der zentral Administration unter Anwendungs Verwaltung auf **Dienst Anwendungen verwalten**.  
  
2.  Klicken Sie auf **einmaliges Anmelden**.  
  
3.  Klicken Sie unter Zielanwendungen verwalten auf **neu**.  
  
4.  Geben Sie unter "Zielanwendungs-ID" eine Textzeichenfolge ein. Die Zeichenfolge muss eindeutig aber ebenfalls leicht einzuprägen sein. Benutzer geben diese Zeichenfolge auf Planungsseiten für die Datenaktualisierung an, wenn sie die in dieser Anwendung gespeicherten Anmeldeinformationen verwenden möchten.  
  
5.  Geben Sie unter Anzeigename einen aussagekräftigen Namen ein. Dieser Name wird nur zu Anzeigezwecken verwendet. Er wird nicht verwendet, um die Zielanwendung in einem Datenaktualisierungsplan anzugeben.  
  
6.  Geben Sie unter E-Mail des Kontakts Ihre E-Mail-Adresse ein.  
  
7.  Wählen Sie unter Ziel Anwendungstyp die Option **Gruppe**aus.  
  
8.  Überspringen Sie die Zielanwendungsseiten-URL. Von der PowerPivot-Datenaktualisierung wird dies nicht verwendet.  
  
9. Klicken Sie auf **Weiter**.  
  
10. Akzeptieren Sie die Standardwerte in den **Feldern Anmelde Informationen für die Zielanwendung für** einmaliges Anmelden angeben nur dann, wenn die Datenquelle die Windows-Authentifizierung verwendet. Wählen Sie andernfalls die Feldtypen für die Datenquelle aus, und bearbeiten Sie dann die Feldnamen dem Typ entsprechend.  
  
     Sie können beispielsweise den SQL Server-Benutzernamen und das SQL Server-Benutzerkennwort für Feldnamen angeben und dann Benutzername und Kennwort für die Feldtypen verwenden.  
  
11. Klicken Sie auf Weiter.  
  
12. Geben Sie unter Administratoren der Zielanwendung die Windows-Domänenbenutzerkonten der SharePoint-Benutzer ein, die über Administratorzugriff auf die Anwendungseinstellungen verfügen sollen.  
  
13. Fügen Sie unter "Elemente" die folgenden Benutzer- und Gruppenkonten hinzu:  
  
    1.  Fügen Sie als die Person, die die Anwendung erstellt, Ihr Windows-Benutzerkonto der Elementenliste hinzu.  
  
    2.  Fügen Sie die Anwendungspoolidentität jeder PowerPivot-Dienstanwendung hinzu, die die Zielanwendung verwendet, um auf ihre gespeicherten Anmeldeinformationen zuzugreifen. Um die Identität anzuzeigen, wechseln Sie zu **Dienst Anwendungen verwalten**, wählen Sie die Power Pivot-Dienst Anwendung aus, indem Sie auf den leeren Bereich neben dem Namen klicken (Dadurch wird die Zeile ausgewählt), und klicken Sie dann auf **Eigenschaften**. Das Sicherheitskonto, das auf dieser Seite angezeigt wird, ist das Konto, das als Element der Zielanwendung hinzugefügt werden soll.  
  
    3.  Fügen Sie Windows-Benutzer- und Gruppenkonten hinzu, die diese Zielanwendung in den Datenquellenabschnitt einer Planungsseite für die Datenaktualisierung eingeben.  
  
14. Klicken Sie auf **OK**.  
  
15. Wählen Sie die soeben erstellte Zielanwendung aus, klicken Sie auf den Pfeil nach unten, und wählen Sie **Anmelde Informationen festlegen.**  
  
16. Geben Sie die Anmeldeinformationen ein, die zum Verbinden mit der Datenquelle verwendet werden sollen (z. B. den Benutzernamen und das Kennwort einer SQL Server-Anmeldung).  
  
17. Klicken Sie auf **OK**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Planen einer Datenaktualisierung &#40;PowerPivot für SharePoint&#41;](schedule-a-data-refresh-powerpivot-for-sharepoint.md)   
 [PowerPivot-Datenaktualisierung mit SharePoint 2010](powerpivot-data-refresh-with-sharepoint-2010.md)  
  
  
