---
title: Erstellen eines domänenbasierten Attributs
ms.custom: ''
ms.date: 07/25/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- domain-based attributes [Master Data Services], creating
- creating domain-based attributes [Master Data Services]
- attributes [Master Data Services], creating domain-based attributes
ms.assetid: 11c31c9f-e6cc-47b7-b76a-d691f84c93c6
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 72f415b6a814019b99d4e73db482286f9d5560b1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "73728530"
---
# <a name="create-a-domain-based-attribute-master-data-services"></a>Erstellen eines domänenbasierten Attributs (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Erstellen Sie in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]ein domänenbasiertes Attribut, um die Werte eines Attributs mit Elementen aus einer Entität aufzufüllen.  
  
## <a name="prerequisites"></a>Voraussetzungen  
 So führen Sie diese Prozedur aus  
  
-   Sie müssen über die Berechtigung verfügen, auf den Funktionsbereich **Systemverwaltung** zuzugreifen.  
  
-   Sie müssen ein Modelladministrator sein. Weitere Informationen finden Sie unter [Administratoren &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
-   Eine Entität muss vorhanden sein, um als Quelle der Attributwerte verwendet zu werden. Um zum Beispiel auf der Grundlage der Color-Entität ein domänenbasiertes Attribut zu erstellen, müssen Sie zuerst die Color-Entität erstellen. Weitere Informationen finden Sie unter [Erstellen einer Entität &#40;Master Data Services&#41;](../master-data-services/create-an-entity-master-data-services.md).  
  
-   Eine Entität muss vorhanden sein, um das Attribut dafür erstellen zu können. Weitere Informationen finden Sie unter [Erstellen einer Entität &#40;Master Data Services&#41;](../master-data-services/create-an-entity-master-data-services.md).  
  
## <a name="attribute-information"></a>Attributinformationen  
 Für jedes erstellte Attribut wird dem Raster eine Zeile mit sieben Spalten hinzugefügt. In der folgenden Tabelle werden diese Spalten beschrieben.  
  
|Column|BESCHREIBUNG|  
|------------|-----------------|  
|Status|Der Attributstatus.<br /><br /> Wenn Sie auf Speichern klicken, wird das Bild ![Symbol zum Aktualisieren des Status](../master-data-services/media/mds-statusicon-updating.png "Symbol für Aktualisierungs Status") angezeigt, das angibt, dass das Attribut aktualisiert wird.<br /><br /> Wenn beim Erstellen oder Bearbeiten eines Attributs Fehler auftreten, wird das Bild ![Symbol für den Fehlerstatus](../master-data-services/media/mds-statusicon-error.png "Symbol für Fehlerstatus") angezeigt.<br /><br /> Andernfalls lautet der Status "OK", und das Bild ![Symbol für den Status OK](../master-data-services/media/mds-statusicon-ok.png "Symbol für Status OK") wird angezeigt.|  
|Name|Der Attributname.|  
|Anzeigename|Der Anzeigename des Attributs.|  
|BESCHREIBUNG|Die Attributbeschreibung.|  
|Pixelbreite anzeigen|Die Breite des Attributs.|  
|Typ und Eigenschaften|Die Typ- und Datentypinformationen des Attributs.|  
|Änderungsnachverfolgung aktivieren|Gibt an, ob das Attribut für die Änderungsnachverfolgung aktiviert ist, und zeigt die Gruppennummer in Klammern.|  
  
 Wenn Sie auf ein Attribut klicken, werden die folgenden Informationen angezeigt.  
  
-   **Erstellt von**: der Name des Benutzers, der das Attribut erstellt hat.  
  
-   **Am**: das Datum und die Uhrzeit der Erstellung des Attributs.  
  
-   **Aktualisiert von**: der Name des Benutzers, der das Attribut zuletzt aktualisiert hat.  
  
-   **Am**: Datum und Uhrzeit der letzten Aktualisierung des Attributs.  
  
### <a name="to-create-a-domain-based-attribute"></a>So erstellen Sie ein domänenbasiertes Attribut  
  
1.  Klicken Sie in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]auf **Systemverwaltung**.  
  
2.  Klicken Sie auf der Seite **Modelle verwalten** auf ein Modell und anschließend auf **Entitäten**.  
  
3.  Wählen Sie auf der Seite **Entitäten verwalten** die Zeile der Entität aus, für die Sie ein Attribut erstellen möchten.  
  
4.  Klicken Sie auf **Attribute**.  
  
5.  Führen Sie auf der Seite **Attribute verwalten** einen der folgenden Schritte aus, und klicken Sie dann auf **Hinzufügen**.  
  
    -   Wenn das Attribut für Blattelemente bestimmt ist, wählen Sie **Blatt** im Listenfeld **Elementtypen** aus.  
  
    -   Wenn das Attribut für konsolidierte Elemente bestimmt ist, wählen Sie **Konsolidiert** im Listenfeld **Elementtypen** aus.  
  
    -   Wenn das Attribut für Sammlungen bestimmt ist, wählen Sie **Sammlung** im Listenfeld **Elementtypen** aus.  
  
6.  Geben Sie im Feld **Name** einen Namen für das Attribut ein. Eine Liste von Wörtern, die nicht als Attributnamen verwendet werden sollten, finden Sie unter [reservierte Wörter &#40;Master Data Services&#41;](../master-data-services/reserved-words-master-data-services.md)  
  
7.  Geben Sie optional einen Anzeigenamen ein, und geben Sie in das Feld **Beschreibung** eine Beschreibung ein.  
  
8.  Geben Sie im Feld **Pixelbreite anzeigen** die Breite der Attributspalte ein, die im **Explorerraster** angezeigt werden soll.  
  
9. Wählen Sie in der Liste **Attributtyp** die Option **Domänenbasiert**aus.  
  
10. Wählen Sie aus der Liste **Domänenentität** die Entität aus, die verwendet werden soll, um die Attributwerte aufzufüllen. 
  
11. **Optional für Domänen basierte Attribute für Blatt Elemente.** Wählen Sie einen übergeordneten Attributfilter, der verwendet wird, um die zulässigen Werte für das domänenbasierte Attribut zu beschränken.  
  
     Bei dem übergeordneten Filterattribut muss es sich um ein weiteres domänenbasiertes Attribut für ein Blattelement in derselben Entität handeln. Eine abgeleitete Hierarchie muss eine Ebene aufweisen, die die hierarchische Beziehung zwischen den Domänenentitäten der beiden Attribute definiert.  
  
     Weitere Informationen zur Einschränkung der zulässigen Werte finden Sie unter [How to filter Domain Based Attribute drop down lists](https://blogs.msdn.microsoft.com/mds/2015/12/03/in-sql-server-2016-master-data-services-how-to-filter-domain-based-attribute-drop-down-lists/)(Wie Sie Dropdownlisten domänenbasierter Attribute filtern), auf dem Master Data Services-Blog.  
  
12. **Optional.** Wählen Sie **Änderungsnachverfolgung aktivieren** aus, um Änderungen an Gruppen von Attributen nachzuverfolgen. Weitere Informationen finden Sie unter [Hinzufügen von Attributen zu einer Änderungsnachverfolgungsgruppe &#40;Master Data Services&#41;](../master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md).  
  
13. Klicken Sie auf **Speichern**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Domänen basierte Attribute &#40;Master Data Services&#41;](../master-data-services/domain-based-attributes-master-data-services.md)   
 [Erstellen Sie eine abgeleitete Hierarchie &#40;Master Data Services&#41;](../master-data-services/create-a-derived-hierarchy-master-data-services.md)   
 [Ändern eines Attribut namens und Datentyps &#40;Master Data Services&#41;](../master-data-services/change-an-attribute-name-and-data-type-master-data-services.md)   
 [Löschen eines Attributs &#40;Master Data Services&#41;](../master-data-services/delete-an-attribute-master-data-services.md)  
  
  
