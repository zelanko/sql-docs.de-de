---
title: Offlineinstallation früherer Versionen der SQL Server-Dokumentation
description: Erfahren Sie, wie Sie Offlinedokumentation für SQL Server 2019, 2017, 2016, 2014 und 2012 installieren können. Verwenden Sie SQL Server Management Studio (SSMS) zum Anzeigen der Offlineinhalte.
ms.prod: sql
ms.technology: ''
ms.topic: conceptual
ms.assetid: 51f8a08c-51d0-41d8-8bc5-1cb4d42622fb
author: markingmyname
ms.author: maghan
ms.date: 04/20/2020
ms.openlocfilehash: 1420e18fbf335e22d44bf78d526ab35c8b1434e5
ms.sourcegitcommit: c37777216fb8b464e33cd6e2ffbedb6860971b0d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2020
ms.locfileid: "82087870"
---
# <a name="install-previous-versions-of-sql-server-documentation-to-view-offline-in-ssms"></a>Installieren früherer Versionen der SQL Server-Dokumentation zur Offlineanzeige in SSMS

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In diesem Artikel wird beschrieben, wie Sie SQL Server-Offlineinhalte herunterladen und in [SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md) anzeigen. Mithilfe von Offlineinhalten können Sie ohne bestehende Internetverbindung auf die Dokumentation zugreifen (allerdings ist für den Download anfangs eine Internetverbindung erforderlich).

