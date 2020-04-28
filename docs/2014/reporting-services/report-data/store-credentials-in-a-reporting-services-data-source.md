---
title: Speichern von Anmeldeinformationen in einer Reporting Services-Datenquelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/23/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- credentials [Reporting Services]
- security [Analysis Services], data sources
- stored credentials [Reporting Services]
- data sources [Reporting Services], stored credentials
ms.assetid: dc700922-97fa-4b30-9547-05bbbec4f09c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 74380cde599c965b64c0389f51df4dc51b54bdbf
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81388285"
---
# <a name="store-credentials-in-a-reporting-services-data-source"></a>Speichern von Anmeldeinformationen in einer Reporting Services-Datenquelle
  Sie können gespeicherte Anmeldeinformationen, mit denen ein [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] -Berichtsserver auf externe Daten für einen Bericht zugreift, konfigurieren. Gespeicherte Anmeldeinformationen werden verwendet, wenn der unbeaufsichtigt ausgeführt, beispielsweise bei einem [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] -Abonnement, das einen Bericht als E-Mail veröffentlicht. Der Berichtsserver ruft die Anmeldeinformationen ab und verwendet sie, wenn die Berichtsverarbeitung geplant oder ausgelöst wird. In diesem Thema werden die einzelnen Schritte für die Konfiguration gespeicherter Anmeldeinformationen für Berichtsserver im einheitlichen Modus und im SharePoint-Modus dargestellt.

||
|-|
|**[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] im einheitlichen Modus &#124; [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] im SharePoint-Modus|

 **In diesem Thema:**

