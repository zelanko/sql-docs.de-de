---
title: Verwenden von Wertbeziehungen in einer Verbunddomäne | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.dm.cdvaluerelations.f1
ms.assetid: 5ee468f0-8538-4620-90e8-63f466c9000e
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 6f6bc24d0224e31f008be0ffaf77266446c15527
ms.sourcegitcommit: 5748d710960a1e3b8bb003d561ff7ceb56202ddb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/09/2019
ms.locfileid: "65481104"
---
# <a name="use-value-relations-in-a-composite-domain"></a>Verwenden von Wertbeziehungen in einer Verbunddomäne
  In diesem Thema wird beschrieben, wie Wertkombinationen angezeigt werden, die während des Wissensermittlungsprozesses in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) für die Verbunddomäne gefunden wurden. Auf dieser Seite wird angezeigt, wie oft die Wertkombinationen vorkommen. Die Wertverwaltung wird nicht für Verbunddomänen unterstützt. Deshalb können Sie für die Werte keine Vorgänge ausführen.  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Prerequisites"></a> Erforderliche Komponenten  
 Um Wertbeziehungen anzuzeigen, müssen Sie eine Verbunddomäne erstellt und geöffnet haben.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Sie müssen über die dqs_kb_editor- oder dqs_administrator-Rolle in der DQS_MAIN-Datenbank verfügen, um Wertbeziehungen in einer Verbunddomäne anzuzeigen.  
  
##  <a name="Use"></a> Anzeigen von Wertbeziehungen  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)] [Ausführen der Data Quality-Clientanwendung](../../2014/data-quality-services/run-the-data-quality-client-application.md).  
  
2.  Öffnen oder erstellen Sie im [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] -Startbildschirm eine Wissensdatenbank. Wählen Sie **Domänenverwaltung** als Aktivität aus, und klicken Sie dann auf **Öffnen** oder **Erstellen**. Weitere Informationen finden Sie unter [Erstellen einer Wissensdatenbank](../../2014/data-quality-services/create-a-knowledge-base.md) oder [Öffnen einer Wissensdatenbank](../../2014/data-quality-services/open-a-knowledge-base.md).  
  
3.  Wählen Sie aus der **Domänenliste** auf der Seite **Domänenverwaltung** die Verbunddomäne aus, für die Sie eine Domänenregel erstellen möchten, oder erstellen Sie eine neue Verbunddomäne. Wenn Sie eine neue Domäne erstellen müssen, finden Sie unter [Create a Composite Domain](../../2014/data-quality-services/create-a-composite-domain.md)weitere Informationen.  
  
4.  Klicken Sie auf die Registerkarte **Wertbeziehungen** .  
  
5.  Zeigen Sie die Häufigkeit für jede Wertkombination an.  
  
    > [!NOTE]  
    >  In der Tabelle **Wert** wird jede Kombination von Werten angezeigt, die in der Verbunddomäne vorhanden ist. Jeder Wert wird in der einzelnen Domäne angezeigt, für die er gilt. Die Tabelle mit den Wertbeziehungen wird standardmäßig nach der Häufigkeit sortiert, aber Sie können auch auf eine andere Spalte klicken, um nach dieser Spalte zu sortieren. Nur Werte mit einer Frequenz größer gleich 20 werden angezeigt.  
  
6.  Sie können keine Werte in der Tabelle ändern. Wenn Sie andere Vorgänge ausgeführt haben, klicken Sie auf **Fertig stellen** , um die Domänenverwaltungsaktivität abzuschließen. Klicken Sie andernfalls auf **Abbrechen**.  
  
##  <a name="FollowUp"></a>Nächster Schritt: Nach dem Anzeigen von Wertbeziehungen  
 Nachdem Sie die Wertbeziehungen angezeigt haben, können Sie andere Domänenverwaltungsaufgaben in der Domäne ausführen. Sie können die Wissensermittlung durchführen, um der Domäne Wissen hinzuzufügen, oder Sie können der Domäne eine Abgleichsrichtlinie hinzufügen. Weitere Informationen finden Sie unter [Durchführen der Wissensermittlung](../../2014/data-quality-services/perform-knowledge-discovery.md), [Verwalten einer Domäne](../../2014/data-quality-services/managing-a-domain.md) oder [Erstellen einer Abgleichsrichtlinie](../../2014/data-quality-services/create-a-matching-policy.md).  
  
  
