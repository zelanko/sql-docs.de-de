---
title: Anzeigen der Ergebnisse zu Ressourcenintegritätsrichtlinien (SQL Server-Hilfsprogramm) | Microsoft-Dokumentation
description: Hier erfahren Sie, wie Sie SQL Server Management Studio zum Anzeigen der Ergebnisse zu Ressourcenintegritätsrichtlinien des SQL Server-Hilfsprogramms für Instanzen von SQL Server und Datenschichtanwendungen verwenden.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 80cb14fb-f4c6-4be2-ba17-eb4e4cddd35f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a3ec26ba8988f36e3deac88373a932ef377f8d59
ms.sourcegitcommit: 04cf7905fa32e0a9a44575a6f9641d9a2e5ac0f8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/07/2020
ms.locfileid: "91810028"
---
# <a name="view-resource-health-policy-results-sql-server-utility"></a>Anzeigen der Ergebnisse zu Ressourcenintegritätsrichtlinien (SQL Server-Hilfsprogramm)

[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

Verwenden Sie das Dashboard des Hilfsprogramms in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , um Ressourcenparameter des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Hilfsprogramms für verwaltete Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und Datenschichtanwendungen anzuzeigen. Weitere Informationen finden Sie unter [Funktionen und Tasks im SQL Server-Hilfsprogramm](../../relational-databases/manage/sql-server-utility-features-and-tasks.md).  

##  <a name="SSMSProcedure"></a>

### <a name="view-sql-server-utility-resource-health-policy-results"></a>Anzeigen der Ergebnisse zu Ressourcenintegritätsrichtlinien des SQL Server-Hilfsprogramms  

1. Klicken Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] (SSMS) auf **Ansicht** und dann auf **Hilfsprogramm-Explorer**, um den Navigationsbereich des Hilfsprogramm-Explorers anzuzeigen. Um den Inhaltsbereich anzuzeigen, klicken Sie auf **Ansicht** und dann auf **Inhalt des Hilfsprogramm-Explorers**.  

2. Klicken Sie im Navigationsbereich auf ![Mit Hilfsprogramm verbinden](../../relational-databases/manage/media/connect-to-utility.gif "Connect_to_Utility")**Mit Hilfsprogramm verbinden**. Wenn Sie keinen Steuerungspunkt für das Hilfsprogramm erstellt bzw. keine Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Datenschichtanwendungen im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Hilfsprogramm registriert haben, erhalten Sie weitere Informationen unter [SQL Server-Hilfsprogramm – Features und Aufgaben](../../relational-databases/manage/sql-server-utility-features-and-tasks.md).  

3. Wählen Sie den UCP-Knoten aus, um Zusammenfassungsdaten für verwaltete Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und Datenschichtanwendungen anzuzeigen. (Klicken Sie zum Aktualisieren der Ansicht mit der rechten Maustaste.) Dashboarddaten werden im Inhaltsbereich angezeigt.  

4. Wählen Sie den Knoten **Verwaltete Instanzen** aus, um Listenansichtsdaten für verwaltete Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] anzuzeigen. (Klicken Sie zum Aktualisieren der Ansicht mit der rechten Maustaste.) Listenansichtsdaten werden im Inhaltsbereich angezeigt.  

5. Wählen Sie den Knoten **Bereitgestellte Datenschichtanwendungen** aus, um Listenansichtsdaten für Datenschichtanwendungen anzuzeigen. (Klicken Sie zum Aktualisieren der Ansicht mit der rechten Maustaste.) Listenansichtsdaten werden im Inhaltsbereich angezeigt.  

## <a name="see-also"></a>Weitere Informationen

- [Funktionen und Tasks im SQL Server-Hilfsprogramm](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)
- [Reduzieren von Informationsrauschen bei Richtlinien zur CPU-Auslastung &#40;SQL Server-Hilfsprogramm&#41;](../../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md)
- [Details zu bereitgestellten Datenschichtanwendungen &#40;SQL Server-Hilfsprogramm&#41;](/previous-versions/sql/sql-server-2016/ee240857(v=sql.130))
- [Details zu verwalteten Instanzen &#40;SQL Server-Hilfsprogramm&#41;](./utility-explorer-f1-help.md)
- [Hilfsprogrammverwaltung &#40;SQL Server-Hilfsprogramm&#41;](/previous-versions/sql/sql-server-2016/ee240832(v=sql.130))