Offlinedokumentation ist für mehrere frühere Versionen von SQL Server verfügbar. Zwar lassen sich [Inhalte für frühere Versionen online](https://docs.microsoft.com/previous-versions/sql/) anzeigen, eine Offlineoption bietet jedoch ein komfortables Zugriffsverfahren für die älteren Inhalte.

## <a name="how-to-download-and-configure-offline-content"></a>Herunterladen und Konfigurieren von Offline Inhalten

Sie können SQL Server-Hilfepakete von Onlinequellen oder lokalen Datenträgern herunterladen und installieren. In den folgenden Abschnitten wird erläutert, wie Sie Offlineinhalte für verschiedene Versionen von SQL Server laden:

- [SQL Server 2019](#sql2019)
- [SQL Server 2017](#sql2017)
- [SQL Server 2016](#sql2016)
- [SQL Server 2014](#sql2014)
- [SQL Server 2012](#sql2012)

## <a name="sql-server-2019"></a><a id="sql2019"></a> SQL Server 2019

Führen Sie die folgenden Schritte aus, um die Offlinedokumentation für SQL Server 2019 zu laden.

1. Wählen Sie in SSMS im Menü „Hilfe“ **Hilfeinhalt hinzufügen und entfernen** aus.

   ![Hinzufügen und Entfernen von Inhalten in Help Viewer](../sql-server/media/sql-server-help-installation/add-remove-content.png)

   Help Viewer öffnet die Registerkarte „Inhalt verwalten“.

2. Um die neuesten Hilfeinhalte für SQL Server 2019 zu suchen, wählen Sie auf der Registerkarte **Inhalte verwalten** unter der Installationsquelle **Online** aus, und geben Sie dann in der Suchleiste *sql server 2019* ein.

   ![Suche nach SQL Server 2019-Dokumentation in Help Viewer](../sql-server/media/sql-server-help-installation/sql-2019-search.png)

   > [!Note]
   > Der lokale Speicherpfad auf der Registerkarte „Inhalt verwalten“ zeigt an, wo der Inhalt auf dem lokalen Computer installiert ist. Wenn Sie den Speicherort ändern möchten, wählen Sie **Verschieben** aus, geben Sie einen anderen Ordnerpfad im Feld **Nach** ein, und wählen Sie anschließend **OK** aus. Wenn die Installation der Hilfe nach dem Ändern des lokalen Speicherpfads fehlschlägt, müssen Sie Help Viewer schließen und anschließend wieder öffnen. Stellen Sie sicher, dass der neue Speicherort im lokalen Speicherpfad angezeigt wird, und versuchen Sie dann noch mal, die Installation durchzuführen.

3. Um die neuesten Hilfeinhalte für SQL Server 2019 zu installieren, wählen Sie neben jedem Inhaltspaket (Buch), das Sie installieren möchten, **Hinzufügen** aus, und wählen Sie dann in der unteren rechten Ecke **Aktualisieren** aus.

   ![Hinzufügen und Aktualisieren von SQL Server 2019-Büchern in Help Viewer](../sql-server/media/sql-server-help-installation/sql-2019-add-update.png)

   > [!NOTE]
   > Wenn Help Viewer beim Hinzufügen von Inhalt nicht mehr reagieren sollte, ändern Sie die Cachezeile „LastRefreshed=\<mm/dd/yyyy> 00:00:00“ in den Dateien „%LOCALAPPDATA%\Microsoft\HelpViewer2.x\HlpViewer_SSMSx_en-US.settings“ oder „HlpViewer_VisualStudiox_en-US.settings“ in ein Datum, das in der Zukunft liegt. Weitere Informationen zu diesem Problem finden Sie unter [Visual Studio Help Viewer friert beim Begrüßungsbildschirm ein](/visualstudio/welcome-to-visual-studio).

4. Sie können überprüfen, ob die SQL Server 2019-Inhalte geladen wurden, indem Sie im Inhaltsbereich links nach *sql server 2019* suchen.

   ![Automatische Aktualisierung von SQL Server 2019-Büchern](../sql-server/media/sql-server-help-installation/sql-2019-content.png)

## <a name="sql-server-2017"></a><a id="sql2017"></a> SQL Server 2017

Führen Sie die folgenden Schritte aus, um die Offlinedokumentation für SQL Server 2017 zu laden.

1. Wählen Sie in SSMS im Menü „Hilfe“ **Hilfeinhalt hinzufügen und entfernen** aus.

   ![Hinzufügen und Entfernen von Inhalten in Help Viewer](../sql-server/media/sql-server-help-installation/add-remove-content.png)

   Help Viewer öffnet die Registerkarte „Inhalt verwalten“.

2. Um die neuesten Hilfeinhalte für SQL Server 2017 zu suchen, wählen Sie auf der Registerkarte **Inhalte verwalten** unter der Installationsquelle **Online** aus, und geben Sie dann in der Suchleiste *sql server 2017* ein.

   ![Suche nach SQL Server 2017-Büchern in Help Viewer](../sql-server/media/sql-server-help-installation/sql-2017-search.png)

   > [!Note]
   > Der lokale Speicherpfad auf der Registerkarte „Inhalt verwalten“ zeigt an, wo der Inhalt auf dem lokalen Computer installiert ist. Wenn Sie den Speicherort ändern möchten, wählen Sie **Verschieben** aus, geben Sie einen anderen Ordnerpfad im Feld **Nach** ein, und wählen Sie anschließend **OK** aus. Wenn die Installation der Hilfe nach dem Ändern des lokalen Speicherpfads fehlschlägt, müssen Sie Help Viewer schließen und anschließend wieder öffnen. Stellen Sie sicher, dass der neue Speicherort im lokalen Speicherpfad angezeigt wird, und versuchen Sie dann noch mal, die Installation durchzuführen.

3. Um die neuesten Hilfeinhalte für SQL Server 2017 zu installieren, wählen Sie neben jedem Inhaltspaket (Buch), das Sie installieren möchten, **Hinzufügen** aus, und wählen Sie dann in der unteren rechten Ecke **Aktualisieren** aus.

   ![Hinzufügen und Aktualisieren von SQL Server 2017-Büchern in Help Viewer](../sql-server/media/sql-server-help-installation/sql-2017-add-update.png)

   > [!NOTE]
   > Wenn Help Viewer beim Hinzufügen von Inhalt nicht mehr reagieren sollte, ändern Sie die Cachezeile „LastRefreshed=\<mm/dd/yyyy> 00:00:00“ in den Dateien „%LOCALAPPDATA%\Microsoft\HelpViewer2.x\HlpViewer_SSMSx_en-US.settings“ oder „HlpViewer_VisualStudiox_en-US.settings“ in ein Datum, das in der Zukunft liegt. Weitere Informationen zu diesem Problem finden Sie unter [Visual Studio Help Viewer friert beim Begrüßungsbildschirm ein](/visualstudio/welcome-to-visual-studio).

4. Sie können überprüfen, ob die SQL Server 2017-Inhalte geladen wurden, indem Sie im Inhaltsbereich links nach *sql server 2017* suchen.

   ![Automatische Aktualisierung von SQL Server 2017-Büchern](../sql-server/media/sql-server-help-installation/sql-2017-content.png)

## <a name="sql-server-2016"></a><a id="sql2016"></a> SQL Server 2016

Führen Sie die folgenden Schritte aus, um die Offlinedokumentation für SQL Server 2016 zu laden.

1. Wählen Sie in SSMS im Menü „Hilfe“ **Hilfeinhalt hinzufügen und entfernen** aus.

   ![Hinzufügen und Entfernen von Inhalten in Help Viewer](../sql-server/media/sql-server-help-installation/add-remove-content.png)

   Help Viewer öffnet die Registerkarte „Inhalt verwalten“.

2. Um die neuesten Hilfeinhalte für SQL Server 2016 zu suchen, wählen Sie auf der Registerkarte **Inhalte verwalten** unter der Installationsquelle **Online** aus, und geben Sie dann in der Suchleiste *sql server 2016* ein.

   ![Suche nach SQL Server 2016-Büchern in Help Viewer](../sql-server/media/sql-server-help-installation/sql-2016-search.png)

   > [!Note]
   > Der lokale Speicherpfad auf der Registerkarte „Inhalt verwalten“ zeigt an, wo der Inhalt auf dem lokalen Computer installiert ist. Wenn Sie den Speicherort ändern möchten, wählen Sie **Verschieben** aus, geben Sie einen anderen Ordnerpfad im Feld **Nach** ein, und wählen Sie anschließend **OK** aus. Wenn die Installation der Hilfe nach dem Ändern des lokalen Speicherpfads fehlschlägt, müssen Sie Help Viewer schließen und anschließend wieder öffnen. Stellen Sie sicher, dass der neue Speicherort im lokalen Speicherpfad angezeigt wird, und versuchen Sie dann noch mal, die Installation durchzuführen.

3. Um die neuesten Hilfeinhalte für SQL Server 2016 zu installieren, wählen Sie neben jedem Inhaltspaket (Buch), das Sie installieren möchten, **Hinzufügen** aus, und wählen Sie dann in der unteren rechten Ecke **Aktualisieren** aus.

   ![Hinzufügen und Aktualisieren von SQL Server 2016-Büchern in Help Viewer](../sql-server/media/sql-server-help-installation/sql-2016-add-update.png)

   > [!NOTE]
   > Wenn Help Viewer beim Hinzufügen von Inhalt nicht mehr reagieren sollte, ändern Sie die Cachezeile „LastRefreshed=\<mm/dd/yyyy> 00:00:00“ in den Dateien „%LOCALAPPDATA%\Microsoft\HelpViewer2.x\HlpViewer_SSMSx_en-US.settings“ oder „HlpViewer_VisualStudiox_en-US.settings“ in ein Datum, das in der Zukunft liegt. Weitere Informationen zu diesem Problem finden Sie unter [Visual Studio Help Viewer friert beim Begrüßungsbildschirm ein](/visualstudio/welcome-to-visual-studio).

4. Sie können überprüfen, ob die SQL Server 2016-Inhalte geladen wurden, indem Sie im Inhaltsbereich links nach *sql server 2016* suchen.

   ![Automatische Aktualisierung von SQL Server 2016-Büchern](../sql-server/media/sql-server-help-installation/sql-2016-content.png)

## <a name="sql-server-2014"></a><a id="sql2014"></a> SQL Server 2014

Führen Sie die folgenden Schritte aus, um die Offlinedokumentation für SQL Server 2014 zu laden.

1. Laden Sie den Inhalt [Produktdokumentation für Microsoft SQL Server 2014 für firewall- und proxygeschützte Umgebungen](https://www.microsoft.com/download/details.aspx?id=42557) aus dem Downloadcenter herunter, und speichern Sie ihn in einem Ordner.

2. Entzippen Sie die Datei, um die MSHA-Datei anzuzeigen.

   ![Setupdatei der SQL Server 2014-Hilfedokumentation](../sql-server/media/sql-server-help-installation/sql-2014-help-content-setup-msha.png)

3. Wählen Sie in SSMS im Menü „Hilfe“ **Hilfeinhalt hinzufügen und entfernen** aus.

   ![Hinzufügen und Entfernen von Inhalten in Help Viewer](../sql-server/media/sql-server-help-installation/add-remove-content.png)

   Help Viewer öffnet die Registerkarte „Inhalt verwalten“.

4. Wählen Sie unter „Installationsquelle“ **Datenträger**, um die neuesten Hilfeinhalte zu installieren, und anschließend die Auslassungspunkte (...) aus.

   ![Quelle „Datenträger“ in Help Viewer – Inhalte verwalten](../sql-server/media/sql-server-help-installation/install-source-disk.png)

   > [!NOTE]
   > Der lokale Speicherpfad auf der Registerkarte „Inhalt verwalten“ zeigt an, wo sich der Inhalt auf dem lokalen Computer befindet. Wenn Sie den Speicherort ändern möchten, wählen Sie **Verschieben** aus, geben Sie einen anderen Ordnerpfad im Feld **Nach** ein, und wählen Sie anschließend **OK** aus.
   Wenn die Installation der Hilfe nach dem Ändern des lokalen Speicherpfads fehlschlägt, müssen Sie Help Viewer schließen und anschließend wieder öffnen. Stellen Sie sicher, dass der neue Speicherort im lokalen Speicherpfad angezeigt wird, und versuchen Sie dann noch mal, die Installation durchzuführen.

5. Navigieren Sie zu dem Ordner, in dem Sie die Inhalte entzippt haben. Wählen Sie die Datei **HelpContentSetup.msha** im Ordner und anschließend **Öffnen** aus.

   ![Öffnen der Datei „SQL Server 2014 Help Content Setup.msha“](../sql-server/media/sql-server-help-installation/sql-2014-open-msha.png)

6. Geben Sie in der Suchleiste *sql server 2014* ein. Wenn Sie die verfügbaren 2014-Inhalte sehen, wählen Sie neben jedem einzelnen Inhaltspaket (Buch), das Sie in Help Viewer installieren möchten, **Hinzufügen**, und wählen Sie dann **Aktualisieren** aus.

   ![Suche nach SQL Server 2014-Büchern in Help Viewer](../sql-server/media/sql-server-help-installation/sql-2014-search.png)

   ![Hinzufügen und Aktualisieren von SQL Server 2014-Büchern in Help Viewer](../sql-server/media/sql-server-help-installation/sql-2014-add-update.png)

    > [!NOTE]
    > Wenn Help Viewer beim Hinzufügen von Inhalt nicht mehr reagieren sollte, ändern Sie die Cachezeile „LastRefreshed=\<mm/dd/yyyy> 00:00:00“ in den Dateien „%LOCALAPPDATA%\Microsoft\HelpViewer2.x\HlpViewer_SSMSx_en-US.settings“ oder „HlpViewer_VisualStudiox_en-US.settings“ in ein Datum, das in der Zukunft liegt. Weitere Informationen zu diesem Problem finden Sie unter [Visual Studio Help Viewer friert beim Begrüßungsbildschirm ein](/visualstudio/welcome-to-visual-studio).

7. Sie können überprüfen, ob die SQL Server 2014-Inhalte installiert wurden, indem Sie im Inhaltsbereich links nach *sql server 2014* suchen.

   ![Automatische Aktualisierung von SQL Server 2014-Büchern](../sql-server/media/sql-server-help-installation/sql-2014-content.png)

## <a name="sql-server-2012"></a><a id="sql2012"></a> SQL Server 2012

Führen Sie die folgenden Schritte aus, um die Offlinedokumentation für SQL Server 2012 zu laden.

1. Laden Sie den Inhalt [Produktdokumentation für Microsoft SQL Server 2012 für firewall- und proxygeschützte Umgebungen](https://www.microsoft.com/download/details.aspx?id=35750) aus dem Downloadcenter herunter, und speichern Sie ihn in einem Ordner.

2. Entzippen Sie die Datei, um die MSHA-Datei anzuzeigen.

   ![Setupdatei für SQL Server 2012-Hilfeinhalte](../sql-server/media/sql-server-help-installation/sql-2012-help-content-setup-msha.png)

3. Wählen Sie in SSMS im Menü „Hilfe“ **Hilfeinhalt hinzufügen und entfernen** aus.

   ![Hinzufügen und Entfernen von Inhalten in Help Viewer](../sql-server/media/sql-server-help-installation/add-remove-content.png)

   Help Viewer öffnet die Registerkarte „Inhalt verwalten“.

4. Wählen Sie unter „Installationsquelle“ **Datenträger**, um die neuesten Hilfeinhalte zu installieren, und anschließend die Auslassungspunkte (...) aus.

   ![Quelle „Datenträger“ in Help Viewer – Inhalte verwalten](../sql-server/media/sql-server-help-installation/install-source-disk.png)

   > [!NOTE]
   > Der lokale Speicherpfad auf der Registerkarte „Inhalt verwalten“ zeigt an, wo sich der Inhalt auf dem lokalen Computer befindet. Wenn Sie den Speicherort ändern möchten, wählen Sie **Verschieben** aus, geben Sie einen anderen Ordnerpfad im Feld **Nach** ein, und wählen Sie anschließend **OK** aus.
   Wenn die Installation der Hilfe nach dem Ändern des lokalen Speicherpfads fehlschlägt, müssen Sie Help Viewer schließen und anschließend wieder öffnen. Stellen Sie sicher, dass der neue Speicherort im lokalen Speicherpfad angezeigt wird, und versuchen Sie dann noch mal, die Installation durchzuführen.

5. Navigieren Sie zu dem Ordner, in dem Sie die Inhalte entzippt haben. Wählen Sie die Datei **HelpContentSetup.msha** im Ordner und anschließend **Öffnen** aus.

   ![Öffnen der Datei „SQL Server 2012 Help Content Setup.msha“](../sql-server/media/sql-server-help-installation/sql-2012-open-msha.png)

6. Geben Sie in der Suchleiste *sql server 2012* ein. Wenn Sie die verfügbaren 2012-Inhalte sehen, wählen Sie neben jedem einzelnen Inhaltspaket (Buch), das Sie in Help Viewer installieren möchten, **Hinzufügen**, und wählen Sie dann **Aktualisieren** aus.

   ![Suche nach SQL Server 2012-Büchern in Help Viewer](../sql-server/media/sql-server-help-installation/sql-2012-search.png)

   ![Hinzufügen und Aktualisieren von SQL Server 2012-Büchern in Help Viewer](../sql-server/media/sql-server-help-installation/sql-2012-add-update.png)

    > [!NOTE]
    > Wenn Help Viewer beim Hinzufügen von Inhalt nicht mehr reagieren sollte, ändern Sie die Cachezeile „LastRefreshed=\<mm/dd/yyyy> 00:00:00“ in den Dateien „%LOCALAPPDATA%\Microsoft\HelpViewer2.x\HlpViewer_SSMSx_en-US.settings“ oder „HlpViewer_VisualStudiox_en-US.settings“ in ein Datum, das in der Zukunft liegt. Weitere Informationen zu diesem Problem finden Sie unter [Visual Studio Help Viewer friert beim Begrüßungsbildschirm ein](/visualstudio/welcome-to-visual-studio).

7. Sie können überprüfen, ob die SQL Server 2012-Inhalte geladen wurden, indem Sie im Inhaltsbereich links nach *sql server 2012* suchen.

   ![Automatisch aktualisierte SQL Server 2012-Dokumentation](../sql-server/media/sql-server-help-installation/sql-2012-content.png)

## <a name="view-offline-documentation"></a>Anzeigen der Offlinedokumentation

Sie können SQL Server-Hilfeinhalte über das Menü **HILFE** in der letzten Version von [SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md) anzeigen.

### <a name="view-offline-help-content-in-ssms"></a>Anzeigen von Offline-Hilfeinhalten in SSMS

Um die installierte Hilfe in SSMS anzuzeigen, wählen Sie im Menü „Hilfe“ **In Help Viewer starten** aus, um den Help Viewer zu starten.

   ![In Help Viewer starten](../sql-server/media/sql-server-help-installation/helpviewer-view-offline.png)  

Help Viewer öffnet sich auf der Registerkarte „Inhalt verwalten“ mit dem installierten Inhaltsverzeichnis für die Hilfe im linken Bereich. Wählen Sie im Inhaltsverzeichnis Artikel aus, um diese auf der rechten Seite anzuzeigen.

> [!TIP]
> Wenn der Inhaltsbereich nicht angezeigt wird, wählen Sie auf der linken Seite „Inhalt“ aus. Wählen Sie das Reißzweckensymbol aus, damit der Inhaltsbereich geöffnet bleibt.  

   ![Help Viewer mit Inhalt](../sql-server/media/sql-server-help-installation/view-offline-all.png)

## <a name="life-cycle-policy"></a>Lebenszyklusrichtlinie

Lesen Sie den Microsoft-Produktlebenszyklus durch, um Informationen zum Support für ein bestimmtes Produkt, einen Dienst oder eine Technologie zu erhalten:

- [Microsoft-Lebenszyklusrichtlinie](https://support.microsoft.com/lifecycle/selectindex)

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu archivierten Inhalten und zu Help Viewer finden Sie unter den Links unten.

- [Direkter Link zu früheren Versionen der SQL Server-Dokumentation](https://docs.microsoft.com/previous-versions/sql/)
- [Microsoft Help Viewer – Visual Studio](https://docs.microsoft.com/visualstudio/help-viewer/overview)
- [SQL Server-Dokumentation, starten](../sql-server/index.yml?view=sql-server-2016)
- [Versionsverwaltungssystem für die SQL-Dokumentation](../sql-server/versioning-system-monikers-ui-sql-server.md?view=sql-server-2016)