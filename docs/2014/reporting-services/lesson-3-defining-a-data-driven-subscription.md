---
title: 'Lektion 3: Definieren eines datengesteuerten Abonnements | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 89197b9b-7502-4fe2-bea3-ed7943eebf3b
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 54fd143d2b3af2596ff44a313b2d35b29fc1604a
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56015539"
---
# <a name="lesson-3-defining-a-data-driven-subscription"></a>Lektion 3: Definieren eines datengesteuerten Abonnements
  In dieser Lektion verwenden Sie die datengesteuerten Abonnementseiten für folgende Zwecke: um eine Verbindung mit einer Abonnementdatenquelle herzustellen, um eine Abfrage zu erstellen, die Abonnementdaten abruft, und um das Resultset den Berichts- und Übermittlungsoptionen zuzuordnen.  
  
> [!NOTE]  
>  Prüfen Sie vor dem Starten, dass der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Agent-Dienst ausgeführt wird. Ist dies nicht der Fall, können Sie das Abonnement nicht speichern.  
  
 In dieser Lektion wird davon ausgegangen, dass Sie Lektion 1 und Lektion 2 abgeschlossen haben und dass die Berichtsdatenquelle gespeicherte Anmeldeinformationen verwendet.  Weitere Informationen finden Sie unter [Lektion 2: Ändern der Eigenschaften der Berichtsdatenquelle](../reporting-services/lesson-2-modifying-the-report-data-source-properties.md).  
  
 In diesem Thema:  
  
