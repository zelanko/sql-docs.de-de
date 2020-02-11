---
title: Installieren von ADO.NET-Data Services zur Unterstützung von Datenfeed-Exporten von SharePoint-Listen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: f32527ae-f623-4e08-adfb-6d3262f5c2ac
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: b9b3ec2d8b7459f9d66313c6a40b1cbc26450e0d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "71952164"
---
# <a name="install-adonet-data-services-to-support-data-feed-exports-of-sharepoint-lists"></a>Installieren von ADO.NET Data Services, um Datenfeedexporte von SharePoint-Listen zu unterstützen
  ADO.NET Data Services sind für einen Datenfeedexport von SharePoint-Listen erforderlich. Da diese Komponente nicht im SharePoint-Programm PrerequisiteInstaller von SharePoint 2010 enthalten ist, müssen Sie sie manuell installieren.  
  
 Ohne diese Voraussetzung erhalten Sie den folgenden Fehler, wenn Sie versuchen, eine SharePoint-Liste zu verwenden, die als Datenfeed exportiert wurde: "DTD ist in diesem XML-dokument nicht zulässig. Zum Aktivieren der DTD-Verarbeitung müssen Sie die 'ProhibitDtd'-Eigenschaft für 'XmlReaderSettings' auf 'Parse' festlegen und die Einstellungen an die 'XmlReader.Create'-Methode übergeben."  
  
 Verwenden Sie die folgenden Anweisungen, um ADO.NET Data Services auf jedem SharePoint-Server zu installieren, für den der Export von Listen als Datenfeeds zulässig sein soll.  
  
### <a name="download-and-install-adonet-data-services"></a>Herunterladen und Installieren von ADO.NET Data Services  
  
1.  Wechseln Sie zur Dokumentation zu Hardware-und Softwareanforderungen für SharePoint 2010-, [Hardware-und Softwareanforderungen (SharePoint 2010)](https://go.microsoft.com/fwlink/?LinkId=169734) .  
  
2.  Suchen Sie unter **Zugriff auf die entsprechende Software**den Link für ADO.NET Data Services 3,5, der dem verwendeten Betriebssystem entspricht (entweder Windows Server 2008 SP2 oder Windows Server 2008 R2).  
  
3.  Klicken Sie auf den Link, und führen Sie das Setupprogramm aus, durch das der Dienst installiert wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [PowerPivot for SharePoint 2010 Installation](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  
