---
title: Die Datei oder Assembly &#39;"Microsoft. Data. Services, Version = 5.0.0, Culture = neutral, PublicKeyToken = b77a5c561934e089&#39; oder einer ihrer Abhängigkeiten konnte nicht geladen werden. Die angegebene Datei wurde nicht gefunden. | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 81ed0f44-8782-462d-af8f-0ba5b975df27
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9bcfdde8b3536bbbf8b2429d51a9ee9aecf0d437
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84547502"
---
# <a name="could-not-load-file-or-assembly-39microsoftdataservices-version3500-cultureneutral-publickeytokenb77a5c561934e08939-or-one-of-its-dependencies-the-system-cannot-find-the-file-specified"></a>Die Datei oder Assembly &#39;"Microsoft. Data. Services, Version = 5.0.0, Culture = neutral, PublicKeyToken = b77a5c561934e089&#39; oder einer ihrer Abhängigkeiten konnte nicht geladen werden. Die angegebene Datei wurde nicht gefunden.
  In SharePoint 2010-Umgebungen mit PowerPivot für SharePoint tritt dieser Fehler auf, wenn Sie versuchen, einen Datenfeed zu exportieren und das System nicht über die erforderliche Version von Microsoft ADO.NET Data Services verfügt.  
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Gilt für:|PowerPivot für SharePoint|  
|Produktversion|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|Ursache|ADO.NET Data Services 3.5 SP1 wurde nicht gefunden.|  
|Meldungstext|Die Datei oder Assembly "Microsoft.Data.Services, Version=3 .5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" oder eine Abhängigkeit davon wurde nicht gefunden. Die angegebene Datei wurde nicht gefunden.|  
  
## <a name="explanation"></a>Erklärung  
 SharePoint 2010 enthält die Schaltfläche Als Datenfeed exportieren, mit der Sie eine SharePoint-Liste als XML-Datenfeed exportieren können. Außerdem unterstützen sowohl Reporting Services in SharePoint-Modus als auch PowerPivot für SharePoint Datenfeedfunktionen, die ADO.NET Data Services erfordern.  
  
 Wenn ADO.NET Data Services nicht installiert sind, tritt dieser Fehler beim Anfordern eines Datenfeeds auf.  
  
## <a name="user-action"></a>Benutzeraktion  
  
1.  Wechseln Sie zur Dokumentation zu Hardware-und Softwareanforderungen für SharePoint 2010, und bestimmen Sie die [Hardware-und Softwareanforderungen (SharePoint 2010)](https://go.microsoft.com/fwlink/?LinkId=169734) ( https://go.microsoft.com/fwlink/?LinkId=169734) .  
  
2.  Suchen Sie unter **Installieren der erforderlichen Software**den Link für ADO.NET Data Services 3.5, der dem verwendeten Betriebssystem entspricht.  
  
3.  Klicken Sie auf den Link, und führen Sie das Setupprogramm aus, durch das der Dienst installiert wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Bereitstellen von PowerPivot-Lösungen in SharePoint](deploy-power-pivot-solutions-to-sharepoint.md)  
  
  
