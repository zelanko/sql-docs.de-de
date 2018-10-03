---
title: Zwischenspeichern von Optionen zur Cacheaktualisierung (Berichts-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 227da40c-6bd2-48ec-aa9c-50ce6c1ca3a6
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: e1fb1f7f249d8252873eb7ecc879aac05fb496b4
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48081550"
---
# <a name="cache-refresh-options-report-manager"></a>Optionen zur Cacheaktualisierung (Berichts-Manager)
  Verwenden Sie die Seite Optionen zur Cacheaktualisierung, um Zeitpläne zum Vorabladen des Caches mit temporären Datenkopien für einen Bericht oder ein freigegebenes Dataset zu erstellen. Ein Aktualisierungsplan enthält einen Zeitplan und bietet die Möglichkeit, Werte für Parameter anzugeben oder zu überschreiben. Bei einem freigegebenen Dataset können keine Werte für Parameter überschrieben werden, die als schreibgeschützt gekennzeichnet sind. Sie können auf der Seite mit den Aktualisierungsoptionen auch mehrere Aktualisierungspläne erstellen und verwenden.  
  
 Die Standardrollenzuweisungen, mit denen Sie verknüpfte Berichte und freigegebene Datasets für Cacheaktualisierungspläne hinzufügen, löschen, ändern und anzeigen können, lauten Inhalts-Manager, Meine Berichte und Verleger.  
  
> [!NOTE]  
>  Diese Funktion ist nicht in jeder Edition von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]verfügbar. Eine Liste der Funktionen, die von den Editionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]unterstützt werden, finden Sie unter [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
## <a name="to-open-the-cache-refresh-plan-properties-page-for-a-report-or-shared-dataset"></a>So öffnen Sie die Eigenschaftenseite "Cacheaktualisierungsplan" für einen Bericht oder ein freigegebenes Dataset  
  
1.  Öffnen Sie den Berichts-Manager, und suchen Sie den Bericht oder das freigegebene Dataset, für den bzw. das Sie die Eigenschaften des Cacheaktualisierungsplans konfigurieren möchten.  
  
2.  Zeigen Sie auf den Bericht oder das freigegebene Dataset, und klicken Sie auf den Dropdownpfeil.  
  
3.  Klicken Sie in der Dropdownliste auf **Verwalten**. Die Seite **Allgemeine Eigenschaften** wird geöffnet.  
  
4.  Klicken Sie auf die Registerkarte **Cacheaktualisierungsplan** .  
  
5.  Um einen neuen Cacheplan zu erstellen, klicken Sie auf **Neuer Cacheaktualisierungsplan**.  
  
    > [!NOTE]  
    >  Sie müssen den SQL Server-Agent-Dienst aktivieren und starten, um einen Cacheaktualisierungsplan zu erstellen.  
  
6.  Um eine Kopie eines Cacheplans zu erstellen und dann anzupassen, klicken Sie auf **Neu aus vorhandenem**.  
  
## <a name="cache-refresh-options"></a>Optionen zur Cacheaktualisierung  
 **Delete**  
 Löscht alle derzeit ausgewählten Aktualisierungspläne.  
  
 **Neu aus vorhandenem**  
 Diese Option wird nur aktiviert, wenn genau ein Cacheaktualisierungsplan ausgewählt ist. Durch diese Option wird ein neuer Aktualisierungsplan erstellt, der vom ursprünglichen Plan kopiert wird. Die Seite Cacheaktualisierungsplan wird geöffnet und enthält bereits die Details des ausgewählten Plans. Anschließend können Sie die Optionen für den Aktualisierungsplan ändern und den Plan mit einer neuen Beschreibung speichern.  
  
 **Neuer cacheaktualisierungsplan**  
 Klicken Sie auf diese Option, um einen neuen Aktualisierungsplan zu erstellen, der in den aktuellen Cacheaktualisierungsoptionen verwendet werden soll.  
  
 **Bearbeiten**  
 Aktivieren Sie diese Option, um den aktuellen Aktualisierungsplan zu bearbeiten.  
  
## <a name="cache-refresh-plan-options"></a>Optionen für Cacheaktualisierungspläne  
 **Beschreibung**  
 Geben Sie eine Beschreibung für den Cacheaktualisierungsplan an.  
  
 **Elementspezifischer Zeitplan**  
 Wählen Sie diese Option, um einen Zeitplan zu erstellen, die nur von diesem Element verwendet wird.  
  
 **Konfigurieren**  
 Klicken Sie auf diese Schaltfläche, um die Seite Zeitplan zu öffnen, auf der Sie Angaben zur Häufigkeit machen können.  
  
 Weitere Informationen finden Sie unter [neuer Zeitplan: Bearbeiten der Zeitplanseite &#40;Berichts-Manager&#41;](../../2014/reporting-services/new-schedule-edit-schedule-page-report-manager.md).  
  
 **Freigegebenen Zeitplan**  
 Aktivieren Sie diese Option, um einen vorhandenen Zeitplan auszuwählen.  
  
 Weitere Informationen finden Sie unter [erstellen, ändern und Löschen von Zeitplänen](subscriptions/create-modify-and-delete-schedules.md).  
  
 **@\<** *Parameter* **>**  
 Geben Sie eine Kombination von Parameterwerten an. Dieser Abschnitt wird nur angezeigt, wenn das aktuelle Dataset oder der aktuelle Bericht über Parameter verfügt.  
  
 Siehe [Angeben von Parametern](#Parameters) im nächsten Abschnitt.  
  
 **Standard verwenden**  
 Aktivieren Sie diese Option, um den vordefinierten Standardwert für diesen Parameter zu verwenden.  
  
##  <a name="Parameters"></a> Angeben von Parametern  
 Zum Erstellen eines Cacheaktualisierungsplans muss jeder Parameter für einen Bericht oder ein freigegebenes Dataset über einen Wert verfügen. Wenn für den Bericht oder das freigegebene Datasetelement in der Definition kein Standardwert angegeben ist, müssen Sie einen Wert angeben. Wenn ein Standardwert vorhanden ist, müssen Sie hier keinen Wert zur Verfügung stellen. Wenn Sie trotzdem einen Wert angeben, überschreibt dieser den Standardwert.  
  
 Um mehrere Kombinationen von Parameterwerten anzugeben, erstellen Sie einen separaten Cacheaktualisierungsplan für jede Kombination.  
  
 Wenn Sie Parameter für einen Bericht oder ein freigegebenes Dataset hinzufügen, ändern oder löschen, kann sich dies auf den Cacheaktualisierungsplan auswirken. Wenn Sie einen Parameter mit einem Standardwert für einen Bericht hinzufügen, einen Parameter entfernen bzw. den Datentyp oder die Schreibschutzoption für den Parameter eines freigegebenen Datasets ändern, werden die Änderungen bei der nächsten Verarbeitung des Cacheaktualisierungsplans wirksam.  
  
### <a name="shared-dataset-parameters"></a>Parameter für freigegebene Datasets  
 Die folgenden Informationen werden für ein freigegebenes Dataset aus der zugehörigen Definition abgeleitet:  
  
-   **Name** Gibt den Namen des Abfrageparameters an.  
  
-   **Type** Gibt den Datentyp des Abfrageparameters an. Da dieser Datentyp unbekannt ist, bis die Datasetabfrage vom Datenanbieter verarbeitet wird, kann der Datentyp erst überprüft werden, nachdem das freigegebene Dataset verarbeitet wurde.  
  
-   **Nullable** Gibt an, ob NULL ein gültiger Wert ist.  
  
-   **ReadOnly** Gibt an, ob dieser Parameter in der Definition des freigegebenen Datasets als schreibgeschützt gekennzeichnet ist. Schreibgeschützte Parameter werden nicht in der Parameterliste für Cacheaktualisierungsoptionen angezeigt. Für diese Parameter muss in der Definition des freigegebenen Datasets ein Standardwert vorhanden sein.  
  
-   **DefaultValues** Standardwerte, die in der Definition des freigegebenen Datasets angegeben wurden. Abfrageparameter können mehrwertig sein. Um die Standardwerte zu überschreiben, geben Sie neue Werte in die Eingabeaufforderungsbereiche des Textfelds ein.  
  
 Wenn in der Definition des freigegebenen Datasets die Option **In Abfrage auslassen** für einen Parameter angegeben ist, müssen Sie keinen Standardwert bereitstellen. Dieses Flag gibt an, dass der Datasetparameter in der Abfrage nicht verwendet wird. Der Parameter ist z. B. in der Definition des freigegebenen Datasets vorhanden, da es sich um einen Berichtsparameter handelt, der ausschließlich im Datasetfilter verwendet wird.  
  
 Um Optionen für Datasetparameter anzuzeigen oder zu ändern, müssen Sie die Definition des freigegebenen Datasets bearbeiten. Weitere Informationen finden Sie unter [Verwalten von freigegebenen Datasets](report-data/manage-shared-datasets.md).  
  
### <a name="report-parameters"></a>Berichtsparameter  
 Damit Sie einen Cacheaktualisierungsplan erstellen können, muss jeder Parameterwert für einen Bericht gültig sein. Sie müssen für jeden Berichtsparameter einen Standardwert eingeben oder auswählen. Der festgelegte Wert überschreibt den für den Berichtsparameter auf dem Berichtsserver definierten Standardwert.  
  
 Parameter müssen die Anforderungen erfüllen, die in den Parametereigenschaften auf dem Berichtsserver angegeben wurden. Wenn die Eigenschaft AllowBlank für einen Berichtsparameter false ist, ist eine leere Zeichenfolge beispielsweise keinen gültigen Wert.  
  
 Zum Anzeigen oder Ändern von Optionen für Berichtsparameter müssen Sie die Berichtsparameter im Bericht oder unabhängig auf dem Berichtsserver bearbeiten. Weitere Informationen finden Sie unter [Berichtsparameter-Konzept &#40;Berichts-Generator und SSRS&#41;](report-design/report-parameters-concepts-report-builder-and-ssrs.md).  
  
## <a name="conditions-that-cause-a-cache-refresh-plan-to-be-inactive"></a>Bedingungen, die bewirken, dass ein Cacheaktualisierungsplan deaktiviert wird  
 Ein Cacheaktualisierungsplan für ein freigegebenes Dataset oder einen Bericht kann unter folgenden Bedingungen deaktiviert werden.  
  
-   Die Cacheoption für freigegebene Datasets oder Berichte ist deaktiviert.  
  
-   Die erforderlichen Parameterwerte sind definiert, ungültig oder fehlen. Alle Abfragen für einen Bericht müssen gültig sein, bevor der Bericht verarbeitet wird. Für einen Bericht, der Unterberichte enthält, werden alle Datasetabfragen, einschließlich Datasets für den Unterbericht, zuerst verarbeitet. Der Bericht kann erst ausgeführt werden, nachdem ein Dataset erfolgreich verarbeitet wurde.  
  
## <a name="conditions-that-cause-a-cache-refresh-plan-to-be-reactivated"></a>Bedingungen, die bewirken, dass ein Cacheaktualisierungsplan erneut aktiviert wird  
 Nach der Deaktivierung eines Plans führen Sie einen der folgenden Schritte aus, um die Auswertung eines Cacheaktualisierungsplans auszulösen:  
  
-   Ändern Sie eine Option für den Plan.  
  
-   Aktivieren Sie das Zwischenspeichern für ein freigegebenes Dataset oder einen Bericht, das bzw. der dem Aktualisierungsplan zugeordnet ist.  
  
-   Deaktivieren oder aktivieren Sie die Schreibschutzoption für einen Datasetabfrageparameter, der dem Aktualisierungsplan zugeordnet ist, und speichern Sie dann die neue Definition auf dem Berichtsserver.  
  
## <a name="see-also"></a>Siehe auch  
 [Aufgaben auf Elementebene](security/tasks-and-permissions-item-level-tasks.md)   
 [Berichts-Manager &#40;einheitlicher SSRS-Modus&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md)   
 [Berichts-Manager-F1-Hilfe](../../2014/reporting-services/report-manager-f1-help.md)   
 [Zwischenspeichern von Berichten (SSRS)](report-server/caching-reports-ssrs.md)   
 [Verwalten von freigegebenen Datasets](report-data/manage-shared-datasets.md)  
  
  
