---
title: Installieren von ADO.NET Data Services um Daten zu unterstützen datenfeedexporte von SharePoint-Listen | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f32527ae-f623-4e08-adfb-6d3262f5c2ac
caps.latest.revision: 6
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: d4241d56aa3257bd0ec2cddf4b439a4939f8ab9f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36056125"
---
# <a name="install-adonet-data-services-to-support-data-feed-exports-of-sharepoint-lists"></a>Installieren von ADO.NET Data Services, um Datenfeedexporte von SharePoint-Listen zu unterstützen
  ADO.NET Data Services sind für einen Datenfeedexport von SharePoint-Listen erforderlich. Da diese Komponente nicht im SharePoint-Programm PrerequisiteInstaller von SharePoint 2010 enthalten ist, müssen Sie sie manuell installieren.  
  
 Ohne diese Voraussetzung erhalten Sie den folgenden Fehler, wenn Sie versuchen, eine SharePoint-Liste zu verwenden, die als Datenfeed exportiert wurde: "DTD ist in diesem XML-dokument nicht zulässig. Zum Aktivieren der DTD-Verarbeitung müssen Sie die 'ProhibitDtd'-Eigenschaft für 'XmlReaderSettings' auf 'Parse' festlegen und die Einstellungen an die 'XmlReader.Create'-Methode übergeben."  
  
 Verwenden Sie die folgenden Anweisungen, um ADO.NET Data Services auf jedem SharePoint-Server zu installieren, für den der Export von Listen als Datenfeeds zulässig sein soll.  
  
### <a name="download-and-install-adonet-data-services"></a>Herunterladen und Installieren von ADO.NET Data Services  
  
1.  Wechseln Sie zu den Hardware- und softwareanforderungen für SharePoint 2010 [Hardware- und Softwareanforderungen (SharePoint 2010)](http://go.microsoft.com/fwlink/?LinkId=169734)  
  
2.  In **Zugriff auf geeignete Software**, suchen Sie den Link für ADO.NET Data Services 3.5, für das Betriebssystem entspricht (Windows Server 2008 SP2 oder Windows Server 2008 R2) verwenden.  
  
3.  Klicken Sie auf den Link, und führen Sie das Setupprogramm aus, durch das der Dienst installiert wird.  
  
## <a name="see-also"></a>Siehe auch  
 [PowerPivot für SharePoint 2010-Installation](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  