---
description: Gespeicherte Prozeduren für Firewallregeln (Azure SQL-Datenbank)
title: Gespeicherte Prozeduren für Firewallregeln
titleSuffix: Azure SQL Database
ms.date: 07/28/2016
ms.service: sql-database
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- firewall rules stored procedures
- firewall_rules, setting
- firewall_rules, Azure SQL Database
- firewall systems, Azure SQL Database
ms.assetid: 3d4c2585-00de-46b5-8eee-0efb71cb3aea
author: VanMSFT
ms.author: vanto
ms.custom: seo-dt-2019
monikerRange: = azuresqldb-current || = azure-sqldw-latest
ms.openlocfilehash: f4597a05c6f1376a39d98894d6e510b7928a450d
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97474661"
---
# <a name="firewall-rules-stored-procedures-azure-sql-database"></a>Gespeicherte Prozeduren für Firewallregeln (Azure SQL-Datenbank)
[!INCLUDE [asdb-asa](../../includes/applies-to-version/asdb-asa.md)]

  Dieser Abschnitt enthält die folgenden gespeicherten Prozeduren, die Firewallregeln festlegen oder löschen. [!INCLUDE[tsql_md](../../includes/tsql-md.md)] Firewallregeln können mit und verwendet werden [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] [!INCLUDE[ssSDW_md](../../includes/sssdw-md.md)] . Weitere Informationen finden Sie unter [Konfigurieren von Firewallregeln für Azure SQL-Datenbank (Übersicht](/azure/azure-sql/database/firewall-configure)).

:::row:::
    :::column:::
        [sp_set_firewall_rule &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database.md)
    :::column-end:::
    :::column:::
        [sp_delete_firewall_rule &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-stored-procedures/sp-delete-firewall-rule-azure-sql-database.md)
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
        [sp_set_database_firewall_rule &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-stored-procedures/sp-set-database-firewall-rule-azure-sql-database.md)
    :::column-end:::
    :::column:::
        [sp_delete_database_firewall_rule &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-stored-procedures/sp-delete-database-firewall-rule-azure-sql-database.md)
    :::column-end:::
:::row-end:::

&nbsp;
  
Verwenden Sie für [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] Windows-Firewallregeln. Weitere Informationen zur Windows-Firewall finden Sie unter [Konfigurieren einer Windows-Firewall für Datenbank-Engine-Zugriff](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md).   
