---
title: Anzeigen der Eigenschaften eines Facets der richtlinienbasierten Verwaltung
description: In diesem Artikel erfahren Sie, wie Sie die Eigenschaften eines Facets der richtlinienbasierten Verwaltung in SQL Server anzeigen. Dazu verwenden Sie SQL Server Management Studio (SSMS).
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, view facet properties
ms.assetid: 022a244c-c2e7-4467-b9a2-c7a27859be22
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 3a5a938928817b8ffb5282b2af7d2a505b442302
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "75558093"
---
# <a name="view-the-properties-of-a-policy-based-management-facet"></a>Anzeigen der Eigenschaften eines Facets der richtlinienbasierten Verwaltung
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  In diesem Thema wird beschrieben, wie Sie die Eigenschaften eines Facets der richtlinienbasierten Verwaltung i mithilfe von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]anzeigen.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Sicherheit](#Security)  
  
-   **Anzeigen der Eigenschaften eines Facets mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Erfordert die Mitgliedschaft in der PolicyAdministratorRole-Rolle in der msdb-Datenbank.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-view-the-properties-of-a-facet"></a>So zeigen Sie die Eigenschaften eines Facets an  
  
1.  Klicken Sie im **Objekt-Explorer**auf das Pluszeichen, um den Server zu erweitern, in dem das Facet mit den anzuzeigenden Eigenschaften enthalten ist.  
  
2.  Klicken Sie auf das Pluszeichen, um den Ordner **Verwaltung** zu erweitern.  
  
3.  Klicken Sie auf das Pluszeichen, um **Richtlinienverwaltung**zu erweitern.  
  
4.  Klicken Sie auf das Pluszeichen, um den Ordner **Facets** zu erweitern.  
  
5.  Klicken Sie mit der rechten Maustaste auf das Facet, dessen Eigenschaften Sie anzeigen möchten, und wählen Sie **Eigenschaften**aus. Weitere Informationen über die verfügbaren Optionen im Dialogfeld **Facet-Eigenschaften –** _Facet-Name_ finden Sie unter Dialogfeld [„Facet-Eigenschaften“, Seite „Allgemein“](../../relational-databases/policy-based-management/facet-properties-dialog-box-general-page.md), [Dialogfeld „Facet-Eigenschaften“, Seite „Abhängige Richtlinien“](../../relational-databases/policy-based-management/facet-properties-dialog-box-dependent-policies-page.md) und [Dialogfeld „Facet-Eigenschaften“, Seite „Abhängige Bedingungen“](../../relational-databases/policy-based-management/facet-properties-dialog-box-dependent-conditions-page.md).  
  
6.  Wenn Sie fertig sind, klicken Sie auf **Schließen**.  

