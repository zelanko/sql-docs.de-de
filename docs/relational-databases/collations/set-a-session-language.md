---
title: Festlegen einer Sitzungssprache | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- errors [SQL Server], international considerations
- globalization [SQL Server], sessions
- time [SQL Server]
- sessions [SQL Server], languages
- international considerations [SQL Server], sessions
- dates [SQL Server], session languages
- global considerations [SQL Server], sessions
- client-side session language
- time [SQL Server], session languages
- messages [SQL Server], international considerations
- server-side session language
ms.assetid: de7f2c90-8f4f-4cfc-94cc-4933a7fd2bde
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: d2acf936682a9c220d08df637778169e9a5b5840
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85719907"
---
# <a name="set-a-session-language"></a>Festlegen einer Sitzungssprache
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  Die Sitzungssprache kann verwendet werden, um festzulegen, wie die folgenden Elemente abhängig von Sprache und Kultur auf dem Server angezeigt werden:  
  
-   Die Sprache, die für Fehlermeldungen und andere Systemmeldungen verwendet wird. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt das Vorhandensein mehrerer Kopien aller Systemfehler-Zeichenfolgen und Meldungen in allen Sprachen, in denen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verfügbar ist. Diese Meldungen können mithilfe der [sys.messages](../../relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages.md) -Katalogsicht angezeigt werden. Wenn Sie eine lokalisierte Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]installieren, sind diese Systemmeldungen für die installierte Sprachversion übersetzt. Standardmäßig erhalten Sie auch die US-englischen Meldungen . Außerdem können Sie benutzerdefinierte Meldungen in einer bestimmten Sprache mithilfe von [sp_addmessage](../../relational-databases/system-stored-procedures/sp-addmessage-transact-sql.md)hinzufügen.  
  
-   Das Format von Datums- und Zeitdaten.  
  
-   Die Namen von Tagen und Monaten, einschließlich Abkürzungen.  
  
-   Der erste Tag der Woche.  
  
-   Währungsdaten.  
  
 Für die Sitzungseinstellungen sind 33 Sprachen verfügbar. Eine Liste der Sprachen finden Sie unter [sys.syslanguages](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md).  
  
## <a name="setting-the-session-language-from-the-server"></a>Festlegen der Sitzungssprache auf dem Server  
 So legen Sie die Sitzungssprache serverseitig fest. Verwenden Sie [SET LANGUAGE](../../t-sql/statements/set-language-transact-sql.md).  
  
## <a name="setting-the-session-language-from-the-client"></a>Festlegen der Sitzungssprache auf dem Client  
 Die Sitzungssprache kann clientseitig mit OLE DB, ODBC oder ADO.NET festgelegt werden. Verwenden Sie für OLE DB die Eigenschaft SSPROP_INIT_CURRENTLANGUAGE. Weitere Informationen hierzu finden Sie unter [Initialisierungs- und Autorisierungseigenschaften](../../relational-databases/native-client-ole-db-data-source-objects/initialization-and-authorization-properties.md).  
  
 Verwenden Sie für ODBC das programmiersprachliche Schlüsselwort. Weitere Informationen finden Sie unter [SQLConfigDataSource](../../relational-databases/native-client-odbc-api/sqlconfigdatasource.md).  
  
 Verwenden Sie für ADO.NET den **Current Language** -Parameter des Objekts **ConnectionString** . Weitere Informationen finden Sie in der Dokumentation zu [!INCLUDE[msCoName](../../includes/msconame-md.md)] Data Access Components (MDAC) Software Development Kit (SDK).  
  
  
