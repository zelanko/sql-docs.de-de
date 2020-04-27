---
title: Konfigurieren des unbeaufsichtigten Daten Aktualisierungs Kontos für Power Pivot (PowerPivot für SharePoint) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 81401eac-c619-4fad-ad3e-599e7a6f8493
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 894e7d4fb5a0234643cf237e767a8ae999e67496
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66087418"
---
# <a name="configure-the-powerpivot-unattended-data-refresh-account-powerpivot-for-sharepoint"></a>Konfigurieren des unbeaufsichtigten Daten Aktualisierungs Kontos für Power Pivot (PowerPivot für SharePoint)
  Das unbeaufsichtigte Datenaktualisierungskonto für PowerPivot ist ein ausgewiesenes Konto zum Ausführen von PowerPivot-Datenaktualisierungsaufträgen in einer SharePoint-Farm. Indem Sie Sie konfigurieren, aktivieren Sie die Option **das von der Administrator konfigurierte Konto** für die Datenaktualisierung verwenden auf der Seite Daten Aktualisierungs Zeitplan (siehe unten). Arbeitsmappenautoren, die eine Datenaktualisierung planen, können diese Option auswählen, wenn sie das unbeaufsichtigte Datenaktualisierungskonto für PowerPivot für die Ausführung eines Datenaktualisierungsauftrags bereitstellen möchten. Weitere Informationen zum Anzeigen der Anmelde Informations Optionen in einem Daten Aktualisierungs Zeitplan finden Sie unter [Planen einer Datenaktualisierung &#40;PowerPivot für SharePoint&#41;](schedule-a-data-refresh-powerpivot-for-sharepoint.md).  
  
 ![SSAS_PowerpivotKJ_DataRefreshCreds](media/ssas-powerpivotkj-datarefreshcreds.gif "SSAS_PowerpivotKJ_DataRefreshCreds")  
  
 **[!INCLUDE[applies](../includes/applies-md.md)]** SharePoint 2010  
  
 Abhängig davon, welche Optionen Sie beim Konfigurieren des Servers ausgewählt haben, könnte das unbeaufsichtigte Datenaktualisierungskonto bereits erstellt sein. In einer Standardkonfiguration wird die Identität des unbeaufsichtigten Datenaktualisierungskontos anfänglich auf das Farmkonto festgelegt. Sie können die Sicherheit Ihrer Bereitstellung verbessern, indem Sie das Konto so ändern, dass es als anderer Benutzer ausgeführt werden soll. Befolgen Sie diese Anweisungen, um das Konto zu ändern: [Aktualisieren Sie die Anmelde Informationen, die von einem vorhandenen unbeaufsichtigten Daten Aktualisierungs Konto für Power Pivot](#bkmk_editUA)  
  
 Für alle anderen Installationsszenarien muss dieses Konto manuell mithilfe der folgenden Anweisungen konfiguriert werden.  
  
 Dieses Thema enthält folgende Abschnitte:  
  
 [Voraussetzungen](#bkmk_prereq)  
  
 [Schritt 1: Erstellen einer Zielanwendung und Festlegen der Anmeldeinformationen](#bkmk_create)  
  
 [Schritt 2: Angeben des unbeaufsichtigten Kontos auf den PowerPivot-Serverkonfigurationsseiten](#bkmk_specifyUA)  
  
 [Schritt 3: Erteilen von Teilnahme Berechtigungen für das Konto](#bkmk_grant)  
  
 [Schritt 4: Erteilen von Leseberechtigungen für den Zugriff auf externe Datenquellen, die bei der Datenaktualisierung verwendet werden](#bkmk_dbread)  
  
 [Schritt 5: Überprüfen der Kontoverfügbarkeit auf den Datenaktualisierungskonfigurationsseiten](#bkmk_verify)  
  
 [Verwenden des unbeaufsichtigten Datenaktualisierungskontos für PowerPivot](#bkmk_use)  
  
 [Aktualisieren der von einem vorhandenen PowerPivot-Konto für die unbeaufsichtigte Datenaktualisierung verwendeten Anmeldeinformationen](#bkmk_editUA)  
  
##  <a name="prerequisites"></a><a name="bkmk_prereq"></a> Voraussetzungen  
 Zur Verwendung der Datenaktualisierung muss Secure Store Service aktiviert und konfiguriert sein, und für die Farm muss ein Hauptschlüssel generiert werden. Anweisungen hierzu finden Sie unter [Power Pivot-Datenaktualisierung mit SharePoint 2010](powerpivot-data-refresh-with-sharepoint-2010.md) .  
  
 Sie müssen im Vorfeld entscheiden, welches Windows-Domänenbenutzerkonto als unbeaufsichtigtes Datenaktualisierungskonto für PowerPivot verwendet werden soll. Dies sollte ein speziell für diesen Zweck erstelltes Konto sein, damit die Verwendung überwacht werden kann.  
  
 Sie müssen die Anwendungsidentität des PowerPivot-Systemdiensts kennen. Sie erhalten diesem Dienst Konto **voll** Zugriffsberechtigungen für das unbeaufsichtigte Daten Aktualisierungs Konto, wenn Sie die Zielanwendung für das Konto in Schritt 1 erstellen. Diese Berechtigungen ermöglichen es dem PowerPivot-Systemdienst, während der Datenaktualisierung die Anmeldeinformationen des Kontos für die unbeaufsichtigte Datenaktualisierung abzurufen. Um die erforderlichen Dienst Kontoinformationen zu erhalten, öffnen Sie die Seite **Dienst Konten konfigurieren** in der zentral Administration, und wählen Sie den von der Power Pivot-Dienst Anwendung verwendeten Dienst Anwendungs Pool aus. Standardmäßig handelt es sich hierbei um den **Dienst Anwendungs Pool-SharePoint-Webdienst System**.  
  
## <a name="configure-the-unattended-powerpivot-data-refresh-account"></a>Konfigurieren des unbeaufsichtigten Datenaktualisierungskontos für PowerPivot  
 Für jede PowerPivot-Dienstanwendung kann nur ein unbeaufsichtigtes Datenaktualisierungskonto für PowerPivot konfiguriert werden. Kontoinformationen werden im Secure Store Service in einer Zielanwendung gespeichert, die auf ein vordefiniertes Windows-Domänenbenutzerkonto festgelegt ist. Nach der Erstellung der Zielanwendung können Sie es auf den Konfigurationsseiten einer PowerPivot-Dienstanwendung als PowerPivot-Datenaktualisierungskonto angeben.  
  
> [!NOTE]  
>  Wenn im unbeaufsichtigten Datenaktualisierungskonto eine Datenaktualisierung ausgeführt wird, werden die Verwendungsberichterstellung und der Datenaktualisierungsverlauf für das Windows-Benutzerkonto aufgezeichnet, das für die unbeaufsichtigte Datenaktualisierung verwendet wird. Wenn eine genauere Aufzeichnung der Personen erfolgen soll, die Datenaktualisierung abfragen oder Zeitpläne besitzen, verwenden Sie ggf. eine der anderen Optionen für die Datenaktualisierung. Lassen Sie beispielsweise Benutzer selbst Anmeldeinformationen eingeben (Standard), oder erstellen Sie zusätzliche Zielanwendungen zum Speichern beliebiger Windows-Anmeldeinformationen, die Sie für die Datenaktualisierung verwenden möchten. Weitere Informationen finden Sie unter [Konfigurieren gespeicherter Anmelde Informationen für die Power Pivot-Datenaktualisierung &#40;PowerPivot für SharePoint&#41;](configure-stored-credentials-data-refresh-powerpivot-sharepoint.md).  
  
 Die Erstellung des Kontos für die unbeaufsichtigte Datenaktualisierung besteht aus fünf Teilen.  
  
-   Erstellen Sie eine Zielanwendung in Secure Store Service für das Konto, und geben Sie die Anmeldeinformationen an.  
  
-   Geben Sie die Zielanwendungs-ID für das Konto für die unbeaufsichtigte Datenaktualisierung auf der Seite zum Konfigurieren der PowerPivot Server-Einstellungen an.  
  
-   Erteilen Sie dem Konto Teilnahmeberechtigungen.  
  
-   Erteilen Sie dem Konto Leseberechtigungen, um während der Datenaktualisierung auf externe Datenquellen zuzugreifen.  
  
-   Überprüfen Sie, ob das Konto auf der Seite für die Verwaltung des Datenaktualisierungszeitplans für eine veröffentlichte PowerPivot-Arbeitsmappe verfügbar ist.  
  
###  <a name="step-1-create-a-target-application-and-set-the-credentials"></a><a name="bkmk_create"></a>Schritt 1: Erstellen einer Zielanwendung und Festlegen der Anmelde Informationen  
  
1.  Klicken Sie in der zentral Administration unter Anwendungs Verwaltung auf **Dienst Anwendungen verwalten**.  
  
2.  Klicken Sie auf **einmaliges Anmelden**.  
  
3.  Klicken Sie unter Zielanwendungen verwalten auf **neu**.  
  
4.  Geben Sie in Zielanwendungs-ID **powerpivotdatarefresh**ein.  
  
5.  Geben Sie im Feld Anzeige Name den Namen **Power Pivot-Datenaktualisierung**ein.  
  
6.  Geben Sie unter E-Mail des Kontakts Ihre E-Mail-Adresse ein.  
  
7.  Wählen Sie unter Ziel Anwendungstyp die Option **individuell**aus.  
  
    > [!NOTE]  
    >  Die Angabe des Kontotyps Individuell ist für dieses Szenario richtig, da nur die PowerPivot-Dienstanwendung die Anmeldeinformationen des unbeaufsichtigten Datenaktualisierungskontos für PowerPivot anfordert. In der Praxis wird das unbeaufsichtigte Datenaktualisierungskonto nur von der Dienstanwendung verwendet, sodass der Kontotyp Individuell die beste Wahl für diese Zielanwendung ist.  
  
8.  Überspringen Sie die Zielanwendungsseiten-URL. Von der PowerPivot-Datenaktualisierung wird dies nicht verwendet.  
  
9. Klicken Sie auf **Weiter**.  
  
10. Übernehmen Sie auf der Seite **Anmelde Informationen für die Secure Store-Zielanwendung angeben** die Standardwerte. Feldnamen und -typen müssen "Windows-Benutzername" und "Windows-Kennwort" sein.  
  
11. Klicken Sie auf **Weiter**.  
  
12. Geben Sie unter Administratoren der Zielanwendung die Anwendungspoolidentität der PowerPivot-Dienstanwendung an. Der Dienst benötigt Berechtigungen für den **voll** Zugriff, damit er zur Laufzeit Informationen zum unbeaufsichtigten Daten Aktualisierungs Konto abrufen kann. Geben Sie außerdem die Windows-Domänenbenutzerkonten weiterer SharePoint-Benutzer an, die über Administratorzugriff auf die Anwendungseinstellungen verfügen sollen.  
  
13. Klicken Sie auf **OK**.  
  
14. Wählen Sie die soeben erstellte Zielanwendung aus, klicken Sie auf den Pfeil nach unten, und wählen Sie **Anmelde Informationen festlegen.**  
  
15. Geben Sie unter **Besitzer**von Anmelde Informationen ein Windows-Domänen Benutzerkonto ein, für das Sie über Berechtigungen zum Aktualisieren der Anmelde Informationen verfügen möchten. Die Anmelde Informationen werden für Daten neue Aktionen verwendet, und die **Besitzer** der Anmelde Informationen verfügen über Berechtigungen zum Ändern der Anmelde Informationen.  
  
16. Klicken Sie auf **OK**.  
  
###  <a name="step-2-specify-the-unattended-account-in-powerpivot-server-configuration-pages"></a><a name="bkmk_specifyUA"></a>Schritt 2: Angeben des unbeaufsichtigten Kontos auf den Power Pivot-Server Konfigurationsseiten  
  
1.  Klicken Sie in der zentral Administration unter Anwendungs Verwaltung auf **Dienst Anwendungen verwalten**.  
  
2.  Suchen Sie die PowerPivot-Dienstanwendung. Sie erkennen eine Dienstanwendung an ihrem Typ. Ein PowerPivot-Dienstanwendungstyp ist **PowerPivot-Dienstanwendung**.  
  
3.  Klicken Sie auf den Namen der PowerPivot-Dienstanwendung. Warten Sie, bis das Power Pivot-Management-Dashboard angezeigt wird.  
  
4.  Klicken Sie in Aktionen in der oberen rechten Ecke auf **Einstellungen für Dienst Anwendung konfigurieren**.  
  
5.  Geben Sie unter Datenaktualisierung unter Unbeaufsichtigtes Power Pivot-Daten Aktualisierungs Konto die Zielanwendungs-ID ein, die Sie in einem vorherigen Schritt erstellt haben: **powerpivotdatarefresh**.  
  
6.  Klicken Sie auf **OK**.  
  
###  <a name="step-3-grant-contribute-permissions-to-the-account"></a><a name="bkmk_grant"></a>Schritt 3: Erteilen von Teilnahme Berechtigungen für das Konto  
 Bevor das unbeaufsichtigte Datenaktualisierungskonto für PowerPivot verwendet werden kann, müssen allen PowerPivot-Arbeitsmappen, für die es verwendet werden soll, Teilnahmeberechtigungen zugewiesen werden. Die Berechtigungsebene ist erforderlich, um die Arbeitsmappe von einer Bibliothek zu öffnen und anschließend nach der Aktualisierung der Daten erneut in der Bibliothek zu speichern.  
  
 Das Zuweisen von Berechtigungen ist ein Schritt, der vom Websitesammlungsadministrator durchgeführt werden muss. SharePoint-Berechtigungen können an der Stammwebsitesammlung oder einer beliebigen darunterliegenden Ebene zugewiesen werden, einschließlich individueller Dokumente und Elemente. Die Art der Festlegung von Berechtigungen variiert je nach erforderlichem Genauigkeitsgrad. Die folgenden Schritte stellen eine Art der Erteilung von Berechtigungen dar.  
  
1.  Klicken Sie auf einer SharePoint-Website unter Website Aktionen auf **Website Berechtigungen**.  
  
2.  Klicken Sie auf **Berechtigungen erteilen**.  
  
3.  Geben Sie im Bereich für die Benutzerauswahl den Namen des Windows-Domänenbenutzerkontos ein, das als unbeaufsichtigtes PowerPivot-Konto ausgewiesen ist. Dies ist der Name des Windows-Domänenbenutzerkontos, das in Secure Store Service als Zielanwendung angegeben wurde.  
  
4.  Wählen Sie unter Berechtigungen erteilen die Option **Benutzern die Berechtigung direkt erteilen**aus.  
  
5.  Wählen Sie **mitwirken**aus, und klicken Sie dann auf **OK**.  
  
###  <a name="step-4-grant-read-permissions-to-access-external-data-sources-used-in-data-refresh"></a><a name="bkmk_dbread"></a>Schritt 4: Erteilen von Leseberechtigungen für den Zugriff auf externe Datenquellen, die bei der Datenaktualisierung verwendet werden  
 Wenn sie Daten in eine PowerPivot-Arbeitsmappe importieren, basieren Verbindungen zu externen Daten häufig auf vertrauenswürdigen oder personifizierten Verbindungen, die die Identität des aktuellen Benutzers verwenden, um eine Verbindung mit der Datenquelle herzustellen. Diese Typen von Verbindungen funktionieren nur, wenn der aktuelle Benutzer über die Berechtigung verfügt, die Daten zu lesen, die er importiert.  
  
 In einem Datenaktualisierungsszenario wird die gleiche Verbindungszeichenfolge, die zum Importieren von Daten verwendet wurde, jetzt erneut verwendet, um die Daten zu aktualisieren. Wenn die Verbindungszeichenfolge den aktuellen Benutzer voraussetzt (z. B. eine Zeichenfolge, die Integrated_Security=SSPI einschließt), dann übergibt der PowerPivot-Systemdienst die Benutzeridentität des PowerPivot-Kontos für die unbeaufsichtigte Datenaktualisierung als den aktuellen Benutzer. Diese Verbindung ist nur erfolgreich, wenn das PowerPivot-Konto für die unbeaufsichtigte Datenaktualisierung über Leseberechtigungen für die externe Datenquelle verfügt.  
  
 Aus diesem Grund müssen Sie dem unbeaufsichtigten Datenaktualisierungskonto für PowerPivot Lesezugriff auf alle externen Datenquellen gewähren, die bei einem Datenaktualisierungsvorgang verwendet werden, der unter dem unbeaufsichtigten Konto ausgeführt wird.  
  
 Wenn Sie Administrator für die in der Organisation verwendeten Datenquellen sind, können Sie eine Anmeldung erstellen und die erforderlichen Berechtigungen zuweisen. Andernfalls müssen Sie sich an die Besitzer der Daten wenden und die Kontoinformationen angeben. Sie müssen das Windows-Domänenbenutzerkonto angeben, das dem PowerPivot-Konto für die unbeaufsichtigte Datenaktualisierung zugeordnet wird. Dies ist das Konto, das Sie in "(Schritt 1): Erstellen einer Zielanwendung und Festlegen der Anmelde Informationen" in diesem Thema angegeben haben.  
  
###  <a name="step-5-verify-account-availability-in-data-refresh-configuration-pages"></a><a name="bkmk_verify"></a>Schritt 5: Überprüfen der Konto Verfügbarkeit auf den Daten Aktualisierungs Konfigurationsseiten  
  
1.  Öffnen Sie die Seite zum Konfigurieren der Datenaktualisierung für eine veröffentlichte Arbeitsmappe, die PowerPivot-Daten enthält. Anweisungen zum Öffnen der Seite finden Sie unter [Planen einer Datenaktualisierung &#40;PowerPivot für SharePoint&#41;](schedule-a-data-refresh-powerpivot-for-sharepoint.md).  
  
2.  Vergewissern Sie sich, dass auf der Seite Daten Aktualisierungs Konfiguration die Option **von der Administrator konfigurierte Daten Aktualisierungs Konto verwenden** aktiviert ist.  
  
3.  Aktivieren Sie das Kontrollkästchen **auch so bald wie möglich aktualisieren** , und klicken Sie dann auf **OK**.  
  
4.  Wählen Sie in der Bibliothek, die die Arbeitsmappe enthält, die Arbeitsmappe aus, klicken Sie auf den rechts angezeigten Pfeil nach unten, und wählen Sie dann **Power Pivot-Datenaktualisierung verwalten**aus. Möglicherweise müssen Sie einige Minuten warten, wenn der Datenaktualisierungsauftrag eine große Datenmenge zurückgibt.  
  
 Wenn ein Fehler auftritt, können Sie auf der Seite Daten Aktualisierungs Verlauf auf **Zeitplan konfigurieren** klicken, um andere Anmelde Informationen zu verwenden. Sie müssen ggf. auch die Anmeldeinformationen der Datenquelle in der ursprünglichen Arbeitsmappe prüfen, um die Verbindungszeichenfolge anzuzeigen, die bei der Datenaktualisierung verwendet wird. Die Verbindungszeichenfolge enthält Informationen zum Serverstandort und der Datenbank, die Sie zur Problembehandlung verwenden können.  
  
 Weitere Informationen zur Problembehandlung finden Sie unter Problembehandlung bei der [Power Pivot-Datenaktualisierung](https://go.microsoft.com/fwlink/p/?LinkID=223279) im TechNet-wiki.  
  
##  <a name="using-the-powerpivot-unattended-data-refresh-account"></a><a name="bkmk_use"></a>Verwenden des unbeaufsichtigten Daten Aktualisierungs Kontos für Power Pivot  
 Nur die erste der drei Anmeldeinformationsoptionen auf der Seite zum Planen der PowerPivot-Datenaktualisierung entspricht dem unbeaufsichtigten Datenaktualisierungskonto. Stellen Sie beim Einrichten des Datenaktualisierungszeitplan sicher, dass diese Option ausgewählt ist.  
  
 ![SSAS_PowerpivotKJ_DataRefreshCreds](media/ssas-powerpivotkj-datarefreshcreds.gif "SSAS_PowerpivotKJ_DataRefreshCreds")  
  
 Verwenden Sie nicht die dritte Anmeldeinformationsoption (für die eine Zielanwendungs-ID eingegeben werden muss), um auf das unbeaufsichtigte Datenaktualisierungskonto für PowerPivot zuzugreifen. Bei Auswahl der dritten Option wird eine zusätzliche Identitätswechselprüfung ausgeführt. Wenn versucht wird, diese für ein unbeaufsichtigtes Datenaktualisierungskonto für PowerPivot (oder für eine Zielanwendung auf Basis des Kontotyps Individuell) zu verwenden, tritt ein Überprüfungsfehler auf. Weitere Informationen zur Verwendung der dritten Option finden Sie unter [Konfigurieren gespeicherter Anmelde Informationen für die Power Pivot-Datenaktualisierung &#40;PowerPivot für SharePoint&#41;](configure-stored-credentials-data-refresh-powerpivot-sharepoint.md).  
  
##  <a name="update-the-credentials-used-by-an-existing-powerpivot-unattended-data-refresh-account"></a><a name="bkmk_editUA"></a>Aktualisieren der von einem vorhandenen Power Pivot-Konto für die unbeaufsichtigten Datenaktualisierung verwendeten Anmelde Informationen  
 Wenn das unbeaufsichtigte Datenaktualisierungskonto bereits beim Setup oder von einem Administrator konfiguriert wurde, können Benutzername und Kennwort durch Bearbeiten der Zielanwendung, von der die Anmeldeinformationen gespeichert werden, aktualisiert werden. Beachten Sie, dass die Windows-Originalidentität, die zuvor mit dem unbeaufsichtigten Datenaktualisierungskonto für PowerPivot verknüpft war, beim Bearbeiten der Anmeldeinformationen in Secure Store Service nicht sichtbar ist. Sie müssen immer sowohl den Benutzernamen als auch das Kennwort für diese Zielanwendung erneut in Secure Store Service eingeben, ganz gleich, ob Sie ein abgelaufenes Kennwort aktualisieren oder ein anderes Konto angeben.  
  
1.  Klicken Sie in der zentral Administration unter Anwendungs Verwaltung auf **Dienst Anwendungen verwalten**.  
  
2.  Klicken Sie auf **einmaliges Anmelden**.  
  
3.  Aktivieren Sie das Kontrollkästchen neben **powerpivotdatarefresh**.  
  
4.  Klicken Sie unter Anmelde Informationen auf **festlegen**.  
  
5.  Geben Sie unter **Besitzer**von Anmelde Informationen ein Windows-Domänen Benutzerkonto ein, für das Sie über Berechtigungen zum Aktualisieren der Anmelde Informationen verfügen möchten. Die Anmelde Informationen werden für Daten neue Aktionen verwendet, und die **Besitzer** der Anmelde Informationen verfügen über Berechtigungen zum Ändern der Anmelde Informationen.  
  
6.  Geben Sie unter Benutzername das Windows-Domänenbenutzerkonto ein, das Teil der Anmeldeinformationen für die unbeaufsichtigte Datenaktualisierung ist.  
  
7.  Geben Sie im Feld Kennwort das Kennwort des Kontos ein, und geben Sie es erneut ein, um das Kennwort zu bestätigen.  
  
8.  Klicken Sie auf **OK**.  
  
 Wenn Sie nicht nur das Kennwort, sondern auch den Benutzernamen für das Konto ändern, müssen Sie sehr wahrscheinlich weitere Konfigurationsschritte ausführen, beispielsweise Erteilen von Leseberechtigungen für externe Datenquellen und SharePoint-Berechtigungen zum Aktualisieren der PowerPivot-Arbeitsmappe. Anweisungen hierzu finden Sie unter Power Pivot-Konto für unbeaufsichtigte Datenaktualisierung Konto Konfiguration: [Schritt 3: Erteilen von Teilnahme Berechtigungen für das Konto](#bkmk_grant)und Fortfahren mit allen verbleibenden Schritten, Abschließen der Überprüfung, ob das Konto ordnungsgemäß konfiguriert ist.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Power Pivot-Datenaktualisierung mit SharePoint 2010](powerpivot-data-refresh-with-sharepoint-2010.md)   
 [Planen einer Datenaktualisierung &#40;PowerPivot für SharePoint&#41;](schedule-a-data-refresh-powerpivot-for-sharepoint.md)   
 [PowerPivot-Datenaktualisierung](power-pivot-sharepoint/power-pivot-data-refresh.md)  
  
  
