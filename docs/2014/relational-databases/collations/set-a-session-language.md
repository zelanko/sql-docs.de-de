---
title: Festlegen einer Sitzungssprache | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 38
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 17df915dc44251d32f27e3693d58baf4ddfebaf2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36057853"
---
# <a name="set-a-session-language"></a>Festlegen einer Sitzungssprache
  Die Sitzungssprache kann verwendet werden, um festzulegen, wie die folgenden Elemente abhängig von Sprache und Kultur auf dem Server angezeigt werden:  
  
-   Die Sprache, die für Fehlermeldungen und andere Systemmeldungen verwendet wird. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt das Vorhandensein mehrerer Kopien aller Systemfehler-Zeichenfolgen und Meldungen in allen Sprachen, in denen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verfügbar ist. Diese Meldungen können mithilfe der [sys.messages](/sql/relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages) -Katalogsicht angezeigt werden. Wenn Sie eine lokalisierte Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installieren, sind diese Systemmeldungen für die installierte Sprachversion übersetzt. Standardmäßig erhalten Sie auch die US-englischen Meldungen . Außerdem können Sie benutzerdefinierte Meldungen in einer bestimmten Sprache mithilfe von [sp_addmessage](/sql/relational-databases/system-stored-procedures/sp-addmessage-transact-sql) hinzufügen.  
  
-   Das Format von Datums- und Zeitdaten.  
  
-   Die Namen von Tagen und Monaten, einschließlich Abkürzungen.  
  
-   Der erste Tag der Woche.  
  
-   Währungsdaten.  
  
 Für die Sitzungseinstellungen sind 33 Sprachen verfügbar. Eine Liste der Sprachen finden Sie unter [sys.syslanguages](/sql/relational-databases/system-compatibility-views/sys-syslanguages-transact-sql).  
  
## <a name="setting-the-session-language-from-the-server"></a>Festlegen der Sitzungssprache auf dem Server  
 So legen Sie die Sitzungssprache serverseitig fest. Verwenden Sie [SET LANGUAGE](/sql/t-sql/statements/set-language-transact-sql).  
  
## <a name="setting-the-session-language-from-the-client"></a>Festlegen der Sitzungssprache auf dem Client  
 Die Sitzungssprache kann clientseitig mit OLE DB, ODBC oder ADO.NET festgelegt werden. Verwenden Sie für OLE DB die Eigenschaft SSPROP_INIT_CURRENTLANGUAGE. Weitere Informationen hierzu finden Sie unter [Initialisierungs- und Autorisierungseigenschaften](../native-client-ole-db-data-source-objects/initialization-and-authorization-properties.md).  
  
 Verwenden Sie für ODBC das programmiersprachliche Schlüsselwort. Weitere Informationen finden Sie unter [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md).  
  
 Verwenden Sie für ADO.NET den **Current Language** -Parameter des Objekts **ConnectionString** . Weitere Informationen finden Sie in der Dokumentation zu [!INCLUDE[msCoName](../../includes/msconame-md.md)] Data Access Components (MDAC) Software Development Kit (SDK).  
  
  
