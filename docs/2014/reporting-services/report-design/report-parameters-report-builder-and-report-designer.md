---
title: Berichtsparameter (Berichts-Generator und Berichts-Designer) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/27/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- SQL Server 2014
f1_keywords:
- sql12.rtp.rptdesigner.subreportproperties.parameters.f1
- sql12.rtp.rptdesigner.reportparameters.general.f1
- "10091"
- "10073"
- "10070"
- sql12.rtp.rptdesigner.reportparameters.advanced.f1
ms.assetid: 58b96555-d876-4f61-bff8-db5764b9f5f9
caps.latest.revision: 36
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: c936c8e8eaac37c18e402206d9ca7bc6e6f0bd9b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36057825"
---
# <a name="report-parameters-report-builder-and-report-designer"></a>Berichtsparameter (Berichts-Generator und Berichts-Designer)
  In diesem Thema werden die allgemeinen Verwendungen von SSRS-Berichtsparametern und die einstellbaren Eigenschaften beschrieben. Zudem erhalten Sie viele weitere Informationen zu Parametern. Mithilfe von Berichtsparametern können Sie Berichtsdaten steuern, eine Verbindung zwischen verwandten Berichten herstellen und die Berichtspräsentation anpassen.  
  
[!INCLUDE[applies](../../includes/applies-md.md)] SharePoint-Modus und einheitlichen Modus
  
 Eine Demonstration über das Hinzufügen von Parametern zu einem Bericht finden Sie unter [Lernprogramm: Hinzufügen von Parametern zu einem Bericht (SSRS)](http://technet.microsoft.com/library/aa337432\(v=SQL.105\).aspx)  

  
##  <a name="bkmk_Common_Uses_for_Parameters"></a> Allgemeine Verwendungsmöglichkeiten für Parameter  
 Im Folgenden sind einige der häufigsten Verwendungsmöglichkeiten für Parameter aufgeführt.  
  
 **Berichtsdaten steuern**  
  
-   Filtern Sie Berichtsdaten in der Datenquelle, indem Sie Datasetabfragen schreiben, die Abfragevariablen enthalten.  
  
-   Filtern Sie Daten von einem freigegebenen Dataset. Wenn Sie einem Bericht ein freigegebenes Dataset hinzufügen, kann die Abfrage nicht geändert werden. Im Bericht können Sie einen Datasetfilter mit einem Verweis auf einen von Ihnen erstellten Berichtsparameter hinzufügen.  
  
-   Ermöglichen der Angabe von Werten durch Benutzer, um die Daten in einem Bericht anzupassen. Beispiel: Angabe von zwei Parametern (Start- und Enddatum) für Umsatzdaten.  
  
 **Eine Verbindung zwischen verwandten Berichten herstellen**  
  
-   Verwenden Sie Parameter, um Hauptberichte mit Drillthroughberichten, Unterberichten sowie verknüpften Berichten zu verbinden. Beim Entwurf von Berichtssätzen können Sie jeden Bericht so entwerfen, dass er Antworten auf ganz bestimmte Fragen liefert. Jeder Bericht kann eine andere Sicht oder Detailebene zu verwandten Informationen bereitstellen. Zum Bereitstellen eines Satzes untereinander verbundener Berichte erstellen Sie Parameter für die verbundenen Daten in den Zielberichten.  
  
     Weitere Informationen finden Sie unter [Drillthroughberichte (Berichts-Generator und SSRS)](drillthrough-reports-report-builder-and-ssrs.md), [Unterberichte (Berichts-Generator und SSRS)](subreports-report-builder-and-ssrs.md) und [Erstellen eines verknüpften Berichts](../reports/create-a-linked-report.md).  
  
-   Anpassen von Parametersätzen für mehrere Benutzer. Erstellen Sie auf der Grundlage eines Verkaufsberichts auf dem Berichtsserver zwei verknüpfte Berichte. In einem der verknüpften Berichte werden vordefinierte Parameterwerte für Vertriebsmitarbeiter, im anderen vordefinierte Parameterwerte für Verkaufsmanager verwendet. Für beide Berichte wird die gleiche Berichtsdefinition verwendet.  
  
 **Berichtspräsentation anpassen**  
  
-   Senden Sie einem Berichtsserver über eine URL-Anforderung Befehle, um das Rendering eines Berichts anzupassen. Weitere Informationen finden Sie unter [URL-Zugriff (SSRS)](../url-access-ssrs.md) und [Übergeben von Berichtsparametern innerhalb einer URL](../pass-a-report-parameter-within-a-url.md).  
  
-   Ermöglichen der Angabe von Werte durch Benutzer, um die Darstellung eines Berichts anzupassen. Beispiel: Angabe eines booleschen Parameters, um anzugeben, ob alle geschachtelten Zeilengruppen in einer Tabelle erweitert oder reduziert werden sollen.  
  
-   Ermöglichen Sie Benutzern das Anpassen von Berichtsdaten und der Darstellung von Berichten, indem Sie Parameter in einen Ausdruck einschließen.  
  
     Weitere Informationen finden Sie unter [Verweise auf Parametersammlungen &#40;Berichts-Generator und SSRS&#41;](built-in-collections-parameters-collection-references-report-builder.md).  
  
##  <a name="UserInterface"></a> Fenster "Parameter"  
 Wenn Sie einen Bericht anzeigen, werden auf der Berichts-Viewer-Symbolleiste alle Parameter angezeigt, sodass ein Benutzer interaktiv Werte angeben kann. Die folgende Abbildung zeigt den Parameterbereich für einen Bericht, der über Parameter verfügt @StartDate, @EndDate, @Subcategory, und @ShowAllRows.  
  
 ![Rs_ParameterStory](../media/rs-parameterstory.gif "Rs_ParameterStory")  
  
1.  **Parameterbereich** Auf der Berichts-Viewer-Symbolleiste werden für jeden Parameter eine Eingabeaufforderung und ein Standardwert angezeigt. Das Parameterlayout auf der Symbolleiste wird automatisch formatiert. Die Reihenfolge richtet sich nach der Reihenfolge, in der die Parameter im Berichtsdatenbereich angezeigt werden.  
  
2.  **@StartDate und @EndDate Parameter** Parameters @StartDate Datentyp `DateTime`. Neben dem Textfeld wird die Eingabeaufforderung "Startdatum" angezeigt. Geben Sie zum Ändern des Datums ein neues Datum in das Textfeld ein, oder verwenden Sie das Kalendersteuerelement.  
  
     Der Parameter @EndDate wird neben @StartDate.  
  
3.  **@Subcategory Parameter** Parameters @Subcategory Datentyp `Text`. Da @Subcategory verfügt über eine Liste verfügbarer Werte gültige Werte werden in einer Dropdownliste angezeigt. Werte müssen aus dieser Liste ausgewählt werden. Da @Subcategory mehrwertig ist, wird eine **Alles markieren** Option wird angezeigt, mit dem Sie zum Aufheben der Auswahl und alle Werte in der Liste auswählen.  
  
4.  **@ShowAllRows Parameter** Parameters @ShowAllRows Datentyp `Boolean`. Mithilfe der Optionsfelder an `True` oder `False`.  
  
5.  **Handle "Parameterbereich ein-/ausblenden"** Klicken Sie auf der Berichts-Viewer-Symbolleiste auf diesen Pfeil, um den Parameterbereich anzuzeigen oder auszublenden.  
  
6.  **Schaltfläche "Parameter"** Klicken Sie in der Berichts-Generator-Vorschau im Menüband auf die Schaltfläche **Parameter** , um den Parameterbereich anzuzeigen oder auszublenden.  
  
7.  **Schaltfläche "Bericht anzeigen"** Klicken Sie auf der Berichts-Viewer-Symbolleiste auf **Bericht anzeigen** , um nach der Eingabe von Parameterwerten den Bericht auszuführen. Wurden für alle Parameter Standardwerte festgelegt, wird der Bericht beim erstmaligen Anzeigen automatisch ausgeführt.  
  
##  <a name="bkmk_Create_Parameters"></a> Erstellen von Parametern  
 Es gibt folgende Möglichkeiten, um Berichtsparameter zu erstellen:  
  
-   Fügen Sie eine Datasetabfrage mit Variablen oder eine gespeicherte Prozedur für ein Dataset mit Eingabeparametern hinzu. Für jede Variable oder jeden Eingabeparameter wird ein Datasetparameter erstellt und für jeden Datasetparameter wird ein Berichtsparameter erstellt.  
  
     Das folgende Bild aus dem Berichts-Generator zeigt eine Datasetabfrage mit einer Variablen (1) und dem entsprechenden Datasetparameter (2) und Berichtsparameter (3).  
  
     ![Dataseteigenschaften (Dialogfeld) und Berichtfenster](../media/datasetquery-parameters.png "Dataseteigenschaften (Dialogfeld) und Berichtfenster")  
  
    > **HINWEIS!** Nicht alle Datenquellen unterstützen Parameter.  
  
     Das Dataset kann eingebettet oder freigegeben sein. Wenn Sie einem Bericht ein freigegebenes Dataset hinzufügen, können als "Intern" markierte Datasetparameter im Bericht nicht überschrieben werden. Nicht als "Intern" markierte Datasetparameter können überschrieben werden.  
  
     Weitere Informationen finden Sie in diesem Thema unter [Datasetabfrage](#bkmk_Dataset_Parameters) .  
  
-   Erstellen Sie einen Parameter manuell aus dem Berichtsdatenbereich.  
  
     Sie können Berichtsparameter so konfigurieren, dass ein Benutzer interaktiv Werte eingeben kann, um den Inhalt oder die Darstellung eines Berichts anzupassen. Berichtsparameter können auch so konfiguriert werden, dass vorkonfigurierte Werte nicht vom Benutzer geändert werden können.  
  

  > **HINWEIS!** Da Parameter auf dem Server unabhängig verwaltet werden, werden durch das erneute Veröffentlichen eines Hauptberichts mit neuen Parametereinstellungen keine im Bericht vorhandenen Parametereinstellungen überschrieben.  
  
-   Fügen Sie einen Berichtsteil hinzu, der Verweise auf einen Parameter oder ein freigegebenes Dataset mit Variablen enthält.  
  
     Berichtsteile werden auf dem Berichtsserver gespeichert und können von anderen Benutzern in deren Berichten verwendet werden. Berichtsteile, bei denen es sich um Parameter handelt, können nicht vom Berichtsserver aus verwaltet werden. Im Berichtsteilkatalog können Sie nach Parametern suchen und sie nach dem Hinzufügen in Ihrem Bericht konfigurieren. Weitere Informationen finden Sie unter [Report Parts &#40;Report Builder and SSRS&#41;](../report-parts-report-builder-and-ssrs.md).  
     
   > **HINWEIS!** Parameter können als separater Berichtsteil für Datenbereiche veröffentlicht werden, die abhängige Datasets mit Parametern enthalten. Obwohl Parameter als Berichtsteil aufgeführt werden, können Sie einem Bericht keinen Berichtsteilparameter direkt hinzufügen. Fügen Sie stattdessen den Berichtsteil hinzu, und alle notwendigen Berichtsparameter werden automatisch aus Datasetabfragen generiert, die enthalten sind oder auf die vom Berichtsteil verwiesen wird. Weitere Informationen zu Berichtsteilen finden Sie unter [Berichtsteile (Berichts-Generator und SSRS)](../report-parts-report-builder-and-ssrs.md) und [Berichtsteile im Berichts-Designer (SSRS)](report-parts-in-report-designer-ssrs.md).  
  
### <a name="parameter-values"></a>Parameterwerte  
 Ihnen stehen folgende Optionen für das Auswählen von Parameterwerten im Bericht zur Verfügung.  
  
-   Wählen Sie einen einzelnen Parameterwert aus einer Dropdownliste aus.  
  
-   Wählen Sie mehrere Parameterwerte aus einer Dropdownliste aus.  
  
-   Wählen Sie einen Wert aus einer Dropdownliste für einen Parameter aus, der die für einen anderen Parameter in der Dropdownliste verfügbaren Werte bestimmt. Dies sind kaskadierende Parameter. Durch kaskadierende Parameter lassen sich tausende Parameterwerte nach und nach zu einer überschaubare Anzahl filtern.  
  
     Weitere Informationen finden Sie unter [Hinzufügen von kaskadierenden Parametern zu einem Bericht &#40;Berichts-Generator und SSRS&#41;](add-cascading-parameters-to-a-report-report-builder-and-ssrs.md).  
  
-   Führen Sie den Bericht aus, ohne zuvor einen Parameterwert auswählen zu müssen, da ein Standardwert für den Parameter erstellt wurde.  
  
##  <a name="bkmk_Report_Parameters"></a> Berichtsparametereigenschaften  
 Sie können die Berichtsparametereigenschaften über das Dialogfeld Berichtseigenschaften ändern. Die folgende Tabelle enthält die Eigenschaften, die für die einzelnen Parameter festgelegt werden können:  
  
|Eigenschaft|Description|  
|--------------|-----------------|  
|Name|Geben Sie einen Namen für den Parameter ein. (Beachten Sie dabei die Groß- und Kleinschreibung.) Der Name muss mit einem Buchstaben beginnen und Buchstaben, Zahlen und einen Unterstrich (_) umfassen. Er darf keine Leerzeichen enthalten. Bei automatisch generierten Parametern stimmt der Name mit dem Parameter in der Datasetabfrage überein. Manuell erstellte Parameter ähneln standardmäßig der Zeichenfolge "ReportParameter1".|  
|Eingabeaufforderung|Der Text, der auf der Berichts-Viewer-Symbolleiste neben dem Parameter angezeigt wird.|  
|Datentyp|Wenn verfügbare Werte für einen Parameter definiert sind, wählt der Benutzer Werte aus einer Dropdownliste, selbst wenn der Datentyp ist `DateTime`. Bei einem Berichtsparameter muss es sich um einen der folgenden Datentypen handeln:<br /><br /> `Boolean`installiert haben. Der Benutzer wählt True oder False über ein Optionsfeld aus.<br /><br /> `DateTime`installiert haben. Der Benutzer wählt ein Datum aus einem Kalendersteuerelement aus.<br /><br /> **Integer**. Der Benutzer gibt Werte in ein Textfeld ein.<br /><br /> **Float**. Der Benutzer gibt Werte in ein Textfeld ein.<br /><br /> `Text`installiert haben. Der Benutzer gibt Werte in ein Textfeld ein.<br /><br /> Weitere Informationen zu berichtsdatentypen finden Sie unter [RDL-Datentypen](../reports/report-definition-language-ssrs.md#bkmk_RDL_Data_Types).|  
|Leeren Wert zulassen|Aktivieren Sie diese Option, wenn als Wert für den Parameter eine leere Zeichenfolge zulässig sein soll.<br /><br /> Wenn Sie für einen Parameter gültige Werte angeben und möchten, dass ein leerer Wert zu den gültigen Werten zählt, muss der Wert zusammen mit den anderen Werten angegeben werden. Durch Aktivieren dieser Option wird den verfügbaren Werten nicht automatisch ein leerer Wert hinzugefügt.|  
|NULL-Wert zulassen|Aktivieren Sie diese Option, wenn für den Parameter ein NULL-Wert zulässig sein soll.<br /><br /> Wenn Sie für einen Parameter gültige Werte angeben und möchten, dass NULL zu den gültigen Werten zählt, muss der Wert zusammen mit den anderen Werten angegeben werden. Durch Aktivieren dieser Option wird den verfügbaren Werten nicht automatisch ein NULL-Wert hinzugefügt.|  
|Mehrere Werte zulassen|Geben Sie verfügbare Werte an, um eine Dropdownliste zu erstellen, aus der die Benutzer auswählen können. Damit können Sie sicherstellen, dass in der Datasetabfrage nur gültige Werte übermittelt werden.<br /><br /> Aktivieren Sie diese Option, wenn für den Parameter mehrere Werte aus einer Dropdownliste zulässig sein können. NULL-Werte sind nicht zulässig. Wenn diese Option ausgewählt ist, werden der Liste der verfügbaren Werte in einer Parameter-Dropdownliste Kontrollkästchen hinzugefügt. Am Anfang der Liste befindet sich ein Kontrollkästchen für die Option **Alles auswählen**. Von den Benutzern können die gewünschten Werte ausgewählt werden.<br /><br /> Wenn sich die Daten, auf denen die Werte basieren, häufig ändern, ist die Liste, die dem Benutzer angezeigt wird, möglicherweise nicht auf dem neuesten Stand.|  
|Sichtbar|Aktivieren Sie diese Option, damit der Berichtsparameter bei Ausführung des Berichts oben im Bericht angezeigt wird. Diese Option ermöglicht es Benutzern, Parameterwerte zur Laufzeit auszuwählen.|  
|Ausgeblendet|Aktivieren Sie diese Option, um den Berichtsparameter im veröffentlichten Bericht auszublenden. Die Berichtsparameterwerte können weiterhin auf eine Berichts-URL, in einer Abonnementdefinition oder auf dem Berichtsserver festgelegt werden.|  
|Intern|Aktivieren Sie diese Option, um den Berichtsparameter auszublenden. Im veröffentlichten Bericht kann der Berichtsparameter nur in der Berichtsdefinition angezeigt werden.|  
|Verfügbare Werte|Wenn Sie für einen Parameter verfügbare Werte angegeben haben, werden die gültigen Werte immer als Dropdownliste angezeigt. Angenommen, Sie geben Sie Verfügbare Werte für eine `DateTime` Parameter, eine Dropdown-Liste für Datumsangaben, die im Parameterbereich anstelle eines Kalendersteuerelements wird angezeigt. Zur Gewährleistung der Konsistenz einer Liste mit Werten zwischen dem Bericht und den Unterberichten können Sie eine Option für die Datenquelle festlegen, sodass für alle Abfragen in den Datasets, die dieser Datenquelle zugeordnet sind, eine einzelne Transaktion verwendet wird.<br /><br /> **\*\* Sicherheitshinweis \* \***  In Berichten, die einen Parameter vom Datentyp enthält `Text`, achten Sie darauf, dass Sie eine Liste der verfügbaren Werte (auch als Liste der gültigen Werte bezeichnet) verwenden, und stellen Sie sicher, dass jeder Benutzer mit dem Ausführen des Berichts nur die Berechtigungen zum Anzeigen der Daten im Bericht. Weitere Informationen finden Sie unter [ &#40;Berichts-Generator&#41;](../report-builder/security-report-builder.md).|  
|Standardwerte|Legen Sie Standardwerte aus einer Abfrage oder aus einer statischen Liste fest.<br /><br /> Besitzt jeder Parameter einen Standardwert, wird der Bericht beim erstmaligen Anzeigen automatisch ausgeführt.|  
|Erweitert:|Legen Sie das Berichtsdefinitionsattribut `UsedInQuery` fest. Dies ist ein Wert, mit dem angegeben wird, ob sich dieser Parameter direkt oder indirekt auf die Daten in einem Bericht auswirkt.<br /><br /> **Aktualisierungszeitpunkt automatisch bestimmen**<br /> Wählen Sie diese Option aus, wenn der Wert vom Berichtsprozessor festgelegt werden soll. Der Wert ist `True`, wenn der Berichtsprozessor eine Datasetabfrage mit einem direkten oder indirekten Verweis auf diesen Parameter findet oder wenn der Bericht Unterberichte enthält.<br /><br /> **Immer aktualisieren**<br /> Wählen Sie diese Option aus, wenn der Berichtsparameter direkt oder indirekt in einer Datasetabfrage oder einem Parameterausdruck verwendet wird. Diese Option legt `UsedInQuery` auf True fest.<br /><br /> **Nie aktualisieren**<br /> Wählen Sie diese Option aus, wenn der Berichtsparameter nicht direkt oder indirekt in einer Datasetabfrage oder einem Parameterausdruck verwendet wird. Diese Option wird `UsedInQuery` auf "false".<br /><br /> **\*\* Vorsicht \*\*** Verwenden Sie **Nie aktualisieren** mit Vorsicht. Auf dem Berichtsserver `UsedInQuery` Steuerelement Cacheoptionen für Berichtsdaten und gerenderte Berichte sowie Parameteroptionen für momentaufnahmeberichte dienen. Wenn Sie **Nie aktualisieren** falsch festgelegt haben, können falsche Berichtsdaten oder Berichte zwischengespeichert werden oder inkonsistente Daten in Momentaufnahmeberichten entstehen. Weitere Informationen finden Sie unter [Berichtsdefinitionssprache (Report Definition Language, RDL) &#40;SSRS&#41;](../reports/report-definition-language-ssrs.md).|  
  
##  <a name="bkmk_Dataset_Parameters"></a> Datasetabfrage  
 Um Daten in der Datasetabfrage zu filtern, können Sie eine Einschränkungsklausel einschließen, mit der die abgerufenen Daten begrenzt werden. Geben Sie dazu die Werte ein, die im Resultset eingeschlossen oder daraus ausgeschlossen werden sollen.  
  
 Verwenden Sie den Abfrage-Designer für die Datenquelle, um eine parametrisierte Abfrage zu erstellen.  
  
-   Im Falle von [!INCLUDE[tsql](../../includes/tsql-md.md)] -Abfragen unterstützen verschiedene Datenquellen eine unterschiedliche Parametersyntax. Unterstützt werden Parameter, die in der Abfrage anhand der Position oder des Namens identifiziert werden. Weitere Informationen finden Sie unter Themen zu spezifischen externen Datenquellentypen in [Daten zu einem Bericht hinzufügen &#40;Berichts-Generator und SSRS&#41;](../report-data/report-datasets-ssrs.md). Im relationalen Abfrage-Designer müssen Sie die Parameteroption für einen Filter auswählen, um eine parametrisierte Abfrage zu erstellen. Weitere Informationen finden Sie unter [Benutzeroberfläche des relationalen Abfrage-Designers (Berichts-Generator)](../report-data/relational-query-designer-user-interface-report-builder.md).  
  
-   Für Abfragen, die auf einer mehrdimensionalen Datenquelle wie Microsoft SQL Server Analysis Services, SAP NetWeaver BI oder Hyperion Essbase basieren, können Sie angeben, ob ein Parameter auf Basis eines Filters erstellt werden soll, den Sie im Abfrage-Designer angeben. Weitere Informationen finden Sie unter [Abfrage-Designer &#40;Berichts-Generator&#41;](../query-designers-report-builder.md) im Thema über den entsprechenden Abfrage-Designer für die Datenerweiterung.  
  
##  <a name="bkmk_Manage_Parameters"></a> Parameterverwaltung für einen veröffentlichten Bericht  
 Wenn Sie einen Bericht entwerfen, werden Berichtsparameter in der Berichtsdefinition gespeichert. Wenn Sie einen Bericht veröffentlichen, werden Berichtsparameter getrennt von der Berichtsdefinition gespeichert und verwaltet.  
  
 Für einen veröffentlichten Bericht können Sie Folgendes verwenden:  
  
-   **Berichtsparametereigenschaften.** Ändern Sie Berichtsparameterwerte direkt auf dem Berichtsserver, unabhängig von der Berichtsdefinition.  
  
-   **Zwischengespeicherte Berichte.** Zum Erstellen eines Cacheplans für einen Bericht muss jeder Parameter über einen Standardwert verfügen. Weitere Informationen finden Sie unter [Zwischenspeichern von Berichten &#40;SSRS&#41;](../report-server/caching-reports-ssrs.md)bestand darin die einzige Möglichkeit, den Cache vorab zu laden.  
  
-   **Zwischengespeicherte freigegebene Datasets.** Zum Erstellen eines Cacheplans für ein freigegebenes Dataset muss jeder Parameter über einen Standardwert verfügen. Weitere Informationen finden Sie unter [Zwischenspeichern von Berichten &#40;SSRS&#41;](../report-server/caching-reports-ssrs.md)bestand darin die einzige Möglichkeit, den Cache vorab zu laden.  
  
-   **Verknüpfte Berichte.** Sie können verknüpfte Berichte mit voreingestellten Parameterwerten erstellen, um Daten für verschiedene Zielgruppen zu filtern. Weitere Informationen finden Sie unter [Erstellen eines verknüpften Berichts](../reports/create-a-linked-report.md).  
  
-   **Berichtsabonnements.** Sie können Parameterwerte angeben, um Daten unter Verwendung von Abonnements zu filtern und Berichte unter Verwendung von Abonnements zu übermitteln. Weitere Informationen finden Sie unter [Abonnements und Übermittlung &#40;Reporting Services&#41;](../subscriptions/subscriptions-and-delivery-reporting-services.md).  
  
-   **URL-Zugriff** Sie können Parameterwerte in einer URL zu einem Bericht angeben. Sie können auch Berichte ausführen und Parameterwerte mit URL-Zugriff angeben. Weitere Informationen finden Sie unter [URL-Zugriff (SSRS)](../url-access-ssrs.md).  
  
 Parametereigenschaften für einen veröffentlichten Bericht bleiben im Allgemeinen erhalten, wenn Sie die Berichtsdefinition erneut veröffentlichen. Falls die Berichtsdefinition als derselbe Bericht erneut veröffentlicht wird und die Parameternamen und Datentypen unverändert sind, bleiben die Eigenschaftseinstellungen erhalten. Wenn Sie Parameter in der Berichtsdefinition hinzufügen bzw. löschen oder den Datentyp oder den Namen eines vorhandenen Parameters ändern, müssen Sie möglicherweise die Parametereigenschaften in dem veröffentlichten Bericht ändern.  
  
 Nicht alle Parameter können in jedem Fall geändert werden. Wenn ein Berichtsparameter einen Standardwert aus einer Datasetabfrage abruft, kann der Wert für einen veröffentlichten Bericht und im Berichtsserver nicht geändert werden. Der zur Laufzeit verwendete Wert wird bestimmt, wenn die Abfrage ausgeführt wird oder bei ausdruckbasierten Parametern, wenn der Ausdruck ausgewertet wird.  
  
 Die Optionen für die Berichtsausführung können die Verarbeitung von Parametern beeinflussen. Für einen Bericht, der als Momentaufnahme ausgeführt wird, sind keine Parameter zulässig, die von einer Abfrage abgeleitet sind, außer die Abfrage enthält Standardwerte für die Parameter.  
  
##  <a name="bkmk_Parameters_Subscription"></a> Parameter für ein Abonnement  
 Sie können ein Abonnement bedarfsgesteuert oder für eine Momentaufnahme definieren und Parameterwerte angeben, die während der Abonnementverarbeitung verwendet werden sollen.  
  
-   **Bedarfsgesteuerter Bericht.**  Für einen bedarfsgesteuerten Bericht können Sie einen Parameterwert angeben, der sich von dem veröffentlichten Wert unterscheidet, der für den Bericht aufgeführt ist. Angenommen, ein Telefonservicebericht verwendet den Parameter *Time Period* , um Kundendienstanforderungen für den aktuellen Tag, die aktuelle Woche oder den aktuellen Monat zurückzugeben. Wenn der Standardparameterwert für den Bericht auf **today**festgelegt ist, kann Ihr Abonnement mithilfe eines anderen Parameterwertes (z.B. **week** oder **month**) einen Bericht mit wöchentlichen oder monatlichen Zahlen erstellen.  
  
-   **Momentaufnahme.**  Für eine Momentaufnahme muss das Abonnement die für die Momentaufnahme definierten Parameterwerte verwenden. Das Abonnement kann einen Parameterwert, der für eine Momentaufnahme definiert ist, nicht überschreiben. Angenommen, Sie abonnieren einen Umsatzbericht für die Westregion, der als Berichtsmomentaufnahme ausgeführt wird, und die Momentaufnahme gibt **Western** als regionalen Parameterwert an. Wenn Sie in diesem Fall ein Abonnement für diesen Bericht erstellen, müssen Sie den Parameterwert **Western** im Abonnement verwenden. Als optischer Hinweis, dass der Parameter ignoriert wird, werden die Parameterfelder auf der Abonnementseite als schreibgeschützte Felder festgelegt.  
  
     Die Optionen für die Berichtsausführung können die Verarbeitung von Parametern beeinflussen. Parametrisierte Berichte, die als Berichtsmomentaufnahmen ausgeführt werden, verwenden die für die Berichtsmomentaufnahme definierten Parameterwerte. Parameterwerte werden auf der Seite für die Parametereigenschaften des Berichts definiert. Für einen Bericht, der als Momentaufnahme ausgeführt wird, sind keine Parameter zulässig, die von einer Abfrage abgeleitet sind, außer die Abfrage enthält Standardwerte für die Parameter.  
  
     Wenn sich nach dem Definieren des Abonnements ein Parameterwert in der Berichtsmomentaufnahme ändert, deaktiviert der Berichtsserver das Abonnement. Das Deaktivieren des Abonnements zeigt an, dass der Bericht geändert wurde. Um das Abonnement zu aktivieren, öffnen und speichern Sie das Abonnement.  
  
> [!NOTE]  
>  Datengesteuerte Abonnements können Parameterwerte verwenden, die aus einer Abonnentendatenquelle abgerufen werden. Weitere Informationen finden Sie unter [Verwenden einer externen Datenquelle für Abonnentendaten &#40;datengesteuertes Abonnement&#41;](../subscriptions/use-an-external-data-source-for-subscriber-data-data-driven-subscription.md).  
  
 Weitere Informationen finden Sie unter [Abonnements und Übermittlung &#40;Reporting Services&#41;](../subscriptions/subscriptions-and-delivery-reporting-services.md).  
  
##  <a name="bkmk_Parameters_Security"></a> Parameter und das Sichern von Daten  
 Gehen Sie beim Verteilen von parametrisierten Berichten, die vertrauliche Informationen enthalten, mit Vorsicht vor. Ein Benutzer kann auf einfache Weise einen Berichtsparameter durch einen anderen Wert ersetzen. Dies führt dazu, dass unbeabsichtigt Informationen veröffentlicht werden.  
  
 Eine sichere Alternative zum Verwenden von Parametern für Mitarbeiterdaten oder persönliche Daten besteht darin, Daten basierend auf Ausdrücken auszuwählen, die das **UserID** -Feld aus der Users-Auflistung enthalten. Die Users-Auflistung stellt eine Methode bereit, um die Identität des Benutzers, der den Bericht ausführt, abzurufen und diese Identität zum Abrufen von benutzerspezifischen Daten zu verwenden.  
  
> [!IMPORTANT]  
>  In Berichten, die einen Parameter vom Typ enthält `String`, achten Sie darauf, dass Sie eine Liste der verfügbaren Werte (auch als Liste der gültigen Werte bezeichnet) verwenden, und stellen Sie sicher, dass jeder Benutzer, der den Bericht ausführt, nur die erforderlichen Berechtigungen zum Anzeigen der Daten im Bericht hat. Wenn Sie einen Parameter vom Typ definieren `String`, erhält der Benutzer ein Textfeld, das jeden beliebigen Wert annehmen kann. Mit einer Liste der verfügbaren Werte werden die Werte eingeschränkt, die eingegeben werden können. Wenn der Berichtsparameter an einen Datasetparameter gebunden ist und Sie keine Liste mit verfügbaren Werten verwenden, kann ein Benutzer des Berichts SQL-Syntax in das Textfeld eingeben. Damit öffnet er den Bericht und Ihren Server potenziell für einen SQL-Injection-Angriff. Wenn der Benutzer über Berechtigungen zum Ausführen der neuen SQL-Anweisung verfügt, können daraus unerwünschte Ergebnisse auf dem Server resultieren.  
>   
>  Wenn ein Berichtsparameter nicht an einen Datasetparameter gebunden ist und die Parameterwerte im Bericht enthalten sind, können die Benutzer des Berichts Ausdruckssyntax oder eine URL in den Parameterwert eingeben und den Bericht für Excel oder HTML rendern. Wenn anschließend ein anderer Benutzer den Bericht anzeigt und auf die gerenderten Parameterinhalte klickt, führt der Benutzer möglicherweise unbeabsichtigt das bösartige Skript bzw. den bösartigen Link aus.  
>   
>  Um das Risiko der versehentlichen Ausführung schädlicher Skripts zu minimieren, sollten gerenderte Berichte nur aus vertrauenswürdigen Quellen geöffnet werden. Weitere Informationen zum Sichern von Berichten finden Sie unter [Sichere Berichte und Ressourcen](../security/secure-reports-and-resources.md).  
  
##  <a name="bkmk_How_To_Topics"></a> Themen zur Vorgehensweise  
 In diesem Abschnitt finden Sie Prozeduren, in denen Schritt für Schritt das Arbeiten mit Parametern und Filtern erläutert wird.  
  
-   [Hinzufügen, ändern oder Löschen von Berichtsparametern &#40;Berichts-Generator und SSRS&#41;](add-change-or-delete-a-report-parameter-report-builder-and-ssrs.md)  
  
-   [Hinzufügen, ändern oder Löschen von verfügbaren Werten für einen Berichtsparameter &#40;Berichts-Generator und SSRS&#41;](add-change-or-delete-available-values-for-a-report-parameter.md)  
  
-   [Hinzufügen, ändern oder Löschen von Standardwerten für einen Berichtsparameter &#40;Berichts-Generator und SSRS&#41;](add-change-or-delete-default-values-for-a-report-parameter.md)  
  
-   [Ändern der Reihenfolge von Berichtsparametern &#40;Berichts-Generator und SSRS&#41;](change-the-order-of-a-report-parameter-report-builder-and-ssrs.md)  
  
-   [Hinzufügen von kaskadierenden Parametern zu einem Bericht &#40;Berichts-Generator und SSRS&#41;](add-cascading-parameters-to-a-report-report-builder-and-ssrs.md)  
  
-   [Hinzufügen eines Filters zu einem Dataset &#40;Berichts-Generator und SSRS&#41;](../report-data/add-a-filter-to-a-dataset-report-builder-and-ssrs.md)  
  
-   [Hinzufügen von Unterberichten und Parametern &#40;Berichts-Generator und SSRS&#41;](add-a-subreport-and-parameters-report-builder-and-ssrs.md)  
  
-   [Gewusst wie: Verwenden von SSRS-Parametern mit gespeicherten Prozeduren](http://go.microsoft.com/fwlink/p/?LinkId=396970)  
  
## <a name="did-this-article-help-you-were-listening"></a>Fanden Sie diesen Artikel nützlich? Wir hören Ihnen zu  
 Welche Informationen suchen Sie, und haben Sie sie gefunden? Wir nehmen uns Ihr Feedback zu Herzen, um unsere Inhalte zu verbessern. Bitte senden Sie Ihre Kommentare an [sqlfeedback@microsoft.com](mailto:sqlfeedback@microsoft.com?subject=Your%20feedback%20about%20the%20Report%20Parameters%20page)  
  
##  <a name="bkmk_Related_Topics"></a> Verwandte Inhalte  
 [Konfigurieren von SSRS-Berichtsparametern (Quiz)](http://go.microsoft.com/fwlink/p/?LinkID=306443)  
  
 [Lernprogramm: Hinzufügen eines Parameters zum Bericht &#40;Berichts-Generator&#41;](../tutorial-add-a-parameter-to-your-report-report-builder.md)  
  
 [Was Sie schon immer invalidreportparameterexception im Berichterstellungsdienst](http://go.microsoft.com/fwlink/p/?LinkId=393118)  
  
 [Berichtsbeispiele (Berichts-Generator und SSRS)](http://go.microsoft.com/fwlink/?LinkId=198283)  
  
 [Ausdruck verwendet wird, in Berichten &#40;Berichts-Generator und SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md)  
  
 [Ausdrücke &#40;Berichts-Generator und SSRS&#41;](expressions-report-builder-and-ssrs.md)  
  
 [Filtern, gruppieren und Sortieren von Daten &#40;Berichts-Generator und SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md)  
  
 [Sicherheit &#40;Berichts-Generator&#41;](../report-builder/security-report-builder.md)  
  
 [Interaktive Sortierung, Dokumentstrukturen und Links &#40;Berichts-Generator und SSRS&#41;](interactive-sort-document-maps-and-links-report-builder-and-ssrs.md)  
  
 [Drillthrough, Drilldown, Unterberichte und geschachtelte Datenbereiche &#40;Berichts-Generator und SSRS&#41;](drillthrough-drilldown-subreports-and-nested-data-regions.md)  
  
  