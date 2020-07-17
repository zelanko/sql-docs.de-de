---
title: Konfigurieren des Data Warehouses für den Steuerungspunkt für das Hilfsprogramm (SQL Server-Hilfsprogramm) | Microsoft Dokumentation
description: Hier erfahren Sie mehr über Utility Management Data Warehouse (UMDW), wo Instanzen von SQL Server Daten speichern. Erfahren Sie, wie Sie den Zeitraum für die Datenaufbewahrung und das Verzeichnis konfigurieren.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: c2c6f050-8cdb-4b8e-ad38-4aae0a949847
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e35e6e779a138633c8ea15c79a2d1370c1b3edcf
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85775988"
---
# <a name="configure-your-utility-control-point-data-warehouse-sql-server-utility"></a>Konfigurieren des Data Warehouses für den Steuerungspunkt für das Hilfsprogramm (SQL Server-Hilfsprogramm)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Die von verwalteten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanzen gesammelten Daten werden im UMDW (Utility Management Data Warehouse) gespeichert. Der UMDW-Dateiname lautet sysutility_mdw.  
  
 Sie können die Beibehaltungsdauer der UMDW-Daten konfigurieren. Weitere Informationen finden Sie unter [Hilfsprogrammverwaltung &#40;SQL Server-Hilfsprogramm&#41;](https://msdn.microsoft.com/library/3e5a00c3-8905-40f0-9ddc-d924df9c2f0d).  
  
 Die folgenden Konfigurationseinstellungen sind in dieser Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]nicht konfigurierbar:  
  
-   UMDW name (UMDW-Name): Sysutility_mdw.  
  
-   Collection set upload frequency (Uploadhäufigkeit des Sammlungssatzes): Every 15 minutes (Alle 15 Minuten).  
  
 Das UMDW-Verzeichnis ist konfigurierbar: \<System drive>:\Programme\Microsoft SQL Server\MSSQL10_50.<UCP_Name>\MSSQL\Data\\, wobei \<System drive> normalerweise dem Laufwerk „C:\“ entspricht. Die Protokolldatei „Sysutility_mdw_\<GUID>_LOG“ befindet sich im selben Verzeichnis.  
  
> [!NOTE]  
>  Der Speicherort der UMDW-Datei (sysutility_mdw) kann mithilfe von Detach/Attach oder ALTER DATABASE geändert werden. Es wird empfohlen, ALTER DATABASE zu verwenden. Weitere Informationen finden Sie unter [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Funktionen und Tasks im SQL Server-Hilfsprogramm](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)  
  
  