-   [Konfigurieren von gespeicherten Anmeldeinformationen für eine berichtsspezifische Datenquelle (einheitlicher Modus)](#bkmk_stored_credentials_data_source_native)

-   [Konfigurieren von gespeicherten Anmeldeinformationen für eine berichtsspezifische Datenquelle (SharePoint-Modus)](#bkmk_stored_credentials_data_source_sharepoint)

-   [Konfigurieren von gespeicherten Anmeldeinformationen für eine freigegebene Datenquelle (einheitlicher Modus)](#bkmk_stored_credentials_shared_data_source_native)

-   [Konfigurieren von gespeicherten Anmeldeinformationen für eine freigegebene Datenquelle (SharePoint-Modus)](#bkmk_stored_credentials_shared_data_source_sharepoint)

##  <a name="security-policy-requirements-for-stored-credentials"></a><a name="bkmk_top"></a>Sicherheitsrichtlinien Anforderungen für gespeicherte Anmelde Informationen
 ![as_powerpivot_refresh_sss_set_key](../../analysis-services/media/as-powerpivot-refresh-sss-set-key.gif "as_powerpivot_refresh_sss_set_key") Für das Konto, das Sie für gespeicherte Anmeldeinformationen verwenden, muss eine der folgenden Sicherheitsrichtlinien auf dem Berichtsserver konfiguriert sein. Es wird empfohlen, dass Sie die Richtlinie mit den mindestens erforderlichen Berechtigungen für Ihre Umgebung auswählen.

1.  **Lokale Anmeldung zulassen** Weitere Informationen finden Sie unter [Lokal anmelden zulassen](https://technet.microsoft.com/library/cc756809\(v=WS.10\).aspx).

2.  **Anmelden als Stapelverarbeitungsauftrag**. Weitere Informationen finden Sie unter [Anmelden als Stapelverarbeitungsauftrag](https://technet.microsoft.com/library/cc755659\(v=ws.10\).aspx).

3.  Allgemeine Informationen zu Richtlinien finden Sie unter [Bearbeiten von Sicherheitseinstellungen für ein Gruppenrichtlinienobjekt](https://technet.microsoft.com/library/cc736516\(v=ws.10\).aspx).

##  <a name="configure-stored-credentials-for-a-report-specific-data-source-native-mode"></a><a name="bkmk_stored_credentials_data_source_native"></a>Konfigurieren gespeicherter Anmelde Informationen für eine Berichts spezifische Datenquelle (einheitlicher Modus)

1.  Navigieren Sie im Berichts-Manager im einheitlichen Modus zu dem Ordner, der den Bericht enthält. Klicken Sie ![im Berichts-Manager für SSRS-Elemente](../media/ssrs-report-manager-item-context-menu.png "Kontextmenü im Berichts-Manager für SSRS-Elemente")auf das Kontextmenü Element Kontextmenü.

2.  Klicken Sie auf **Verwalten** und dann auf **Datenquellen**.

3.  Wählen Sie **Eine benutzerdefinierte Datenquelle**.

4.  Wählen Sie in der Liste **Datenquellentyp** die Datenverarbeitungserweiterung aus, die zum Verarbeiten von Daten aus der Datenquelle verwendet wird.

5.  Geben Sie für **Verbindungs Zeichenfolge**die Verbindungs Zeichenfolge an, die der Berichts Server zum Herstellen einer Verbindung mit der Datenquelle verwendet. Das folgende Beispiel veranschaulicht eine Verbindungs Zeichenfolge zum Herstellen einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] Verbindung mit der-Datenbank:

    ```
    data source=<servername>;initial catalog=AdventureWorks2012
    ```

6.  Wählen Sie für **Verbindung herstellen über**die Option **Anmeldeinformationen, die sicher auf dem Berichtsserver gespeichert sind**aus.

7.  Geben Sie einen Benutzernamen und ein Kennwort ein.

    -   Wenn das Konto ein Windows-Domänen Benutzerkonto ist, geben Sie es im \<folgenden Format \\ an:\>Domäne><Konto, und wählen Sie dann **beim Herstellen einer Verbindung mit der Datenquelle als Windows-Anmelde Informationen verwenden aus.**

    -   Wenn Benutzername und Kennwort Datenbank-Anmeldeinformationen sind, wählen Sie **Beim Herstellen einer Verbindung mit der Datenquelle als Windows-Anmeldeinformationen verwenden**nicht aus. Wenn der Datenbankserver Identitätswechsel oder Delegierung unterstützt, können Sie die Option **Die Identität des authentifizierten Benutzers annehmen, nachdem eine Verbindung zur Datenquelle hergestellt wurde**auswählen.

8.  Klicken Sie auf **Anwenden**.

     ![Pfeilsymbol mit Rückverweis auf den Seitenanfang](../../2014-toc/media/uparrow16x16.gif "Pfeilsymbol, das mit dem Link „Zurück zum Anfang“ verwendet wird") [Anforderungen an Sicherheitsrichtlinien für gespeicherte Anmeldeinformationen](#bkmk_top)

##  <a name="configure-stored-credentials-for-a-report-specific-data-source-sharepoint-mode"></a><a name="bkmk_stored_credentials_data_source_sharepoint"></a>Konfigurieren gespeicherter Anmelde Informationen für eine Berichts spezifische Datenquelle (SharePoint-Modus)

1.  Rufen Sie die Dokumentbibliothek mit dem Bericht auf, und klicken Sie anschließend auf das offene Menü ![Kontextmenü der Dokumentbibliothek für SSRS-Elemente](../media/ssrs-sharepoint-item-context-menu.png "Kontextmenü der Dokumentbibliothek für SSRS-Elemente").

2.  Klicken Sie erst auf das zweite offene Menü ![Kontextmenü der Dokumentbibliothek für SSRS-Elemente](../media/ssrs-sharepoint-item-context-menu.png "Kontextmenü der Dokumentbibliothek für SSRS-Elemente") und anschließend auf **Datenquellen verwalten**.

3.  Klicken Sie auf den Namen der **benutzerdefinierten** Datenquelle, die Sie mit gespeicherten Anmeldeinformationen konfigurieren möchten.

4.  Wählen Sie in der Liste **Datenquellentyp** die Datenverarbeitungserweiterung aus, die zum Verarbeiten von Daten aus der Datenquelle verwendet wird.

5.  Geben Sie für **Verbindungs Zeichenfolge**die Verbindungs Zeichenfolge an, die der Berichts Server zum Herstellen einer Verbindung mit der Datenquelle verwendet. Das folgende Beispiel veranschaulicht eine Verbindungs Zeichenfolge zum Herstellen einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] Verbindung mit der-Datenbank:

    ```
    data source=<servername>;initial catalog=AdventureWorks2012
    ```

6.  Wählen Sie für **Anmelde**Informationen die Option **gespeicherte Anmelde**Informationen aus.

7.  Geben Sie einen **Benutzernamen** und ein **Kennwort**ein.

    -   Wenn das Konto ein Windows-Domänen Benutzerkonto ist, geben Sie es im \<folgenden Format \\ an:\>Domäne><Konto, und wählen Sie dann **beim Herstellen einer Verbindung mit der Datenquelle als Windows-Anmelde Informationen verwenden aus.**

    -   Wenn der Benutzername und das Kennwort Datenbankanmeldeinformationen sind, wählen Sie nicht **Als Windows-Anmeldeinformationen verwenden**aus. Wenn der Datenbankserver Identitätswechsel oder Delegierung unterstützt, wählen Sie ggf. die Option **Ausführungskontext für dieses Konto festlegen**aus.

8.  Klicken Sie auf **OK**.

     ![Pfeilsymbol mit Rückverweis auf den Seitenanfang](../../2014-toc/media/uparrow16x16.gif "Pfeilsymbol, das mit dem Link „Zurück zum Anfang“ verwendet wird") [Anforderungen an Sicherheitsrichtlinien für gespeicherte Anmeldeinformationen](#bkmk_top)

##  <a name="configure-stored-credentials-for-a-shared-data-source-native-mode"></a><a name="bkmk_stored_credentials_shared_data_source_native"></a>Konfigurieren gespeicherter Anmelde Informationen für eine freigegebene Datenquelle (einheitlicher Modus)

1.  Navigieren Sie im Berichts-Manager im einheitlichen Modus zum freigegebenen Datenquellenelement. ![Symbol für freigegebene Datenquelle](../media/hlp-16datasource.png "Symbol für freigegebene Datenquelle")

2.  Klicken Sie ![im Berichts-Manager für SSRS-Elemente](../media/ssrs-report-manager-item-context-menu.png "Kontextmenü im Berichts-Manager für SSRS-Elemente") auf das Kontextmenü Kontextmenü, und klicken Sie dann auf **Verwalten**.

3.  Geben Sie in der Liste **Daten Quellentyp** die Datenverarbeitungs Erweiterung an, die zum Verarbeiten von Daten aus der Datenquelle verwendet wird.

4.  Geben Sie für **Verbindungs Zeichenfolge**die Verbindungs Zeichenfolge an, die der Berichts Server zum Herstellen einer Verbindung mit der Datenquelle verwendet. [!INCLUDE[msCoName](../../../includes/msconame-md.md)] empfiehlt, dass Sie keine Anmeldeinformationen in der Verbindungszeichenfolge angeben.

     Das folgende Beispiel veranschaulicht eine Verbindungs Zeichenfolge, die zum Herstellen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] einer Verbindung mit der lokalen Datenbank verwendet wird:

    ```
    data source=<localservername>; initial catalog=AdventureWorks2012
    ```

5.  Geben Sie einen Benutzernamen und ein Kennwort ein.

    -   Wenn das Konto ein Windows-Domänen Benutzerkonto ist, geben Sie es im \<folgenden Format \\ an:\>Domäne><Konto, und wählen Sie dann **beim Herstellen einer Verbindung mit der Datenquelle als Windows-Anmelde Informationen verwenden aus.**

    -   Wenn Benutzername und Kennwort Datenbank-Anmeldeinformationen sind, wählen Sie **Beim Herstellen einer Verbindung mit der Datenquelle als Windows-Anmeldeinformationen verwenden**nicht aus. Wenn der Datenbankserver Identitätswechsel oder Delegierung unterstützt, können Sie die Option **Die Identität des authentifizierten Benutzers annehmen, nachdem eine Verbindung zur Datenquelle hergestellt wurde**auswählen.

6.  Klicken Sie auf **Anwenden**.

     ![Pfeilsymbol mit Rückverweis auf den Seitenanfang](../../2014-toc/media/uparrow16x16.gif "Pfeilsymbol, das mit dem Link „Zurück zum Anfang“ verwendet wird") [Anforderungen an Sicherheitsrichtlinien für gespeicherte Anmeldeinformationen](#bkmk_top)

##  <a name="configure-stored-credentials-for-a-shared-data-source-sharepoint-mode"></a><a name="bkmk_stored_credentials_shared_data_source_sharepoint"></a>Konfigurieren gespeicherter Anmelde Informationen für eine freigegebene Datenquelle (SharePoint-Modus)

1.  Rufen Sie in der Dokumentbibliothek das freigegebene Datenquellelement auf. ![Freigegebenes Datenquellsymbol](../media/hlp-16datasource.png "Symbol für freigegebene Datenquelle")

2.  Klicken Sie erst auf das zweite offene Menü ![Kontextmenü der Dokumentbibliothek für SSRS-Elemente](../media/ssrs-sharepoint-item-context-menu.png "Kontextmenü der Dokumentbibliothek für SSRS-Elemente") und anschließend auf ![Datenquellen verwalten](../media/ssrs-sharepoint-item-context-menu.png "Kontextmenü der Dokumentbibliothek für SSRS-Elemente").

3.  Klicken Sie auf **Datenquellendefinition bearbeiten**.

4.  Geben Sie in der Liste **Daten Quellentyp** die Datenverarbeitungs Erweiterung an, die zum Verarbeiten von Daten aus der Datenquelle verwendet wird.

5.  Geben Sie für **Verbindungs Zeichenfolge**die Verbindungs Zeichenfolge an, die der Berichts Server zum Herstellen einer Verbindung mit der Datenquelle verwendet. [!INCLUDE[msCoName](../../../includes/msconame-md.md)] empfiehlt, dass Sie keine Anmeldeinformationen in der Verbindungszeichenfolge angeben.

     Das folgende Beispiel veranschaulicht eine Verbindungs Zeichenfolge, die zum Herstellen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] einer Verbindung mit der lokalen Datenbank verwendet wird:

    ```
    data source=<localservername>; initial catalog=AdventureWorks2012
    ```

6.  Geben Sie einen Benutzernamen und ein Kennwort ein.

    -   Wenn das Konto ein Windows-Domänen Benutzerkonto ist, geben Sie es im \<folgenden Format \\ an:\>Domäne><Konto, und wählen Sie dann **als Windows-Anmelde Informationen verwenden aus.**

    -   Wenn der Benutzername und das Kennwort Datenbankanmeldeinformationen sind, wählen Sie nicht **Als Windows-Anmeldeinformationen verwenden**aus. Wenn der Datenbankserver Identitätswechsel oder Delegierung unterstützt, können Sie die Option **Ausführungs Kontext für dieses Konto festlegen**auswählen.

7.  Klicken Sie auf **OK**.

     ![Pfeilsymbol mit Rückverweis auf den Seitenanfang](../../2014-toc/media/uparrow16x16.gif "Pfeilsymbol, das mit dem Link „Zurück zum Anfang“ verwendet wird") [Anforderungen an Sicherheitsrichtlinien für gespeicherte Anmeldeinformationen](#bkmk_top)

## <a name="see-also"></a>Weitere Informationen
 [Angeben von Anmelde Informationen und Verbindungsinformationen für Berichtsdaten Quellen](../../integration-services/connection-manager/data-sources.md) [Konfigurieren von Datenquellen Eigenschaften für einen Bericht &#40;Berichts-Manager&#41;](configure-data-source-properties-for-a-report-report-manager.md) [erstellen, löschen oder Ändern einer freigegebenen Datenquelle &#40;Berichts-Manager&#41;&#40;](../create-delete-or-modify-a-shared-data-source-report-manager.md) [Datenquellen Eigenschaften Seite](../data-sources-properties-page-report-manager.md) Berichts-Manager&#41;&#40;[Seite neue Datenquelle](../new-data-source-page-report-manager.md) Berichts-Manager&#41;


