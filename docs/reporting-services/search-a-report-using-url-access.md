---
title: Durchsuchen eines Berichts mit URL-Zugriff | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: reporting-services
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- searching reports
- text searches [Reporting Services]
- URL access [Reporting Services], report searches
ms.assetid: 6f3410c4-7944-448f-bae8-bab3e8152d46
caps.latest.revision: 34
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 7c29c0b4dce06371fc489d8c04f59655057b19a1
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
ms.locfileid: "33026307"
---
# <a name="search-a-report-using-url-access"></a>Suchen eines Berichts mithilfe von URL-Zugriff
  Mit einem URL-Zugriff können Sie einen Bericht nach einem bestimmten Textteil durchsuchen. Legen Sie dazu den Wert des *rc:FindString* -Parameters in der URL auf den Text fest, nach dem Sie suchen möchten. Beschränken Sie außerdem mit dem *rc:StartFind* - und dem *rc:EndFind* -Parameter Ihre Suche auf bestimmte Seiten im Bericht.  
  
## <a name="example"></a>Beispiel  
 In dem folgenden Beispiel für den URL-Zugriff wird nach dem ersten Vorkommen des Texts "Mountain-400" im Beispielbericht Product Catalog gesucht. Die Suche beginnt auf der ersten Seite und endet auf der fünften Seite:  
  
```  
http://server/Reportserver?/SampleReports/Product Catalog&rs:Command=Render&rc:StartFind=1&rc:EndFind=5&rc:FindString=Mountain-400  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [URL-Zugriff &#40;SSRS&#41;](../reporting-services/url-access-ssrs.md)   
 [URL Access Parameter Reference (URL-Zugriffsparameterverweis)](../reporting-services/url-access-parameter-reference.md)  
  
  
