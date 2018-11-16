---
title: Konfigurieren von virtuellen Servern unter IIS | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- virtual servers in RDS [ADO]
ms.assetid: 2b4786c6-40c4-4ce1-9ad4-03df436e0aff
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c248afac72fac013759ad80f69dea199756a4010
ms.sourcegitcommit: 1a5448747ccb2e13e8f3d9f04012ba5ae04bb0a3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/12/2018
ms.locfileid: "51559527"
---
# <a name="configuring-virtual-servers-on-iis"></a>Konfigurieren von virtuellen Servern unter IIS
Beim Erstellen virtueller Server in Internet Information Services 4.0 sind die folgenden zwei zusätzliche Schritte erforderlich, um den virtuellen Server für mit RDS zu konfigurieren:  
  
1.  Wenn Sie den Server einrichten, überprüfen Sie "Zulassen der Execute-Zugriff".  
  
2.  Msadcs.dll zu verschieben *Vroot*\msadc, wobei *Vroot* das Basisverzeichnis des virtuellen Servers ist.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="see-also"></a>Siehe auch  
 [Grundlegendes zu RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)


