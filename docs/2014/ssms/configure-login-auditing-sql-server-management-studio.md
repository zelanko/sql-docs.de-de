---
title: Konfigurieren der Anmeldungsüberwachung (SQL Server Management Studio) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- auditing [SQL Server]
- audits [SQL Server], logins
- logins [SQL Server], auditing
ms.assetid: 16961116-57ac-4eef-8037-791b26ade548
caps.latest.revision: 20
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6a1e2878be466f75a2dc6ee17935d4f4f73db016
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "43811756"
---
# <a name="configure-login-auditing-sql-server-management-studio"></a>Konfigurieren der Anmeldungsüberwachung (SQL Server Management Studio)
  In diesem Thema wird beschrieben, wie die Anmeldeüberwachung in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] konfiguriert wird, um die [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]-Anmeldeaktivität zu überwachen. Die Anmeldungsüberwachung kann so konfiguriert werden, dass die folgenden Ereignisse im Fehlerprotokoll aufgezeichnet werden.  
  
-   Fehlgeschlagene Anmeldungen  
  
-   Erfolgreiche Anmeldungen  
  
-   Erfolgreiche und fehlgeschlagene Anmeldungen  
  
 Sie müssen [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] neu starten, damit die Option wirksam wird.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-configure-login-auditing"></a>So konfigurieren Sie die Anmeldungsüberwachung  
  
1.  Stellen Sie in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]mithilfe des Objekt-Explorers eine Verbindung mit einer Instanz von [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] her.  
  
2.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf den Servernamen, und klicken Sie auf **Eigenschaften**.  
  
3.  Wählen Sie auf der Seite **Sicherheit** unter **Anmeldungsüberwachung** die gewünschte Option aus, und schließen Sie die Seite **Servereigenschaften** .  
  
4.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf den Servernamen, und klicken Sie dann auf **Neu starten**.  
  
  
