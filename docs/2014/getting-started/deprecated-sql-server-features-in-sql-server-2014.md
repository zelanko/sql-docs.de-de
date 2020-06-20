---
title: Veraltete SQL Server Features in SQL Server 2014 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: fdc0c778-cc8d-42ab-8833-4deb4329f37a
author: rothja
ms.author: jroth
ms.openlocfilehash: 7e4d888eee5ea6048d61007728bb436dabdccb8e
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84926992"
---
# <a name="deprecated-sql-server-features-in-sql-server-2014"></a>Als veraltet markierte SQL Server-Funktionen in SQL Server 2014
  In diesem Thema werden die als veraltet markierten Funktionen beschrieben, die in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]noch verfügbar sind. Diese Funktionen werden voraussichtlich in einer zukünftigen Version von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]entfernt. Als veraltet markierte Funktionen sollten in neuen Anwendungen nicht verwendet werden.  
  
## <a name="features-not-supported-in-the-next-version-of-ssnoversion"></a>Funktionen, die in der nächsten Version von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] nicht unterstützt werden  
 Die folgenden [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] -Funktionen werden in der nächsten Version von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]nicht mehr unterstützt. Verwenden Sie diese Funktionen nicht zum Entwickeln neuer Anwendungen, und ändern Sie so bald wie möglich die Anwendungen, in denen diese Funktionen zurzeit verwendet werden. Die Spalte Funktionsname wird in Ablaufverfolgungsereignissen als ObjectName und in Leistungsindikatoren sowie sys.dm_os_performance_counters als instance_name angezeigt. Die Funktions-ID wird in Ablaufverfolgungsereignissen als ObjectId angezeigt.  
  
|Category|Als veraltet markierte Funktion|Ersatz|Feature name|Feature ID|  
|--------------|------------------------|-----------------|------------------|----------------|  
|Datenprogrammierbarkeit|[sys. soap_endpoints &#40;Transact-SQL-&#41;](/sql/relational-databases/system-catalog-views/sys-soap-endpoints-transact-sql)|Windows Communications Foundation (WCF) oder ASP.NET|Systemeigene XML-Webdienste|22|  
|Datenprogrammierbarkeit|[sys. endpoint_webmethods &#40;Transact-SQL-&#41;](/sql/relational-databases/system-catalog-views/sys-endpoint-webmethods-transact-sql)|Windows Communications Foundation (WCF) oder ASP.NET|Systemeigene XML-Webdienste|23|  
  
### <a name="slipstream-functionality"></a>Slipstreamfunktionalität  
 Die [Produkt Update Funktion](/previous-versions/sql/sql-server-2012/hh231670(v=sql.110)?redirectedfrom=MSDN) wurde in SQL Server 2012 als Erweiterung der slipstreamfunktionalität eingeführt, die in PCU1 verfügbar war [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] . In SQL Server 2014 ist die Produkt Update-Funktion die empfohlene Methode für das das Slipstreaming SQL Server. Daher sollten die Befehlszeilenparameter/*PCUSource* und/*CUSource*, die der ursprünglichen slipstreamfunktionalität zugeordnet sind, nicht mehr verwendet werden. Diese Parameter funktionieren weiterhin, werden jedoch möglicherweise in einer zukünftigen Version von Setup entfernt [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Der empfohlene Parameter für die Verwendung von ist/*UpdateSource* , der die Funktionalität der ursprünglichen slipstreamparameter,/*PCUSource* und/*CUSource*, kombiniert.  
  
 Weitere Informationen zur slipstreamfunktionalität, die in PCU1 verfügbar war [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] , finden Sie unter [Slipstream a SQL Server Update](https://go.microsoft.com/fwlink/?LinkId=219945) ( https://go.microsoft.com/fwlink/?LinkId=219945) .  
 Informationen zur Verwendung von/*UpdateSource* für die Slipstream-SQL Server Builds finden Sie in den folgenden Ressourcen:
 
 - [Vorgehensweise beim Patchen SQL Server 2012-Setups mit einem aktualisierten Setup Paket (mit UpdateSource zum Einrichten einer intelligenten Installation)](https://blogs.msdn.microsoft.com/jason_howell/2012/08/28/how-to-patch-sql-server-2012-setup-with-an-updated-setup-package-using-updatesource-to-get-a-smart-setup/)
 
 - [SQL Server 2012-Setup ist noch intelligenter...](https://techcommunity.microsoft.com/t5/SQL-Server-Support/SQL-Server-2012-Setup-just-got-smarter-8230/ba-p/317440)
 
## <a name="see-also"></a>Weitere Informationen  
 [Abwärtskompatibilität](../../2014/getting-started/backward-compatibility.md)  
  
  
