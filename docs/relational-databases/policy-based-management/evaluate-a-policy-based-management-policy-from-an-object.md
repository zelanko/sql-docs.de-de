---
title: Auswerten einer Richtlinie der richtlinienbasierten Verwaltung von einem Objekt aus | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: performance-monitor
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, evaluate policy
ms.assetid: b9e9d646-4894-4dee-a02a-0c71a8dc020e
caps.latest.revision: 8
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 686b6ebac2c21c3e12f594340a8542efae97baee
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="evaluate-a-policy-based-management-policy-from-an-object"></a>Auswerten einer Richtlinie der richtlinienbasierten Verwaltung von einem Objekt aus
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  In diesem Thema wird beschrieben, wie eine Richtlinie aus einer Serverinstanz, Datenbank oder einem Datenbankobjekt in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]ausgewertet wird.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Security](#Security)  
  
-   **Auswerten einer Richtlinie aus einem Objekt mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungsmaßnahmen  
  
###  <a name="Restrictions"></a> Einschränkungen  
  
-   Der Ausführungsmodus wird als Teil der Richtlinie definiert und kann im Dialogfeld **Richtlinien auswerten** nicht geändert werden.  
  
-   Das Dialogfeld **Richtlinien auswerten** zeigt nur Richtlinien an, die für das Datenbankobjekt geeignet sind.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Erfordert die Mitgliedschaft in der PolicyAdministratorRole-Rolle in der msdb-Datenbank.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-evaluate-a-policy-from-an-object"></a>So werten Sie eine Richtlinie für ein Objekt aus  
  
1.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf eine Serverinstanz, eine Datenbank oder ein Datenbankobjekt, zeigen Sie auf **Richtlinien**, und wählen Sie dann **Auswerten**aus.  
  
2.  Wählen Sie im Dialogfeld **Richtlinien auswerten** eine oder mehrere Richtlinien aus, und klicken Sie auf **Auswerten** , um die Richtlinie im Auswertungsmodus auszuführen. Dadurch wird ein Kompatibilitätsbericht für den Zielsatz generiert. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird jedoch nicht neu konfiguriert, und es wird auch keine zukünftige Kompatibilität durchgesetzt. Für Ziele, die mit den ausgewählten Richtlinien nicht übereinstimmen und Eigenschaften besitzen, die von der richtlinienbasierten Verwaltung neu konfiguriert werden können, erzwingen Sie die Richtlinieneinhaltung, indem Sie auf **Anwenden**klicken. Weitere Informationen zu den Optionen im Dialogfeld **Richtlinien auswerten** finden Sie unter [Evaluate Policies Dialog Box, Policy Selection Page](../../relational-databases/policy-based-management/evaluate-policies-dialog-box-policy-selection-page.md), [Evaluate Policies Dialog Box, Evaluation Results Page](../../relational-databases/policy-based-management/evaluate-policies-dialog-box-evaluation-results-page.md)und [Results Detailed View Dialog Box](../../relational-databases/policy-based-management/results-detailed-view-dialog-box.md).  
  
3.  Wenn Sie fertig sind, klicken Sie auf **Schließen**.  
  
  
