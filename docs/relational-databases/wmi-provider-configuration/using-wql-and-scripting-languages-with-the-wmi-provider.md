---
title: Zugreifen auf den WMI-Anbieter mit WQL und Skripterstellung
description: Erfahren Sie, wie Sie mit dem WMI-Anbieter auf SQL Server Dienste und Netzwerkeinstellungen zugreifen, indem Sie einen WQL-Editor oder ein Abfrage Tool oder eine Skriptsprache verwenden.
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- queries [WMI]
- scripts [WMI]
- query language [WMI]
- WMI Query Language [WMI]
- WQL [WMI]
- WMI Provider for Configuration Management, WQL
- WMI Provider for Configuration Management, scripts
ms.assetid: c1e64905-3c2b-4974-88f4-abf17cf7e289
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: db39dfd29532f2a0fd2d61ce4a987e0aada7d6c5
ms.sourcegitcommit: bf5e9cb3a2caa25d0a37f401b3806b7baa5adea8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/24/2020
ms.locfileid: "85295403"
---
# <a name="using-wql-and-scripting-languages-with-the-wmi-provider"></a>Verwenden von WQL und Skriptsprachen mit dem WMI-Anbieter
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Verwaltungsanwendungen greifen auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Dienste und -Netzwerkeinstellungen mithilfe des WMI-Anbieters (Windows Management Instrumentation) für Konfigurationsverwaltungsobjekte auf zwei verschiedene Arten zu:  
  
-   Mithilfe eines WQL-Editors oder eines Abfragetools, wie beispielsweise WBEMTest.exe, zum Abfragen des Objektsatzes mit der WMI-Sprache (WQL)  
  
-   Mithilfe einer Skriptsprache, z. B. VBScript  
  
 Alternativ können [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Dienste und -Netzwerkeinstellungen programmgesteuert mithilfe von verwalteten WMI-Objekten in SMO verwaltet werden. Weitere Informationen zum Programmieren von WMI-verwalteten Objekten finden [Sie unter Verwalten von Diensten und Netzwerkeinstellungen mit dem WMI-Anbieter](../../relational-databases/server-management-objects-smo/tasks/managing-services-and-network-settings-by-using-wmi-provider.md).  
  
 Der Zugriff auf den WMI-Anbieter für die Konfigurationsverwaltung erfolgt über den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Konfigurations-Manager und über [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console. Weitere Informationen zum Zugreifen auf den WMI-Anbieter über eine Benutzeroberfläche finden [Sie unter Verwalten von Diensten &#40;SQL Server-Konfigurations-Manager&#41;](https://msdn.microsoft.com/library/78dee169-df0c-4c95-9af7-bf033bc9fdc6).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Zugreifen auf den WMI-Anbieter für die Konfigurations Verwaltung mit WQL](../../relational-databases/wmi-provider-configuration/access-wmi-provider-for-configuration-management-using-wql.md)   
 [Zugreifen auf den WMI-Anbieter mit VBScript](../../relational-databases/wmi-provider-configuration/access-wmi-provider-for-configuration-management-using-vbscript.md)  
  
  
