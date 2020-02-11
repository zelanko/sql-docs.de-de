---
title: Konfigurieren des Data Warehouses für den Steuerungspunkt für das Hilfsprogramm (SQL Server-Hilfsprogramm) | Microsoft Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: c2c6f050-8cdb-4b8e-ad38-4aae0a949847
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: d2a9f40c2d1566a1f8ca5f054467f61da1920e5f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62805936"
---
# <a name="configure-your-utility-control-point-data-warehouse-sql-server-utility"></a>Konfigurieren des Data Warehouses für den Steuerungspunkt für das Hilfsprogramm (SQL Server-Hilfsprogramm)
  Die von verwalteten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanzen gesammelten Daten werden im UMDW (Utility Management Data Warehouse) gespeichert. Der UMDW-Dateiname lautet sysutility_mdw.  
  
 Sie können die Beibehaltungsdauer der UMDW-Daten konfigurieren. Weitere Informationen finden Sie unter [Hilfsprogrammverwaltung &#40;SQL Server-Hilfsprogramm&#41;](../../database-engine/utility-administration-sql-server-utility.md).  
  
 Die folgenden Konfigurationseinstellungen sind in dieser Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]nicht konfigurierbar:  
  
-   UMDW-Name: Sysutility_mdw.  
  
-   Uploadfrequenz für den Sammlungssatz: Alle 15 Minuten  
  
 Das UMDW-Verzeichnis ist konfigurierbar: \<Systemlaufwerk>:\Programme\Microsoft SQL Server\MSSQL10_50.<UCP_Name>\MSSQL\Data\\, wobei \<Systemlaufwerk> normalerweise Laufwerk C:\ entspricht. Die Protokolldatei „Sysutility_mdw_\<GUID>_LOG“ befindet sich im selben Verzeichnis.  
  
> [!NOTE]  
>  Der Speicherort der UMDW-Datei (sysutility_mdw) kann mithilfe von Detach/Attach oder ALTER DATABASE geändert werden. Es wird empfohlen, ALTER DATABASE zu verwenden. Weitere Informationen finden Sie unter [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Funktionen und Tasks im SQL Server-Hilfsprogramm](sql-server-utility-features-and-tasks.md)  
  
  
