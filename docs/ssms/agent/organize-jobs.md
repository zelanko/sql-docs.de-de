---
description: Aufträge organisieren
title: Aufträge organisieren
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- job category
- organize jobs
ms.assetid: 629c3e06-f933-483b-8621-280dbb7a7bd1
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: ad737fea7ae2a9c55977ffb9d838fdcbeccad412
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88319046"
---
# <a name="organize-jobs"></a>Aufträge organisieren
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> In [Azure SQL Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) werden derzeit die meisten, aber nicht alle, SQL Server-Agent-Features unterstützt. Details dazu finden Sie unter [T-SQL-Unterschiede zwischen Azure SQL Managed Instance und SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Auftragskategorien helfen Ihnen dabei, Ihre Aufträge zum einfachen Filtern und Gruppieren zu organisieren. Sie können z. B. alle Aufträge für die Datenbanksicherung in der Datenbankwartungskategorie organisieren. Sie können zudem eigene Auftragskategorien erstellen.  
  
> [!WARNING]  
> Multiserverkategorien sind nur auf einem Masterserver vorhanden. Auf einem Masterserver ist nur eine Standardauftragskategorie verfügbar: [**Nicht kategorisiert (Multiserver)**]. Beim Herunterladen eines Multiserverauftrags wird seine Kategorie auf dem Zielserver in **Aufträge vom MSX** geändert.  
  
## <a name="related-tasks"></a>Related Tasks  
  
|BESCHREIBUNG|Thema|  
|-|-|  
|Beschreibt, wie eine Auftragskategorie erstellt wird.|[Erstellen einer Auftragskategorie](../../ssms/agent/create-a-job-category.md)|  
|Beschreibt, wie eine Auftragskategorie gelöscht wird.|[Löschen einer Auftragskategorie](../../ssms/agent/delete-a-job-category.md)|  
|Beschreibt, wie ein Auftrag einer Auftragskategorie zugewiesen wird.|[Zuweisen eines Auftrags zu einer Auftragskategorie](../../ssms/agent/assign-a-job-to-a-job-category.md)|  
|Beschreibt, wie die Mitgliedschaft in einer Auftragskategorie geändert wird.|[Change the Membership of a Job Category](../../ssms/agent/change-the-membership-of-a-job-category.md)|  
|Beschreibt, wie die Kategorieinformationen aufgelistet werden.|[Auflisten von Informationen zu Auftragskategorien](../../ssms/agent/list-job-category-information.md)|  
  
