---
title: Konfigurieren des unbeaufsichtigten PowerPivot für die unbeaufsichtigte Datenaktualisierung (PowerPivot für SharePoint)-Konto | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: 81401eac-c619-4fad-ad3e-599e7a6f8493
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 51cc5f71c3a3e7515238aef08e97316e549c0e70
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62680558"
---
# <a name="configure-the-powerpivot-unattended-data-refresh-account-powerpivot-for-sharepoint"></a>Konfigurieren des unbeaufsichtigten PowerPivot für die unbeaufsichtigte Datenaktualisierung (PowerPivot für SharePoint)-Konto
  Das unbeaufsichtigte Datenaktualisierungskonto für PowerPivot ist ein ausgewiesenes Konto zum Ausführen von PowerPivot-Datenaktualisierungsaufträgen in einer SharePoint-Farm. Durch die Konfiguration, die Sie aktivieren die **verwenden, das vom Administrator konfigurierte Konto für die datenaktualisierung** -Option in einem zeitplanseite datenaktualisierung (siehe unten). Arbeitsmappenautoren, die eine Datenaktualisierung planen, können diese Option auswählen, wenn sie das unbeaufsichtigte Datenaktualisierungskonto für PowerPivot für die Ausführung eines Datenaktualisierungsauftrags bereitstellen möchten. Weitere Informationen dazu, wie Sie die Optionen für Anmeldeinformationen in einen Zeitplan zur datenaktualisierung anzeigen, finden Sie unter [Planen einer Datenaktualisierung &#40;PowerPivot für SharePoint&#41;](schedule-a-data-refresh-powerpivot-for-sharepoint.md).  
  
 ![SSAS_PowerpivotKJ_DataRefreshCreds](media/ssas-powerpivotkj-datarefreshcreds.gif "SSAS_PowerpivotKJ_DataRefreshCreds")  
  
 **[!INCLUDE[applies](../includes/applies-md.md)]**  SharePoint 2010  
  
 Abhängig davon, welche Optionen Sie beim Konfigurieren des Servers ausgewählt haben, könnte das unbeaufsichtigte Datenaktualisierungskonto bereits erstellt sein. In einer Standardkonfiguration wird die Identität des unbeaufsichtigten Datenaktualisierungskontos anfänglich auf das Farmkonto festgelegt. Sie können die Sicherheit Ihrer Bereitstellung verbessern, indem Sie das Konto so ändern, dass es als anderer Benutzer ausgeführt werden soll. Um das Konto zu ändern, gehen Sie wie folgt vor: [Aktualisieren Sie die Anmeldeinformationen ein, die einem vorhandenen PowerPivot unbeaufsichtigte datenaktualisierungskonto](#bkmk_editUA).  
  
 Für alle anderen Installationsszenarien muss dieses Konto manuell mithilfe der folgenden Anweisungen konfiguriert werden.  
  
 Dieses Thema enthält folgende Abschnitte:  
  
 [Erforderliche Komponenten](#bkmk_prereq)  
  
 [Schritt 1: Erstellen einer Zielanwendung und Festlegen der Anmeldeinformationen](#bkmk_create)  
  
 [Schritt 2: Angeben des unbeaufsichtigten Kontos in PowerPivot-Serverkonfigurationsseiten](#bkmk_specifyUA)  
  
 [Schritt 3: GRANT Teilnahmeberechtigungen verfügen, um das Konto](#bkmk_grant)  
  
 [Schritt 4: Erteilen von Leseberechtigungen für den Zugriff auf externe Datenquellen, die bei der datenaktualisierung verwendet](#bkmk_dbread)  
  
 [Schritt 5: Überprüfen der kontoverfügbarkeit datenaktualisierungskonfigurationsseiten](#bkmk_verify)  
  
 [Verwenden die für die unbeaufsichtigte Datenaktualisierung von PowerPivot-Konto](#bkmk_use)  
  
 [Aktualisieren Sie die Anmeldeinformationen ein, die einem vorhandenen PowerPivot für die unbeaufsichtigte datenaktualisierung Konto](#bkmk_editUA)  
  
##  <a name="bkmk_prereq"></a> Erforderliche Komponenten  
 Zur Verwendung der Datenaktualisierung muss Secure Store Service aktiviert und konfiguriert sein, und für die Farm muss ein Hauptschlüssel generiert werden. Anleitungen hierzu finden Sie unter [PowerPivot-Datenaktualisierung mit SharePoint 2010](powerpivot-data-refresh-with-sharepoint-2010.md)  
  
 Sie müssen im Vorfeld entscheiden, welches Windows-Domänenbenutzerkonto als unbeaufsichtigtes Datenaktualisierungskonto für PowerPivot verwendet werden soll. Dies sollte ein speziell für diesen Zweck erstelltes Konto sein, damit die Verwendung überwacht werden kann.  
  
 Sie müssen die Anwendungsidentität des PowerPivot-Systemdiensts kennen. Sie geben dieses Dienstkonto **Vollzugriff** Berechtigungen für die unbeaufsichtigte datenaktualisierungskonto bei der Erstellung der Zielanwendung dafür in Schritt 1. Diese Berechtigungen ermöglichen es dem PowerPivot-Systemdienst, während der Datenaktualisierung die Anmeldeinformationen des Kontos für die unbeaufsichtigte Datenaktualisierung abzurufen. Um die erforderlichen Dienstkontoinformationen abzurufen, öffnen die **Dienstkonten konfigurieren** Seite in der zentralen Verwaltung, und wählen Sie die von der PowerPivot-dienstanwendung verwendeten Dienstanwendungspool. Standardmäßig ist dies die **Dienstanwendungspool – Systemstandard für SharePoint-Webdienste**.  
  
## <a name="configure-the-unattended-powerpivot-data-refresh-account"></a>Konfigurieren des unbeaufsichtigten Datenaktualisierungskontos für PowerPivot  
 Für jede PowerPivot-Dienstanwendung kann nur ein unbeaufsichtigtes Datenaktualisierungskonto für PowerPivot konfiguriert werden. Kontoinformationen werden im Secure Store Service in einer Zielanwendung gespeichert, die auf ein vordefiniertes Windows-Domänenbenutzerkonto festgelegt ist. Nach der Erstellung der Zielanwendung können Sie es auf den Konfigurationsseiten einer PowerPivot-Dienstanwendung als PowerPivot-Datenaktualisierungskonto angeben.  
  
> [!NOTE]  
>  Wenn im unbeaufsichtigten Datenaktualisierungskonto eine Datenaktualisierung ausgeführt wird, werden die Verwendungsberichterstellung und der Datenaktualisierungsverlauf für das Windows-Benutzerkonto aufgezeichnet, das für die unbeaufsichtigte Datenaktualisierung verwendet wird. Wenn eine genauere Aufzeichnung der Personen erfolgen soll, die Datenaktualisierung abfragen oder Zeitpläne besitzen, verwenden Sie ggf. eine der anderen Optionen für die Datenaktualisierung. Lassen Sie beispielsweise Benutzer selbst Anmeldeinformationen eingeben (Standard), oder erstellen Sie zusätzliche Zielanwendungen zum Speichern beliebiger Windows-Anmeldeinformationen, die Sie für die Datenaktualisierung verwenden möchten. Weitere Informationen finden Sie unter [konfigurieren gespeicherter Anmeldeinformationen für die PowerPivot-Datenaktualisierung &#40;PowerPivot für SharePoint&#41;](configure-stored-credentials-data-refresh-powerpivot-sharepoint.md).  
  
 Die Erstellung des Kontos für die unbeaufsichtigte Datenaktualisierung besteht aus fünf Teilen.  
  
-   Erstellen Sie eine Zielanwendung in Secure Store Service für das Konto, und geben Sie die Anmeldeinformationen an.  
  
-   Geben Sie die Zielanwendungs-ID für das Konto für die unbeaufsichtigte Datenaktualisierung auf der Seite zum Konfigurieren der PowerPivot Server-Einstellungen an.  
  
-   Erteilen Sie dem Konto Teilnahmeberechtigungen.  
  
-   Erteilen Sie dem Konto Leseberechtigungen, um während der Datenaktualisierung auf externe Datenquellen zuzugreifen.  
  
-   Überprüfen Sie, ob das Konto auf der Seite für die Verwaltung des Datenaktualisierungszeitplans für eine veröffentlichte PowerPivot-Arbeitsmappe verfügbar ist.  
  
###  <a name="bkmk_create"></a>Schritt 1: Erstellen einer Zielanwendung und Festlegen der Anmeldeinformationen  
  
1.  Klicken Sie in der Zentraladministration unter Anwendungsverwaltung auf **Dienstanwendungen verwalten**.  
  
2.  Klicken Sie auf **Secure Store Service-**.  
  
3.  Klicken Sie unter Zielanwendungen verwalten auf **neu**.  
  
4.  Geben Sie in Zielanwendungs-ID **PowerPivotDataRefresh**.  
  
5.  Geben Sie unter Anzeigename **PowerPivot-Datenaktualisierung**.  
  
6.  Geben Sie unter E-Mail des Kontakts Ihre E-Mail-Adresse ein.  
  
7.  Wählen Sie in der Art der Zielanwendung, **einzelne**.  
  
    > [!NOTE]  
    >  Die Angabe des Kontotyps Individuell ist für dieses Szenario richtig, da nur die PowerPivot-Dienstanwendung die Anmeldeinformationen des unbeaufsichtigten Datenaktualisierungskontos für PowerPivot anfordert. In der Praxis wird das unbeaufsichtigte Datenaktualisierungskonto nur von der Dienstanwendung verwendet, sodass der Kontotyp Individuell die beste Wahl für diese Zielanwendung ist.  
  
8.  Überspringen Sie die Zielanwendungsseiten-URL. Von der PowerPivot-Datenaktualisierung wird dies nicht verwendet.  
  
9. Klicken Sie auf **Weiter**.  
  
10. In der **Anmeldeinformationen Felder für die Secure Store-Zielanwendung angeben** Seite, die Standardwerte übernehmen. Feldnamen und -typen müssen "Windows-Benutzername" und "Windows-Kennwort" sein.  
  
11. Klicken Sie auf **Weiter**.  
  
12. Geben Sie unter Administratoren der Zielanwendung die Anwendungspoolidentität der PowerPivot-Dienstanwendung an. Der Dienst erfordert **Vollzugriff** Kontoinformationen zur Laufzeit aktualisieren Sie Berechtigungen so, dass die It für die unbeaufsichtigte Daten abgerufen werden kann. Geben Sie außerdem die Windows-Domänenbenutzerkonten weiterer SharePoint-Benutzer an, die über Administratorzugriff auf die Anwendungseinstellungen verfügen sollen.  
  
13. Klicken Sie auf **OK**.  
  
14. Wählen Sie die Zielanwendung, die Sie gerade erstellt haben, klicken Sie auf den Pfeil nach unten aus, und wählen **Anmeldeinformationen festlegen.**  
  
15. In **Besitzer der Anmeldeinformationen**, geben Sie ein Windows-Domänenbenutzerkonto, dass Sie berechtigt, die Anmeldeinformationen aktualisieren möchten. Die Anmeldeinformationen für datenaktualisierungen verwendet und die **Besitzer der Anmeldeinformationen** über Berechtigungen verfügen, um die Anmeldeinformationen zu ändern.  
  
16. Klicken Sie auf **OK**.  
  
###  <a name="bkmk_specifyUA"></a>Schritt 2: Angeben des unbeaufsichtigten Kontos in PowerPivot-Serverkonfigurationsseiten  
  
1.  Klicken Sie in der Zentraladministration unter Anwendungsverwaltung auf **Dienstanwendungen verwalten**.  
  
2.  Suchen Sie die PowerPivot-Dienstanwendung. Sie erkennen eine Dienstanwendung an ihrem Typ. Ein PowerPivot-Dienstanwendungstyp ist **PowerPivot-Dienstanwendung**.  
  
3.  Klicken Sie auf den Namen der PowerPivot-Dienstanwendung. Warten Sie das PowerPivot-Management-Dashboard angezeigt werden.  
  
4.  In der oberen rechten Ecke, klicken Sie im Aktionsbereich auf **Einstellungen für dienstanwendung konfigurieren**.  
  
5.  Geben Sie unter Datenaktualisierung in PowerPivot für die unbeaufsichtigte Datenaktualisierungskonto die Sie in einem vorherigen Schritt erstellte zielanwendungs-ID: **PowerPivotDataRefresh**.  
  
6.  Klicken Sie auf **OK**.  
  
###  <a name="bkmk_grant"></a>Schritt 3: GRANT Teilnahmeberechtigungen verfügen, um das Konto  
 Bevor das unbeaufsichtigte Datenaktualisierungskonto für PowerPivot verwendet werden kann, müssen allen PowerPivot-Arbeitsmappen, für die es verwendet werden soll, Teilnahmeberechtigungen zugewiesen werden. Die Berechtigungsebene ist erforderlich, um die Arbeitsmappe von einer Bibliothek zu öffnen und anschließend nach der Aktualisierung der Daten erneut in der Bibliothek zu speichern.  
  
 Das Zuweisen von Berechtigungen ist ein Schritt, der vom Websitesammlungsadministrator durchgeführt werden muss. SharePoint-Berechtigungen können an der Stammwebsitesammlung oder einer beliebigen darunterliegenden Ebene zugewiesen werden, einschließlich individueller Dokumente und Elemente. Die Art der Festlegung von Berechtigungen variiert je nach erforderlichem Genauigkeitsgrad. Die folgenden Schritte stellen eine Art der Erteilung von Berechtigungen dar.  
  
1.  Klicken Sie auf einer SharePoint-Website im Menü Websiteaktionen auf **Websiteberechtigungen**.  
  
2.  Klicken Sie auf **Berechtigungen erteilen**.  
  
3.  Geben Sie im Bereich für die Benutzerauswahl den Namen des Windows-Domänenbenutzerkontos ein, das als unbeaufsichtigtes PowerPivot-Konto ausgewiesen ist. Dies ist der Name des Windows-Domänenbenutzerkontos, das in Secure Store Service als Zielanwendung angegeben wurde.  
  
4.  Erteilen von Berechtigungen wählen **Benutzern eine Berechtigung direkt erteilen**.  
  
5.  Wählen Sie **mitwirken**, und klicken Sie dann auf **OK**.  
  
###  <a name="bkmk_dbread"></a> Schritt 4: Erteilen von Leseberechtigungen für den Zugriff auf externe Datenquellen, die bei der datenaktualisierung verwendet  
 Wenn sie Daten in eine PowerPivot-Arbeitsmappe importieren, basieren Verbindungen zu externen Daten häufig auf vertrauenswürdigen oder personifizierten Verbindungen, die die Identität des aktuellen Benutzers verwenden, um eine Verbindung mit der Datenquelle herzustellen. Diese Typen von Verbindungen funktionieren nur, wenn der aktuelle Benutzer über die Berechtigung verfügt, die Daten zu lesen, die er importiert.  
  
 In einem Datenaktualisierungsszenario wird die gleiche Verbindungszeichenfolge, die zum Importieren von Daten verwendet wurde, jetzt erneut verwendet, um die Daten zu aktualisieren. Wenn die Verbindungszeichenfolge den aktuellen Benutzer voraussetzt (z. B. eine Zeichenfolge, die Integrated_Security=SSPI einschließt), dann übergibt der PowerPivot-Systemdienst die Benutzeridentität des PowerPivot-Kontos für die unbeaufsichtigte Datenaktualisierung als den aktuellen Benutzer. Diese Verbindung ist nur erfolgreich, wenn das PowerPivot-Konto für die unbeaufsichtigte Datenaktualisierung über Leseberechtigungen für die externe Datenquelle verfügt.  
  
 Aus diesem Grund müssen Sie dem unbeaufsichtigten Datenaktualisierungskonto für PowerPivot Lesezugriff auf alle externen Datenquellen gewähren, die bei einem Datenaktualisierungsvorgang verwendet werden, der unter dem unbeaufsichtigten Konto ausgeführt wird.  
  
 Wenn Sie Administrator für die in der Organisation verwendeten Datenquellen sind, können Sie eine Anmeldung erstellen und die erforderlichen Berechtigungen zuweisen. Andernfalls müssen Sie sich an die Besitzer der Daten wenden und die Kontoinformationen angeben. Sie müssen das Windows-Domänenbenutzerkonto angeben, das dem PowerPivot-Konto für die unbeaufsichtigte Datenaktualisierung zugeordnet wird. Dies ist das Konto, das Sie in "(Step 1) angegeben: Erstellen einer Zielanwendung und Festlegen der Anmeldeinformationen"in diesem Thema.  
  
###  <a name="bkmk_verify"></a> Schritt 5: Überprüfen der kontoverfügbarkeit datenaktualisierungskonfigurationsseiten  
  
1.  Öffnen Sie die Seite zum Konfigurieren der Datenaktualisierung für eine veröffentlichte Arbeitsmappe, die PowerPivot-Daten enthält. Anweisungen dazu, wie Sie die Seite zu öffnen, finden Sie unter [Planen einer Datenaktualisierung &#40;PowerPivot für SharePoint&#41;](schedule-a-data-refresh-powerpivot-for-sharepoint.md).  
  
2.  Überprüfen Sie, ob die **verwenden, das vom Administrator konfigurierte Konto für die datenaktualisierung** Option in der datenaktualisierungskonfigurationsseite aktiviert ist.  
  
3.  Wählen Sie die **außerdem so bald wie möglich aktualisieren** Kontrollkästchen, und klicken Sie dann auf **OK**.  
  
4.  Wählen Sie in der Bibliothek, die die Arbeitsmappe enthält, die Arbeitsmappe, klicken Sie auf den nach rechts angezeigten Pfeil nach unten und wählen Sie dann **PowerPivot-Datenaktualisierung verwalten**. Möglicherweise müssen Sie einige Minuten warten, wenn der Datenaktualisierungsauftrag eine große Datenmenge zurückgibt.  
  
 Wenn ein Fehler auftritt, können Sie klicken **Zeitplan konfigurieren** aktualisieren Sie in den Daten die Seite "Verlauf", um verschiedene Anmeldeinformationen auszuprobieren. Sie müssen ggf. auch die Anmeldeinformationen der Datenquelle in der ursprünglichen Arbeitsmappe prüfen, um die Verbindungszeichenfolge anzuzeigen, die bei der Datenaktualisierung verwendet wird. Die Verbindungszeichenfolge enthält Informationen zum Serverstandort und der Datenbank, die Sie zur Problembehandlung verwenden können.  
  
 Weitere Informationen zur Problembehandlung finden Sie unter [Problembehandlung bei der PowerPivot-Datenaktualisierung](https://go.microsoft.com/fwlink/p/?LinkID=223279) im TechNet Wiki.  
  
##  <a name="bkmk_use"></a> Verwenden die für die unbeaufsichtigte Datenaktualisierung von PowerPivot-Konto  
 Nur die erste der drei Anmeldeinformationsoptionen auf der Seite zum Planen der PowerPivot-Datenaktualisierung entspricht dem unbeaufsichtigten Datenaktualisierungskonto. Stellen Sie beim Einrichten des Datenaktualisierungszeitplan sicher, dass diese Option ausgewählt ist.  
  
 ![SSAS_PowerpivotKJ_DataRefreshCreds](media/ssas-powerpivotkj-datarefreshcreds.gif "SSAS_PowerpivotKJ_DataRefreshCreds")  
  
 Verwenden Sie nicht die dritte Anmeldeinformationsoption (für die eine Zielanwendungs-ID eingegeben werden muss), um auf das unbeaufsichtigte Datenaktualisierungskonto für PowerPivot zuzugreifen. Bei Auswahl der dritten Option wird eine zusätzliche Identitätswechselprüfung ausgeführt. Wenn versucht wird, diese für ein unbeaufsichtigtes Datenaktualisierungskonto für PowerPivot (oder für eine Zielanwendung auf Basis des Kontotyps Individuell) zu verwenden, tritt ein Überprüfungsfehler auf. Weitere Informationen zur Verwendung die dritte Option finden Sie unter [konfigurieren gespeicherter Anmeldeinformationen für die PowerPivot-Datenaktualisierung &#40;PowerPivot für SharePoint&#41;](configure-stored-credentials-data-refresh-powerpivot-sharepoint.md).  
  
##  <a name="bkmk_editUA"></a> Aktualisieren Sie die Anmeldeinformationen ein, die einem vorhandenen PowerPivot für die unbeaufsichtigte datenaktualisierung Konto  
 Wenn das unbeaufsichtigte Datenaktualisierungskonto bereits beim Setup oder von einem Administrator konfiguriert wurde, können Benutzername und Kennwort durch Bearbeiten der Zielanwendung, von der die Anmeldeinformationen gespeichert werden, aktualisiert werden. Beachten Sie, dass die Windows-Originalidentität, die zuvor mit dem unbeaufsichtigten Datenaktualisierungskonto für PowerPivot verknüpft war, beim Bearbeiten der Anmeldeinformationen in Secure Store Service nicht sichtbar ist. Sie müssen immer sowohl den Benutzernamen als auch das Kennwort für diese Zielanwendung erneut in Secure Store Service eingeben, ganz gleich, ob Sie ein abgelaufenes Kennwort aktualisieren oder ein anderes Konto angeben.  
  
1.  Klicken Sie in der Zentraladministration unter Anwendungsverwaltung auf **Dienstanwendungen verwalten**.  
  
2.  Klicken Sie auf **Secure Store Service-**.  
  
3.  Aktivieren Sie das Kontrollkästchen neben **PowerPivotDataRefresh**.  
  
4.  Klicken Sie unter Anmeldeinformationen auf **festgelegt**.  
  
5.  In **Besitzer der Anmeldeinformationen**, geben Sie ein Windows-Domänenbenutzerkonto, dass Sie berechtigt, die Anmeldeinformationen aktualisieren möchten. Die Anmeldeinformationen für datenaktualisierungen verwendet und die **Besitzer der Anmeldeinformationen** über Berechtigungen verfügen, um die Anmeldeinformationen zu ändern.  
  
6.  Geben Sie unter Benutzername das Windows-Domänenbenutzerkonto ein, das Teil der Anmeldeinformationen für die unbeaufsichtigte Datenaktualisierung ist.  
  
7.  Geben Sie im Feld Kennwort das Kennwort des Kontos ein, und geben Sie es erneut ein, um das Kennwort zu bestätigen.  
  
8.  Klicken Sie auf **OK**.  
  
 Wenn Sie nicht nur das Kennwort, sondern auch den Benutzernamen für das Konto ändern, müssen Sie sehr wahrscheinlich weitere Konfigurationsschritte ausführen, beispielsweise Erteilen von Leseberechtigungen für externe Datenquellen und SharePoint-Berechtigungen zum Aktualisieren der PowerPivot-Arbeitsmappe. Anleitungen finden Sie in diesem Schritt PowerPivot für die unbeaufsichtigte Konfiguration: [Schritt 3: GRANT Teilnahmeberechtigungen verfügen, um das Konto](#bkmk_grant), und fahren Sie alle verbleibenden Schritte aus, mit dem Abschluss bei der Überprüfung, dass das Konto ordnungsgemäß konfiguriert ist.  
  
## <a name="see-also"></a>Siehe auch  
 [PowerPivot-Datenaktualisierung mit SharePoint 2010](powerpivot-data-refresh-with-sharepoint-2010.md)   
 [Planen einer Datenaktualisierung &#40;PowerPivot für SharePoint&#41;](schedule-a-data-refresh-powerpivot-for-sharepoint.md)   
 [PowerPivot-Datenaktualisierung](power-pivot-sharepoint/power-pivot-data-refresh.md)  
  
  
