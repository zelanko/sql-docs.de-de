---
title: Erstellen eines Versionsflags (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- creating version flags [Master Data Services]
- version flags [Master Data Services], creating
- versions [Master Data Services], creating flags
ms.assetid: 3067e1e3-05b7-4f11-9206-c612ef4e7e42
caps.latest.revision: 5
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 8e749d7e0be27ec7ea749073f89f192972a354f2
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37287546"
---
# <a name="create-a-version-flag-master-data-services"></a>Erstellen eines Versionsflags (Master Data Services)
  Erstellen Sie in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]ein Versionsflag, das Sie einer Version zuweisen. Das Flag kann die Version angeben, die Benutzer oder abonnierende Systeme verwenden sollten.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 So führen Sie diese Prozedur aus  
  
-   Sie müssen über die Berechtigung verfügen, auf den Funktionsbereich **Versionsverwaltung** zuzugreifen.  
  
-   Sie müssen ein Modelladministrator sein. Weitere Informationen finden Sie unter [Administratoren &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
### <a name="to-create-a-version-flag"></a>So erstellen Sie ein Versionsflag  
  
1.  Klicken Sie in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]auf **Versionsverwaltung**.  
  
2.  Zeigen Sie auf der Seite **Versionen verwalten** in der Menüleiste auf **Verwalten** und klicken Sie dann auf **Flags**.  
  
3.  Wählen Sie auf der Seite **Versionsflags verwalten** im Feld **Modell** das Modell aus, für das Sie ein Flag erstellen möchten.  
  
4.  Klicken Sie auf **Hinzufügen**.  
  
5.  Geben Sie im Feld **Name** einen Namen ein.  
  
6.  Geben Sie im Feld **Beschreibung** eine Beschreibung ein.  
  
7.  Wählen Sie im Feld **Nur Versionen, für die ein Commit ausgeführt wurde** **True** aus, um anzugeben, dass das Flag nur Versionen mit dem Status **Commit wurde ausgeführt** zugewiesen werden kann. Wählen Sie **False** aus, um anzugeben, dass das Flag Versionen mit beliebigem Status zugewiesen werden kann.  
  
8.  Klicken Sie auf **Speichern**.  
  
## <a name="next-steps"></a>Nächste Schritte  
  
-   [Zuweisen eines Flags zu einer Version &#40;Master Data Services&#41;](../../2014/master-data-services/assign-a-flag-to-a-version-master-data-services.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Versionen &#40;Master Data Services&#41;](../../2014/master-data-services/versions-master-data-services.md)   
 [Ändern des Namens eines Versionsflags &#40;Master Data Services&#41;](../../2014/master-data-services/change-a-version-flag-name-master-data-services.md)  
  
  
