---
title: Durchsuchen eines Berichts mit URL-Zugriff | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
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
manager: mblythe
ms.openlocfilehash: 95989e61ed3b5d77e6896ae9896b1db495ff0a32
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36049115"
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
 [URL Access Parameter Reference (URL-Zugriffsparameterverweis)](url-access-parameter-reference.md)  
  
  