---
title: Erstellen und Verwalten von Abonnements für Berichtsserver im einheitlichen Modus | Microsoft-Dokumentation
ms.date: 05/28/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: subscriptions
ms.topic: conceptual
helpviewer_keywords:
- standard subscriptions [Reporting Services]
- subscriptions [Reporting Services], standard
ms.assetid: 5ab1c661-9bfa-434a-b315-faac34ed12b1
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 5bcfeabda2eda62a6a4118ac5542e83a4b0afd66
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "76971315"
---
# <a name="create-and-manage-subscriptions-for-native-mode-report-servers"></a>Erstellen und Verwalten von Abonnements für Berichtsserver im einheitlichen Modus
  Ein Standardabonnement wird von einzelnen Benutzern erstellt, die einen Bericht per E-Mail oder an einen freigegebenen Ordner übermitteln möchten. Dieses Thema stellt Informationen zu Standardabonnements bereit, die von einzelnen Benutzern erstellt und verwaltet werden. Für datengesteuerte Abonnements gelten unterschiedliche Anforderungen und Schritte, die in einem anderen Thema behandelt werden. Weitere Informationen finden Sie unter [Erstellen, Ändern und Löschen von datengesteuerten Abonnements](../../reporting-services/subscriptions/create-modify-and-delete-data-driven-subscriptions.md).  
  
 **In diesem Artikel:**  
  
