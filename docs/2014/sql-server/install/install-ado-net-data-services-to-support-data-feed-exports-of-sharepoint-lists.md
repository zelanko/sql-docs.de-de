---
title: Installieren von ADO.NET Data Services zur Unterstützung von datenfeedexporte von SharePoint-Listen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: f32527ae-f623-4e08-adfb-6d3262f5c2ac
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 622d729e0b86a210bbdaaedf29818a49e81ed2ce
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66094660"
---
# <a name="install-adonet-data-services-to-support-data-feed-exports-of-sharepoint-lists"></a>Installieren von ADO.NET Data Services, um Datenfeedexporte von SharePoint-Listen zu unterstützen
  ADO.NET Data Services sind für einen Datenfeedexport von SharePoint-Listen erforderlich. Da diese Komponente nicht im SharePoint-Programm PrerequisiteInstaller von SharePoint 2010 enthalten ist, müssen Sie sie manuell installieren.  
  
 Ohne diese Voraussetzung erhalten Sie den folgenden Fehler, wenn Sie versuchen, eine SharePoint-Liste verwenden, die als Datenfeed exportiert wurde: "Aus Sicherheitsgründen ist DTD in dieser XML-Dokument nicht zulässig. Zum Aktivieren der DTD-Verarbeitung müssen Sie die 'ProhibitDtd'-Eigenschaft für 'XmlReaderSettings' auf 'Parse' festlegen und die Einstellungen an die 'XmlReader.Create'-Methode übergeben."  
  
 Verwenden Sie die folgenden Anweisungen, um ADO.NET Data Services auf jedem SharePoint-Server zu installieren, für den der Export von Listen als Datenfeeds zulässig sein soll.  
  
### <a name="download-and-install-adonet-data-services"></a>Herunterladen und Installieren von ADO.NET Data Services  
  
1.  Wechseln Sie zu den Hardware- und softwareanforderungen für SharePoint 2010 [Hardware- und Softwareanforderungen (SharePoint 2010)](https://go.microsoft.com/fwlink/?LinkId=169734)  
  
2.  In **Zugriff auf geeignete Software**, suchen Sie den Link für ADO.NET Data Services 3.5, für das Betriebssystem entspricht (entweder Windows Server 2008 SP2 oder Windows Server 2008 R2) verwenden.  
  
3.  Klicken Sie auf den Link, und führen Sie das Setupprogramm aus, durch das der Dienst installiert wird.  
  
## <a name="see-also"></a>Siehe auch  
 [PowerPivot für SharePoint 2010-Installation](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  
