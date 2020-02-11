---
title: Erstellen eines Versionsflags
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- creating version flags [Master Data Services]
- version flags [Master Data Services], creating
- versions [Master Data Services], creating flags
ms.assetid: 3067e1e3-05b7-4f11-9206-c612ef4e7e42
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 25c52ac4dc179940f1a3c45fd5200cf3525c56f9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "73729554"
---
# <a name="create-a-version-flag-master-data-services"></a>Erstellen eines Versionsflags (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Erstellen Sie in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]ein Versionsflag, das Sie einer Version zuweisen. Das Flag kann die Version angeben, die Benutzer oder abonnierende Systeme verwenden sollten.  
  
## <a name="prerequisites"></a>Voraussetzungen  
 So führen Sie diese Prozedur aus  
  
-   Sie müssen über die Berechtigung verfügen, auf den Funktionsbereich **Versionsverwaltung** zuzugreifen.  
  
-   Sie müssen ein Modelladministrator sein. Weitere Informationen finden Sie unter [Administratoren &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
-   Sie müssen über die Berechtigung für den Zugriff auf den Funktionsbereich „Versionsverwaltung“ verfügen. Weitere Informationen finden Sie unter [Funktions Bereichs Berechtigungen &#40;Master Data Services&#41;](../master-data-services/functional-area-permissions-master-data-services.md).  
  
### <a name="to-create-a-version-flag"></a>So erstellen Sie ein Versionsflag  
  
1.  Klicken Sie in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]auf **Versionsverwaltung**.  
  
2.  Zeigen Sie auf der Seite **Versionen verwalten** in der Menüleiste auf **Verwalten** und klicken Sie dann auf **Flags**.  
  
3.  Wählen Sie auf der Seite **Versionsflags verwalten** im Feld **Modell** das Modell aus, für das Sie ein Flag erstellen möchten.  
  
4.  Klicken Sie auf **Hinzufügen**.  
  
5.  Geben Sie im Feld **Name** einen Namen ein.  
  
6.  Geben Sie in das Feld **Beschreibung** eine Beschreibung ein.  
  
7.  Wählen Sie im Feld **Nur Versionen, für die ein Commit ausgeführt wurde****True** aus, um anzugeben, dass das Flag nur Versionen mit dem Status **Commit wurde ausgeführt** zugewiesen werden kann. Wählen Sie **False** aus, um anzugeben, dass das Flag Versionen mit beliebigem Status zugewiesen werden kann.  
  
8.  Klicken Sie auf **Speichern**.  
  
## <a name="next-steps"></a>Nächste Schritte  
  
-   [Zuweisen eines Flags zu einer Version &#40;Master Data Services&#41;](../master-data-services/assign-a-flag-to-a-version-master-data-services.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Versionen &#40;Master Data Services&#41;](../master-data-services/versions-master-data-services.md)   
 [Ändern Sie den Namen eines versionsflags &#40;Master Data Services&#41;](../master-data-services/change-a-version-flag-name-master-data-services.md)  
  
  
