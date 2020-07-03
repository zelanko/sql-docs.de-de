---
title: Verwenden von WQL zum Zugreifen auf den WMI-Anbieter
description: Verwenden Sie dieses Beispiel, um zu erfahren, wie Sie Windows-Verwaltungsinstrumentation Abfrage Sprachanweisungen für den WMI-Anbieter für die Computer Verwaltung in SQL Server ausführen.
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- query language [WMI]
- WMI Query Language [WMI]
- WQL [WMI]
- WMI Provider for Configuration Management, WQL
ms.assetid: 26499530-d93b-452b-bbe4-217ef1d11e68
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 7efe4f3f8456dc68171b804d7afd28f565a4fbe2
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85888244"
---
# <a name="access-wmi-provider-for-configuration-management-using-wql"></a>Zugreifen auf WMI-Anbieter für die Konfigurationsverwaltung mit WQL
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  In diesem Abschnitt wird beschrieben, wie [!INCLUDE[msCoName](../../includes/msconame-md.md)] WQL-Anweisungen (Windows Management Instrumentation Query Language, Abfragesprache der Windows-Verwaltungsinstrumentation) für den WMI-Anbieter für die Computerverwaltung ausgeführt werden.  
  
 Im Beispiel wird ein WQL-Editor, WBEMtest.exe, zum Ausführen von WQL-Abfragen für den WMI-Anbieter verwendet, um [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Dienste, -Netzwerkprotokolle und -Aliasnamen aufzuzählen.  
  
### <a name="querying-services-using-wbemtest"></a>Abfragen von Diensten mit WBEMtest  
  
1.  Klicken Sie im **Startmenü** auf **Ausführen**, und geben Sie dann **Wbemtest**ein.  
  
2.  Das Dialogfeld WBEMtest.exe wird angezeigt. Klicken Sie auf **Verbinden**.  
  
3.  Geben Sie im ersten Textfeld den Namespace für den WMI-Anbieter für die Computerverwaltung ein: root\Microsoft\SqlServer\ComputerManagement11. Klicken Sie auf **Verbinden**.  
  
4.  Klicken Sie auf **Abfragen**. Geben Sie eine Abfrage ein, die die aktuellen Dienste zurückgibt, die auf dem lokalen Computer ausgeführt werden: **Select \* from SqlService.** Klicken Sie auf **Übernehmen**.  
  
5.  Verfeinern Sie die Abfrage weiter, indem Sie **Where Service Name = "MSSQLSERVER"** hinzufügen.  
  
  
