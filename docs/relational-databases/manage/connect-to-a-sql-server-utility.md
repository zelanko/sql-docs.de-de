---
title: Verbinden mit einem SQL Server-Hilfsprogramm
description: Hier erfahren Sie, wie Sie eine Verbindung mit einem SQL Server-Hilfsprogramm herstellen, damit Sie die Integrität von SQL Server-Ressourcen verwalten können. Sie können die Verbindung über SQL Server Management Studio (SSMS) herstellen.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: b9b90b8d-241f-4b74-ac14-de7b10ea1821
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: fb961ccd1a1ec3013e186c7b45a54004ff400e07
ms.sourcegitcommit: e08d28530e0ee93c78a4eaaee8800fd687babfcc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/14/2020
ms.locfileid: "86301789"
---
# <a name="connect-to-a-sql-server-utility"></a>Verbinden mit einem SQL Server-Hilfsprogramm

[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

Bevor Sie eine Verbindung mit einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Hilfsprogramm herstellen können, müssen Sie einen Steuerungspunkt für das Hilfsprogramm erstellen. Weitere Informationen finden Sie unter [Funktionen und Tasks im SQL Server-Hilfsprogramm](../../relational-databases/manage/sql-server-utility-features-and-tasks.md).  

Um die Ressourcenintegrität von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] anzuzeigen und zu verwalten, stellen Sie mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] (SSMS) eine Verbindung mit einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Hilfsprogramm her.  

So stellen Sie über SSMS eine Verbindung mit einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Hilfsprogramm her:  

1. Starten Sie SSMS.

2. Stellen Sie in SSMS eine Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]her.

3. Wählen Sie **Ansicht** und dann **Hilfsprogramm-Explorer** aus.

4. Klicken Sie im Navigationsbereich des Hilfsprogramm-Explorers auf :::image type="icon" source="media/connect-to-utility.gif" border="false"::: **Mit Hilfsprogramm verbinden**.

5. Geben Sie im Dialogfeld **Mit Server verbinden** den Namen der UCP-Instanz an, und klicken Sie dann auf **Verbinden**.

6. Zeigen Sie den Navigationsbereich des Hilfsprogramm-Explorers an, um eine Strukturansicht der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Ressourcen im UCP einzublenden.

Beim Erstellen eines neuen UCPs werden Sie ebenfalls mit dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Hilfsprogramm verbunden. Weitere Informationen finden Sie unter [Erstellen eines Steuerungspunkts für das SQL Server-Hilfsprogramm &#40;SQL Server-Hilfsprogramm&#41;](../../relational-databases/manage/create-a-sql-server-utility-control-point-sql-server-utility.md).

## <a name="see-also"></a>Weitere Informationen

- [Funktionen und Tasks im SQL Server-Hilfsprogramm](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)
- [Anzeigen der Ergebnisse zu Ressourcenintegritätsrichtlinien &#40;SQL Server-Hilfsprogramm&#41;](../../relational-databases/manage/view-resource-health-policy-results-sql-server-utility.md)