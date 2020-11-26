---
title: Neuigkeiten in der SQL Server-Installation | Microsoft-Dokumentation
description: In diesem Artikel werden einige Änderungen am SQL Server-Installationsprozess zusammengefasst, darunter die SysPrep-Unterstützung und das Upgrade von SQL Server 2005.
ms.custom: ''
ms.date: 08/23/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 9b136b27-4779-4284-904f-b5a1c12bdcc0
author: cawrites
ms.author: chadam
ms.openlocfilehash: 459a40bdd51f1762e81bf17a362d1941ee7b01be
ms.sourcegitcommit: 5a1ed81749800c33059dac91b0e18bd8bb3081b1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/23/2020
ms.locfileid: "96120885"
---
# <a name="what39s-new-in-sql-server-installation"></a>Neuigkeiten in der SQL Server-Installation
[!INCLUDE [SQL Server Windows Only - ASDBMI ](../../includes/applies-to-version/sql-windows-only-asdbmi.md)]

 Die Installation wird nur für x64-Prozessoren unterstützt. Weitere Informationen finden Sie unter [Hardware- und Softwareanforderungen für die Installation von SQL Server](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).
  
 Beim Installieren von [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] werden Sie aufgefordert, das Verzeichnis anzugeben, in dem das extrahierte Paket gespeichert werden soll. Wenn kein Speicherort angegeben wird, wird der Server standardmäßig auf dem Systemlaufwerk des Computers installiert. Die extrahierten Dateien bleiben nach dem Abschluss der [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] -Installation erhalten.  
  
 SysPrep wird für alle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Installationen unterstützt. SysPrep unterstützt jetzt Failoverclusterinstallationen. Weitere Informationen finden Sie unter [Überlegungen zur Installation von SQL Server mit SysPrep](../../database-engine/install-windows/considerations-for-installing-sql-server-using-sysprep.md) und [Installieren von SQL Server mit SysPrep](../../database-engine/install-windows/install-sql-server-using-sysprep.md).  
  
 Upgrades von [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] werden unterstützt, die \-parallele\- Ausführung jedoch nicht. Weitere Informationen zur Unterstützung von [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]finden Sie unter [Unterstützte Versions- und Editionsupgrades](../../database-engine/install-windows/supported-version-and-edition-upgrades.md).  
 
  
## <a name="see-also"></a>Weitere Informationen  
[Neues in SQL Server 2017](../../sql-server/what-s-new-in-sql-server-2017.md)

[Spezifikationen der maximalen Kapazität für SQL Server](../../sql-server/maximum-capacity-specifications-for-sql-server.md)   

[Planen einer SQL Server-Installation](../../sql-server/install/planning-a-sql-server-installation.md)   

[Hardware- und Softwareanforderungen für die Installation von SQL Server](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)  
  
