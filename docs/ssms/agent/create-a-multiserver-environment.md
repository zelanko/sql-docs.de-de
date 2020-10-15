---
description: Erstellen einer Multiserverumgebung
title: Erstellen einer Multiserverumgebung
ms.custom: seo-lt-2019
ms.date: 01/30/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, multiserver environments
- master servers [SQL Server], about master servers
- target servers [SQL Server], about target servers
- multiserver environments [SQL Server]
ms.assetid: edc2b60d-15da-40a1-8ba3-f1d473366ee6
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 356fb010386f3675a3f62073dacc4cd28cf09e9c
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/14/2020
ms.locfileid: "92038283"
---
# <a name="create-a-multiserver-environment"></a>Erstellen einer Multiserverumgebung
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> In [Azure SQL Managed Instance](/azure/sql-database/sql-database-managed-instance) werden derzeit die meisten, aber nicht alle, SQL Server-Agent-Features unterstützt. Details dazu finden Sie unter [T-SQL-Unterschiede zwischen Azure SQL Managed Instance und SQL Server](/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Die Multiserververwaltung erfordert, dass Sie einen Masterserver (MSX) und einen oder mehrere Zielserver (TSX) einrichten. Aufträge, die auf allen Zielservern verarbeitet werden, müssen zuerst auf dem Masterserver definiert werden, und dann zu den Zielservern heruntergeladen werden.  
  
Standardmäßig sind die vollständige TLS-Verschlüsselung (Transport Layer Security), früher als SSL-Verschlüsselung (Secure Sockets Layer) bekannt, und die Zertifikatüberprüfung für Verbindungen zwischen Masterservern und Zielservern aktiviert. Weitere Informationen finden Sie unter [Festlegen von Verschlüsselungsoptionen auf Zielservern](../../ssms/agent/set-encryption-options-on-target-servers.md).  
  
Wenn Sie eine große Anzahl von Zielservern haben, vermeiden Sie, den Masterserver auf einem Produktionsserver zu definieren, der bedeutende Leistungsanforderungen bezüglich anderer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Funktionalität hat, da der Zielserverdatenverkehr die Leistung auf dem Produktionsserver verlangsamen kann. Wenn Sie auch Ereignisse an einen dedizierten Masterserver weiterleiten, können Sie die Administration auf einem Server zentralisieren. Weitere Informationen finden Sie unter [Verwalten von Ereignissen](../../ssms/agent/manage-events.md).  
  
> [!NOTE]  
> Um die Multiserver-Auftragsverarbeitung verwenden zu können, muss das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienstkonto Mitglied der **msdb** -Datenbankrolle **TargetServersRole** auf dem Masterserver sein. Der Masterserver-Assistent fügt dieser Rolle im Rahmen des Eintragungsprozesses automatisch das Dienstkonto hinzu.  
  
## <a name="considerations-for-multiserver-environments"></a>Überlegungen zu Multiserverumgebungen  
  
Beachten Sie die folgenden Punkte, wenn Sie eine Multiserverumgebung erstellen:  
  
-   Verwenden Sie die aktuellste Version als Masterserver. Die aktuelle und die beiden Vorgängerversionen werden unterstützt.

-   Jeder Zielserver berichtet nur einem Masterserver. Sie müssen einen Zielserver aus einem Masterserver austragen, bevor Sie ihn bei einem anderen Masterserver eintragen können.  
  
-   Wenn Sie den Namen eines Zielservers ändern, müssen Sie ihn vor der Namensänderung austragen und danach wieder eintragen.  
  
-   Wenn Sie eine Multiserverkonfiguration auflösen möchten, müssen Sie alle Zielserver aus dem Masterserver austragen.  
  
-   SQL Server Integration Services unterstützt nur Zielserver, die über dieselbe Version wie der Masterserver oder eine höhere Version verfügen.  
  
## <a name="related-tasks"></a>Related Tasks  
In den folgenden Themen werden allgemeine Aufgaben zum Erstellen einer Multiserverumgebung beschrieben.  
  
|BESCHREIBUNG|Thema|  
|---------------|---------|  
|Beschreibt, wie ein Masterserver erstellt wird.|[Einrichten eines Masterservers](../../ssms/agent/make-a-master-server.md)|  
|Beschreibt, wie ein Zielserver erstellt wird.|[Erstellen eines Zielservers](../../ssms/agent/make-a-target-server.md)|  
|Beschreibt, wie ein Zielserver bei einem Masterserver eingetragen wird.|[Eintragen eines Zielservers bei einem Masterserver](../../ssms/agent/enlist-a-target-server-to-a-master-server.md)|  
|Beschreibt, wie der Austritt eines Zielservers aus einem Masterserver vollzogen wird.|[Vollziehen des Austritts eines Zielservers aus einem Masterserver](../../ssms/agent/defect-a-target-server-from-a-master-server.md)|  
|Beschreibt, wie der Austritt mehrerer Zielserver aus einem Masterserver vollzogen wird.|[Vollziehen des Austritts mehrerer Zielserver aus einem Masterserver](../../ssms/agent/defect-multiple-target-servers-from-a-master-server.md)|  
|Beschreibt, wie der Status eines Zielservers überprüft wird.|[sp_help_targetserver (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-help-targetserver-transact-sql.md)<br /><br />[sp_help_targetservergroup (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-help-targetservergroup-transact-sql.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
[Problembehandlung von proxybasierten Multiserveraufträgen](../../ssms/agent/troubleshoot-multiserver-jobs-that-use-proxies.md)  
