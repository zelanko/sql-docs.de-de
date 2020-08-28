---
description: Lösungen für den Remotedatenzugriff
title: Lösungen für den Remote Datenzugriff | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS [ADO]
ms.assetid: d311cc67-7db7-4c43-9590-d465564695e4
author: rothja
ms.author: jroth
ms.openlocfilehash: 849ef40c124cfe611f72c6ad5f258d678c24c963
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88977601"
---
# <a name="solutions-for-remote-data-access"></a>Lösungen für den Remotedatenzugriff
## <a name="the-issue"></a>Das Problem  
 ADO ermöglicht Ihrer Anwendung den direkten Zugriff auf und das Ändern von Datenquellen (manchmal auch als System mit zwei Ebenen bezeichnet). Wenn beispielsweise die Verbindung mit der Datenquelle hergestellt wird, in der die Daten enthalten sind, handelt es sich um eine direkte Verbindung in einem System mit zwei Ebenen.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
 Möglicherweise möchten Sie jedoch indirekt über einen Vermittler wie Microsoft® Internetinformationsdienste (IIS) auf Datenquellen zugreifen. Diese Anordnung wird manchmal als System mit drei Ebenen bezeichnet. Bei IIS handelt es sich um ein Client/Server-System, das eine effiziente Möglichkeit bietet, eine lokale oder Client Anwendung einen Remote Server oder-Server im Internet oder in einem Intranet aufzurufen. Das Serverprogramm erhält Zugriff auf die Datenquelle und verarbeitet optional die gesammelten Daten.  
  
 Die Intranetwebseite enthält z. b. eine Anwendung, die in Microsoft® Visual Basic Scripting Edition (VBScript) geschrieben ist, die eine Verbindung mit IIS herstellt. IIS stellt wiederum eine Verbindung mit der tatsächlichen Datenquelle her, ruft die Daten ab, verarbeitet Sie auf irgendeine Weise und gibt dann die verarbeiteten Informationen an die Anwendung zurück.  
  
 In diesem Beispiel ist die Anwendung niemals direkt mit der Datenquelle verbunden. IIS hat. Und IIS haben mithilfe von ADO auf die Daten zugegriffen.  
  
> [!NOTE]
>  Die Client/Server-Anwendung muss nicht auf dem Internet oder einem Intranet (d. h. webbasiert) basieren. Sie kann nur aus kompilierten Programmen in einem lokalen Netzwerk bestehen. Der typische Fall ist jedoch eine webbasierte Anwendung.  
  
 Da einige visuelle Steuerelemente, z. b. ein Raster, ein Kontrollkästchen oder eine Liste, die zurückgegebenen Informationen verwenden können, müssen die zurückgegebenen Informationen problemlos von einem visuellen Steuerelement verwendet werden.  
  
 Sie wünschen eine einfache und effiziente Anwendungsprogrammierschnittstelle, die Systeme mit drei Ebenen unterstützt und Informationen so einfach wie möglich zurückgibt, wenn Sie auf einem System mit zwei Ebenen abgerufen wurden. Remote Data Service (RDS) ist diese Schnittstelle.  
  
## <a name="the-solution"></a>Die Lösung  
 RDS definiert ein Programmiermodell: die Abfolge von Aktivitäten, die für den Zugriff auf und die Aktualisierung einer Datenquelle erforderlich sind, um Zugriff auf Daten über einen Vermittler zu erhalten, z. b. Internetinformationsdienste (IIS). Das Programmiermodell fasst die gesamte Funktionalität von RDS zusammen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Grundlegendes RDS-Programmiermodell](./basic-rds-programming-model.md)   
 [RDS-Szenario](./rds-scenario.md)   
 [RDS-Tutorial](./rds-tutorial.md)   
 [Verwendung und Sicherheit von RDS](./rds-usage-and-security.md)