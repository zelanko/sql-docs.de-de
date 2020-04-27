---
title: Erstellen, ändern und Löschen eines datengesteuerten Abonnements | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- query-based subscriptions [Reporting Services]
- queries [Reporting Services], data-driven subscriptions
- subscriptions [Reporting Services], data-driven
- data-driven subscriptions
ms.assetid: 0ba2093e-9393-4eb6-af06-9da10988cfaf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 68a9d73139154ffd3d1343fb54a33ce103d6d7ea
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66100943"
---
# <a name="create-modify-and-delete-a-data-driven-subscription"></a>Erstellen, Ändern und Löschen eines datengesteuerten Abonnements
  Ein datengesteuertes Abonnement ist ein abfragebasiertes Abonnement, das die Datenwerte abfragt, die zum Verarbeiten des Abonnements zur Laufzeit verwendet werden. Wenn das Abonnement ausgelöst wird, wird eine Abfrage verarbeitet, die aktuelle Informationen über Empfänger, Berichtsübermittlungsoptionen, Renderingformate und Parametereinstellungen abruft. Die Abfrageergebnisse werden mit der Abonnementdefinition kombiniert. Dabei wird ein dynamisches Abonnement erstellt, das  Daten verwendet, die bereits in einer Mitarbeiterdatenbank, einer Kundendatenbank oder einer beliebigen Datenbank liegen und Informationen enthalten,  die als Abonnentendaten verwendbar sind.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im einheitlichen Modus &#124; im SharePoint-Modus|  
  
 **In diesem Thema:**  
  
