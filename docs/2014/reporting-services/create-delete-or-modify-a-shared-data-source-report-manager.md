---
title: Erstellen, löschen oder Ändern einer freigegebenen Datenquelle (Berichts-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- shared data sources [Reporting Services]
- removing shared data sources
- data sources [Reporting Services], shared
- deleting shared data sources
- modifying shared data sources
ms.assetid: cd7bace3-f8ec-4ee3-8a9f-2f217cdca9f2
caps.latest.revision: 47
author: maggiesmsft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e48edf78d8b0a73c01871b47ac24fa1f0bf8babb
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37202690"
---
# <a name="create-delete-or-modify-a-shared-data-source-report-manager"></a>Erstellen, Löschen oder Ändern einer freigegebenen Datenquelle (Berichts-Manager)
  Mit einer freigegebenen Datenquelle werden Verbindungseigenschaften für eine Datenquelle angegeben. Falls Sie über eine Datenquelle verfügen, die von einer großen Anzahl Berichte, Modelle oder datengesteuerter Abonnements verwendet wird, sollten Sie die Erstellung einer freigegebenen Datenquelle in Erwägung ziehen, um den Aufwand für die Pflege der Verbindungsinformationen an mehreren Stellen zu verringern.  
  
 Das folgende Symbol bezeichnet eine freigegebene Datenquelle in der Ordnerhierarchie des Berichts-Managers:  
  
 ![Symbol freigegebene Datenquelle](media/hlp-16datasource.png "Shared data source icon")  
Symbol für freigegebene Datenquelle  
  
### <a name="to-create-a-shared-data-source"></a>So erstellen Sie eine freigegebene Datenquelle  
  
1.  Starten Sie [Berichts-Manager &#40;einheitlicher SSRS-Modus&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md).  
  
2.  Navigieren Sie im Berichts-Manager zur Seite **Inhalt** .  
  
3.  Klicken Sie auf **Neue Datenquelle**. Die Seite **Neue Datenquelle** wird geöffnet.  
  
4.  Geben Sie einen Namen für das Element ein. Ein Name muss mindestens ein Zeichen enthalten und muss mit einem Buchstaben beginnen. Er kann auch Sonderzeichen enthalten, er darf jedoch keine Leerzeichen und folgende Zeichen nicht enthalten: ; ? : @ & = +, $ / * \< > | " /.  
  
5.  Optional können Sie auch eine Beschreibung eingeben, um Benutzern Informationen zur Verbindung bereitzustellen. Diese Beschreibung wird auf der Seite **Inhalt** im Berichts-Manager angezeigt.  
  
6.  Geben Sie in der Liste **Datenquellentyp** die Datenverarbeitungserweiterung an, die zum Verarbeiten von Daten aus der Datenquelle verwendet wird.  
  
7.  Geben Sie in das Feld **Verbindungszeichenfolge**die Verbindungszeichenfolge an, die vom Berichtsserver zum Herstellen der Verbindung zur Datenquelle verwendet wird. Es wird empfohlen, dass Sie keine Anmeldeinformationen in der Verbindungszeichenfolge angeben.  
  
     Das folgende Beispiel zeigt eine Verbindungszeichenfolge für die Verbindung mit der lokalen [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] Datenbank:  
  
    ```  
    data source=<localservername>; initial catalog=AdventureWorks2012  
    ```  
  
8.  Geben Sie für **Verbindung herstellen über**an, wie die Anmeldeinformationen bei Ausführung des Berichts abgerufen werden:  
  
    -   Wenn der Benutzer zur Eingabe eines Anmeldenamens und eines Kennworts aufgefordert werden soll, klicken Sie auf **Bereitgestellte Anmeldeinformationen vom Benutzer, der den Bericht ausführt**. Klicken Sie auf **Beim Herstellen einer Verbindung mit der Datenquelle als Windows-Anmeldeinformationen verwenden**, um die vom Benutzer eingegebenen Anmeldeinformationen als Windows-Anmeldeinformationen zu verwenden. Wenn der Benutzername und das Kennwort Datenbank-Anmeldeinformationen darstellen, sollten Sie diese Option nicht aktivieren.  
  
    -   Wenn Sie die Datenquelle als freigegebene Datenquelle mit gespeicherten, vom Besitzer der Datenquelle verwalteten Anmeldeinformationen verwenden möchten bzw. für Berichte, die Abonnements oder andere geplante Vorgänge (z.B. automatisierte Berichtsverlaufgenerierung) unterstützen, klicken Sie auf **Anmeldeinformationen, die sicher auf dem Berichtsserver gespeichert sind**. Wenn der Datenbankserver Identitätswechsel oder Delegierung unterstützt, können Sie die Option **Die Identität des authentifizierten Benutzers annehmen, nachdem eine Verbindung zur Datenquelle hergestellt wurde**auswählen.  
  
    -   Wenn der Berichtsserver die Anmeldeinformationen des auf den Bericht zugreifenden Benutzers an den Server übergeben soll, der die externe Datenquelle hostet, klicken Sie auf **Integrierte Sicherheit von Windows**. In diesem Fall wird der Benutzer nicht aufgefordert, einen Benutzernamen oder ein Kennwort einzugeben.  
  
    -   Klicken Sie auf **Anmeldeinformationen sind nicht erforderlich**, wenn Sie eine Datenquelle verwenden, die nicht mit Anmeldeinformationen arbeitet (z.B. wenn es sich bei der Datenquelle um eine XML-Datei handelt, auf die vom Dateisystem zugegriffen wird). Diesen Typ Anmeldeinformationen sollten Sie nur dann angeben, wenn er von der Datenquelle unterstützt wird. Wenn Sie diese Option für eine Datenquelle aktivieren, die Authentifizierung erfordert, schlägt die Verbindungsherstellung fehl. Vergewissern Sie sich bei der Auswahl dieser Option, dass Sie das unbeaufsichtigte Ausführungskonto konfigurieren, mit dem der Berichtsserver eine Verbindung zu anderen Computern herstellen kann, um Daten oder Dateien abzurufen, wenn keine Anmeldeinformationen zur Verfügung stehen.  
  
     Weitere Informationen zum Konfigurieren von Anmeldeinformationen finden Sie unter [angeben der Anmeldeinformationen und Verbindungsinformationen für Berichtsdatenquellen-Verbindungen](report-data/specify-credential-and-connection-information-for-report-data-sources.md). Weitere Informationen zum Konto für die unbeaufsichtigte Ausführung finden Sie unter [Konfigurieren des unbeaufsichtigten Ausführungskontos (SSRS-Konfigurations-Manager)](install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md).  
  
9. Klicken Sie auf die Schaltfläche **Verbindung testen** , um die Datenquellenkonfiguration zu überprüfen.  
  
    > [!NOTE]  
    >  Die Schaltfläche zum Testen der Verbindung wird für den XML-Datenquellentyp nicht unterstützt.  
  
10. Klicken Sie auf **OK**.  
  
### <a name="to-modify-a-shared-data-source"></a>So ändern Sie eine freigegebene Datenquelle  
  
1.  Navigieren Sie im Berichts-Manager zur Seite Inhalt.  
  
2.  Navigieren Sie zum freigegebenen Datenquellenelement, zeigen Sie auf das Element, klicken Sie auf die Dropdownliste, und klicken Sie im Kontextmenü auf **Verwalten**. Die Seite **Eigenschaften** wird geöffnet.  
  
3.  Ändern Sie die Datenquelle, und klicken Sie anschließend auf **Anwenden**.  
  
### <a name="to-delete-a-shared-data-source"></a>So löschen Sie eine freigegebene Datenquelle  
  
-   Navigieren Sie im Berichts-Manager zur Seite **Inhalt** , und führen Sie eine der folgenden Aktionen aus:  
  
    -   Navigieren Sie zum Element der freigegebenen Datenquelle.  
  
         Klicken Sie auf das Element, um es zu öffnen. Die Seite Allgemeine Eigenschaften wird geöffnet.  
  
         Klicken Sie auf **Löschen**, und klicken Sie anschließend auf **OK**.  
  
    -   Navigieren Sie auf der Seite **Inhalt** zu dem Ordner, der die zu löschende Datenquelle enthält.  
  
         Zeigen Sie auf das Element, klicken Sie auf die Dropdownliste, und klicken Sie im Kontextmenü auf **Löschen**.  
  
         [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Datenverbindungen, Datenquellen und Verbindungszeichenfolgen in Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md)   
 [Inhalt der Seite &#40;Berichts-Manager&#41;](../../2014/reporting-services/contents-page-report-manager.md)   
 [Erstellen, ändern und Löschen von freigegebenen Datenquellen &#40;SSRS&#41;](report-data/create-modify-and-delete-shared-data-sources-ssrs.md)   
 [Verwalten von Berichtsdatenquellen](report-data/manage-report-data-sources.md)   
 [Konfigurieren von Datenquelleneigenschaften für einen Bericht &#40;Berichts-Manager&#41;](report-data/configure-data-source-properties-for-a-report-report-manager.md)  
  
  
