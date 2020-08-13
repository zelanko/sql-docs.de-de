---
title: Durchsuchen eines Berichts mit URL-Zugriff | Microsoft-Dokumentation
description: Hier erfahren Sie, wie Sie mithilfe von URL-Zugriff einen Bericht suchen. Legen Sie beispielsweise den Parameter „rc:FindString“ in der URL auf den Text fest, nach dem Sie suchen möchten.
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
helpviewer_keywords:
- searching reports
- text searches [Reporting Services]
- URL access [Reporting Services], report searches
ms.assetid: 6f3410c4-7944-448f-bae8-bab3e8152d46
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: c7d5ba7b312bb89942fd899f4c769179a0c97bab
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87238432"
---
# <a name="search-a-report-using-url-access"></a>Suchen eines Berichts mithilfe von URL-Zugriff
  Mit einem URL-Zugriff können Sie einen Bericht nach einem bestimmten Textteil durchsuchen. Legen Sie dazu den Wert des *rc:FindString* -Parameters in der URL auf den Text fest, nach dem Sie suchen möchten. Beschränken Sie außerdem mit dem *rc:StartFind* - und dem *rc:EndFind* -Parameter Ihre Suche auf bestimmte Seiten im Bericht.  
  
## <a name="example"></a>Beispiel  
 In dem folgenden Beispiel für den URL-Zugriff wird nach dem ersten Vorkommen des Texts "Mountain-400" im Beispielbericht Product Catalog gesucht. Die Suche beginnt auf der ersten Seite und endet auf der fünften Seite:  
  
```  
https://server/Reportserver?/SampleReports/Product Catalog&rs:Command=Render&rc:StartFind=1&rc:EndFind=5&rc:FindString=Mountain-400  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [URL-Zugriff &#40;SSRS&#41;](../reporting-services/url-access-ssrs.md)   
 [URL Access Parameter Reference (URL-Zugriffsparameterverweis)](../reporting-services/url-access-parameter-reference.md)  
  
  
