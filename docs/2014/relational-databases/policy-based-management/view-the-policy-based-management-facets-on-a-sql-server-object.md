---
title: Anzeigen der Facets der richtlinienbasierten Verwaltung für ein SQL Server-Objekt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Policy-Based Management, view facets
ms.assetid: 5f423b9f-a6c4-41a7-9d8d-8f4926ce1fb4
caps.latest.revision: 7
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e95abe9e853c0e90bed9d58765fae1640f9885f8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36048051"
---
# <a name="view-the-policy-based-management-facets-on-a-sql-server-object"></a>Anzeigen der Facets der richtlinienbasierten Verwaltung für ein SQL Server-Objekt
  In diesem Thema wird beschrieben, wie Sie alle Facets der richtlinienbasierten Verwaltung, die auf ein bestimmtes SQL Server-Objekt in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] angewendet wurden, mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]anzeigen.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Security](#Security)  
  
-   **Anzeigen aller Facets in einem Objekt mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungsmaßnahmen  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Erfordert die Mitgliedschaft in der PolicyAdministratorRole-Rolle in der msdb-Datenbank.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-view-all-of-the-facets-in-an-object"></a>So zeigen Sie alle Facets in einem Objekt an  
  
1.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ein Instanzobjekt, eine Datenbank oder ein Datenbankobjekt, und klicken Sie dann auf **Facets**.  
  
2.  Wählen Sie im Dialogfeld **Facets anzeigen** > *Objektname* in der Liste **Facet** ein Facet aus, dessen Eigenschaften Sie anzeigen möchten. Weitere Informationen zu den Optionen in diesem Dialogfeld finden Sie unter [View Facets Dialog Box](view-facets-dialog-box.md).  
  
3.  Wenn Sie fertig sind, klicken Sie auf **OK**.  
  
  