---
title: Bearbeiten einer Entität
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- entities [Master Data Services], changing name
ms.assetid: 6a5b9f14-6dfc-49d7-a771-e96461d4feae
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 4329f618b812bb566d974c5434ef0362b1383f2d
ms.sourcegitcommit: 09ccd103bcad7312ef7c2471d50efd85615b59e8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73729296"
---
# <a name="edit-an-entity-master-data-services"></a>Bearbeiten einer Entität (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]können Sie eine Entität bearbeiten.  
  
## <a name="prerequisites"></a>Prerequisites  
 So führen Sie diese Prozedur aus  
  
-   Sie müssen über die Berechtigung verfügen, auf den Funktionsbereich **Systemverwaltung** zuzugreifen.  
  
-   Sie müssen ein Modelladministrator sein. Weitere Informationen finden Sie unter [Administratoren &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md)zuzugreifen.  
  
### <a name="to-edit-an-entity"></a>So bearbeiten Sie eine Entität  
  
1.  Klicken Sie in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]auf **Systemverwaltung**.  
  
2.  Wählen Sie auf der Seite **Modell verwalten** im Raster ein Modell aus, und klicken Sie dann auf **Entitäten**.  
  
3.  Wählen Sie auf der Seite **Entitäten verwalten** im Raster die Zeile für die Entität aus, die Sie ändern möchten, und klicken Sie anschließend auf **Bearbeiten**.  
  
4.  Geben Sie im Feld **Name** den aktualisierten Namen für die Entität ein.  
  
5.  Geben Sie im Feld **Beschreibung** die aktualisierte Beschreibung der Entität ein.  
  
6.  Geben Sie im Feld **Name für Stagingtabellen** den aktualisierten Namen für die Stagingtabelle ein.  
  
7.  Wählen Sie für das Feld **Transaktionsprotokolltyp** den aktualisierten Transaktionsprotokolltyp in der Dropdownliste aus.  
  
     Weitere Informationen finden Sie unter [Ändern des Transaktionsprotokolltyps von Entitäten &#40;Master Data Services&#41;](../master-data-services/change-the-entity-transaction-log-type-master-data-services.md).  
  
8.  Aktivieren oder deaktivieren Sie das Kontrollkästchen **Codewerte automatisch erstellen**.  
  
     Weitere Informationen finden Sie unter [Automatische Codeerstellung &#40;Master Data Services&#41;](../master-data-services/automatic-code-creation-master-data-services.md)  
  
9. Aktivieren oder deaktivieren Sie das Kontrollkästchen **Datenkomprimierung aktivieren**. Die Zeilenkomprimierung ist standardmäßig aktiviert.  
  
     Weitere Informationen finden Sie unter [Datenkomprimierung](../relational-databases/data-compression/data-compression.md).  
  
## <a name="status"></a>Status  
 Die Statusspalte im Raster zeigt den Status des Vorgangs für die Entität. Wenn Sie auf **Entität speichern**klicken, wird das folgende Bild angezeigt, das angibt, dass die Entität aktualisiert wird.  
  
 ![Symbol für Aktualisierungs Status](../master-data-services/media/mds-statusicon-updating.png "Symbol für Aktualisierungs Status")  
  
 Wenn beim Erstellen oder Bearbeiten einer Entität Fehler auftreten, wird das folgende Bild angezeigt.  
  
 ![Symbol für Fehlerstatus](../master-data-services/media/mds-statusicon-error.png "Symbol für Fehlerstatus")  
  
 Falls der Status "OK" lautet, wird das folgende Bild angezeigt.  
  
 ![Symbol für Status OK](../master-data-services/media/mds-statusicon-ok.png "Symbol für Status OK")  
  
## <a name="see-also"></a>Siehe auch  
 [Explizite Hierarchien &#40;Master Data Services&#41;](../master-data-services/explicit-hierarchies-master-data-services.md)   
 [Löschen einer Entität &#40;Master Data Services&#41;](../master-data-services/delete-an-entity-master-data-services.md)   
 [Entitäten &#40;Master Data Services&#41;](../master-data-services/entities-master-data-services.md)  
  
  
