---
title: 'Datenbank-Engine: Breaking Changes | Microsoft-Dokumentation'
titleSuffix: SQL Server 2017
description: Wichtige Änderungen an Funktionen der Datenbank-Engine in SQL Server 2017
ms.custom: seo-lt-2019
ms.date: 12/13/2019
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: release-landing
ms.topic: conceptual
helpviewer_keywords:
- breaking changes 2017 [SQL Server]
ms.assetid: ''
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 2140c54c8954006c4285eaccbb59f2f0c4964577
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "77074498"
---
# <a name="breaking-changes-to-database-engine-features-in-sssqlv14-md"></a>Wichtige Änderungen an Funktionen der Datenbank-Engine in [!INCLUDE[sssqlv14-md](../includes/sssqlv14-md.md)]
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]


  In diesem Artikel werden Breaking Changes in [!INCLUDE[sssqlv14-md](../includes/sssqlv14-md.md)] [!INCLUDE[ssDE](../includes/ssde-md.md)] beschrieben. Diese Änderungen können u. U. zur Funktionsunfähigkeit von Anwendungen, Skripts oder Funktionen führen, die auf früheren Versionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]basieren. Diese Probleme können nach einem Upgrade auftreten.  
  
## <a name="breaking-changes-in-sssqlv14-md-ssde"></a>Breaking Changes in [!INCLUDE[sssqlv14-md](../includes/sssqlv14-md.md)] [!INCLUDE[ssDE](../includes/ssde-md.md)]  
  
-  CLR verwendet die Codezugriffssicherheit (Code Access Security, CAS) im .NET Framework, die nicht länger als Sicherheitsbegrenzung unterstützt wird. Ab [!INCLUDE[sssqlv14-md](../includes/sssqlv14-md.md)][!INCLUDE[ssDE](../includes/ssde-md.md)] wird eine `sp_configure`-Option mit der Bezeichnung `clr strict security` eingeführt, um die Sicherheit von CLR-Assemblys zu erhöhen. CLR Strict Security ist standardmäßig aktiviert und behandelt `SAFE`- und `EXTERNAL_ACCESS`-Assemblys so, als wären Sie als `UNSAFE` gekennzeichnet. Die Option `clr strict security` kann für die Abwärtskompatibilität deaktiviert werden, es wird jedoch nicht empfohlen. Wenn `clr strict security` deaktiviert ist, kann eine CLR-Assembly, die mit `PERMISSION_SET = SAFE` erstellt wurde, möglicherweise auf externe Systemressourcen zugreifen, nicht verwalteten Code aufrufen und **sysadmin**-Privilegien erwerben. Nachdem Sie Strict Security aktiviert haben, können Assemblys, die nicht signiert sind, nicht geladen werden. Wenn eine Datenbank über `SAFE`- oder `EXTERNAL_ACCESS`-Assemblys verfügt, können `RESTORE`- oder `ATTACH DATABASE`-Anweisungen abgeschlossen werden, aber die Assemblys können möglicherweise nicht geladen werden.   
  Um die Assemblys zu laden, müssen Sie jede Assembly entweder bearbeiten, ablegen oder neu erstellen, damit sie mit einem Zertifikat oder asymmetrischen Schlüssel signiert ist, der über einen entsprechenden Anmeldenamen mit der `UNSAFE ASSEMBLY`-Berechtigung auf dem Server verfügt. Weitere Informationen finden Sie unter [CLR Strict Security](../database-engine/configure-windows/clr-strict-security.md). 
  
-  Die Algorithmen MD2, MD4, MD5, SHA und SHA-1 sind ab [!INCLUDE[ssSQL15](../includes/sssql15-md.md)] veraltet. Bis [!INCLUDE[ssSQL15](../includes/sssql15-md.md)] werden selbstsignierte Zertifikate mit SHA-1 erstellt. Ab [!INCLUDE[ssSQL17](../includes/sssql17-md.md)] werden selbstsignierte Zertifikate mit SHA-256 erstellt.

## <a name="previous-versions"></a><a name="previous-versions"></a> Vorgängerversionen  

- [Fehlerhafte Änderungen an Funktionen der Datenbank-Engine in SQL Server 2016](../database-engine/breaking-changes-to-database-engine-features-in-sql-server-2016.md)

- [Fehlerhafte Änderungen an Funktionen der Datenbank-Engine in SQL Server 2014](https://docs.microsoft.com/sql/database-engine/breaking-changes-to-database-engine-features-in-sql-server-2016?view=sql-server-2014#SQL14)

#### <a name="archived-documentation-for-very-old-versions-of-sql-server"></a>Archivierte Dokumentationen von sehr alten Versionen von SQL Server

[!INCLUDE[Archived documentation for very old versions of SQL Server](../includes/paragraph-content/previous-versions-archive-documentation-sql-server.md)]

## <a name="see-also"></a>Weitere Informationen  
 [Als veraltet markierte Funktionen der Datenbank-Engine in SQL Server 2016](../database-engine/deprecated-database-engine-features-in-sql-server-2016.md)   
 [Nicht mehr unterstützte Datenbank-Engine-Funktionalität in SQL Server 2016](../database-engine/discontinued-database-engine-functionality-in-sql-server-2016.md)   
 [Abwärtskompatibilität der SQL Server-Datenbank-Engine](../database-engine/sql-server-database-engine-backward-compatibility.md)   
 [ALTER DATABASE-Kompatibilitätsgrad &#40;Transact-SQL&#41;](../t-sql/statements/alter-database-transact-sql-compatibility-level.md)  
  
  
