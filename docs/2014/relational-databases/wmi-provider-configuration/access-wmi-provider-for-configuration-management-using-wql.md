---
title: Zugreifen auf WMI-Anbieter für die Konfigurationsverwaltung mit WQL | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- query language [WMI]
- WMI Query Language [WMI]
- WQL [WMI]
- WMI Provider for Configuration Management, WQL
ms.assetid: 26499530-d93b-452b-bbe4-217ef1d11e68
caps.latest.revision: 16
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c3c9ced24edc7e7f3537a73d074cf7cd73128dc8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36050515"
---
# <a name="access-wmi-provider-for-configuration-management-using-wql"></a>Zugreifen auf WMI-Anbieter für die Konfigurationsverwaltung mit WQL
  In diesem Abschnitt wird beschrieben, wie [!INCLUDE[msCoName](../../includes/msconame-md.md)] WQL-Anweisungen (Windows Management Instrumentation Query Language, Abfragesprache der Windows-Verwaltungsinstrumentation) für den WMI-Anbieter für die Computerverwaltung ausgeführt werden.  
  
 Im Beispiel wird ein WQL-Editor, WBEMtest.exe, zum Ausführen von WQL-Abfragen für den WMI-Anbieter verwendet, um [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Dienste, -Netzwerkprotokolle und -Aliasnamen aufzuzählen.  
  
### <a name="querying-services-using-wbemtest"></a>Abfragen von Diensten mit WBEMtest  
  
1.  Aus der **starten** Menü klicken Sie auf **ausführen**, und geben Sie dann `WBEMtest`.  
  
2.  Das Dialogfeld WBEMtest.exe wird angezeigt. Klicken Sie auf **Verbinden**.  
  
3.  Geben Sie im ersten Textfeld den Namespace für den WMI-Anbieter für die Computerverwaltung ein: root\Microsoft\SqlServer\ComputerManagement11. Klicken Sie auf **Verbinden**.  
  
4.  Klicken Sie auf **Abfrage**. Geben Sie eine Abfrage, die die aktuellen Dienste zur Ausführung auf dem lokalen Computer zurückgibt: **wählen \* aus SqlService.** Klicken Sie auf **Anwenden**.  
  
5.  Verfeinern Sie die Abfrage weiter, indem Sie `WHERE ServiceName = "MSSQLSERVER"` hinzufügen.  
  
  