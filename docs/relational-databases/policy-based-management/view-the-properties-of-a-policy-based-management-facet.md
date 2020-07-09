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
ms.openlocfilehash: d2aa58294e23f32ebfc1a43d300ab54cd6622aa4
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85774071"
---
# <a name="view-the-properties-of-a-policy-based-management-facet"></a>Anzeigen der Eigenschaften eines Facets der richtlinienbasierten Verwaltung
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  In diesem Thema wird beschrieben, wie Sie die Eigenschaften eines Facets der richtlinienbasierten Verwaltung i mithilfe von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]anzeigen.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Sicherheit](#Security)  
  
-   **Anzeigen der Eigenschaften eines Facets mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Erfordert die Mitgliedschaft in der PolicyAdministratorRole-Rolle in der msdb-Datenbank.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-view-the-properties-of-a-facet"></a>So zeigen Sie die Eigenschaften eines Facets an  
  
1.  Klicken Sie im **Objekt-Explorer**auf das Pluszeichen, um den Server zu erweitern, in dem das Facet mit den anzuzeigenden Eigenschaften enthalten ist.  
  
2.  Klicken Sie auf das Pluszeichen, um den Ordner **Verwaltung** zu erweitern.  
  
3.  Klicken Sie auf das Pluszeichen, um **Richtlinienverwaltung**zu erweitern.  
  
4.  Klicken Sie auf das Pluszeichen, um den Ordner **Facets** zu erweitern.  
  
5.  Klicken Sie mit der rechten Maustaste auf das Facet, dessen Eigenschaften Sie anzeigen möchten, und wählen Sie **Eigenschaften**aus. Weitere Informationen über die verfügbaren Optionen im Dialogfeld **Facet-Eigenschaften –** _Facet-Name_ finden Sie unter Dialogfeld [„Facet-Eigenschaften“, Seite „Allgemein“](../../relational-databases/policy-based-management/facet-properties-dialog-box-general-page.md), [Dialogfeld „Facet-Eigenschaften“, Seite „Abhängige Richtlinien“](../../relational-databases/policy-based-management/facet-properties-dialog-box-dependent-policies-page.md) und [Dialogfeld „Facet-Eigenschaften“, Seite „Abhängige Bedingungen“](../../relational-databases/policy-based-management/facet-properties-dialog-box-dependent-conditions-page.md).  
  
6.  Wenn Sie fertig sind, klicken Sie auf **Schließen**.  

