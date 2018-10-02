---
title: Konfigurieren der Anmeldungsüberwachung (SQL Server Management Studio) | Microsoft-Dokumentation
ms.custom: ''
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
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e178239dd02bf67d667cda964a6023c0b7b4e8c3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47853448"
---
# <a name="configure-login-auditing-sql-server-management-studio"></a>Konfigurieren der Anmeldungsüberwachung (SQL Server Management Studio)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
In diesem Thema wird beschrieben, wie die Anmeldeüberwachung in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] konfiguriert wird, um die [!INCLUDE[ssDEnoversion](../includes/ssdenoversion_md.md)]-Anmeldeaktivität zu überwachen. Die Anmeldungsüberwachung kann so konfiguriert werden, dass die folgenden Ereignisse im Fehlerprotokoll aufgezeichnet werden.  
  
-   Fehlgeschlagene Anmeldungen  
  
-   Erfolgreiche Anmeldungen  
  
-   Erfolgreiche und fehlgeschlagene Anmeldungen  
  
Sie müssen [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] neu starten, damit die Option wirksam wird.  
  
## <a name="SSMSProcedure"></a>Verwenden von SQL Server Management Studio  
  
#### <a name="to-configure-login-auditing"></a>So konfigurieren Sie die Anmeldungsüberwachung  
  
1.  Stellen Sie in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]mithilfe des Objekt-Explorers eine Verbindung mit einer Instanz von [!INCLUDE[ssDEnoversion](../includes/ssdenoversion_md.md)] her.  
  
2.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf den Servernamen, und klicken Sie auf **Eigenschaften**.  
  
3.  Wählen Sie auf der Seite **Sicherheit** unter **Anmeldungsüberwachung** die gewünschte Option aus, und schließen Sie die Seite **Servereigenschaften** .  
  
4.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf den Servernamen, und klicken Sie dann auf **Neu starten**.  
  
