---
title: Erstellen eines numerischen Attributs (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- attributes [Master Data Services], creating number attributes
- creating number attributes [Master Data Services]
ms.assetid: c0dbb6d8-ba78-485a-a40d-6d5cb7e75d0a
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 484774165ea1997b98fc9dc0919f5be7450dd4c7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "65483366"
---
# <a name="create-a-numeric-attribute-master-data-services"></a>Erstellen eines numerischen Attributs (Master Data Services)
  Erstellen Sie in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]ein numerisches Attribut, wenn Sie möchten, dass Benutzer eine Zahl als Attributwert eingeben.  
  
> [!NOTE]  
>  Numerische Attribute weisen bestimmte Einschränkungen auf. Weitere Informationen finden Sie unter [Attribute &#40;Master Data Services&#41;](attributes-master-data-services.md).  
  
## <a name="prerequisites"></a>Voraussetzungen  
 So führen Sie diese Prozedur aus  
  
-   Sie müssen über die Berechtigung verfügen, auf den Funktionsbereich **Systemverwaltung** zuzugreifen.  
  
-   Sie müssen ein Modelladministrator sein. Weitere Informationen finden Sie unter [Administratoren &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md).  
  
-   Eine Entität muss vorhanden sein, um das Attribut dafür erstellen zu können. Weitere Informationen finden Sie unter [Erstellen einer Entität &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-entity-master-data-services.md).  
  
### <a name="to-create-a-numeric-attribute"></a>So erstellen Sie ein numerisches Attribut  
  
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
  
10. Wählen Sie aus der Liste **Datentyp****Zahl**aus.  
  
11. Geben Sie im Feld **Dezimalstellen** die Anzahl der Ziffern ein, die nach einem Dezimalzeichen eingegeben werden können.  
  
12. Wählen Sie in der Liste **Eingabemaske** ein Format für negative Zahlen aus.  
  
13. Optional können Sie **Änderungsnachverfolgung aktivieren** auswählen, um Änderungen an Gruppen von Attributen nachzuverfolgen. Weitere Informationen finden Sie unter [Hinzufügen von Attributen zu einer Änderungsnachverfolgungsgruppe &#40;Master Data Services&#41;](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md) .  
  
14. Klicken Sie auf **Attribut speichern**.  
  
15. Klicken Sie auf der Seite **Entitätsverwaltung** auf **Entität speichern**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Attribute &#40;Master Data Services&#41;](attributes-master-data-services.md)   
 [Ändern eines Attribut namens &#40;Master Data Services&#41;](change-an-attribute-name-and-data-type-master-data-services.md)   
 [Erstellen eines domänenbasierten Attributs &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md)   
 [Erstellen Sie ein Datei Attribut &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-file-attribute-master-data-services.md)  
  
  
