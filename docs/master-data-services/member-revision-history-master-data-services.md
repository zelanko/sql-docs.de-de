---
title: Elementrevisionsverlauf
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 113069c5-12e6-48ec-b443-b42e14f77308
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 4bc3d2a084f7f1ec3abcf9e3d3bbcaf82e4749e8
ms.sourcegitcommit: 09ccd103bcad7312ef7c2471d50efd85615b59e8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73729110"
---
# <a name="member-revision-history-master-data-services"></a>Elementrevisionsverlauf (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Ein Elementrevisionsverlauf wird jedes Mal aufgezeichnet, wenn ein Element geändert wird, falls der Protokolltyp der Entitätsbuchung „Member“ ist.  
  
 Weitere Informationen zu Transaktionsprotokolltypen finden Sie unter [Ändern des Transaktionsprotokolltyps von Entitäten &#40;Master Data Services&#41;](../master-data-services/change-the-entity-transaction-log-type-master-data-services.md).  
  
 Elementrevisionsverläufe werden aufgezeichnet, wenn die folgenden Änderungen auftreten.  
  
-   Elemente werden erstellt, gelöscht, erneut aktiviert oder bereinigt.  
  
-   Attributwerte werden geändert.  
  
-   Elemente werden in eine Hierarchie oder Sammlung verschoben.  
  
## <a name="view-and-manage-revision-history-by-entity"></a>Anzeigen und Verwalten des Revisionsverlaufs je Entität  
 Im Funktionsbereich des Explorers können Sie die Revision für alle Elemente in der Entität anzeigen. Wenn Sie über Aktualisierungsberechtigungen verfügen, können Sie das Element auf eine frühere Version zurücksetzen.  
  
 **So zeigen Sie den Revisionsverlauf an und verwalten ihn**  
  
1.  Wählen Sie in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]das Modell und die Version und klicken Sie anschließend auf **Explorer**.  
  
2.  Wählen Sie die Entität aus dem Menü **Entitäten** aus.  
  
3.  Klicken Sie auf **Verlauf anzeigen** , um alle Verlaufsdaten der Entität anzuzeigen.  
  
4.  Klicken Sie auf **Filter** , um die Daten zu filtern.  
  
5.  Klicken Sie auf die Spaltenüberschrift, um die Daten zu sortieren.  
  
6.  Wenn Sie über Aktualisierungsberechtigungen verfügen, klicken Sie auf **Element wiederherstellen** , um die gewählte Version zurückzusetzen.  
  
## <a name="view-and-manage-revision-history-by-member"></a>Anzeigen und Verwalten des Revisionsverlaufs durch Element  
 Im Funktionsbereich des Explorers können Sie die Überarbeitungen für ein Element anzeigen, wenn Sie über Leseberechtigungen für das Element verfügen. Wenn Sie über Aktualisierungsberechtigungen verfügen, können Sie das Element auf eine frühere Überarbeitung zurücksetzen oder Anmerkungen zur Überarbeitung hinzufügen.  
  
1.  Wählen Sie in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]das Modell und die Version und klicken Sie anschließend auf **Explorer**.  
  
2.  Wählen Sie die Entität aus dem Menü **Entitäten** aus.  
  
3.  Wählen Sie das Element aus.  
  
4.  Klicken Sie auf **Verlauf anzeigen** im rechten Bereich.  
  
## <a name="log-retention-setting"></a>Einstellung für Protokollbeibehaltung  
 Sie können konfigurieren, wie lange Verlaufsdaten beibehalten werden, indem Sie die Eigenschaft **Protokollaufbewahrung in Tagen** in den Systemeinstellungen für die [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]-Datenbank festlegen, und durch Festlegen von **Protokollaufbewahrung in Tagen**, wenn Sie ein Modell erstellen oder bearbeiten.  
  
## <a name="related-task"></a>Verwandte Aufgabe  
  
|Taskbeschreibung|Thema|  
|----------------------|-----------|  
|Zurücksetzen des Elementrevisionsverlaufs|[Zurücksetzen des Elementrevisionsverlaufs &#40;Master Data Services&#41;](../master-data-services/rollback-member-revision-history-master-data-services.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen eines Modells &#40;Master Data Services&#41;](../master-data-services/create-a-model-master-data-services.md)   
 [Systemeinstellungen &#40;Master Data Services&#41;](../master-data-services/system-settings-master-data-services.md)  
  
  