-   [Allgemeine Anforderungen für Abonnements](#bkmk_create_subscription)  
  
-   [So erstellen Sie ein Dateifreigabeabonnement](#bkmk_create_fileshare_subscription)  
  
-   [So erstellen Sie ein E-Mail-Abonnement](#bkmk_create_email_subscription)  
  
-   [So ändern Sie ein Abonnement](#bkmk_modify_subscription)  
  
-   [So löschen Sie ein Abonnement](#bkmk_delete_subscription)  
  
##  <a name="general-requirements-for-subscriptions"></a><a name="bkmk_create_subscription"></a> Allgemeine Anforderungen für Abonnements  
 In diesem Artikel wird erläutert, wie mit dem Webportal in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Abonnements auf einem Berichtsserver im einheitlichen Modus erstellt werden. Nach der Definition eines Abonnements können Sie im Webportal auf der Seite „Meine Abonnements“ oder auf der Registerkarte **Abonnements** eines bestimmten Berichts darauf zugreifen.  
  
 [Erstellen und Verwalten von Abonnements für Berichtsserver im SharePoint-Modus](../../reporting-services/subscriptions/create-and-manage-subscriptions-for-sharepoint-mode-report-servers.md) erklärt, wie mit den Anwendungsseiten auf einer SharePoint-Site Berichte auf einem SharePoint-Modus-Berichtsserver abonniert werden.  
  
-   Zum Verwenden der E-Mail-Übermittlung muss vor dem Erstellen des Abonnements der Berichtsserver für SMTP-Server- oder -Gateway-Verbindungen konfiguriert sein. Weitere Informationen finden Sie unter [E-Mail-Übermittlung in Reporting Services](../../reporting-services/subscriptions/e-mail-delivery-in-reporting-services.md).  
  
-   Zum Verwenden der Dateifreigabeübermittlung muss bereits ein Zielordner definiert sein. Weitere Informationen finden Sie unter [Abonnementeinstellungen und ein Dateifreigabekonto (Konfigurations-Manager)](../install-windows/subscription-settings-and-a-file-share-account-configuration-manager.md).  
  
 Bevor Sie einen Bericht abonnieren können, muss die Berichtsdatenquelle so konfiguriert sein, dass gespeicherte oder keine Anmeldeinformationen verwendet werden. Weitere Informationen finden Sie unter [Speichern von Anmeldeinformationen in einer Reporting Services-Datenquelle](../../reporting-services/report-data/store-credentials-in-a-reporting-services-data-source.md). Wenn dies nicht der Fall ist, ist die Schaltfläche **Neues Abonnement** nicht verfügbar.  
  
 In diesem Artikel wird nicht erläutert, wie ein datengesteuertes Abonnement erstellt wird. Anleitungen zum Erstellen eines datengesteuerten Abonnements finden Sie unter [Erstellen eines datengesteuerten Abonnements &#40;SSRS-Tutorial&#41;](../../reporting-services/create-a-data-driven-subscription-ssrs-tutorial.md).  
  
## <a name="to-create-a-file-share-subscription"></a><a name="bkmk_create_fileshare_subscription"></a> So erstellen Sie ein Dateifreigabeabonnement  
  
1. Durchsuchen Sie [das Webportal eines Berichtsservers (einheitlicher SSRS-Modus)](../../reporting-services/web-portal-ssrs-native-mode.md).  
  
2.  Navigieren Sie zum gewünschten Bericht. Klicken Sie mit der rechten Maustaste auf den Bericht, und wählen Sie dann **Abonnieren** aus.  
  
3.  **Beschreibung**: Geben Sie eine Beschreibung für das Berichtsabonnement ein, die maximal 512 Zeichen lang ist.  
  
4.  **Besitzer**: Das Besitzerfeld hat den aktuellen Benutzer als Standardwert und kann nicht bearbeitet werden, wenn Sie ein Abonnement erstellen. Nachdem das Abonnement gespeichert ist, können Sie jedoch die Eigenschaften des Abonnements ändern, einschließlich des Besitzers und der Beschreibung.  

5. Wählen Sie unter **Typ des Abonnements** das Optionsfeld **Standardabonnement** aus.

6. Wählen unter dem Abschnitt **Zeitplan** eine der folgenden Optionen aus:  
   - **Freigegebener Zeitplan**.  
   - **Berichtsspezifischer Zeitplan**.  

    Weitere Informationen zu Zeitplänen finden Sie unter [Zeitpläne](../../reporting-services/subscriptions/schedules.md).
  
7. Wählen Sie unter **Ziel** die Option **Windows-Dateifreigabe** aus.  
  
8. Geben Sie unter **Übermittlungsoptionen (Windows-Dateifreigabe)** Folgendes an:  
   - **Dateiname**: Geben Sie einen Dateinamen für den Bericht ein.
   - **Beim Erstellen der Datei eine Erweiterung hinzufügen**: Diese Option fügt dem Dateinamen eine Erweiterung um drei Zeichen hinzu. Die Dateierweiterung wird vom Berichtsausgabeformat bestimmt, das Sie auswählen.  
   - **Pfad**: Geben Sie einen UNC-Pfad (Universal Naming Convention) zu einem vorhandenen Ordner ein, an den Sie die Berichte senden möchten, (z.B. \\<Servername\>\<Meine Berichte>). Beginnen Sie die Pfadangabe mit zwei umgekehrten Schrägstrichen (\\). Geben Sie keinen umgekehrten Schrägstrich am Ende an.  
  
     ![Dateifreigabeabonnement](../../reporting-services/subscriptions/media/create-and-manage-subscriptions-for-native-mode-report-servers/subscription-file-share-delivery-option.png "Dateifreigabeabonnement")  
  
   - **Renderformat**: Wählen Sie ein Berichtsausgabeformat zur Dateiübermittlung aus. Wählen Sie ein Format aus, das der Desktopanwendung entspricht, die Sie verwenden, um den Bericht zu öffnen. Vermeiden Sie Formate, die einen Bericht nicht in einem einzigen Datenstrom rendern oder die Interaktivität einführen, die in einer statischen Datei (beispielsweise HTML 4.0) nicht unterstützt wird.  
  
   - **Anmeldeinformationen**: Wählen Sie aus, ob Sie das Dateifreigabekonto oder normale Windows-Benutzeranmeldeinformationen verwenden möchten. **Dateifreigabekonto verwenden** ist deaktiviert, wenn Ihr Berichtsadministrator kein Dateifreigabekonto konfiguriert hat. Weitere Informationen finden Sie unter [Abonnementeinstellungen und ein Dateifreigabekonto &#40;Konfigurations-Manager&#41;](../../reporting-services/install-windows/subscription-settings-and-a-file-share-account-configuration-manager.md). Geben Sie in die Textfelder **Benutzername** und **Kennwort** die Anmeldeinformationen ein, die für den Zugriff auf die Dateifreigabe erforderlich sind. Verwenden Sie für den Benutzernamen das Format *\<Domäne>* \\ *\<Benutzername>* .  
  
   - **Optionen für das Überschreiben**:  
     - **Eine vorhandene Datei mit einer neueren Version überschreiben**.  
     - **Die Datei nicht überschreiben, wenn eine frühere Version vorhanden ist**: Die Übermittlung wird nicht durchgeführt, falls eine vorhandene Datei erkannt wird.  
     - **Dateinamen inkrementieren, wenn neuere Versionen hinzugefügt werden**: Der Berichtsserver fügt eine Zahl an den Dateinamen an, um ihn von vorhandenen Dateien des gleichen Namens zu unterscheiden.  

9. Geben Sie für einen parametrisierten Bericht Parameter an, die für den Bericht in diesem Abonnement verwendet werden sollen. Die Parameter können sich von denen unterscheiden, die für die Ausführung des Berichts bei Bedarf oder in anderen geplanten Vorgängen verwendet werden.  
  
Der Bericht wird als statische Datei übermittelt. Wenn der Bericht interaktive Funktionen enthält (z. B. Links zu zusätzlichen Zeilen oder Spalten), stehen diese Funktionen nicht zur Verfügung.  
  
##  <a name="to-create-an-e-mail-subscription"></a><a name="bkmk_create_email_subscription"></a> So erstellen Sie ein E-Mail-Abonnement  
  
1. Durchsuchen Sie [das Webportal eines Berichtsservers (einheitlicher SSRS-Modus)](../../reporting-services/web-portal-ssrs-native-mode.md).  
  
2. Navigieren Sie zum gewünschten Bericht. Klicken Sie mit der rechten Maustaste auf den Bericht, und wählen Sie dann **Abonnieren** aus.  
  
3. **Beschreibung**: Geben Sie eine Beschreibung für das Berichtsabonnement ein, die maximal 512 Zeichen lang ist.  
  
4.  **Besitzer**: Das Besitzerfeld hat den aktuellen Benutzer als Standardwert und kann nicht bearbeitet werden, wenn Sie ein Abonnement erstellen. Nachdem das Abonnement gespeichert ist, können Sie jedoch die Eigenschaften des Abonnements ändern, einschließlich des Besitzers und der Beschreibung.  

5. Wählen Sie unter **Typ des Abonnements** das Optionsfeld **Standardabonnement** aus.

6. Wählen unter dem Abschnitt **Zeitplan** eine der folgenden Optionen aus:  
   - **Freigegebener Zeitplan**.  
   - **Berichtsspezifischer Zeitplan**.  

    Weitere Informationen zu Zeitplänen finden Sie unter [Zeitpläne](../../reporting-services/subscriptions/schedules.md).
  
7. Klicken Sie unter **Ziel** auf **E-Mail**.  Wenn die Option **E-Mail** nicht verfügbar ist, wurde der Berichtsserver nicht für E-Mail-Abonnements konfiguriert. Weitere Informationen finden Sie unter [Konfigurieren von E-Mail für eine Reporting Services-Dienstanwendung](../../reporting-services/install-windows/configure-e-mail-for-a-reporting-services-service-application.md).
  
8. Geben Sie unter **Übermittlungsoptionen (E-Mail)** Folgendes an:
   - **An**: Der Empfängername im „An:“-Feld ist selbstadressiert, wofür Ihr Domänenbenutzerkonto verwendet wird. Stellen Sie sicher, dass das Format [benutzername]@[domain.com] ist. Berichtsserver-Konfigurationseinstellungen legen fest, ob das Feld **An** bereits mit Ihrem Benutzerkonto ausgefüllt wird. Weitere Informationen zum Ädern der Konfigurationseinstellung für E-Mail-Adressen finden Sie unter [Konfigurieren von E-Mail für eine Reporting Services-Dienstanwendung](../../reporting-services/install-windows/configure-e-mail-for-a-reporting-services-service-application.md).

     >[!NOTE]  
     > Abhängig von Ihren Berechtigungen können Sie auch die E-Mail-Adresse eingeben, an die der Bericht geliefert werden soll. Mehrere E-Mail-Adressen müssen durch ein Semikolon (;) getrennt werden. Sie können weitere E-Mail-Adressen in die Textfelder **Cc**, **Bcc**und **Antwort an** eingeben. Für dieses Verfahren müssen Sie über die Berechtigung zum Verwalten von Abonnements verfügen.  
  
   - **Betreff:** Standardmäßig „Der @ReportName-Bericht wurde zum Zeitpunkt '@ExecutionTime' ausgeführt“. Sie können den Betreff bearbeiten. Beachten Sie jedoch, dass @ReportName und @ExecutionTime die einzigen globalen Variablen sind, die im **Betreff**-Feld unterstützt werden.  
  
     ![E-Mail-Abonnement](../../reporting-services/subscriptions/media/create-and-manage-subscriptions-for-native-mode-report-servers/subscription-e-mail-delivery-option.png "E-Mail-Abonnement")  

   - **Bericht einschließen**: Wählen Sie diese Option aus, um eine Kopie des Berichts einzubetten oder anzufügen. Das Format des Berichts wird durch das ausgewählte Renderingformat bestimmt. Wählen Sie diese Option nicht aus, wenn Sie annehmen, dass die Berichtsgröße das maximale Limit des E-Mail-Systems überschreitet.  
  
   - **Link einschließen**: Wählen Sie diese Option aus, um einen URL-Link zum Bericht im Textkörper der E-Mail-Nachricht einzuschließen.  
  
     >[!NOTE]  
     >Wenn Sie diese beiden Optionen deaktivieren, wird nur der Benachrichtigungstext in der Betreffzeile gesendet.  
  
   - Wählen Sie ein Renderingformat aus dem Listenfeld **Renderformat** aus. Diese Option ist verfügbar, wenn Sie die Option **Bericht einschließen** auswählen, um eine Kopie des Berichts einzubetten oder anzufügen.  
      - Um den Bericht in den Textkörper der E-Mail-Nachricht einzubetten, wählen Sie **MHTML (Webarchiv)** aus.  
      - Um den Bericht als Anhang zu senden, wählen Sie eines der anderen Renderingformate aus.  
  
   - Wählen im Listenfeld **Priorität** eine Priorität aus. In [!INCLUDE[msCoName](../../includes/msconame-md.md)] Exchange legt diese Einstellung ein Flag für die Wichtigkeitsstufe der E-Mail-Nachricht fest.  
   - Geben Sie einen **Kommentar** ein, wenn gewünscht.
  
9. Geben Sie für einen parametrisierten Bericht Parameter an, die für den Bericht in diesem Abonnement verwendet werden sollen. Die von Ihnen angegebenen Parameter können sich von denen unterscheiden, die für die Ausführung des Berichts bei Bedarf oder in anderen geplanten Vorgängen verwendet werden.  
  
##  <a name="to-modify-a-subscription"></a><a name="bkmk_modify_subscription"></a> So ändern Sie ein Abonnement  
 Ein Abonnement kann jederzeit geändert werden. Falls Sie ein Abonnement ändern, während es verarbeitet wird, werden die aktualisierten Einstellungen verwendet, falls sie im Berichtsserver gespeichert sind, bevor die Übermittlungserweiterung die Abonnementdaten erhält. Andernfalls werden die vorhandenen Einstellungen verwendet.  
  
 Ein Benutzer, der ein Abonnement erstellt, ist Besitzer dieses Abonnements. Jeder Benutzer kann seine eigenen Abonnements ändern oder löschen. Sie können den Besitzer des Berichts aus der Seite mit den Abonnementseigenschaften, oder programmgesteuert automatisch ändern. Weitere Informationen finden Sie unter  
  
-   [Verwenden von PowerShell, um Reporting Services-Abonnenten zu ändern und aufzulisten sowie ein Abonnement auszuführen](../../reporting-services/subscriptions/manage-subscription-owners-and-run-subscription-powershell.md)  
  
-   <xref:ReportService2010.ReportingService2010.ChangeSubscriptionOwner%2A>  
  
 Um nach einem Abonnement zu suchen, verwenden Sie die Seite **Meine Abonnements** , oder zeigen Sie die mit einem Bericht verknüpften Abonnementdefinitionen an. Es ist nicht möglich, direkt oder basierend auf Besitzernamen, Triggerinformationen, Statusinformationen usw. nach einem Abonnement zu suchen.  
  
 Abonnements können auch von Berichtsserveradministratoren geändert oder gelöscht werden.  
  
>[!NOTE]  
> Ein Berichtsserveradministrator kann nicht zentral alle einzelnen Abonnements verwalten, die auf einem bestimmten Berichtsserver verwendet werden. Berichtsserveradministratoren können jedoch auf jedes einzelne Abonnement zugreifen, um es zu ändern oder zu löschen.  
  
##  <a name="to-delete-a-subscription"></a><a name="bkmk_delete_subscription"></a> So löschen Sie ein Abonnement  
So löschen Sie ein Abonnement:  
  
1. Durchsuchen Sie [das Webportal eines Berichtsservers (einheitlicher SSRS-Modus)](../../reporting-services/web-portal-ssrs-native-mode.md).  
  
2. Wählen Sie im Webportal auf der Symbolleiste **Meine Abonnements** aus, und navigieren Sie zu dem Abonnement, das Sie ändern oder löschen möchten.  
  
3. Klicken Sie mit der rechten Maustaste auf den Bericht, und wählen Sie dann **Löschen** aus.  
  
Informationen zum Beenden eines Abonnements, das zurzeit auf dem Berichtsserver ausgeführt wird, finden Sie unter [Verwalten eines ausgeführten Prozesses](../../reporting-services/subscriptions/manage-a-running-process.md).  
  
 Falls Sie ein Abonnement beenden möchten und es nicht finden können, notieren Sie sich den Bericht, den Sie erhalten, und suchen Sie anhand des Namens danach. Wenn Sie auf den Bericht zugegriffen haben, können Sie sich aus dem Abonnement entfernen. Falls Sie das Abonnement nicht finden können, handelt es sich möglicherweise um ein datengesteuertes Abonnement. Weitere Informationen erhalten Sie von Ihrem Berichtsserveradministrator.  
  
 Ein Abonnement wird automatisch gelöscht, wenn der zugrunde liegende Bericht gelöscht wird. Wenn Sie ein Abonnement während der Verarbeitung löschen, wird das Abonnement beendet, falls der Löschvorgang durchgeführt wird, bevor die Übermittlungserweiterung die Abonnementdaten erhält. Andernfalls wird die Verarbeitung des Abonnements fortgesetzt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen und Verwalten von Abonnements für Berichtsserver im SharePoint-Modus](../../reporting-services/subscriptions/create-and-manage-subscriptions-for-sharepoint-mode-report-servers.md)  
 [Verwenden von PowerShell, um Reporting Services-Abonnenten zu ändern und aufzulisten sowie ein Abonnement auszuführen](../../reporting-services/subscriptions/manage-subscription-owners-and-run-subscription-powershell.md)  
 [Datengesteuerte Abonnements](../../reporting-services/subscriptions/data-driven-subscriptions.md)  
 [Abonnements und Übermittlung (Reporting Services)](../../reporting-services/subscriptions/subscriptions-and-delivery-reporting-services.md)  
 [Das Webportal eines Berichtsservers (einheitlicher SSRS-Modus)](../../reporting-services/web-portal-ssrs-native-mode.md)  
 [Verwenden von „Meine Abonnements“ (Berichtsserver im einheitlichen Modus)](../../reporting-services/subscriptions/use-my-subscriptions-native-mode-report-server.md)  
