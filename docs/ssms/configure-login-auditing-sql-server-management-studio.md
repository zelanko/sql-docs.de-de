---
description: Konfigurieren der Anmeldungsüberwachung (SQL Server Management Studio)
title: Konfigurieren der Anmeldungsüberwachung (SQL Server Management Studio)
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- auditing [SQL Server]
- audits [SQL Server], logins
- logins [SQL Server], auditing
ms.assetid: 16961116-57ac-4eef-8037-791b26ade548
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 26a61a26350cb566a4526893c877eb5825afc6f1
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88417946"
---
# <a name="configure-login-auditing-sql-server-management-studio"></a>Konfigurieren der Anmeldungsüberwachung (SQL Server Management Studio)
[!INCLUDE[sqlserver](../includes/applies-to-version/sqlserver.md)]
In diesem Thema wird beschrieben, wie die Anmeldeüberwachung in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] konfiguriert wird, um die [!INCLUDE[ssDEnoversion](../includes/ssdenoversion_md.md)]-Anmeldeaktivität zu überwachen. Die Anmeldungsüberwachung kann so konfiguriert werden, dass die folgenden Ereignisse im Fehlerprotokoll aufgezeichnet werden.  
  
-   Fehlgeschlagene Anmeldungen  
  
-   Erfolgreiche Anmeldungen  
  
-   Erfolgreiche und fehlgeschlagene Anmeldungen  
  
Sie müssen [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] neu starten, damit die Option wirksam wird.  
  
## <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a>Verwenden von SQL Server Management Studio  
  
#### <a name="to-configure-login-auditing"></a>So konfigurieren Sie die Anmeldungsüberwachung  
  
1.  Stellen Sie in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]mithilfe des Objekt-Explorers eine Verbindung mit einer Instanz von [!INCLUDE[ssDEnoversion](../includes/ssdenoversion_md.md)] her.  
  
2.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf den Servernamen, und klicken Sie auf **Eigenschaften**.  
  
3.  Wählen Sie auf der Seite **Sicherheit** unter **Anmeldungsüberwachung** die gewünschte Option aus, und schließen Sie die Seite **Servereigenschaften** .  
  
4.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf den Servernamen, und klicken Sie dann auf **Neu starten**.  
  
