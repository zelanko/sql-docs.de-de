---
title: Durchsuchen eines Berichts mit URL-Zugriff | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- searching reports
- text searches [Reporting Services]
- URL access [Reporting Services], report searches
ms.assetid: 6f3410c4-7944-448f-bae8-bab3e8152d46
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: e0296acddd21319949ff2f76757c5297eb1bceb4
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56023788"
---
# <a name="search-a-report-using-url-access"></a>Suchen eines Berichts mithilfe von URL-Zugriff
  Mit einem URL-Zugriff können Sie einen Bericht nach einem bestimmten Textteil durchsuchen. Legen Sie dazu den Wert des *rc:FindString* -Parameters in der URL auf den Text fest, nach dem Sie suchen möchten. Beschränken Sie außerdem mit dem *rc:StartFind* - und dem *rc:EndFind* -Parameter Ihre Suche auf bestimmte Seiten im Bericht.  
  
## <a name="example"></a>Beispiel  
 In dem folgenden Beispiel für den URL-Zugriff wird nach dem ersten Vorkommen des Texts "Mountain-400" im Beispielbericht Product Catalog gesucht. Die Suche beginnt auf der ersten Seite und endet auf der fünften Seite:  
  
```  
http://server/Reportserver?/SampleReports/Product Catalog&rs:Command=Render&rc:StartFind=1&rc:EndFind=5&rc:FindString=Mountain-400  
```  
  
## <a name="see-also"></a>Siehe auch  
 [URL-Zugriff &#40;SSRS&#41;](url-access-ssrs.md)   
 [URL-Zugriffsparameterverweis](url-access-parameter-reference.md)  
  
  
