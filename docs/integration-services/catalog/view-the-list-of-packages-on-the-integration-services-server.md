---
title: Anzeigen der Liste der auf dem Integration Services-Server gespeicherten Pakete | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 67a992d1-7524-4f4b-b3d8-ebd9e5ea82a8
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f301b1e98d58d39c1d060bc3270349d0f2448cfd
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2018
ms.locfileid: "35408162"
---
# <a name="view-the-list-of-packages-on-the-integration-services-server"></a>Anzeigen der Liste der auf dem Integration Services-Server gespeicherten Pakete
  Sie können die Liste der Pakete mit einer von zwei Methoden anzeigen, die in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] auf dem Server gespeichert sind.  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] -Zugriff  
 Fragen Sie die Sicht [catalog.packages &#40;SSISDB-Datenbank&#41;](../../integration-services/system-views/catalog-packages-ssisdb-database.md) ab, um die Liste der auf dem Server gespeicherten Pakete anzuzeigen.  
  
 In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
 Folgen Sie der unten angegebenen Prozedur, um mit dem Objekt-Explorer in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]auf dem Server gespeicherten Pakete anzuzeigen.  
  
### <a name="to-view-packages-using-includessmanstudiofullincludesssmanstudiofull-mdmd"></a>So zeigen Sie Pakete an mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
  
1.  Stellen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]eine Verbindung zum [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Server her. Dies bedeutet, dass eine Verbindung mit der [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] -Instanz hergestellt werden muss, die als Host für die [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Datenbank fungiert.  
  
2.  Erweitern Sie im Objekt-Explorer die Struktur, um den Knoten **Integration Services-Kataloge** anzuzeigen.  
  
3.  Erweitern Sie den Knoten **Integration Services-Kataloge** , um den Knoten **SSISDB** anzuzeigen.  
  
4.  Erweitern Sie den Knoten **SSISDB** , um eine Liste mit mindestens einem Ordner anzuzeigen. Jeder Ordner enthält mindestens ein Projekt im Ordner **Projekte** , und jedes Projekt enthält mindestens ein Paket im Ordner **Pakete** .  
  
  
