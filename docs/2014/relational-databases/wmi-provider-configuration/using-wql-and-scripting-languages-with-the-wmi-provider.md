---
title: Verwenden von WQL und Skriptsprachen mit dem WMI-Anbieter für die Konfigurationsverwaltung | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
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
caps.latest.revision: 17
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 4dc000220a4ced29074489bbc06556bbc07a18ce
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36162212"
---
# <a name="using-wql-and-scripting-languages-with-the-wmi-provider-for-configuration-management"></a>Verwenden von WQL und Skriptsprachen mit dem WMI-Anbieter für die Konfigurationsverwaltung
  Verwaltungsanwendungen greifen auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Dienste und -Netzwerkeinstellungen mithilfe des WMI-Anbieters (Windows Management Instrumentation) für Konfigurationsverwaltungsobjekte auf zwei verschiedene Arten zu:  
  
-   Mithilfe eines WQL-Editors oder eines Abfragetools, wie beispielsweise WBEMTest.exe, zum Abfragen des Objektsatzes mit der WMI-Sprache (WQL)  
  
-   Mithilfe einer Skriptsprache, z. B. VBScript  
  
 Alternativ können [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Dienste und -Netzwerkeinstellungen programmgesteuert mithilfe von verwalteten WMI-Objekten in SMO verwaltet werden. Weitere Informationen über das Programmieren von WMI Objekte verwaltet werden, finden Sie unter [Verwalten von Diensten und Netzwerkeinstellungen durch die Verwendung der WMI-Anbieter](../server-management-objects-smo/tasks/managing-services-and-network-settings-by-using-wmi-provider.md).  
  
 Der Zugriff auf den WMI-Anbieter für die Konfigurationsverwaltung erfolgt über den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Konfigurations-Manager und über [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console. Weitere Informationen zum Zugreifen auf den WMI-Anbieter über eine Benutzeroberfläche finden Sie unter [Verwalten von Diensten: Themen &#40;SQL Server-Konfigurations-Manager&#41;](../../database-engine/managing-services-how-to-topics-sql-server-configuration-manager.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Zugreifen auf WMI-Anbieter für Konfigurationsverwaltung mit WQL](access-wmi-provider-for-configuration-management-using-wql.md)   
 [Ändern der erweiterten Eigenschaften des SQL Server-Diensts mit VBScript](access-wmi-provider-for-configuration-management-using-vbscript.md)  
  
  