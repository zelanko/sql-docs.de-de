---
title: Erstellen eines Datenattributs (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
helpviewer_keywords:
- creating date attributes [Master Data Services]
- attributes [Master Data Services], creating date attributes
ms.assetid: 22a8f1a3-b4f2-4cfa-8495-7daad5ce9d12
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 4eeebefcda3a1ecb542e33b2a4a59a46f302b303
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48083740"
---
# <a name="create-a-date-attribute-master-data-services"></a>Erstellen eines Datenattributs (Master Data Services)
  Erstellen Sie in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]ein Datumsattribut, wenn Sie möchten, dass Benutzer ein Datum als Attributwert eingeben.  
  
> [!NOTE]  
>  Das Attribut heißt DateTime, aber Zeitwerte werden nicht unterstützt.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 So führen Sie diese Prozedur aus  
  
-   Sie müssen über die Berechtigung verfügen, auf den Funktionsbereich **Systemverwaltung** zuzugreifen.  
  
-   Sie müssen ein Modelladministrator sein. Weitere Informationen finden Sie unter [Administratoren &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
-   Sie müssen eine Entität haben, für das Sie das Attribut erstellen. Weitere Informationen finden Sie unter [Erstellen einer Entität &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-entity-master-data-services.md).  
  
### <a name="to-create-a-date-attribute"></a>So erstellen Sie ein Datumsattribut  
  
1.  Klicken Sie in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]auf **Systemverwaltung**.  
  
2.  Zeigen Sie auf der Seite **Modellansicht** auf der Menüleiste auf **Verwalten** , und klicken Sie auf **Entitäten**.  
  
3.  Wählen Sie auf der Seite **Entitätsverwaltung** aus der Liste **Modell** ein Modell aus.  
  
4.  Wählen Sie die Zeile für die Entität aus, für die Sie ein Attribut erstellen möchten.  
  
5.  Klicken Sie auf **Ausgewählte Entität bearbeiten**.  
  
6.  Auf der Seite **Entität bearbeiten** .  
  
    -   Wenn das Attribut für Blattelemente bestimmt ist, klicken Sie im Bereich **Blattelementattribute** auf **Blattattribut hinzufügen**.  
  
    -   Wenn das Attribut für konsolidierte Elemente bestimmt ist, klicken Sie im Bereich **Konsolidierte Elementattribute** auf **Konsolidiertes Attribut hinzufügen**.  
  
    -   Wenn das Attribut für Auflistungen bestimmt ist, klicken Sie im Bereich **Auflistungsattribute** auf **Auflistungsattribut hinzufügen**.  
  
7.  Aktivieren Sie die Option **Freiform** auf der Seite **Attribut hinzufügen** .  
  
8.  Geben Sie im Feld **Name** einen Namen für das Attribut ein. Eine Liste von Wörtern, die nicht als Attributnamen verwendet werden sollten, finden Sie unter [Reservierte Wörter &#40;Master Data Services&#41;](../../2014/master-data-services/reserved-words-master-data-services.md).  
  
9. Geben Sie im Feld **Pixelbreite anzeigen** die Breite der Attributspalte ein, die im **Explorerraster** angezeigt werden soll.  
  
10. Wählen Sie aus der Liste **Datentyp** die Option **DateTime**aus.  
  
11. Wählen Sie aus der Liste **Eingabeformat** ein Format für Datumsangaben aus.  
  
12. Optional können Sie **Änderungsnachverfolgung aktivieren** auswählen, um Änderungen an Gruppen von Attributen nachzuverfolgen. Weitere Informationen finden Sie unter [Hinzufügen von Attributen zu einer Änderungsnachverfolgungsgruppe &#40;Master Data Services&#41;](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md).  
  
13. Klicken Sie auf **Attribut speichern**.  
  
14. Klicken Sie auf der Seite **Entitätsverwaltung** auf **Entität speichern**.  
  
## <a name="to-display-the-time-portion-of-a-datetime-value"></a>So zeigen Sie den Zeitbereich eines datetime-Werts an  
 Damit der Zeitbereich eines datetime-Werts in der Benutzeroberfläche angezeigt wird, müssen Sie ein geeignetes Eingabeformat für das Attribut auswählen. Da keine der integrierten Masken für Datetime-Attribute hierzu geeignet ist, können Sie eine neue Maske hinzufügen, die die Anzeige der Uhrzeit ermöglicht. Fügen Sie dazu der Tabelle mdm.tblList der MDS-Datenbank, in der integrierte Masken gespeichert werden, eine Zeile hinzu. Die Zeile sollte über die folgenden Werte verfügen:  
  
|||  
|-|-|  
|ListCode|lstInputMask|  
|ListName|Eingabeformat|  
|Seq|19|  
|List Option|dd/MM/yyyy hh:mm:ss tt|  
|Option ID|19|  
|Sichtbar|1|  
|Group_ID|3|  
  
 Nachdem Sie in die Tabelle mdm.tblList eine Zeile mit den oben angegebenen Werten eingegeben haben, steht im Listenfeld Eingabeformat die Maske "dd/MM/yyyy hh:mm:ss tt" zur Verfügung. Anschließend können Sie diese Maske auswählen, um das Datum und die Uhrzeit in einer datetime-Attributspalte einer Entität im MDS-Explorer anzuzeigen.  
  
 Die Input Mask ist eine benutzerdefinierte .NET DateTime-Formatzeichenfolge. Weitere Informationen finden Sie unter [Benutzerdefinierte Datums- und Uhrzeit-Formatzeichenfolgen](https://msdn.microsoft.com/en-us/library/8kb3ddd4\(v=vs.110\).aspx)  
  
## <a name="see-also"></a>Siehe auch  
 [Attribute &#40;Master Data Services&#41;](../../2014/master-data-services/attributes-master-data-services.md)   
 [Ändern eines Attributnamens &#40;Master Data Services&#41;](change-an-attribute-name-and-data-type-master-data-services.md)   
 [Erstellen eines domänenbasierten Attributs &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md)   
 [Erstellen eines Dateiattributs &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-file-attribute-master-data-services.md)  
  
  
