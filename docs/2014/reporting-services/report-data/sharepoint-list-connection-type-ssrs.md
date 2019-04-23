---
title: SharePoint-Listenverbindungstyp (SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 2c4adf2f-e9c4-4fae-bd3c-97fe64436caf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 43864fb135faf61a2a0205199d7717d7b5c04026
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "59946886"
---
# <a name="sharepoint-list-connection-type-ssrs"></a>SharePoint-Listenverbindungstyp (SSRS)
  Wenn Sie Daten aus einer Microsoft SharePoint-Liste in den Bericht einschließen möchten, müssen Sie ein Dataset hinzufügen oder erstellen, das auf einer Berichtsdatenquelle vom Typ "Microsoft SharePoint-Liste" basiert. Dies ist ein integrierter Datenquellentyp, der auf der Microsoft SQL Server Reporting Services-Datenerweiterung für die SharePoint-Liste basiert. Verwenden Sie diesen Datenquellentyp, um eine Verbindung mit [!INCLUDE[SPF2010](../../includes/spf2010-md.md)]-, [!INCLUDE[SPS2010](../../includes/sps2010-md.md)]-, [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] 3.0- und [!INCLUDE[offSPServ](../../includes/offspserv-md.md)] 2007-Websites herzustellen und Listendaten abzurufen.  
  
 Verwenden Sie die Informationen in diesem Thema, um eine Datenquelle zu erstellen. Schrittweise Anweisungen finden Sie unter [hinzufügen und Prüfen einer Datenverbindung oder Datenquelle &#40;Berichts-Generator und SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md).  
  
##  <a name="Connection"></a> Verbindungszeichenfolge  
 Die Verbindungszeichenfolge für eine SharePoint-Liste ist die URL zur SharePoint-Website oder -Unterwebsite, z. B. `http://MySharePointWeb/MySharePointSite` oder `http://MySharePointWeb/MySharePointSite/Subsite`.  
  
 Im Abfrage-Designer werden automatisch die SharePoint-Listen angezeigt, für die Sie ausreichende Zugriffsberechtigungen besitzen.  
  
 Weitere Beispiele für Verbindungszeichenfolgen finden Sie unter [Datenverbindungen, Datenquellen und Verbindungszeichenfolgen in Berichts-Generator](../data-connections-data-sources-and-connection-strings-in-report-builder.md).  
  
##  <a name="Credentials"></a> Anmeldeinformationen  
 Anmeldeinformationen sind erforderlich, um Abfragen auszuführen und den Bericht lokal oder vom Berichtsserver aus in der Vorschau anzuzeigen. Nachdem Sie den Bericht veröffentlicht haben, müssen Sie eventuell die Anmeldeinformationen für die Datenquelle ändern, sodass die Berechtigungen zum Abrufen der Daten beim Ausführen des Berichts auf dem Berichtsserver gültig sind. Die von dieser Datenerweiterung unterstützten Anmeldeinformationstypen hängen von der SharePoint-Technologiekonfiguration für die als Datenquelle verwendete SharePoint-Liste ab.  
  
 In den folgenden Tabellen wird das Verhalten beim Abrufen von Anmeldeinformationen für die SharePoint-Listenerweiterung erläutert, und zwar bei der Verbindung mit der SharePoint-Liste einer lokalen Farm oder einer SharePoint-Remoteliste.  
  
 **Tabelle 1** wird für Berichte verwendet, die auf einer älteren Windows SharePoint-Website bereitgestellt werden. Ältere Windows-Websites unterstützen ausschließlich Kerberos, NTLM und die formularbasierte Authentifizierung (FBA). **Tabelle 2** wird für Berichte verwendet, die auf einer SharePoint-Website mit anspruchsbasierter Authentifizierung bereitgestellt werden.  
  
 **Tabelle 1**  
  
||Unterstützte Anmeldeinformationen|Windows-Authentifizierung im klassischen Modus|<sup>3</sup> Anspruchsauthentifizierung|  
|-|---------------------------|-----------------------------------------|----------------------------------------|  
|SharePoint-Liste einer lokalen Farm|Windows-Authentifizierung (integriert) oder SharePoint-Benutzertoken|Ja|Ja|  
||Gespeichert, Eingabeaufforderung, Keine (mit Windows-Anmeldeinformationen<sup>1</sup>)|Ja|Nein|  
|SharePoint-Remoteliste|Windows-Authentifizierung (integriert) oder SharePoint-Benutzertoken|Ja|Keine<sup>2</sup>|  
||Gespeichert, Eingabeaufforderung, Keine (mit Windows-Anmeldeinformationen<sup>1</sup>)|Ja|Keine<sup>2</sup>|  
  
 **Tabelle 2**  
  
||Unterstützte Anmeldeinformationen|Windows-Authentifizierung im klassischen Modus|<sup>3</sup> Anspruchsauthentifizierung|  
|-|---------------------------|-----------------------------------------|----------------------------------------|  
|SharePoint-Liste einer lokalen Farm|Windows-Authentifizierung (integriert) oder SharePoint-Benutzertoken|Ja|Ja|  
||Gespeichert, Eingabeaufforderung, Keine (mit Windows-Anmeldeinformationen<sup>1</sup>)|Nein|Nein|  
|SharePoint-Remoteliste|Windows-Authentifizierung (integriert) oder SharePoint-Benutzertoken|Ja|Keine<sup>2</sup>|  
||Gespeichert, Eingabeaufforderung, Keine (mit Windows-Anmeldeinformationen<sup>1</sup>)|Nein|Keine<sup>2</sup>|  
  
 <sup>1</sup> gespeicherte Anmeldeinformationen oder Eingabeaufforderung Anmeldeinformationen werden bei nicht-Windows-Anmeldeinformationen wird nicht unterstützt.  
  
 <sup>2</sup> formularbasierte und anspruchsbasierte Authentifizierung werden SharePoint-remotelisten nicht unterstützt.  
  
 <sup>3</sup> Windows-Authentifizierung, formularbasierte Authentifizierung (FBA), Secure Application Markup Language (SAML) Token, sonstige Identitätsanbieter oder eine Kombination von mehr als einer der oben genannten aufgeführten Authentifizierungsanbieter.  
  
 **Windows-Authentifizierung**  
 Diese Option wird nicht für eine SharePoint-Technologie unterstützt, die für die Verwendung mit einem Berichtsserver im Modus „Vertrauenswürdiges Konto“ konfiguriert ist. Dies gilt nur für Versionen vor SQL Server 2012 Reporting Services.  
  
 Bei einer SharePoint-Technologie, die für die Verwendung mit einem Berichtsserver im integrierten Windows-Modus konfiguriert ist, gilt diese Option sowohl für den aktuellen Windows-Benutzer als auch den aktuellen SharePoint-Benutzer.  
  
 Diese Option wird nicht für eine SharePoint-Technologie unterstützt, die für die Verwendung ohne Berichtsserver (lokaler Modus) konfiguriert ist. Weitere Informationen zum lokalen Modus finden Sie unter [Berichte im lokalen Modus im Vergleich mit Berichten im verbundenen Modus im Berichts-Viewer (Reporting Services im SharePoint-Modus)](../local-vs-connected-mode-report-viewer-reporting-services-sharepoint-mode.md).  
  
 **Anmeldeinformationen sind nicht erforderlich (keine Anmeldeinformationen verwenden):**  
 Diese Option setzt voraus, dass zuvor das Konto für die unbeaufsichtigte Ausführung auf dem Berichtsserver konfiguriert wird. Weitere Informationen finden Sie unter [Konfigurieren des Kontos für die unbeaufsichtigte Ausführung (SSRS-Konfigurations-Manager)](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md).  
  
 Weitere Informationen zur Unterstützung der anspruchsbasierten Authentifizierung in der Microsoft BI-Struktur finden Sie unter [Verwenden der anspruchsbasierten Authentifizierung in der Microsoft BI-Struktur](https://social.technet.microsoft.com/wiki/contents/articles/15274.using-claims-authentication-across-the-microsoft-bi-stack.aspx).  
  
 Weitere Informationen finden Sie unter [Datenverbindungen, Datenquellen und Verbindungszeichenfolgen in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md), [angeben von Anmeldeinformationen im Berichts-Generator](../specify-credentials-in-report-builder.md), und [von unterstützte Datenquellen Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md).  
  
##  <a name="Query"></a> Abfragen  
 Erstellen Sie auf Grundlage der Datenquelle ein neues Dataset, und öffnen Sie dann den entsprechenden Abfrage-Designer, um eine Abfrage zu entwerfen. Weitere Informationen finden Sie unter [Erstellen eines freigegebenen Datasets oder eingebetteten Datasets &#40;Berichts-Generator und SSRS&#41;](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md).  
  
 Der grafische Abfrage-Designer für SharePoint-Listen zeigt vier Bereiche an:  
  
 **SharePoint-Listen**  Zeigt eine Liste aller SharePoint-Listen auf der Website für diese Datenquelle an. Wählen Sie eine Liste aus, und wählen Sie dann die Felder aus, die Sie in die Abfrage einschließen möchten. Die Namen der Felder in diesem Bereich sind die SharePoint-Anzeigenamen, die auch als Anzeigenamen bezeichnet werden. Zeigen Sie mit dem Mauszeiger auf ein Element, um die folgenden Eigenschaften in der QuickInfo anzuzeigen:  
  
-   **Name** Der eindeutige Name des Felds.  
  
-   **Bezeichner** Der eindeutige Bezeichner des Felds.  
  
-   **Feldtyp** Der Datentyp des Felds.  
  
-   **Ausgeblendet** Zeigt an, ob das Feld in der SharePoint-Listenansicht angezeigt wird.  
  
 Die Auswahl von Feldern aus mehreren Listen wird nicht unterstützt. Sie können einen Datensatz für jede Liste erstellen und Felder aus jedem Datensatz auswählen. Wenn die Listen über ein gemeinsames Feld verfügen, können Sie die Suchfunktion in einem Tablix-Datenbereich verwenden, der an einen Datensatz gebunden ist, um einen Wert aus dem anderen Datensatz abzurufen, der nicht an den Datenbereich gebunden ist. Weitere Informationen finden Sie unter [Lookup-Funktion (Berichts-Generator und SSRS)](../report-design/report-builder-functions-lookup-function.md).  
  
-   **Ausgewählte Felder**  Zeigt die Felder an, die Sie ausgewählt haben. Die Namen der Felder in diesem Bereich sind Anzeigenamen, die ein SharePoint-Benutzer angegeben hat. Wenn Sie den Abfrage-Designer schließen, werden diese Namen in der Dataset-Feldauflistung im Berichtsdatenbereich angezeigt. Die Beziehung zwischen eindeutigen Namen und Anzeigenamen steht auf der Seite [Dataseteigenschaften (Dialogfeld), Felder (Berichts-Generator)](../dataset-properties-dialog-box-fields-report-builder.md).  
  
-   **Übernommene Filter**  Schränkt die Daten ein, die aus der SharePoint-Liste zurückgegeben werden, bevor die Daten an den Bericht zurückgegeben werden. Wählen Sie den Feldnamen, den Operator und den Wert aus, die verwendet werden sollen, um die abgerufenen Daten in der Liste einzuschränken. Die Operatoren hängen vom Datentyp des Werts ab, den Sie auswählen.  
  
     Sie können die Sortierreihenfolge nicht ändern und keine Gruppen im grafischen Abfrage-Designer angeben. Legen Sie festgelegte Sortierungsausdrücke für das Berichtsdataset und Gruppenausdrücke für die Datenbereiche des Berichts aus, wenn Sie dies möchten. Abfrageparameter werden nicht unterstützt. Um Daten im Bericht zu filtern, verwenden Sie Berichtsfilter oder Berichtsparameter, die Sie erstellen. Weitere Informationen finden Sie unter [Filtern, Gruppieren und Sortieren von Daten &#40;Berichts-Generator und SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) und [Berichtsparameter &#40;Berichts-Generator und Berichts-Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md).  
  
-   **Abfrageergebnisse**  Zeigt Beispielzeilen an, die bei Ausführung der Abfrage zurückgegeben werden. Wenn sich die Werte in der SharePoint-Liste auf der SharePoint-Website häufig ändern, unterscheiden sich die in den Abfrageergebnissen angezeigten Werte möglicherweise von den Werten, die im Bericht angezeigt werden.  
  
-   **Ausgewählte Felder**  Zeigt die Felder an, die Sie ausgewählt haben. Die Namen der Felder in diesem Bereich sind Anzeigenamen, die ein SharePoint-Benutzer angegeben hat. Wenn Sie den Abfrage-Designer schließen, werden diese Namen in der Dataset-Feldauflistung im Berichtsdatenbereich angezeigt. Die Beziehung zwischen eindeutigen Namen und Anzeigenamen steht auf der Seite [Dataseteigenschaften (Dialogfeld), Felder (Berichts-Generator)](../dataset-properties-dialog-box-fields-report-builder.md).  
  
-   **Übernommene Filter**  Schränkt die Daten ein, die aus der SharePoint-Liste zurückgegeben werden, bevor die Daten an den Bericht zurückgegeben werden. Wählen Sie den Feldnamen, den Operator und den Wert aus, die verwendet werden sollen, um die abgerufenen Daten in der Liste einzuschränken. Die Operatoren hängen vom Datentyp des Werts ab, den Sie auswählen.  
  
     Sie können die Sortierreihenfolge nicht ändern und keine Gruppen im grafischen Abfrage-Designer angeben. Legen Sie festgelegte Sortierungsausdrücke für das Berichtsdataset und Gruppenausdrücke für die Datenbereiche des Berichts aus, wenn Sie dies möchten. Abfrageparameter werden nicht unterstützt. Um Daten im Bericht zu filtern, verwenden Sie Berichtsfilter oder Berichtsparameter, die Sie erstellen. Weitere Informationen finden Sie unter [Filtern, Gruppieren und Sortieren von Daten &#40;Berichts-Generator und SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) und [Berichtsparameter &#40;Berichts-Generator und Berichts-Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md).  
  
-   **Abfrageergebnisse**  Zeigt Beispielzeilen an, die bei Ausführung der Abfrage zurückgegeben werden. Wenn sich die Werte in der SharePoint-Liste auf der SharePoint-Website häufig ändern, unterscheiden sich die in den Abfrageergebnissen angezeigten Werte möglicherweise von den Werten, die im Bericht angezeigt werden.  
  
 Weitere Informationen finden Sie unter [Designer für SharePoint-Listenabfragen (Berichts-Generator)](sharepoint-list-query-designer-report-builder.md).  
  
### <a name="query-text"></a>Abfragetext  
 Wenn Sie die Abfrage anzeigen möchten, die im grafischen Abfrage-Designer generiert wird, wechseln Sie zum textbasierten Abfrage-Designer. In dieser Ansicht können Sie die XML anzeigen, die vom grafischen Abfrage-Designer erstellt wird. Die XML umfasst Elemente für den Listennamen, die Feldauflistung und den Filter.  
  
#### <a name="example-1-specified-fields-for-a-list"></a>Beispiel 1. Angegebene Felder für eine Liste  
 Im folgenden Beispiel wird eine wohlgeformte SharePoint-Abfrage dargestellt:  
  
```  
<RSSharePointList>  
<listName>MyList</listName>  
<viewFields>  
  <FieldRef Name="Field1"/>  
  <FieldRef Name="Field4"/>  
</viewFields>  
<Query>  
  <Where>  
    <And>  
      <Gt>  
        <FieldRef Name="Field1"/>  
        <Value Type="Integer">1</Value>  
      </Gt>  
      <IsNotNull>  
        <FieldRef Name="Field2"/>  
        <Value Type="string"/>  
      </IsNotNull>   
    </And>  
  </Where>  
</Query>  
</RSSharePointList>  
```  
  
 Sie können diese Ansicht der Abfrage bearbeiten, solange es wohlgeformter XML-Text bleibt.  
  
#### <a name="example-2-all-fields-for-a-list"></a>Beispiel 2. Alle Felder für eine Liste  
 Sie können auch nur den Namen einer Liste angeben, und alle Felder einschließlich der ausgeblendete Felder werden zurückgegeben. Im folgenden Beispiel werden alle Felder aus einer Liste, die Tasks genannt wird:  
  
```  
<RSSharePointList>  
<listName>Tasks</listName>  
</RSSharePointList>  
```  
  
 Alle Felder für die Liste "Tasks" werden in den Abfrageergebnissen zurückgegeben.  
  
##  <a name="Parameters"></a> Parameter  
 Parameter werden von dieser Datenerweiterung nicht unterstützt.  
  
  
##  <a name="HowTo"></a> Themen zur Vorgehensweise  
 Dieser Abschnitt enthält schrittweise Anweisungen zum Arbeiten mit Datenverbindungen, Datenquellen und Datasets.  
  
 [Hinzufügen und Prüfen einer Datenverbindung oder Datenquelle &#40;Berichts-Generator und SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md)  
  
 [Erstellen eines freigegebenen Datasets oder eingebetteten Datasets &#40;Berichts-Generator und SSRS&#41;](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)  
  
 [Hinzufügen eines Filters zu einem Dataset &#40;Berichts-Generator und SSRS&#41;](add-a-filter-to-a-dataset-report-builder-and-ssrs.md)  
  
  
##  <a name="Related"></a> Verwandte Abschnitte  
 Diese Abschnitte der Dokumentation enthalten umfassende grundlegende Informationen zu Berichtsdaten sowie Informationen zum Definieren, Anpassen und Verwenden der mit Daten zusammenhängenden Teile eines Berichts.  
  
 [Hinzufügen von Daten zu einem Bericht &#40;Berichts-Generator und SSRS&#41;](report-datasets-ssrs.md)  
 Bietet eine Übersicht über den Zugriff auf Daten für den Bericht.  
  
 [Datenverbindungen, Datenquellen und Verbindungszeichenfolgen in Berichts-Generator](../data-connections-data-sources-and-connection-strings-in-report-builder.md)  
 Enthält Informationen zu Datenverbindungen und Datenquellen.  
  
 [Erstellen von Berichten zu eingebetteten und freigegebenen Datasets &#40;Berichts-Generator und SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 Enthält Informationen zu eingebetteten und freigegebenen Datasets.  
  
 [Datasetfelder-Sammlung &#40;Berichts-Generator und SSRS&#41;](dataset-fields-collection-report-builder-and-ssrs.md)  
 Enthält Informationen zur von der Abfrage generierten Datasetfeldauflistung.  
  
 [Von Reporting Services unterstützte Datenquellen (SSRS)](../create-deploy-and-manage-mobile-and-paginated-reports.md) in der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Dokumentation der [Onlinedokumentation](https://go.microsoft.com/fwlink/?linkid=121312) zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
 Enthält ausführliche Informationen zur Plattform- und Versionsunterstützung für die einzelnen Datenerweiterungen.  
  
  
## <a name="see-also"></a>Siehe auch  
 [Berichtsparameter &#40;Berichts-Generator und Berichts-Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md)   
 [Filtern, Gruppieren und Sortieren von Daten &#40;Berichts-Generator und SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [Ausdrücke &#40;Berichts-Generator und SSRS&#41;](../report-design/expressions-report-builder-and-ssrs.md)  
  
  
