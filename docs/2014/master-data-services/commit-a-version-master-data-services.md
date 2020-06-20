---
title: Durchführen eines Commits für eine Version (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- committing versions [Master Data Services]
- versions [Master Data Services], committing
ms.assetid: 6b967a39-b333-4b84-9e5f-4fb07e156826
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 82633564746672df867999f2540cdc3746d08631
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84971973"
---
# <a name="commit-a-version-master-data-services"></a>Durchführen eines Commits für eine Version (Master Data Services)
  Führen Sie in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]einen Commit für eine Version eines Modells durch, um Änderungen an den Elementen des Modells und den Attributen zu verhindern. Versionen mit ausgeführtem Commit können nicht entsperrt werden.  
  
## <a name="prerequisites"></a>Voraussetzungen  
 So führen Sie diese Prozedur aus  
  
-   Sie müssen über die Berechtigung verfügen, auf den Funktionsbereich **Versionsverwaltung** zuzugreifen.  
  
-   Sie müssen ein Modelladministrator sein. Weitere Informationen finden Sie unter [Administratoren &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
-   Der Status der Version muss **Gesperrt**sein. Weitere Informationen finden Sie unter [Sperren einer Version &#40;Master Data Services&#41;](../../2014/master-data-services/lock-a-version-master-data-services.md).  
  
-   Alle Elemente müssen erfolgreich überprüft worden sein.  
  
### <a name="to-commit-a-version"></a>So führen Sie einen Commit für eine Version durch  
  
1.  Klicken Sie in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]auf **Versionsverwaltung**.  
  
2.  Klicken Sie auf der Seite **Versionen verwalten** auf der Menüleiste auf **Version überprüfen**.  
  
3.  Wählen Sie auf der Seite **Version überprüfen** das Modell und die Version aus, für das bzw. die Sie einen Commit durchführen möchten.  
  
4.  Klicken Sie auf **Commit ausführen**.  
  
5.  Klicken Sie im Bestätigungsdialogfeld auf **OK**.  
  
## <a name="next-steps"></a>Nächste Schritte  
  
-   [Erstellen eines Versionsflags &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-version-flag-master-data-services.md)  
  
-   [Zuweisen eines Flags zu einer Version &#40;Master Data Services&#41;](../../2014/master-data-services/assign-a-flag-to-a-version-master-data-services.md)  
  
-   [Kopieren einer Version &#40;Master Data Services&#41;](../../2014/master-data-services/copy-a-version-master-data-services.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Versionen &#40;Master Data Services&#41;](../../2014/master-data-services/versions-master-data-services.md)  
  
  