-   [Erstellen und Ändern eines datengesteuerten Abonnements](#bkmk_create_and_modify)  
  
-   [Definieren einer Abfrage zum Abrufen von Abonnementdaten](#bkmk_define_query)  
  
-   [Ausführen eines Abonnements](#bkmk_run_subscription)  
  
-   [Verwalten und Entfernen eines datengesteuerten Abonnements](#bkmk_manage_and_delete)  
  
##  <a name="create-and-modify-a-data-driven-subscription"></a><a name="bkmk_create_and_modify"></a>Erstellen und Ändern eines datengesteuerten Abonnements  
 Verwenden Sie im Berichts-Manager die Seiten zum Erstellen eines datengesteuerten Abonnements, um ein neues datengesteuertes Abonnement zu erstellen oder ein vorhandenes Abonnement zu ändern. Diese Seiten führen Sie schrittweise durch das Erstellen oder Ändern eines Abonnements. Ein bereits erstelltes Abonnement öffnen Sie mithilfe der Seite Meine Abonnements und der Abonnementliste eines Berichts. Erfahren Sie, wie Sie ein datengesteuertes Abonnement erstellen, indem Sie die Seite [Erstellen eines datengesteuerten Abonnements (SSRS-Tutorial)](../create-a-data-driven-subscription-ssrs-tutorial.md) aufrufen.  
  
 Um ein datengesteuertes Abonnement zu erstellen, wählen Sie einen Bericht aus, der gespeicherte oder keine Anmeldeinformationen verwendet. Beim Erstellen des datengesteuerten Abonnements sollten Sie eine Benennungskonvention für das Beschreibungsfeld festlegen, damit Standardabonnements problemlos von datengesteuerten Abonnements unterschieden werden können.  
  
#### <a name="to-create-a-data-driven-subscription-native-mode"></a>So erstellen Sie ein datengesteuertes Abonnement (einheitlicher Modus)  
  
1.  Navigieren Sie im Berichts-Manager zum Ordner, der den Bericht enthält, zeigen Sie auf den Bericht, öffnen Sie das Menü **Optionen**, und klicken Sie auf Verwalten.  
  
2.  Wählen Sie die Registerkarte **Abonnements** aus.  
  
3.  Klicken Sie auf die Schaltfläche **Neues datengesteuertes Abonnement** .  
  
#### <a name="to-create-a-data-driven-subscription-sharepoint-mode"></a>So erstellen Sie ein datengesteuertes Abonnement (SharePoint-Modus)  
  
1.  Zeigen Sie in der SharePoint-Dokumentbibliothek auf den Bericht, öffnen Sie das Menü "Optionen", und klicken Sie auf **Abonnements verwalten**.  
  
2.  Klicken Sie auf **Datengesteuertes Abonnement hinzufügen**.  
  
#### <a name="to-modify-an-existing-data-driven-subscription-native-mode"></a>So ändern Sie ein vorhandenes datengesteuertes Abonnement (einheitlicher Modus)  
  
1.  Navigieren Sie in Berichts-Manager zu dem Ordner, der den Bericht enthält, zeigen Sie auf den Bericht, öffnen Sie das Menü Optionen, und klicken Sie auf **Verwalten**.  
  
2.  Klicken Sie auf die Registerkarte **Abonnements** . Klicken Sie alternativ auf den Link **Meine Abonnements** in der oben im des Berichts-Managers.  
  
3.  Wählen Sie das Abonnement aus, das Sie ändern möchten. Das folgende Symbol weist auf ein datengesteuerte Abonnement hin: ![Symbol für datengesteuerte Abonnements](../media/hlp-16subscriptiondd.gif "Datengesteuertes Abonnement (Symbol)")  
  
#### <a name="to-modify-an-existing-data-driven-subscription-sharepoint-mode"></a>So ändern Sie ein vorhandenes datengesteuertes Abonnement (SharePoint-Modus)  
  
1.  Zeigen Sie in der SharePoint-Dokumentbibliothek auf den Bericht, öffnen Sie das Menü "Optionen", und klicken Sie auf **Abonnements verwalten**.  
  
2.  Wählen Sie das Abonnement aus, das Sie ändern möchten.  
  
> [!NOTE]  
>  Jeder angegebene Wert kann geändert werden. Alle Werte werden so wie beim Erstellen angezeigt, außer dem Kennwort, mit dem auf den Abonnentendatenspeicher zugegriffen wird. Sie müssen das Kennwort bei jeder Änderung von Werten auf der zweiten Seite oder einer beliebigen nachfolgenden Seite erneut eingeben.  
  
 Bevor Sie ein datengesteuertes Abonnement erstellen können, müssen die folgenden Anforderungen erfüllt sein:  
  
-   **Berichtsanforderungen**. Der Bericht muss gespeicherte oder keine Anmeldeinformationen zum Abrufen des Inhalts zur Laufzeit verwenden. Sie können keine Berichte abonnieren, die angenommene oder delegierte Anmeldeinformationen zum Verbinden mit einer externen Datenquelle verwenden. Die Anmeldeinformationen des Benutzers, der das Abonnement erstellt oder besitzt, sind zum Zeitpunkt der Verarbeitung des Abonnements nicht verfügbar. Bei den gespeicherten Anmeldeinformationen kann es sich um ein Windows-Konto oder ein Datenbank-Benutzerkonto handeln. Weitere Informationen finden Sie unter [Angeben der Anmeldeinformationen und Verbindungsinformationen für Berichtsdatenquellen](../report-data/specify-credential-and-connection-information-for-report-data-sources.md).  
  
     Sie können keine mit dem Berichts-Generator erstellten Berichte abonnieren, die ein Modell als Datenquelle verwenden, das Sicherheitseinstellungen für Modellelemente enthält. Diese Einschränkung bezieht sich nur auf Berichte, die Sicherheitseinstellungen für Modellelemente verwenden.  
  
     Sie können keine datengesteuerten Abonnements für Berichte erstellen, die den `User!UserID` -Ausdruck enthalten.  
  
-   **Datenanforderungen**. Es muss eine externe Datenquelle mit Abonnentendaten vorhanden sein, auf die zugegriffen werden kann.  
  
-   **Benutzeranforderungen**. Der Autor des Abonnements benötigt die Berechtigungen "Berichte verwalten" sowie "Alle Abonnements verwalten". Weitere Informationen zu Berechtigungen auf Elementebene finden Sie unter [Aufgaben und Berechtigungen](../security/tasks-and-permissions.md). Außerdem muss er über die notwendigen Anmeldeinformationen für den Zugriff auf die externe Datenquelle mit Abonnentendaten verfügen.  
  
##  <a name="define-a-query-that-retrieves-subscription-information"></a><a name="bkmk_define_query"></a>Hiermit wird eine Abfrage zum Abrufen von Abonnement Informationen definiert.  
 Für ein datengesteuertes Abonnement muss eine Abfrage oder ein Befehl zum Abrufen von Abonnentendaten angegeben werden. Die Abfrage sollte pro Abonnent eine Zeile generieren. Falls Sie die E-Mail-Übermittlungserweiterung verwenden, sollte die Abfrage für jeden Abonnenten einen gültigen E-Mail-Alias zurückgeben. Die Anzahl von durchgeführten Übermittlungen basiert auf der Anzahl der von der Abfrage zurückgegebenen Zeilen. Besteht das Rowset aus 10.000 Zeilen, übermittelt das Abonnement 10.000 Berichte.  
  
 Wenn die Ausführung der Abfrage zeitaufwändig ist, können Sie den Timeoutwert erhöhen, um eine schnellere Verarbeitung zu ermöglichen.  
  
 Für diesen Schritt muss die Abfrage überprüft werden. Erst dann können Sie den Vorgang fortsetzen. Bei der Überprüfung wird die Abfrage nicht verarbeitet, es wird jedoch eine Liste aller Spalten im Rowset zurückgegeben, sodass Sie später auf diese Spalten verweisen können. Falls die Überprüfung der Abfrage fehlschlägt, können Sie den Vorgang nicht fortsetzen. Dies ist der Fall, wenn die Verbindung zur Datenquelle ungültig ist oder die Abfragesyntax fehlerhaft ist. Klicken Sie auf die Schaltfläche **Zurück** , um die Angaben zur Datenquelle zu korrigieren.  
  
##  <a name="run-a-subscription"></a><a name="bkmk_run_subscription"></a>Ausführen eines Abonnements  
 Konfigurieren Sie die Bedingungen für die Abonnementausführung. Sie können einen Zeitplan konfigurieren, oder mit den Updates einer Momentaufnahme zur Berichtsausführung die Verarbeitung des Abonnements auslösen.  
  
 ![Hinweis](../media/rs-fyinote.png "Hinweis") Es gibt zwar keine Funktion in der Benutzeroberfläche, die Sie zum sofortigen Ausführen eines Abonnements verwenden können, aber Sie können ein einfaches Windows PowerShell-Skript verwenden, um die Ausführung eines Abonnements zu initiieren. Weitere Informationen finden Sie im Abschnitt "Skript: ausführen (auslösen) eines einzelnen Abonnements" unter [Verwenden von PowerShell zum Ändern und auflisten Reporting Services Abonnement Besitzern und Ausführen eines Abonnements](manage-subscription-owners-and-run-subscription-powershell.md).  
  
 Zeitplan und Bedingungen für die Ausführung datengesteuerter Abonnements sind mit der Verarbeitung von Standardabonnements identisch.  
  
##  <a name="manage-and-delete-a-data-driven-subscription"></a><a name="bkmk_manage_and_delete"></a>Verwalten und Löschen eines datengesteuerten Abonnements  
 Ein datengesteuertes Abonnement, das gerade verarbeitet wird, kann auf der Seite Aufträge verwalten des Berichts-Managers nicht beendet oder gelöscht werden. Aus diesem Grund ist es vorteilhaft, einen freigegebenen Zeitplan zu verwenden, um ein datengesteuertes Abonnement auszulösen. Falls Sie die Verarbeitung eines Abonnements vorübergehend unterbinden möchten, können Sie den Zeitplan anhalten, mit dem das Abonnement ausgelöst wird. Weitere Informationen finden Sie unter [Erstellen und Verwalten von Abonnements für Berichtsserver im einheitlichen Modus](../create-manage-subscriptions-native-mode-report-servers.md).  
  
 Um ein datengesteuertes Abonnement zu löschen, wählen Sie dieses auf der Seite „Meine Abonnements“ oder auf der Seite „Abonnements“ aus, und klicken Sie anschließend auf **Löschen**.  
  
 Anweisungen zum Abbrechen eines datengesteuerten Abonnements finden Sie unter [Verwalten eines ausgeführten Prozesses](manage-a-running-process.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Standard Abonnements &#40;Reporting Services im einheitlichen Modus erstellen, ändern und löschen&#41;](create-and-manage-subscriptions-for-native-mode-report-servers.md)   
 [Abonnements und Übermittlung &#40;Reporting Services&#41;](subscriptions-and-delivery-reporting-services.md)   
 [Berichts-Manager &#40;einheitlicher SSRS-Modus&#41;](../report-manager-ssrs-native-mode.md)   
 [Erstellen und Verwalten von Abonnements für Berichtsserver im einheitlichen Modus](../create-manage-subscriptions-native-mode-report-servers.md)   
 [Die Seite "Abonnements" &#40;Berichts-Manager&#41;](../subscriptions-page-report-manager.md)   
 [Meine Abonnements (Seite) (Berichts-Manager)](../my-subscriptions-page-report-manager.md)  
  
  
