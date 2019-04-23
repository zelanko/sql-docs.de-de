---
title: Erstellen eines datengesteuerten Abonnementseite (Berichts-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 814b4653-572a-48c7-847f-b310ba0f3046
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 625afedabdb376f913d3353e2bda343bba66e3e1
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "59964816"
---
# <a name="create-data-driven-subscription-page-report-manager"></a>Datengesteuertes Abonnement erstellen (Seite) (Berichts-Manager)
  Mithilfe der Seiten Erstellen eines datengesteuerten Abonnements können Sie ein Abonnement erstellen oder ändern, das bei jeder Ausführung eine Abonnentendatenbank nach Abonnementinformationen abfragt. Datengesteuerte Abonnements verwenden die Abfrageergebnisse, um die Empfänger des Abonnements, Übermittlungseinstellungen und Berichtsparameterwerte zu bestimmen. Zur Laufzeit führt der Berichtsserver eine Abfrage aus, um die für das Abonnement verwendeten Einstellungen abzurufen. Sie können die Seiten Erstellen eines datengesteuerten Abonnements verwenden, um die Abfrage zu definieren und den Abonnementeinstellungen Abfragewerte zuzuweisen. Die von Ihnen für ein datengesteuertes Abonnement angegebenen Werte und Optionen werden ähnlich wie bei einem Assistenten auf mehrere Seiten verteilt. Insgesamt handelt es sich um sieben Seiten.  
  
 Wenn Sie ein datengesteuertes Abonnement erstellen möchten, müssen Sie mit dem Schreiben einer Abfrage oder eines Befehls zum Abrufen der Daten für das Abonnement vertraut sein. Sie müssen auch über einen Datenspeicher verfügen, der die Abonnentendaten (beispielsweise die Namen der Abonnenten und ihre E-Mail-Adressen) enthält, die für das Abonnement verwendet werden.  
  
 Diese Seite steht nur für Benutzer mit erweiterten Berechtigungen zur Verfügung. Wenn die Standardsicherheit verwendet wird, können keine datengesteuerten Abonnements für Berichte im Ordner Meine Berichte verwendet werden.  
  
> [!NOTE]  
>  Diese Funktion ist nicht in jeder Edition von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]verfügbar. Eine Liste der Funktionen, die von den Editionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]unterstützt werden, finden Sie unter [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
## <a name="navigation"></a>Navigation  
 Verwenden Sie folgendes Verfahren, um zu dieser Position in der Benutzeroberfläche zu navigieren.  
  
###### <a name="to-open-the-data-driven-subscription-page"></a>So öffnen Sie die Seite Datengesteuertes Abonnement  
  
1.  Öffnen Sie den Berichts-Manager, und suchen Sie den Bericht, für den Sie ein datengesteuertes Abonnement erstellen möchten.  
  
2.  Zeigen Sie auf den Bericht, und klicken Sie auf den Dropdownpfeil.  
  
3.  Klicken Sie im Dropdownmenü auf **Verwalten**. Dadurch wird die Seite **Allgemeine Eigenschaften** für den Bericht geöffnet.  
  
4.  Wählen Sie die Registerkarte **Abonnements** , und klicken Sie dann auf **Neues datengesteuertes Abonnement**.  
  
    > [!NOTE]  
    >  Diese Schaltfläche ist nur verfügbar, wenn die Berichtsdatenquelle gespeicherte Anmeldeinformationen verwenden muss.  
  
## <a name="start-a-subscription-page-1"></a>Starten eines Abonnements (Seite 1)  
 **Beschreibung**  
 Stellen Sie eine Beschreibung für das Abonnement bereit. Die Beschreibung wird in den Abonnementlisten in **Meine Abonnements** und auf der Registerkarte **Abonnements** des Berichts angezeigt.  
  
 **Geben Sie, wie Empfänger benachrichtigt werden**  
 Wählen Sie die Übermittlungserweiterung aus, die zum Verteilen des Berichts verwendet werden soll. Für jedes Abonnement kann nur eine Übermittlungserweiterung verwendet werden. Die folgenden Optionen stehen zur Verfügung:  
  
-   Wählen Sie die Option **Berichtsserver-Dateifreigabe** , um Berichte an eine Dateifreigabe zu übermitteln. Der Bericht wird als statische, vom Berichtsserver getrennte Datei übermittelt. Weitere Informationen finden Sie unter [File Share Delivery in Reporting Services](subscriptions/file-share-delivery-in-reporting-services.md).  
  
-   Wählen Sie die Option **Berichtsserver-E-Mail** , um Berichte an einen E-Mail-Posteingang zu übermitteln. Weitere Informationen finden Sie unter [E-Mail Delivery in Reporting Services](subscriptions/e-mail-delivery-in-reporting-services.md).  
  
-   Wählen Sie die Option **NULL-Übermittlungsanbieter** , um Berichte an die Berichtsserver-Datenbank zu übermitteln. Mithilfe dieser Option werden Berichtsmomentaufnahmen erstellt. Wählen Sie diese Option aus, wenn benutzerspezifische oder parametrisierte Berichtsmomentaufnahmen gemäß einem bestimmten Zeitplan auf dem Berichtsserver vorab geladen werden sollen. Weitere Informationen finden Sie unter [Zwischenspeichern von Berichten &#40;SSRS&#41;](report-server/caching-reports-ssrs.md)bestand darin die einzige Möglichkeit, den Cache vorab zu laden.  
  
 **Geben Sie eine Datenquelle, die Empfängerinformationen enthält**  
 Geben Sie an, wie die Datenquellenverbindung definiert ist. Sie können eine freigegebene Datenquelle auswählen, wenn diese die erforderlichen Verbindungsinformationen enthält. Verbindungsinformationen können auch direkt im Abonnement angegeben werden.  
  
 Die Datenquelle stellt Abonnentendaten bereit. Diese Daten können beispielsweise die Namen von Mitarbeitern, Mitarbeiter-IDs, E-Mail-Adressen und bevorzugte Exportformate (wie HTML oder PDF) enthalten. Wenn Sie die E-Mail-Übermittlungserweiterung des Berichtsservers verwenden, sollte die Datenquelle die E-Mail-Adressen enthalten.  
  
## <a name="specify-a-connection-page-2"></a>Angeben einer Verbindung (Seite 2)  
 Wenn Sie eine freigegebene Datenquelle angegeben haben, können Sie auf dieser Seite das freigegebene Datenquellenelement auswählen. Mithilfe des Baumsteuerelements können Sie zum gewünschten Element wechseln und dieses auswählen. Falls Sie eine Verbindung für dieses Abonnement definieren, können Sie auf dieser Seite die folgenden Optionen angeben.  
  
 **Verbindungstyp**  
 Wählen Sie die Datenverarbeitungserweiterung für die Datenquelle aus.  
  
 **Verbindungszeichenfolge**  
 Geben Sie eine Verbindungszeichenfolge ein, die zum Herstellen einer Verbindung mit der Datenquelle verwendet werden soll.  
  
 **Herstellen einer Verbindung mit**  
 Geben Sie die Anmeldeinformationen ein, die beim Herstellen einer Verbindung mit der Datenquelle verwendet werden sollen. Die Anmeldeinformationen werden als verschlüsselte Werte in der Berichtsserver-Datenbank gespeichert.  
  
 Falls die Datenquelle die Windows-Authentifizierung verwendet, wählen Sie die Option **Windows-Anmeldeinformationen verwenden** , wenn eine Verbindung mit der Datenquelle hergestellt wird.  
  
 Wählen Sie Anmeldeinformationen sind nicht erforderlich, wenn Sie eine Datenquelle verwenden, die Benutzerverbindungen nicht authentifiziert (wenn die Datenquelle beispielsweise eine XML-Datei ist). Diese Option erfordert, dass Sie vorher das unbeaufsichtigte Ausführungskonto konfiguriert haben. Weitere Informationen finden Sie unter [Konfigurieren des Kontos für die unbeaufsichtigte Ausführung (SSRS-Konfigurations-Manager)](install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md).  
  
## <a name="specify-a-query-page-3"></a>Angeben einer Abfrage (Seite 3)  
 Verwenden Sie diese Seite, um die Abfrage einzugeben, die die Abonnentendaten abruft. Die besten Ergebnisse erzielen Sie, wenn Sie die Abfrage zunächst in SQL Server Management Studio ausführen, bevor Sie sie in dem datengesteuerten Abonnement verwenden. Sie können dann die Ergebnisse untersuchen, um sicherzustellen, dass Sie die Informationen erhalten, die Sie benötigen. Auf folgende wichtige Punkte sollten Sie bei den Abfrageergebnissen achten:  
  
-   Die Spalten im Resultset bestimmen die Werte, die Sie für Übermittlungsoptionen und Berichtsparameter angeben können. Wenn Sie zum Beispiel ein datengesteuertes Abonnement für die E-Mail-Übermittlung erstellen, sollte der Resultset eine Spalte mit E-Mail-Adressen enthalten.  
  
-   Die Zeilen im Resultset bestimmen die Anzahl von Berichtsübermittlungen, die generiert werden. Wenn der Resultset 10.000 Zeilen enthält, generiert der Berichtsserver 10.000 Benachrichtigungen und Übermittlungen.  
  
 **Dataseteigenschaften**  
 Geben Sie eine SQL-Abfrage oder einen Befehl an, mit der bzw. dem ein Resultset mit je einer Zeile für jeden Empfänger des Abonnements abgerufen wird. Auf den nachfolgenden Seiten wird das Resultset verwendet, um datengesteuerte Erweiterungseinstellungen aufzufüllen.  
  
 **Timeout**  
 Geben Sie einen Timeoutwert für die Abfrage ein. Dieser Wert muss groß genug sein, damit die Abfrageverarbeitung abgeschlossen werden kann.  
  
 **Überprüfen**  
 Klicken Sie auf **Überprüfen** , um die Abfrage zu überprüfen. Die Abfrage muss gültige Ergebnisse ergeben, damit Sie fortfahren können. Falls Sie nicht auf **Überprüfen**klicken, wird die Abfrage überprüft, sobald Sie auf **Weiter**klicken.  
  
## <a name="set-delivery-options-page-4"></a>Festlegen von Übermittlungsoptionen (Seite 4)  
 Auf der vierten Seite geben Sie Übermittlungserweiterungsoptionen an. Die auf der Seite angezeigten Optionen stammen aus der Übermittlungserweiterung. Wie Sie diese Optionen angeben, hängt von der Präsentation der Optionen durch die Übermittlungserweiterung ab. Falls die Erweiterung keine Einstellungen enthält, werden keine Optionen auf dieser Seite angezeigt.  
  
|Option|Zweck|  
|-----------------|----------------|  
|**Geben Sie einen statischen Wert**|Es wird ein konstanter Wert als Übermittlungseinstellung verwendet. Einige Übermittlungserweiterungen stellen statische Werte bereit, aus denen Sie auswählen können. Beispielsweise stellt Berichtsserver-E-Mail-Übermittlung Werte für die Optionen **Bericht einschließen**, **Renderformat**, **Priorität**und **Link einschließen**bereit.|  
|**Ruft den Wert aus der Datenbank**|Verwenden Sie einen Wert aus dem Resultset. Die Spalten des Resultsets können verwendet werden, um Abonnentendaten und Berichtsparameterwerte bereitzustellen.|  
|**Kein Wert**|Die Einstellung wird im Abonnement nicht verwendet.|  
  
#### <a name="set-delivery-options-for-file-share-delivery"></a>Festlegen von Übermittlungsoptionen zur Dateifreigabeübermittlung  
 Die Dateifreigabe-Übermittlungserweiterung wird häufig verwendet, da sie keine vorherige Konfiguration erfordert. In der folgenden Tabelle werden die Optionen beschrieben, die Sie für die Dateifreigabe-Übermittlungserweiterung festlegen können.  
  
 **Dateiname**  
 Gibt einen Dateinamen für den Bericht an. Die Dateifreigabe-Übermittlungserweiterung übermittelt einen Bericht als statische Anwendungsdatei an einen freigegebenen Ordner. In den meisten Fällen sollten Sie einen Wert aus der Datenbank verwenden, um den Dateinamen zu erstellen. Abhängig davon, wie Sie den Schreibmodus festlegen, führt die Verwendung eines statischen Werts dazu, dass jede neue Übermittlung die vorherige Übermittlung überschreibt.  
  
 **Pfad**  
 Gibt einen freigegebenen Ordner an, auf den über eine Netzwerkverbindung zugegriffen werden kann. Überprüfen, diesen Ordner kann zugegriffen werden, indem Sie **ausführen** im Startmenü, und geben Sie den Ordnerpfad im folgenden Format: \\ \\< Computername\>\\< FreigegebenerOrdnerName\>.  
  
 **Renderformat**  
 Gibt das Ausgabeformat für die Datei an. Der Berichtsserver kann die Datei in den Anwendungsformaten schreiben, die den Renderingerweiterungen entsprechen, die auf dem Berichtsserver installiert sind.  
  
 **Schreibmodus**  
 Geben Sie an, ob der Berichtsserver die alte Datei durch die neue Version überschreiben, die neue Datei an die alte anhängen oder die Übermittlung abbrechen soll, wenn eine Datei mit dem gleichen Namen gefunden wird.  
  
 **Dateierweiterung**  
 Geben Sie True an, damit eine Dateierweiterung angefügt wird, die dem von Ihnen gewählten Renderformat entspricht.  
  
 **Benutzername**  
 Geben Sie das Domänenbenutzerkonto ein, die Berechtigung zum Hinzufügen von Dateien in den freigegebenen Ordner im folgenden Format: \<Domäne >\\< Benutzername\>.  
  
 **Kennwort**  
 Geben Sie das Kennwort für das Konto ein.  
  
## <a name="set-parameters-page-5"></a>Festlegen von Parametern (Seite 5)  
 Falls ein Bericht Parameter enthält, müssen Sie angeben, welche Parameterwerte für den Bericht verwendet werden sollen. Parameterwerte können aus der Abonnentendatenquelle abgerufen werden. Wenn Sie z. B. einen regionalen Vertriebsbericht verwenden, der auf der Grundlage einer Regionalkennzahl parametrisiert ist, können Sie Regionsinformationen für jeden einzelnen Mitarbeiter abrufen, wenn diese Informationen in der Mitarbeiterdatenbank gespeichert sind.  
  
|Option|Zweck|  
|-----------------|----------------|  
|**Geben Sie einen statischen Wert**|Verwenden Sie einen konstanten Wert für den Parameter, wenn Sie denselben Parameter für alle Abonnenten verwenden möchten. Wenn der Parameter mehrwertig ist, können Sie einen Wert aus der Liste auswählen.|  
|**Standard verwenden**|Einige Berichte enthalten einen Standardwert für alle oder einige der Parameter. Wenn der Berichtsparameter einen Standardwert hat, klicken Sie auf dieses Kontrollkästchen, um diesen Standardwert zu verwenden.|  
|**Ruft den Wert aus der Datenbank**|Verwenden Sie einen Wert aus dem Resultset. Die Spalten des Resultsets können als Quelle für einen Datenwert ausgewählt werden, der mit jeder Abonnementinstanz verwendet wird.|  
  
## <a name="specify-a-trigger-page-6"></a>Angeben eines Triggers (Seite 6)  
 Wählen Sie ein Ereignis aus, das die Abonnementverarbeitung initiiert.  
  
|Option|Zweck|  
|-----------------|----------------|  
|**Wenn die Berichtsdaten auf dem Berichtsserver aktualisiert wird**|Falls der Bericht für die Ausführung als Momentaufnahme zur Berichtsausführung konfiguriert ist, können Sie angeben, dass das Abonnement verarbeitet wird, wenn die Momentaufnahme aktualisiert wird.|  
|**Nach einem Zeitplan, der für dieses Abonnement erstellt wurde**|Führen Sie das Abonnement zu einem bestimmten Datum und zu einer bestimmten Uhrzeit aus.|  
|**Nach einem freigegebenen Zeitplan**|Führen Sie das Abonnement mithilfe der durch einen freigegebenen Zeitplan angegebenen Zeitplaninformationen aus.|  
  
## <a name="schedule-a-subscription-page-7"></a>Planen eines Abonnements (Seite 7)  
 Beim Planen des Abonnements müssen Sie die Häufigkeit angeben, mit der der Bericht übermittelt wird. Die erste Gruppe von Optionen gibt eine Kategorie der Häufigkeit an (Stunde, Tag, Woche usw.). Die zweite Gruppe von Optionen, die angezeigt wird, basiert auf der ersten Auswahl.  
  
 **Hourly**  
 Definieren Sie einen Zeitplan mit stündlicher Ausführung.  
  
 **Pro Tag**  
 Definieren Sie einen Zeitplan, der an den von Ihnen angegebenen Tagen zu einer bestimmten Uhrzeit (Stunde und Minute) ausgeführt wird. Sie können Tage auf folgende Weise angeben: Jede  *\<Tag >*, an jedem Arbeitstag und alle  *\<Anzahl >* Tag. Wenn eine Option ausgewählt ist, stehen die anderen nicht zur Verfügung, auch wenn es so aussieht, als seien die anderen Tage ebenfalls ausgewählt.  
  
 **Wöchentlich**  
 Definieren Sie einen Zeitplan, der zu der von Ihnen angegebenen Uhrzeit (Stunde und Minute) wöchentlich ausgeführt wird. Der Zeitabstand kann vollständige Wochen betragen (z. B. alle zwei Wochen) oder Tage innerhalb einer Woche.  
  
 **Monatliche**  
 Definieren Sie einen Zeitplan mit monatlicher Ausführung. Innerhalb eines Monats können Sie einen Tag auf der Grundlage eines Musters auswählen (z. B. den letzten Sonntag jeden Monats) oder spezifische Kalenderdaten angeben (z. B. den 1. und 15., um den ersten und fünfzehnten Tag jeden Monats anzugeben). Mithilfe von Kommas und Bindestrichen können Sie mehrere Tage und Bereiche angeben (Beispiel: 1, 5, 7-12, 21).  
  
 **Einmal**  
 Definieren Sie einen Zeitplan mit einmaliger Ausführung. Im Abschnitt **Anfangs- und Enddatum** können Sie den Tag angeben, an dem der Zeitplan ausgeführt werden soll. Dieser Zeitplan läuft unmittelbar nach seiner Verarbeitung ab.  
  
 **Start- und Enddatum**  
 Geben Sie das Anfangsdatum für den Beginn der Gültigkeit des Zeitplans und das Enddatum für den Ablauf des Zeitplans an. Zeitpläne laufen ohne Benachrichtigung ab. Nach dem Enddatum kann ein Zeitplan nicht mehr ausgeführt werden.  
  
## <a name="saving-the-subscription"></a>Speichern des Abonnements  
 Die Schaltfläche **Fertig stellen** ist aktiviert, wenn ausreichende Informationen für das Abonnement zur Verfügung stehen. Klicken Sie auf **Fertig stellen** , um das Abonnement fertig zu stellen.  
  
## <a name="see-also"></a>Siehe auch  
 [Berichts-Manager &#40;einheitlicher SSRS-Modus&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md)   
 [Data-Driven Subscriptions](subscriptions/data-driven-subscriptions.md)   
 [Erstellen eines datengesteuerten Abonnements &#40;SSRS-Tutorial&#41;](create-a-data-driven-subscription-ssrs-tutorial.md)   
 [Angeben der Anmeldeinformationen und Verbindungsinformationen für Berichtsdatenquellen](report-data/specify-credential-and-connection-information-for-report-data-sources.md)   
 [Abonnements und Übermittlung &#40;Reporting Services&#41;](subscriptions/subscriptions-and-delivery-reporting-services.md)   
 [Berichts-Manager (F1-Hilfe)](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
