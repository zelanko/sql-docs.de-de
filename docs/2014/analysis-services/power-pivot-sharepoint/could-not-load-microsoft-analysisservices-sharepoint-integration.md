---
title: Konnte nicht geladen werden, Datei oder Assembly &#39;Microsoft.Data.Services, Version = 3.5.0.0, Culture = Neutral, PublicKeyToken = b77a5c561934e089&#39; oder eine ihrer Abhängigkeiten. Die angegebene Datei wurde nicht gefunden. | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: 81ed0f44-8782-462d-af8f-0ba5b975df27
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 49e2ce59b8662a8deaf47099c967355150dca201
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/13/2018
ms.locfileid: "53371512"
---
# <a name="could-not-load-file-or-assembly-39microsoftdataservices-version3500-cultureneutral-publickeytokenb77a5c561934e08939-or-one-of-its-dependencies-the-system-cannot-find-the-file-specified"></a>Konnte nicht geladen werden, Datei oder Assembly &#39;Microsoft.Data.Services, Version = 3.5.0.0, Culture = Neutral, PublicKeyToken = b77a5c561934e089&#39; oder eine ihrer Abhängigkeiten. Die angegebene Datei wurde nicht gefunden.
  In SharePoint 2010-Umgebungen mit PowerPivot für SharePoint tritt dieser Fehler auf, wenn Sie versuchen, einen Datenfeed zu exportieren und das System nicht über die erforderliche Version von Microsoft ADO.NET Data Services verfügt.  
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Betrifft|PowerPivot für SharePoint|  
|Produktversion|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|Ursache|ADO.NET Data Services 3.5 SP1 wurde nicht gefunden.|  
|Meldungstext|Die Datei oder Assembly "Microsoft.Data.Services, Version=3 .5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" oder eine Abhängigkeit davon wurde nicht gefunden. Die angegebene Datei wurde nicht gefunden.|  
  
## <a name="explanation"></a>Erklärung  
 SharePoint 2010 enthält die Schaltfläche Als Datenfeed exportieren, mit der Sie eine SharePoint-Liste als XML-Datenfeed exportieren können. Außerdem unterstützen sowohl Reporting Services in SharePoint-Modus als auch PowerPivot für SharePoint Datenfeedfunktionen, die ADO.NET Data Services erfordern.  
  
 Wenn ADO.NET Data Services nicht installiert sind, tritt dieser Fehler beim Anfordern eines Datenfeeds auf.  
  
## <a name="user-action"></a>Benutzeraktion  
  
1.  Wechseln Sie zu den Hardware- und softwareanforderungen für SharePoint 2010 [bestimmen von Hardware- und Softwareanforderungen (SharePoint 2010)](https://go.microsoft.com/fwlink/?LinkId=169734) (https://go.microsoft.com/fwlink/?LinkId=169734).  
  
2.  Suchen Sie unter **Installieren der erforderlichen Software**den Link für ADO.NET Data Services 3.5, der dem verwendeten Betriebssystem entspricht.  
  
3.  Klicken Sie auf den Link, und führen Sie das Setupprogramm aus, durch das der Dienst installiert wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Bereitstellen von PowerPivot-Lösungen in SharePoint](deploy-power-pivot-solutions-to-sharepoint.md)  
  
  
