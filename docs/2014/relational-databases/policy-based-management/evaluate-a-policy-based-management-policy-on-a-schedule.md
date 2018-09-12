---
title: Auswerten einer Richtlinie der richtlinienbasierten Verwaltung nach einem Zeitplan | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, evaluate policy
ms.assetid: bea09522-ff47-4037-ab55-a98ea7c10099
caps.latest.revision: 6
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 760c52393015b6b4481048a04a5a04a3f2fe8f0e
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "43808736"
---
# <a name="evaluate-a-policy-based-management-policy-on-a-schedule"></a>Auswerten einer Richtlinie der richtlinienbasierten Verwaltung nach einem Zeitplan
  In diesem Thema wird beschrieben, wie Sie eine Richtlinie der richtlinienbasierten Verwaltung mithilfe von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] nach einem Zeitplan in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]auswerten.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Security](#Security)  
  
-   **Auswerten einer Richtlinie nach einem Zeitplan mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungsmaßnahmen  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Erfordert die Mitgliedschaft in der PolicyAdministratorRole-Rolle in der msdb-Datenbank.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-evaluate-a-policy-on-a-schedule"></a>So werten Sie eine Richtlinie nach einem Zeitplan aus  
  
1.  Klicken Sie im **Objekt-Explorer**auf das Pluszeichen, um den Server zu erweitern, in dem der auszuwertende Richtlinienzeitplan enthalten ist.  
  
2.  Klicken Sie auf das Pluszeichen, um den Ordner **Verwaltung** zu erweitern.  
  
3.  Klicken Sie auf das Pluszeichen, um **Richtlinienverwaltung**zu erweitern.  
  
4.  Klicken Sie auf das Pluszeichen, um den Ordner **Richtlinien** zu erweitern.  
  
5.  Klicken Sie mit der rechten Maustaste auf die Richtlinie, deren Zeitplan Sie auswerten möchten, und wählen Sie **Eigenschaften**aus.  
  
6.  Klicken Sie im Dialogfeld **Richtlinie öffnen** > *Richtlinienname* in der Liste **Auswertungsmodus** auf die Option **Nach Zeitplan**.  
  
7.  Klicken Sie unter **Zeitplan**auf **Auswählen** , um einen vorhandenen Zeitplan anzugeben, oder klicken Sie auf **Neu** , um einen neuen Zeitplan zu erstellen.  
  
8.  Wenn Sie fertig sind, klicken Sie auf **OK**.  
  
  
