---
title: Erstellen, ändern und Löschen von Standardabonnements (Reporting Services im einheitlichen Modus) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- standard subscriptions [Reporting Services]
- subscriptions [Reporting Services], standard
ms.assetid: 5ab1c661-9bfa-434a-b315-faac34ed12b1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c929fd63cb886eaad301697d4eee245ffb30301c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66100989"
---
# <a name="create-modify-and-delete-standard-subscriptions-reporting-services-in-native-mode"></a>Erstellen, Ändern und Löschen von Standardabonnements (Reporting Services im einheitlichen Modus)
  Ein Standardabonnement wird von einzelnen Benutzern erstellt, die einen Bericht per E-Mail oder an einen freigegebenen Ordner übermitteln möchten. Ein Standardabonnement wird stets über den Bericht definiert, auf dem es basiert.  
  
 Ein Benutzer, der ein Abonnement erstellt, ist Besitzer dieses Abonnements. Jeder Benutzer kann seine eigenen Abonnements ändern oder löschen.  
  
> [!NOTE]  
>  Beginnend mit [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] können Sie den Besitz eines Abonnements programmgesteuert übertragen. Es gibt keine Benutzeroberfläche, mit der Sie den Besitz von Abonnements übertragen können. Weitere Informationen finden Sie unter <xref:ReportService2010.ReportingService2010.ChangeSubscriptionOwner%2A>.  
  
 In Abhängigkeit von den Einstellungen in der Konfigurationsdatei **RSReportServer.config** können Benutzer zusätzliche Benutzer zu einem Abonnement hinzufügen (z. B. kann ein Manager die E-Mail-Adressen seiner Mitarbeiter hinzufügen, damit jeder eine Kopie des Berichts erhält). Dies wird nur unterstützt, wenn das Feld An: beim Definieren einzelner Abonnements angezeigt wird. Weitere Informationen finden Sie unter [Konfigurieren eines Berichtsservers für die e-Mail-Übermittlung &#40;SSRS-Konfigurations-Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md).  
  
 Dieses Thema stellt Informationen zu Standardabonnements bereit, die von einzelnen Benutzern erstellt und verwaltet werden. Für datengesteuerte Abonnements gelten unterschiedliche Anforderungen und Schritte, die in einem anderen Thema behandelt werden. Weitere Informationen finden Sie unter [erstellen, ändern und Löschen eines datengesteuerten Abonnements](data-driven-subscriptions.md).  
  
 In diesem Thema:  
  
-   [Zum Erstellen eines Abonnements](#bkmk_create_subscription)  
  
-   [So erstellen Sie ein Dateifreigabeabonnement](#bkmk_create_fileshare_subscription)  
  
-   [So erstellen Sie ein E-Mail-Abonnement](#bkmk_create_email_subscription)  
  
-   [So ändern Sie ein Abonnement](#bkmk_modify_subscription)  
  
-   [So löschen Sie ein Abonnement](#bkmk_delete_subscription)  
  
##  <a name="bkmk_create_subscription"></a> Zum Erstellen eines Abonnements  
 Zur Erstellung eines Abonnements wählen Sie das Tool und den Ansatz aus, die für die Berichtsserverbereitstellung gültig sind:  
  
-   In diesem Thema wird erläutert, wie mit dem [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Berichts-Manager Abonnements auf einem Berichtsserver im einheitlichen Modus erstellt werden. Nach der Definition eines Abonnements können Sie im Berichts-Manager auf der Seite Meine Abonnements oder auf der Registerkarte **Abonnements** eines bestimmten Berichts darauf zugreifen.  
  
-   [Erstellen und Verwalten von Abonnements für Berichtsserver im SharePoint-Modus](create-and-manage-subscriptions-for-sharepoint-mode-report-servers.md) erläutert, wie die Anwendungsseiten auf einer SharePoint-Website zum Abonnieren von Berichten auf einem Berichtsserver, der im integrierten SharePoint-Modus ausgeführt wird.  
  
 Dieses Thema enthält Anweisungen für das Erstellen eines E-Mail-Abonnements und eines Dateifreigabe-Übermittlungsabonnements.  
  
-   Zum Verwenden der E-Mail-Übermittlung muss vor dem Erstellen des Abonnements der Berichtsserver für SMTP-Server- oder -Gateway-Verbindungen konfiguriert sein.  
  
-   Zum Verwenden der Dateifreigabeübermittlung müssen bereits Zielordner definiert sein. Weitere Informationen finden Sie unter [Konfigurieren eines Berichtsservers für die e-Mail-Übermittlung &#40;SSRS-Konfigurations-Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md).  
  
 Bevor Sie einen Bericht abonnieren können, muss die Berichtsdatenquelle so konfiguriert sein, dass gespeicherte oder keine Anmeldeinformationen verwendet werden. Weitere Informationen finden Sie unter [Speichern von Anmeldeinformationen in einer Reporting Services-Datenquelle](../report-data/store-credentials-in-a-reporting-services-data-source.md). Wenn dies nicht der Fall ist, ist die Schaltfläche **Neues Abonnement** nicht verfügbar.  
  
 In diesem Thema wird nicht erläutert, wie ein datengesteuertes Abonnement erstellt wird. Informationen zum Erstellen eines datengesteuerten Abonnements finden Sie unter [Erstellen eines datengesteuerten Abonnements &#40;SSRS-Tutorial&#41;](../create-a-data-driven-subscription-ssrs-tutorial.md) oder in der Onlinehilfe zur Seite „Erstellen eines datengesteuerten Abonnements im Berichts-Manager“.  
  
###  <a name="bkmk_create_fileshare_subscription"></a> So erstellen Sie ein Dateifreigabeabonnement  
  
1.  Starten Sie den [Berichts-Manager &#40;einheitlicher SSRS-Modus&#41;](../report-manager-ssrs-native-mode.md).  
  
2.  Navigieren Sie im Berichts-Manager auf der Seite **Inhalt** zum Bericht, den Sie abonnieren möchten. Klicken Sie auf den Bericht, um ihn zu öffnen.  
  
3.  Klicken Sie auf die Registerkarte **Abonnements** , und klicken Sie anschließend auf **Neues Abonnement**.  
  
4.  Wählen Sie unter **Übermittelt von**die Option **Windows-Dateifreigabe**aus.  
  
5.  Geben Sie unter **Dateiname**einen Dateinamen für den Bericht ein.  
  
6.  Wählen Sie **Beim Erstellen der Datei eine Dateinamenerweiterung hinzufügen**aus. Mit dieser Option wird dem Dateinamen eine aus drei Zeichen bestehende Dateierweiterung hinzugefügt. Die Dateierweiterung wird vom Berichtsausgabeformat bestimmt, das Sie auswählen.  
  
7.  In der **Pfad** Text geben einen Universal Naming Convention (UNC)-Pfad zu einem vorhandenen Ordner, in dem Sie die Berichte senden möchten (z. B. \\ \\< Servername\>\\< Meine Berichte\>). Beginnen Sie die Pfadangabe mit zwei umgekehrten Schrägstrichen (\\). Geben Sie keinen umgekehrten Schrägstrich am Ende an.  
  
8.  Wählen Sie unter Renderformat zur Dateiübermittlung ein Berichtsausgabeformat aus. Wählen Sie ein Format aus, das der Desktopanwendung entspricht, die Sie verwenden, um den Bericht zu öffnen. Vermeiden Sie Formate, die einen Bericht nicht in einem einzigen Datenstrom rendern oder die Interaktivität einführen, die in einer statischen Datei (beispielsweise HTML 4.0) nicht unterstützt wird.  
  
9. Geben Sie in die Textfelder **Benutzername** und **Kennwort** die Anmeldeinformationen ein, die für den Zugriff auf die Dateifreigabe erforderlich sind. Verwenden Sie für den Benutzernamen das Format *\<Domäne>* \\ *\<Benutzername>* .  
  
10. Geben Sie Optionen zum Überschreiben an. Wenn Sie auf **Die Datei nicht überschreiben, wenn eine frühere Version vorhanden ist**klicken, wird die Übermittlung nicht durchgeführt, falls eine vorhandene Datei entdeckt wird. Wenn Sie auf **Dateinamen inkrementieren, wenn neuere Versionen hinzugefügt werden**klicken, hängt der Berichtsserver eine Zahl an den Dateinamen an, um ihn von vorhandenen Dateien desselben Namens zu unterscheiden.  
  
11. Geben Sie an, wann der Bericht übermittelt werden soll:  
  
    -   Klicken Sie zum Festlegen eines Übermittlungszeitpunkts auf **Wenn die geplante Berichtsausführung abgeschlossen ist** , und klicken Sie auf **Zeitplan auswählen** . Eine Zeitplanseite wird geöffnet.  
  
    -   Um einen vordefinierten, freigegebenen Zeitplan auszuwählen, der bereits über das gewünschte Datum, die Uhrzeit und Wiederholungsinformationen verfügt, klicken Sie auf **Nach einem freigegebenen Zeitplan**, und wählen Sie dann den gewünschten Zeitplan aus.  
  
    -   Klicken Sie auf**Nach Aktualisierung des Berichtsinhalts**, um einen Bericht zu übermitteln, wenn eine Berichtsmomentaufnahme mit einer neueren Version aktualisiert wurde. Wenn Sie einen Bericht abonnieren, der Daten zu geplanten Zeiten abruft, legt der Zeitplan für die Aktualisierung der Daten fest, wann das Abonnement verarbeitet wird.  
  
        > [!NOTE]  
        >  Diese Option ist nur für Momentaufnahmen verfügbar, die bereits einem Updatezeitplan zugeordnet sind.  
  
12. Geben Sie für einen parametrisierten Bericht Parameter an, die für den Bericht in diesem Abonnement verwendet werden sollen. Die Parameter können sich von denen unterscheiden, die für die Ausführung des Berichts bei Bedarf oder in anderen geplanten Vorgängen verwendet werden.  
  
 Der Bericht wird als statische Datei übermittelt. Wenn der Bericht interaktive Funktionen enthält (z. B. Links zu zusätzlichen Zeilen oder Spalten), stehen diese Funktionen nicht zur Verfügung.  
  
###  <a name="bkmk_create_email_subscription"></a> So erstellen Sie ein E-Mail-Abonnement  
  
1.  Navigieren Sie im Berichts-Manager auf der Seite **Inhalt** zum Bericht, den Sie abonnieren möchten. Klicken Sie auf den Bericht, um ihn zu öffnen.  
  
2.  Klicken Sie auf die Registerkarte **Abonnements** , und klicken Sie anschließend auf **Neues Abonnement**.  
  
3.  Wählen Sie unter **Übermittelt von**die Option **E-Mail**aus. Wenn dieser Übermittlungstyp nicht verfügbar ist, wurde der Berichtsserver nicht für E-Mail-Abonnements konfiguriert.  
  
4.  Im Feld **An** ist der Empfängername bereits als Ihr Domänenbenutzerkonto angegeben. Berichtsserver-Konfigurationseinstellungen legen fest, ob das Feld **An** bereits mit Ihrem Benutzerkonto ausgefüllt wird. Weitere Informationen zum Ändern der Einstellungen für e-Mail-Adressen finden Sie unter [Konfigurieren eines Berichtsservers für die e-Mail-Übermittlung &#40;SSRS-Konfigurations-Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md).  
  
    > [!NOTE]  
    >  Abhängig von Ihren Berechtigungen können Sie auch die E-Mail-Adresse eingeben, an die der Bericht geliefert werden soll. Mehrere E-Mail-Adressen müssen durch ein Semikolon (;) getrennt werden. Sie können weitere E-Mail-Adressen in die Textfelder **Cc**, **Bcc**und **Antwort an** eingeben. Für dieses Verfahren müssen Sie über die Berechtigung zum Verwalten von Abonnements verfügen.  
  
5.  Wählen Sie die Übermittlungsoptionen wie folgt aus:  
  
    -   Wählen Sie **Bericht einschließen**aus, um eine Kopie des Berichts einzubetten oder anzufügen. Das Format des Berichts wird durch das ausgewählte Renderingformat bestimmt. Wählen Sie diese Option nicht aus, wenn Sie annehmen, dass die Berichtsgröße das maximale Limit des E-Mail-Systems überschreitet.  
  
    -   Wählen Sie **Link einschließen**aus, um einen URL-Link zum Bericht im Textkörper der E-Mail-Nachricht einzuschließen.  
  
    > [!NOTE]  
    >  Wenn Sie diese beiden Optionen deaktivieren, wird nur der Benachrichtigungstext in der Betreffzeile gesendet.  
  
6.  Wählen Sie ein Renderingformat aus dem Listenfeld **Renderformat** aus. Diese Option ist verfügbar, wenn Sie die Option **Bericht einschließen** auswählen, um eine Kopie des Berichts einzubetten oder anzufügen.  
  
    -   Um den Bericht in den Textkörper der E-Mail-Nachricht einzubetten, wählen Sie **Webarchiv**aus.  
  
    -   Um den Bericht als Anhang zu senden, wählen Sie eines der anderen Renderingformate aus.  
  
7.  Wählen im Listenfeld **Priorität** eine Priorität aus. In [!INCLUDE[msCoName](../../includes/msconame-md.md)] Exchange legt diese Einstellung ein Flag für die Wichtigkeitsstufe der E-Mail-Nachricht fest.  
  
8.  Geben Sie an, wann der Bericht übermittelt werden soll:  
  
    -   Klicken Sie zum Planen eines Übermittlungszeitpunkts auf **Wenn die geplante Berichtsausführung abgeschlossen ist** , und klicken Sie auf **Zeitplan auswählen**. Eine Zeitplanseite wird geöffnet.  
  
    -   Um einen vordefinierten, freigegebenen Zeitplan auszuwählen, der bereits über das gewünschte Datum, die Uhrzeit und Wiederholungsinformationen verfügt, klicken Sie auf **Nach einem freigegebenen Zeitplan**, und wählen Sie dann den gewünschten Zeitplan aus.  
  
    -   Klicken Sie auf**Nach Aktualisierung des Berichtsinhalts**, um einen Bericht zu übermitteln, wenn eine Berichtsmomentaufnahme mit einer neueren Version aktualisiert wurde. Wenn Sie einen Bericht abonnieren, der Daten zu geplanten Zeiten abruft, legt der Zeitplan für die Aktualisierung der Daten fest, wann das Abonnement verarbeitet wird.  
  
    > [!NOTE]  
    >  Diese Option ist nur für Momentaufnahmen verfügbar, die bereits einem Updatezeitplan zugeordnet sind.  
  
9. Geben Sie für einen parametrisierten Bericht Parameter an, die für den Bericht in diesem Abonnement verwendet werden sollen. Die von Ihnen angegebenen Parameter können sich von denen unterscheiden, die für die Ausführung des Berichts bei Bedarf oder in anderen geplanten Vorgängen verwendet werden.  
  
##  <a name="bkmk_modify_subscription"></a> So ändern Sie ein Abonnement  
 Ein Abonnement kann jederzeit geändert werden. Falls Sie ein Abonnement ändern, während es verarbeitet wird, werden die aktualisierten Einstellungen verwendet, wenn sie in der Berichtsserver-Datenbank gespeichert werden, bevor die Übermittlungserweiterung die Abonnementdaten erhält. Andernfalls werden die vorhandenen Einstellungen verwendet.  
  
 Um nach einem Abonnement zu suchen, verwenden Sie die Seite **Meine Abonnements** , oder zeigen Sie die mit einem Bericht verknüpften Abonnementdefinitionen an. Es ist nicht möglich, direkt oder basierend auf Besitzernamen, Triggerinformationen, Statusinformationen usw. nach einem Abonnement zu suchen.  
  
 Abonnements können auch von Berichtsserveradministratoren geändert oder gelöscht werden.  
  
> [!NOTE]  
>  Ein Berichtsserveradministrator kann nicht zentral alle einzelnen Abonnements verwalten, die auf einem bestimmten Berichtsserver verwendet werden. Berichtsserveradministratoren können jedoch auf jedes einzelne Abonnement zugreifen, um es zu ändern oder zu löschen.  
  
##  <a name="bkmk_delete_subscription"></a> So löschen Sie ein Abonnement  
 So löschen Sie ein Abonnement  
  
1.  Starten Sie den [Berichts-Manager &#40;einheitlicher SSRS-Modus&#41;](../report-manager-ssrs-native-mode.md).  
  
2.  Klicken Sie im Berichts-Manager auf der globalen Symbolleiste auf **Meine Abonnements** , und navigieren Sie zu dem Abonnement, das Sie ändern oder löschen möchten.  
  
3.  Oder suchen Sie stattdessen auf der Registerkarte **Abonnements** eines geöffneten Berichts das Abonnement, das Sie ändern oder löschen möchten. Führen Sie eine der folgenden Aktionen aus:  
  
    1.  Klicken Sie zum Ändern eines Abonnements auf **Bearbeiten**.  
  
    2.  Aktivieren Sie zum Löschen eines Abonnements das Kontrollkästchen neben dem Abonnement, und klicken Sie dann auf **Löschen**.  
  
 In diesem Thema wird nicht beschrieben, wie ein Abonnement beendet wird, das zurzeit auf dem Berichtsserver ausgeführt wird. Weitere Informationen zum Kündigen von Abonnements finden Sie unter [Verwalten eines ausgeführten Prozesses](manage-a-running-process.md)  
  
 Wenn Sie ein Abonnement beenden möchten und es nicht finden können, notieren Sie sich den Bericht, den Sie erhalten, und suchen Sie anhand des Namens nach diesem Bericht. Wenn Sie auf den Bericht zugegriffen haben, können Sie sich aus dem Abonnement entfernen. Falls Sie das Abonnement nicht finden können, handelt es sich möglicherweise um ein datengesteuertes Abonnement. Weitere Informationen erhalten Sie von Ihrem Berichtsserveradministrator.  
  
 Ein Abonnement wird automatisch gelöscht, wenn der zugrunde liegende Bericht gelöscht wird. Wenn Sie ein Abonnement während der Verarbeitung löschen, wird das Abonnement beendet, falls der Löschvorgang durchgeführt wird, bevor die Übermittlungserweiterung die Abonnementdaten erhält. Andernfalls wird die Verarbeitung des Abonnements fortgesetzt.  
  
## <a name="see-also"></a>Siehe auch  
 [Aufgaben und Berechtigungen](../security/tasks-and-permissions.md)   
 [Erstellen und Verwalten von Abonnements für Berichtsserver im SharePoint-Modus](create-and-manage-subscriptions-for-sharepoint-mode-report-servers.md)   
 [Erstellen und Verwalten von Abonnements für Berichtsserver im einheitlichen Modus](../create-manage-subscriptions-native-mode-report-servers.md)   
 [Data-Driven Subscriptions](data-driven-subscriptions.md)   
 [Abonnements und Übermittlung &#40;Reporting Services&#41;](subscriptions-and-delivery-reporting-services.md)   
 [Berichts-Manager &#40;einheitlicher SSRS-Modus&#41;](../report-manager-ssrs-native-mode.md)   
 [Verwenden von „Meine Abonnements“](use-my-subscriptions-native-mode-report-server.md)  
  
  
