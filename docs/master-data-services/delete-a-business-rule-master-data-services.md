---
description: Löschen einer Geschäftsregel (Master Data Services)
title: Löschen einer Geschäftsregel
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- deleting business rules [Master Data Services]
- business rules [Master Data Services], deleting
ms.assetid: b97aa4f9-569f-451d-ad62-65b81f980299
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 1a649c1d04d1d52fee2864991bbe051b04814ee6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88461760"
---
# <a name="delete-a-business-rule-master-data-services"></a>Löschen einer Geschäftsregel (Master Data Services)

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]können Sie eine Geschäftsregel löschen, die Sie nicht mehr benötigen.  
  
> [!NOTE]  
>  Sie können die Überprüfung von Daten anhand einer Geschäftsregel unterbinden, indem Sie die Geschäftsregel ausschließen, anstatt sie zu löschen. Weitere Informationen finden Sie unter [Ausschließen einer Geschäftsregel &#40;Master Data Services&#41;](../master-data-services/exclude-a-business-rule-master-data-services.md).  
  
## <a name="prerequisites"></a>Voraussetzungen  
 So führen Sie diese Prozedur aus  
  
-   Sie müssen über die Berechtigung verfügen, auf den Funktionsbereich **System Verwaltung** zuzugreifen.  
  
-   Sie müssen ein Modelladministrator sein. Weitere Informationen finden Sie unter [Administratoren &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
### <a name="to-delete-a-business-rule"></a>So löschen Sie eine Geschäftsregel  
  
1.  Klicken Sie in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]auf **Systemverwaltung**.  
  
2.  Zeigen Sie auf der Menüleiste auf **Verwalten** , und klicken Sie auf **Geschäftsregeln**.  
  
3.  Wählen Sie auf der Seite **Geschäftsregeln** in der Dropdownliste **Modell** ein Modell aus.  
  
4.  Wählen Sie in der Dropdownliste **Entität** eine Entität aus.  
  
5.  Wählen Sie in der Dropdownliste **Member Types** (Elementtypen) einen Typ des Elements aus, auf das die Geschäftsregel angewendet werden soll.  
  
6.  Klicken Sie im Raster auf die Zeile der Geschäftsregel, die Sie löschen möchten.  
  
7.  Klicken Sie auf **Löschen**.  
  
8.  Klicken Sie im Bestätigungsdialogfeld auf **OK**. Der Wert in der Spalte **Geschäftsregelstatus** ist **Löschen ausstehend**.  
  
9. Klicken Sie auf **Alle veröffentlichen**.  
  
10. Klicken Sie im Bestätigungsdialogfeld auf **OK**. Die gelöschten Geschäftsregel wird nicht mehr im Raster angezeigt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausschließen einer Geschäftsregel &#40;Master Data Services&#41;](../master-data-services/exclude-a-business-rule-master-data-services.md)   
 [Erstellen und Veröffentlichen einer Geschäftsregel &#40;Master Data Services&#41;](../master-data-services/create-and-publish-a-business-rule-master-data-services.md)   
 [Geschäftsregeln &#40;Master Data Services&#41;](../master-data-services/business-rules-master-data-services.md)  
  
  