-   [Starten Sie den Assistenten für datengesteuertes Abonnement](#bkmk_startwizard)  
  
-   [Schritt 1 - Beschreibung definieren](#bkmk_definesubscription)  
  
-   [Schritt 2: eine Verbindung mit der Abonnentendatenquelle definieren](#bkmk_defineconnectiontosubscriber)  
  
-   [Schritt 3: Definieren Sie eine Abfrage zum Abrufen von Abonnentendaten](#bkmk_definequery)  
  
-   [Schritt 4: Festlegen von Übermittlungsoptionen](#bkmk_set_deliveryoptions)  
  
-   [Schritt 5: Konfigurieren Sie einen Parameterwert zum variieren der Berichtsausgabe](#bkmk_configure_parameter)  
  
-   [Schritt 6: die Planung eines Abonnements](#bkmk_schedule_subscription)  
  
##  <a name="bkmk_startwizard"></a> Starten Sie den Assistenten für datengesteuertes Abonnement  
  
1.  Klicken Sie im Berichts-Manager auf **Home**, und navigieren Sie zum Ordner mit dem Bericht **Sales Orders** .  
  
2.  Klicken Sie im Kontextmenü des Berichts auf **Verwalten**und dann auf die Registerkarte **Abonnements** .  
  
3.  Klicken Sie auf **Neues datengesteuertes Abonnement**. Wenn diese Schaltfläche nicht angezeigt wird, verfügen Sie möglicherweise nicht über Inhalts-Manager-Berechtigungen.  
  
##  <a name="bkmk_definesubscription"></a> Schritt 1 - Beschreibung definieren  
  
1.  Geben Sie **Lieferung Verkaufsauftrag** bei Beschreibung ein.  
  
2.  Wählen Sie **Windows-Dateifreigabe** für **Angeben, wie die Empfänger benachrichtigt werden**.  
  
3.  Wählen Sie **Nur für dieses Abonnement angeben**und klicken Sie dann auf **Weiter**.  
  
##  <a name="bkmk_defineconnectiontosubscriber"></a> Schritt 2: eine Verbindung mit der Abonnentendatenquelle definieren  
  
1.  Wählen Sie **Microsoft SQL Server** als Quelldatentyp aus.  
  
2.  Geben Sie unter Verbindungszeichenfolge die folgende Verbindungszeichenfolge ein:  
  
    ```  
    data source=localhost; initial catalog=Subscribers  
    ```  
  
    > [!NOTE]  
    >  "Abonnenten" ist die Datenbank, die Sie in Lektion 1 erstellt haben.  
  
3.  Klicken Sie auf **Anmeldeinformationen, die sicher im Berichtsserver gespeichert sind**.  
  
4.  Geben Sie unter **Benutzername** und **Kennwort**Ihren Benutzernamen und Ihr Kennwort für die Domäne ein. Geben Sie unter **Benutzername**sowohl die Domäne als auch das Benutzerkonto an.  
  
    > [!NOTE]  
    >  Die Anmeldeinformationen, die für die Verbindung mit einer Abonnentendatenquelle verwendet werden, werden nicht an [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]zurückgegeben. Wenn Sie das Abonnement später ändern, müssen Sie das Kennwort zum Herstellen der Verbindung mit der Datenquelle erneut eingeben.  
  
5.  Wählen Sie **Als Windows-Anmeldeinformationen verwenden, wenn eine Verbindung zur Datenquelle hergestellt wird**aus, und klicken Sie dann auf **Weiter**.  
  
##  <a name="bkmk_definequery"></a> Schritt 3: Definieren Sie eine Abfrage zum Abrufen von Abonnentendaten  
  
1.  Geben Sie im Abfragefeld folgende Abfrage ein:  
  
    ```  
    Select * from OrderInfo  
    ```  
  
2.  Geben Sie ein Timeout von 30 Sekunden an.  
  
3.  Klicken Sie auf **Überprüfen**, und klicken Sie dann auf **Weiter**.  
  
##  <a name="bkmk_set_deliveryoptions"></a> Schritt 4: Festlegen von Übermittlungsoptionen  
  
1.  Wählen Sie für **Dateiname**die Option **Rufen Sie den Wert aus der Datenbank ab**aus. Wählen Sie das Feld **Reihenfolge**aus.  
  
2.  Wählen Sie für **Pfad**die Option **Geben Sie einen statischen Wert an**aus. Geben Sie in "Wert festlegen" den Namen einer öffentlichen Dateifreigabe ein, für die Sie Schreibberechtigungen besitzen (z. B. `\\mycomputer\public\myreports`).  
  
3.  Wählen Sie für **Renderformat**die Option **Rufen Sie den Wert aus der Datenbank ab**aus. Wählen Sie **Format**aus.  
  
4.  Wählen Sie für den **Schreibmodus**die Option **Geben Sie einen statischen Wert an** aus, und wählen Sie **AutoIncrement**aus.  
  
5.  Wählen Sie für **Dateierweiterung**die Option **Geben Sie einen statischen Wert an** aus, und wählen Sie **True**aus.  
  
6.  Wählen Sie für **Benutzernamen**die Option **Geben Sie einen statischen Wert an**aus. Geben Sie Ihr Domänenbenutzerkonto an. Geben Sie ihn in folgendem Format ein: `<domain>\<account>`. Das Benutzerkonto muss über Berechtigungen zum Pfad verfügen, den Sie in den vorherigen Schritten konfiguriert haben.  
  
7.  Wählen Sie für **Kennwort**die Option **Geben Sie einen statischen Wert an**aus. Geben Sie Ihr Kennwort ein. Achten Sie darauf, dass Sie das Kennwort richtig eingeben. Das Kennwort wird nicht durch den Assistenten überprüft.  
  
8.  Klicken Sie auf **Weiter.**  
  
##  <a name="bkmk_configure_parameter"></a> Schritt 5: Konfigurieren Sie einen Parameterwert zum variieren der Berichtsausgabe  
  
1.  Wählen Sie für **OrderNumber**die Option **Rufen Sie den Wert aus der Datenbank ab**aus. Wählen Sie in "Wert" die Option **Reihenfolge**aus. Klicken Sie auf **Weiter.**  
  
##  <a name="bkmk_schedule_subscription"></a> Schritt 6: die Planung eines Abonnements  
  
1.  Klicken Sie auf **Nach einem Zeitplan, der für dieses Abonnement erstellt wurde**und dann auf **Weiter**.  
  
2.  Klicken Sie in **Zeitplandetails**auf **Einmal**.  
  
3.  Geben Sie eine Startzeit an, die ein paar Minuten nach der aktuellen Zeit liegt.  
  
4.  Klicken Sie auf **Fertig stellen**.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Beim Ausführen des Abonnements werden vier Berichtsdateien an die von Ihnen angegebene Dateifreigabe übermittelt, eine für jeden Auftrag in der *Abonnenten* -Datenquelle. Jede Übermittlung muss im Hinblick auf die Daten (sie müssen sich auf einen bestimmten Auftrag beziehen), das Renderingformat und das Dateiformat eindeutig sein. Sie können jeden Bericht von dem freigegebenen Ordner aus öffnen, um sicherzustellen, dass jede Version entsprechend den von Ihnen festgelegten Abonnementoptionen angepasst wurde.  
  
 ![Liste der Dateien, die vom Abonnement erstellt werden](../../2014/tutorials/media/ssrs-tutorial-datadriven-subscription-filelist.gif "List of files created by the subscription").  
  
 Die Abonnementseite im Berichts-Manager enthält das **Letzte Ausführungsdatum** und den **Status** des Abonnements.  
  
> [!NOTE]  
>  Aktualisieren Sie die Seite, nachdem das Abonnement ausgeführt wurde, um die aktualisierten Informationen zu sehen.  
  
 ![Abonnementergebnisse im Berichts-Manager](../../2014/tutorials/media/ssrs-tutorial-datadriven-subscription-status-reportmanager.gif "Subscription results in Report Manager")  
  
 Dies ist der letzte Schritt im Lernprogramm "Definieren eines datengesteuerten Abonnements". Weitere Informationen zu anderen [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Tutorials finden Sie unter [Reporting Services-Tutorials &#40;SSRS&#41;](../reporting-services/reporting-services-tutorials-ssrs.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen eines datengesteuerten Abonnements &#40;SSRS-Tutorial&#41;](../reporting-services/create-a-data-driven-subscription-ssrs-tutorial.md)   
 [Abonnements und Übermittlung &#40;Reporting Services&#41;](subscriptions/subscriptions-and-delivery-reporting-services.md)   
 [Data-Driven Subscriptions](subscriptions/data-driven-subscriptions.md)   
 [Erstellen, ändern und Löschen eines datengesteuerten Abonnements](subscriptions/create-modify-and-delete-data-driven-subscriptions.md)   
 [Verwenden einer externen Datenquelle für Abonnentendaten &#40;datengesteuertes Abonnement&#41;](subscriptions/use-an-external-data-source-for-subscriber-data-data-driven-subscription.md)  
  
  
