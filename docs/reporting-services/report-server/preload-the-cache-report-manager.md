---
title: Vorabladen des Caches (SSRS)| Microsoft-Dokumentation
ms.date: 05/14/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server
ms.topic: conceptual
helpviewer_keywords:
- cache [Reporting Services]
- preloading cache
ms.assetid: 152a1051-8aa5-4c01-bc85-f8be8971b0cd
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 6b2be1e020354f47aa21dc83f17ff6169bcf2d72
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "66175000"
---
# <a name="preload-the-cache"></a>Vorabladen des Caches  
  Sie können den Cache für ein freigegebenes Dataset vorab laden, indem Sie einen Cacheaktualisierungsplan für das freigegebene Dataset erstellen.  
  
 Sie können den Cache für einen Bericht in die zwei Weisen vorab laden:  
  
1.  Erstellen Sie einen Cacheaktualisierungsplan für den Bericht. Dies ist die bevorzugte Methode.  
  
2.  Verwenden Sie ein datengesteuertes Abonnement zum Vorabladen des Caches mit Instanzen parametrisierter Berichte. In [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Versionen vor [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]bestand darin die einzige Möglichkeit, den Cache vorab zu laden. Weitere Informationen finden Sie unter [Zwischenspeichern von Berichten &#40;SSRS&#41;](../../reporting-services/report-server/caching-reports-ssrs.md)bestand darin die einzige Möglichkeit, den Cache vorab zu laden.  
  
 Die folgenden Bedingungen müssen erfüllt sein, bevor Sie einen Bericht oder ein freigegebenes Dataset zwischenspeichern können:  
  
-   Für das freigegebene Dataset oder den Bericht muss die Zwischenspeicherung aktiviert sein.  
  
-   Die freigegebenen Datenquellen für das freigegebene Dataset oder den Bericht müssen für die Verwendung gespeicherter Anmeldeinformationen oder keiner Anmeldeinformationen konfiguriert sein.  
  
-   Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst muss ausgeführt werden.  
  
## <a name="to-preload-the-cache-by-creating-a-cache-refresh-plan"></a>So laden Sie den Cache vorab, indem Sie einen Cacheaktualisierungsplan erstellen  
  
1. Starten Sie [das Webportal eines Berichtsservers](../../reporting-services/web-portal-ssrs-native-mode.md "Das Webportal eines Berichtsservers").  
  
2. Wählen Sie auf dem Home-Bildschirm die Option **Durchsuchen** aus, und navigieren Sie durch die Ordnerhierarchie, um das Element zu ermitteln, das Sie zwischenspeichern möchten.  
  
3. Klicken Sie in der oberen rechten Ecke des Elements auf die Schaltfläche mit den drei Auslassungspunkten, und wählen Sie aus dem Dropdownmenü die Option **Verwalten** aus.  
  
4. Wählen Sie im vertikalen Menü auf der linken Seite die Registerkarte **Caching** aus.  
  
5. Um die Zwischenspeicherung für ein Dataset zu aktivieren, wählen Sie das Optionsfeld **Kopien von diesem Dataset zwischenspeichern und bei Verfügbarkeit verwenden** aus. Darunter wird der Abschnitt **Cacheablauf** angezeigt. Wählen Sie eins der folgenden Optionsfelder aus:

    - **Cache läuft ab nach x Minuten** (geben Sie die gewünschte Anzahl von Minuten ein).
    - **Cache läuft ab nach Zeitplan**.  Reporting Services bietet freigegebene und berichtsspezifische Zeitpläne, mit denen Sie die Verarbeitung, konsistente Inhalte und die Leistung der Berichtsverteilung steuern können. Weitere Informationen finden Sie unter [Create, Modify, and Delete Schedules](../../reporting-services/subscriptions/create-modify-and-delete-schedules.md "Create, Modify, and Delete Schedules"). Für Zeitpläne stehen Ihnen verschiedene Optionen zur Verfügung, in diesem Fall für den Ablauf des Caches: Wählen Sie eine der beiden unten genannten Zeitplanoptionen aus:  
      - Aktivieren Sie das Optionsfeld **Freigegebener Zeitplan**, und wählen Sie aus dem Dropdownfeld **Freigegebenen Zeitplan auswählen** einen Zeitplan aus. Weitere Informationen finden Sie unter [Schedules](../../reporting-services/subscriptions/schedules.md "Zeitpläne").  
      - Aktivieren Sie das Optionsfeld **Berichtsspezifischer Zeitplan**, und wählen Sie ggf. den Link **Zeitplan bearbeiten** aus, um die Seite *Zeitplandetails* anzuzeigen.  

         ![Die Webportalseite mit Details zum Zeitplan des Cacheablaufs für Datasets](../../reporting-services/report-server/media/preload-the-cache/web-portal-dataset-cache-schedule-details.png "Detailseite zum Zeitplan für ein Datasetcache")

          Auf dieser Seite können Sie Folgendes auswählen:
         - Die Art des Zeitplans:
           - **Stunde** – zur stündlichen Ausführung des Zeitplans. Geben Sie die genauen Stunden- und Minutenwerte sowie die Startzeit ein.
           - **Tag** – wählen Sie eine der drei folgenden Optionen aus:  
              - **An den folgenden Tagen:** (So, Mo, Di, Mi, Do, Fr, Sa).
              - **An jedem Arbeitstag**
              - **Nach dieser Anzahl von Tagen wiederholen** – geben Sie eine Zahl an.  
           - **Woche** – geben Sie die beiden folgenden Elemente an:
              - **Nach dieser Anzahl von Wochen wiederholen** – geben Sie eine Zahl an.  
              - **An Tagen** – wählen Sie die Wochentage aus, an denen eine Ausführung stattfinden soll.  
           - **Monat** – wählen Sie aus folgenden Optionen aus:
              - **In Monatswoche**  
                 - Wählen Sie aus dem Dropdownfeld den gewünschten Wert aus (1., 2., 3., 4. oder Letzte).  
                 - **An Wochentag** – aktivieren Sie mindestens ein Kontrollkästchen (So, Mo, Di, Mi, Do, Fr, Sa).  
                 - **An Kalendertag(en)** – geben Sie an, am wievielten Tag eines Monats der Zeitplan ausgeführt werden soll. Geben Sie mehrere Tage durch Kommas getrennt oder einen Zeitbereich mit Bindestrich oder eine Kombination daraus ein (z.B. 1,3-5).  
           - **Einmal** – einmalige Ausführung.  
         - **Startzeit** – die Uhrzeit, zu der der Zeitplan starten soll.  
         - **Start- und Enddatum** – geben Sie das Startdatum und optional das Enddatum des Zeitplans an.
         - Klicken Sie auf **Anwenden**, um den Zeitplan zu speichern.  
           > [!NOTE]
           > Wenn für das Element keine Zwischenspeicherung aktiviert ist, werden Sie aufgefordert, das Zwischenspeichern zu aktivieren. Um die Zwischenspeicherung zu aktivieren, klicken Sie auf **OK**.  

         - Wählen Sie **Cacheaktualisierungsplan erstellen** aus, um den Cachezeitplan zu erstellen bzw. zu speichern.  
         Die Seite **Cacheaktualisierungspläne** wird geöffnet. Hier können Sie folgende Aktionen ausführen:
           - Fügen Sie einen neuen Cacheaktualisierungsplan hinzu.
           - Erstellen Sie einen neuen Cacheaktualisierungsplan aus einem vorhandenen Plan.
           - Aktualisieren Sie die Seite „Cacheaktualisierungspläne“.
           - Löschen Sie einen Plan.
           - Suchen Sie anhand des Namens nach einem Plan.

         Wenn noch keine Cacheaktualisierungspläne gespeichert wurden, ist die Liste leer, und „Hinzufügen“ ist die einzige verfügbare Option. Wählen Sie **+ Neuer Cacheaktualisierungsplan** aus, um einen neuen Plan hinzuzufügen. Die Seite **Neuer Cacheaktualisierungsplan** wird angezeigt.  
           - Geben Sie eine **Beschreibung** in das erste Textfeld ein, um den Aktualisierungsplan zu benennen.  
           - Wählen Sie unter **Cache nach folgendem Zeitplan aktualisieren** eins der folgenden Optionsfelder aus:  
             - **Freigegebener Zeitplan** – wählen Sie aus dem angrenzenden Dropdownfeld einen freigegebenen Zeitplan aus. 
             - **Berichtsspezifischer Zeitplan** – bearbeiten Sie den Zeitplan wie in Schritt 2.2 oben beschrieben, indem Sie ggf. den Link **Zeitplan bearbeiten** auswählen, um die Seite *Zeitplandetails* anzuzeigen. 
             - Wenn Sie einen Plan hinzufügen, wählen Sie **Cacheaktualisierungsplan erstellen** aus, um den Plan zu speichern. Wählen Sie **Anwenden** aus, wenn Sie einen vorhandenen Plan bearbeiten.  
      Sie kehren zur aktualisierten Seite **Cacheaktualisierungspläne** zurück.
  
## <a name="to-preload-the-cache-with-a-user-specific-report-by-using-a-data-driven-subscription"></a>So laden Sie den Cache mit einem benutzerspezifischen Bericht vorab, indem Sie ein datengesteuertes Abonnement verwenden

1. Starten Sie [das Webportal eines Berichtsservers](../../reporting-services/web-portal-ssrs-native-mode.md "Das Webportal eines Berichtsservers").  
2. Wählen Sie auf dem Home-Bildschirm die Option **Durchsuchen** aus, und navigieren Sie durch die Ordnerhierarchie, um den Bericht zu ermitteln, den Sie zwischenspeichern möchten.  
3. Klicken Sie mit der rechten Maustaste auf den Bericht, und wählen Sie **Abonnieren** aus dem Dropdownmenü aus. Die Seite **Neue Abonnements** wird angezeigt.  
4. Geben Sie im Textfeld **Beschreibung** eine Beschreibung für das Abonnement ein.  
5. Das Optionsfeld **Abonnementtyp** zeigt zwei Optionen an:  
   - **Standardabonnement** – zum Generieren und Übermitteln eines Berichts.
   - **Datengesteuertes Abonnement** – zum Generieren und Übermitteln eines Berichts für jede Zeile in einem Dataset. Wählen Sie diese Option aus, um den Cache vorab zu laden.
6. Wählen Sie im Abschnitt **Zeitplan** eins der folgenden Optionsfelder aus:
   - **Freigegebener Zeitplan** – wählen Sie aus dem Dropdownfeld einen freigegebenen Zeitplan aus.  
   - **Berichtsspezifischer Zeitplan** – bearbeiten Sie den Zeitplan wie in Schritt 2.2 oben beschrieben, indem Sie ggf. den Link **Zeitplan bearbeiten** auswählen, um die Seite *Zeitplandetails* anzuzeigen.  
7. Der Abschnitt **Ziel** zeigt folgende Auswahloptionen in einem Dropdownfeld an:
    - **Windows-Dateifreigabe**
    - **E-Mail**
    - **NULL-Übermittlungsanbieter** – wählen Sie für diese Aufgabe den NULL-Übermittlungsanbieter aus.  
8. Bearbeiten oder erstellen Sie im Abschnitt **Dataset** ein Dataset für dieses Berichtsabonnement, indem Sie auf die Schaltfläche **Dataset bearbeiten** klicken.  
9. Auf der Seite **Dataset bearbeiten** im Abschnitt **Datenquelle** wählen Sie die Datenquelle aus, die die Berichtsparameterwerte und Übermittlungsoptionen enthält. Folgende Optionen stehen zur Auswahl:  
   - **Eine freigegebene Datenquelle** – klicken Sie auf die drei Auslassungspunkte, und wählen Sie im Ordner *Freigegebene Datenquelle* eine freigegebene Datenquelle aus.
   - **Eine benutzerdefinierte Datenquelle** – sehr wahrscheinlich müssen Sie diese Option auswählen, es sei denn, Sie oder jemand anders haben bereits die unten genannten Schritte ausgeführt, um eine Datenquelle als freigegebene Datenquelle zu erstellen.  
     - Geben Sie den Verbindungstyp, die Verbindungszeichenfolge und die Anmeldeinformationen für den Zugriff auf die Datenquelle mit Abonnentendaten an. Das folgende Beispiel zeigt eine Verbindungszeichenfolge, die für die Verbindung mit einer SQL Server-Datenbank mit dem Namen „Subscribers“ verwendet wird.  
  
   ```T-SQL
   data source=<servername>;initial catalog=Subscribers  
   ```
  
10. Geben Sie im Abschnitt **Abfrage** die Abfrage an, die die gewünschten Abonnentendaten abruft.  Beispiel:  
  
    ```T-SQL  
    Select * from RptSubscribers  
    ```
  
    Sie können auch den Timeoutzeitraum für Abfragen erhöhen, deren Verarbeitung lange dauert.  
  
11. Wählen Sie **Überprüfen** aus. Die Abfrage muss überprüft werden, bevor der Vorgang fortgesetzt werden kann. Wenn die Meldung **Überprüfung erfolgreich** angezeigt wird, wird unter der Schaltfläche **Überprüfen** eine Liste mit Datasetfeldern angezeigt. Klicken Sie auf **Anwenden**, um die benutzerdefinierte Datenquelle zu erstellen.  
  
12. Sie kehren zur Seite **Neues Abonnement** zurück.  Geben Sie im Abschnitt **Berichtsparameter** Berichtsparameterwerte für die angezeigten Berichtsparameter an, sofern vorhanden.  

13. Klicken Sie auf **Abonnement erstellen**.  
  
14. Die Seite **Abonnements** wird mit Ihrem neuen datengesteuerten Abonnement angezeigt. Auf dieser Seite können Sie das Abonnement aktivieren, wenn Sie soweit sind. Aktivieren Sie das Kontrollkästchen links neben dem Abonnement, und klicken Sie auf die Schaltfläche **Aktivieren**. ![Schaltfläche „Aktivieren“ auf der Abonnementsseite](../../reporting-services/report-server/media/preload-the-cache/subscriptions-page-enable-button.png "Die Schaltfläche „Aktivieren“ auf der Abonnementsseite")

15. Geben Sie an, wann das Abonnement verarbeitet wird. Wählen Sie nicht **Wenn die Berichtsdaten auf dem Berichtsserver aktualisiert werden** aus. Diese Option ist nur für Berichtsmomentaufnahmen verfügbar. Wenn Sie einen vorhandenen Zeitplan verwenden möchten, wählen Sie **Nach einem freigegebenen Zeitplan** aus.  
  
     Zum Erstellen eines benutzerdefinierten Zeitplans wählen Sie **Nach einem Zeitplan, der für dieses Abonnement erstellt wurde** aus und klicken dann auf **Weiter**. Konfigurieren Sie den Zeitplan, und klicken Sie dann auf **Fertig stellen**.  
  
    > [!NOTE]  
    > Die Abonnenten empfangen nur dann den neuesten Bericht, wenn der von Ihnen konfigurierte Zeitplan konsistent mit dem Zeitplan für die Berichtsübermittlung ist, den Sie für die Abonnenten definiert haben. Weitere Informationen finden Sie unter [Das Webportal eines Berichtsservers](../../reporting-services/web-portal-ssrs-native-mode.md  "Das Webportal eines Berichtsservers").  
  
16. Konfigurieren Sie die Ausführungsoptionen für den Bericht wie folgt: Wählen Sie auf der Berichtsseite die Registerkarte **Eigenschaften** aus.  
  
17. Wählen Sie im linken Bereich die Registerkarte **Ausführung** aus.  
  
18. Wählen Sie auf der Seite die Option **Diesen Bericht mit den neuesten Daten rendern**.  
  
19. Wählen Sie eine der folgenden zwei Cacheoptionen aus, und konfigurieren Sie die Ablaufzeit wie folgt:  
  
    - Wenn die zwischengespeicherte Kopie nach einem bestimmten Zeitraum ablaufen soll, klicken Sie auf **Eine temporäre Kopie des Berichts zwischenspeichern. Diese Kopie soll nach der folgenden Anzahl von Minuten ablaufen.** Geben Sie die Anzahl von Minuten für den Berichtsablauf ein.  
  
    - Wenn die zwischengespeicherte Kopie nach einem Zeitplan ablaufen soll, klicken Sie auf **Eine temporäre Kopie des Berichts zwischenspeichern. Die Kopie des Berichts läuft gemäß dem folgenden Zeitplan ab.** Klicken Sie auf **Konfigurieren**, oder wählen Sie einen freigegebenen Zeitplan aus, um einen Zeitplan für den Berichtsablauf festzulegen.  
  
20. Wählen Sie **Übernehmen**.
  
## <a name="see-also"></a>Weitere Informationen  

 [Datengesteuerte Abonnements](../../reporting-services/subscriptions/data-driven-subscriptions.md)  
 [Erstellen eines datengesteuerten Abonnements &#40;SSRS-Tutorial&#41;](../../reporting-services/create-a-data-driven-subscription-ssrs-tutorial.md)  
 [Leistung, Momentaufnahmen, Zwischenspeichern (Reporting Services)](../../reporting-services/report-server/performance-snapshots-caching-reporting-services.md)  
 [Set Report Processing Properties (Festlegen von Berichtsverarbeitungseigenschaften)](../../reporting-services/report-server/set-report-processing-properties.md)  
 [Zwischenspeichern von Berichten &#40;SSRS&#41;](../../reporting-services/report-server/caching-reports-ssrs.md)  
 [Working with shared datasets (Arbeiten mit freigegebenen Datasets)](../../reporting-services/work-with-shared-datasets-web-portal.md)  
  
