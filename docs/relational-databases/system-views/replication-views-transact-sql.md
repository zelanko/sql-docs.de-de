---
title: Replikations Sichten (Transact-SQL) | Microsoft-Dokumentation
description: Replikations Sichten enthalten Informationen, die von der Replikation in SQL Server verwendet werden. Die Sichten ermöglichen einen leichteren Zugriff auf Daten in Replikationstabellen.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- distribution databases [SQL Server replication], system views
- metadata [SQL Server], views
- views [SQL Server], replication
- replication views [SQL Server]
- publications [SQL Server replication], system views
- articles [SQL Server replication], system views
- replication metadata [SQL Server]
- subscriptions [SQL Server replication], system views
- system views [SQL Server], replication
ms.assetid: 93e5056d-0d93-4a48-ba33-72762eb995d8
author: stevestein
ms.author: sstein
ms.openlocfilehash: ab4088aa563befcb32eaaf8fe129716b789f516b
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87243611"
---
# <a name="replication-views-transact-sql"></a>Replikationssichten (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Diese Sichten enthalten Informationen, die von der Replikation in verwendet werden [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Die Sichten ermöglichen einen einfacheren Zugriff auf Daten in den [Replikationssystem Tabellen](../../relational-databases/system-tables/replication-tables-transact-sql.md). Sichten werden in einer Benutzerdatenbank erstellt, wenn diese Datenbank als Veröffentlichungs- oder Abonnementdatenbank aktiviert wird. Wird die Datenbank aus der Replikationstopologie entfernt, dann werden auch alle Replikationsobjekte aus Benutzerdatenbanken entfernt. Die bevorzugte Methode für den Zugriff auf Replikations Metadaten ist die Verwendung [gespeicherter Replikations Proze](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
> [!IMPORTANT]  
>  Systemsichten sollten von keinem Benutzer direkt geändert werden.  
  
## <a name="replication-views"></a>Replikationssichten  
 Im Folgenden wird eine Liste der von der Replikation verwendeten Systemsichten aufgeführt. Die Liste ist nach Datenbanken gruppiert.  
  
### <a name="replication-views-in-the-msdb-database"></a>Replikationssichten in der msdb-Datenbank  

:::row:::
    :::column:::
        [MSdatatype_mappings &#40;Transact-SQL-&#41;](../../relational-databases/system-views/msdatatype-mappings-transact-sql.md)
    :::column-end:::
    :::column:::
        [sysdatatypeer Mappings &#40;Transact-SQL-&#41;](../../relational-databases/system-views/sysdatatypemappings-transact-sql.md)
    :::column-end:::
:::row-end:::

### <a name="replication-views-in-the-distribution-database"></a>Replikationssichten in der Verteilungsdatenbank  

:::row:::
    :::column:::
        [IHextendedArticleView &#40;Transact-SQL-&#41;](../../relational-databases/system-views/ihextendedarticleview-transact-sql.md)

        [Ihextendedabonptionview &#40;Transact-SQL-&#41;](../../relational-databases/system-views/ihextendedsubscriptionview-transact-sql.md)

        [IHsyscolumns &#40;Transact-SQL-&#41;](../../relational-databases/system-views/ihsyscolumns-transact-sql.md)

        [MSdistribution_status &#40;Transact-SQL-&#41;](../../relational-databases/system-views/msdistribution-status-transact-sql.md)

        [sysarticlecolumns &#40;System Ansicht&#41; &#40;Transact-SQL-&#41;](../../relational-databases/system-views/sysarticlecolumns-system-view-transact-sql.md)
    :::column-end:::
    :::column:::
        [sysarticles &#40;System Ansicht&#41; &#40;Transact-SQL-&#41;](../../relational-databases/system-views/sysarticles-system-view-transact-sql.md)

        [sysextendedarticlesview &#40;Transact-SQL-&#41;](../../relational-databases/system-views/sysextendedarticlesview-transact-sql.md)

        [syspublications &#40;Systemsicht&#41; &#40;Transact-SQL&#41;](../../relational-databases/system-views/syspublications-system-view-transact-sql.md)

        [syssubscriptions &#40;Systemsicht&#41; &#40;Transact-SQL&#41;](../../relational-databases/system-views/syssubscriptions-system-view-transact-sql.md)
    :::column-end:::
:::row-end:::

### <a name="replication-views-in-the-publication-database"></a>Replikationssichten in der Veröffentlichungsdatenbank  

:::row:::
    :::column:::
        [sysmergeextendedarticlesview &#40;Transact-SQL-&#41;](../../relational-databases/system-views/sysmergeextendedarticlesview-transact-sql.md)

        [systranschemas &#40;Transact-SQL-&#41;](../../relational-databases/system-views/systranschemas-transact-sql.md)
    :::column-end:::
    :::column:::
        [sysmergepartitioninfoview &#40;Transact-SQL-&#41;](../../relational-databases/system-views/sysmergepartitioninfoview-transact-sql.md)
    :::column-end:::
:::row-end:::

### <a name="replication-views-in-the-subscription-database"></a>Replikationssichten in der Abonnementdatenbank  

:::row:::
    :::column:::
        [sysmergeextendedarticlesview &#40;Transact-SQL-&#41;](../../relational-databases/system-views/sysmergeextendedarticlesview-transact-sql.md)

        [sysmergepartitioninfoview &#40;Transact-SQL-&#41;](../../relational-databases/system-views/sysmergepartitioninfoview-transact-sql.md)
    :::column-end:::
    :::column:::
        [systranschemas &#40;Transact-SQL-&#41;](../../relational-databases/system-views/systranschemas-transact-sql.md)
    :::column-end:::
:::row-end:::
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikationstabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
