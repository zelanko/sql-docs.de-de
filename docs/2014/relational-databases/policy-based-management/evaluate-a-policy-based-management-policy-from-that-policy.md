---
title: Auswerten einer Richtlinie der richtlinienbasierten Verwaltung von der Richtlinie aus | Microsoft-Dokumentation
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
ms.assetid: 0b3214bd-d0ab-45ab-9281-3d95507abe54
caps.latest.revision: 6
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 22a638a5fd9d4d430bf9ebf83168cd1902322a22
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "43815316"
---
# <a name="evaluate-a-policy-based-management-policy-from-that-policy"></a>Auswerten einer Richtlinie der richtlinienbasierten Verwaltung von der Richtlinie aus
  In diesem Thema wird beschrieben, wie Sie eine Richtlinie auswerten, indem diese Richtlinie in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]verwendet wird.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Security](#Security)  
  
-   **Auswerten einer Richtlinie mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungsmaßnahmen  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Erfordert die Mitgliedschaft in der PolicyAdministratorRole-Rolle in der msdb-Datenbank.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-evaluate-a-policy"></a>So werten Sie eine Richtlinie aus  
  
1.  Klicken Sie im **Objekt-Explorer**auf das Pluszeichen, um den Server zu erweitern, in dem die auszuwertende Richtlinie enthalten ist  
  
2.  Klicken Sie auf das Pluszeichen, um den Ordner **Verwaltung** zu erweitern.  
  
3.  Klicken Sie auf das Pluszeichen, um **Richtlinienverwaltung**zu erweitern.  
  
4.  Klicken Sie auf das Pluszeichen, um den Ordner **Richtlinien** zu erweitern.  
  
5.  Klicken Sie mit der rechten Maustaste auf die Richtlinie, die Sie auswerten möchten, und wählen Sie **Auswerten**aus.  
  
6.  Im Dialogfeld **Ergebnisse auswerten**  werden die Ergebnisse der Richtlinienauswertung angezeigt. Für Ziele, die mit der Richtlinie nicht übereinstimmen und die Eigenschaften besitzen, die von der richtlinienbasierten Verwaltung neu konfiguriert werden können, erzwingen Sie die Einhaltung, indem Sie auf **Anwenden**klicken. Weitere Informationen zu den Optionen im Dialogfeld **Richtlinien auswerten** finden Sie unter [Evaluate Policies Dialog Box, Policy Selection Page](evaluate-policies-dialog-box-policy-selection-page.md) und [Evaluate Policies Dialog Box, Evaluation Results Page](evaluate-policies-dialog-box-evaluation-results-page.md).  
  
7.  Wenn Sie fertig sind, klicken Sie auf **Schließen**.  
  
  
