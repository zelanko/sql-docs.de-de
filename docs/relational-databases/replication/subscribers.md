---
title: Abonnenten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.newsubwizard.subscribers.f1
helpviewer_keywords:
- Subscribers [SQL Server replication]
ms.assetid: 43fb2454-c220-4d25-a826-83c332eb00d2
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-current||>=sql-server-2014||=sqlallproducts-allversions
ms.openlocfilehash: 6988274ce4c8f8bf38d89c156150b37589529dae
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "68769472"
---
# <a name="subscribers"></a>Abonnenten
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md.md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Geben Sie die [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Abonnenten oder die Nichtabonnenten von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] an, die ein Abonnent für die ausgewählte Veröffentlichung erhalten.


[!INCLUDE[azure-sql-db-replication-supportability-note](../../includes/azure-sql-db-replication-supportability-note.md)]
  
## <a name="options"></a>Tastatur  
 **Abonnenten**  
 Aktivieren Sie das Kontrollkästchen im Raster, um die zugehörige [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenquelle oder nicht von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stammende Datenquelle als Abonnent für die auf der Seite **Veröffentlichung** ausgewählte Veröffentlichung zu aktivieren. Wenn der Abonnent nicht aufgeführt ist, klicken Sie auf **Abonnent hinzufügen** oder **SQL Server-Abonnenten hinzufügen**.  
  
 **Abonnementdatenbank**  
 Die in dieser Spalte angezeigten Informationen sowie die über die Spalte verfügbaren Aktionen sind vom Typ des in der **Abonnenten** -Spalte aufgeführten Abonnenten abhängig:  
  
-   Wählen Sie für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Abonnenten eine Abonnementdatenbank aus der Liste **Abonnementdatenbank** aus, oder erstellen Sie eine neue Datenbank, indem Sie in derselben Liste den Befehl **Neue Datenbank** auswählen.  
  
    > [!NOTE]  
    >  Wenn Sie den Verleger als einen Abonnenten aktivieren, darf die Abonnementdatenbank nicht mit der Veröffentlichungsdatenbank identisch sein.  
  
-   Bei Nicht-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Abonnenten wird die Abonnementdatenbank nicht angezeigt. Geben Sie im Feld **Datenquellenname** des Dialogfelds **Nicht-SQL Server-Abonnenten hinzufügen** die Datenbank und weitere Verbindungsinformationen an. Sie rufen dieses Dialogfeld auf, in dem Sie zuerst auf **Abonnent hinzufügen** und anschließend auf **Nicht-SQL Server-Abonnenten hinzufügen**klicken.  
  
 **Abonnent hinzufügen**  
 Fügen Sie einen Server zur Liste der Server hinzu, die als Abonnenten aktiviert werden können. Diese Schaltfläche wird angezeigt, wenn alle der folgenden Bedingungen erfüllt sind:  
  
-   Die von Ihnen ausgewählte Veröffentlichung ist eine Momentaufnahme- oder Transaktionsveröffentlichung, die keine Updateabonnements unterstützt.  
  
    > [!NOTE]  
    >  Wenn die Veröffentlichung, die Sie abonnieren, über [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Abonnements verfügt und die Veröffentlichung für Nicht-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Abonnenten noch nicht aktiviert ist, können Sie kein Nicht-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Abonnement hinzufügen.  
  
-   Das Abonnement ist ein Pushabonnement.  
  
-   Als Verleger für die ausgewählte Veröffentlichung wird [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] oder höher verwendet.  
  
 Wenn Sie auf **Abonnent hinzufügen** klicken, wird ein Menü mit zwei Auswahlmöglichkeiten angezeigt: **SQL Server-Abonnenten hinzufügen** und **Nicht-SQL Server-Abonnenten hinzufügen**. Klicken Sie auf **Nicht-SQL Server-Abonnenten hinzufügen** , um einen Oracle- oder IBM DB2-Abonnenten hinzuzufügen.  
  
 **SQL Server-Abonnenten hinzufügen**  
 Fügen Sie einen Server zur Liste der Server hinzu, die als Abonnenten aktiviert werden können. Diese Schaltfläche wird angezeigt, wenn eine oder mehrere der folgenden Bedingungen zutreffen:  
  
-   Die von Ihnen ausgewählte Veröffentlichung ist eine Mergeveröffentlichung oder eine Momentaufnahme- oder Transaktionsveröffentlichung, die Updateabonnements unterstützt.  
  
-   Das Abonnement ist ein Pullabonnement.  
  
-   Als Verleger für die ausgewählte Veröffentlichung wird eine Version vor [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]verwendet. Bei früheren Versionen wird die Schaltfläche nur angezeigt, wenn eine oder mehrere der folgenden Bedingungen zutreffen:  
  
    -   Sie sind Mitglied der festen Serverrolle **sysadmin** auf dem Verleger.  
  
    -   Der Abonnent wurde über die Seite **Abonnenten** des Dialogfelds **Verlegereigenschaften** hinzugefügt.  
  
    -   Die Veröffentlichung lässt anonyme Abonnements zu.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [Non-SQL Server Subscribers](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md)   
 [Abonnieren von Veröffentlichungen](../../relational-databases/replication/subscribe-to-publications.md)  
  
  
