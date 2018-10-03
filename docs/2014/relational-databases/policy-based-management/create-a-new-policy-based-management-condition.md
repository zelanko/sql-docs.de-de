---
title: Erstellen einer neuen Bedingung der richtlinienbasierten Verwaltung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, creating policy conditions
ms.assetid: 8a612f7e-6c70-49db-a4de-48431e097cc5
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: c0e2394f5d470cc523c16346cfb2f091043b948d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48155532"
---
# <a name="create-a-new-policy-based-management-condition"></a>Erstellen einer neuen Bedingung der richtlinienbasierten Verwaltung
  In diesem Thema wird beschrieben, wie Sie eine Bedingung der richtlinienbasierte Verwaltung in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]erstellen.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Security](#Security)  
  
-   **Erstellen einer Bedingung mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungsmaßnahmen  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Erfordert die Mitgliedschaft in der PolicyAdministratorRole-Rolle in der msdb-Datenbank.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-create-a-condition"></a>So erstellen Sie eine Bedingung  
  
1.  Klicken Sie im **Objekt-Explorer**auf das Pluszeichen, um den Server zu erweitern, auf dem Sie die Bedingung der richtlinenbasierten Verwaltung erstellen möchten.  
  
2.  Klicken Sie auf das Pluszeichen, um den Ordner **Verwaltung** zu erweitern.  
  
3.  Klicken Sie auf das Pluszeichen, um **Richtlinienverwaltung**zu erweitern.  
  
4.  Klicken Sie auf das Pluszeichen, um den Ordner **Facets** zu erweitern.  
  
5.  Klicken Sie mit der rechten Maustaste auf das Facet, in dem Sie eine neue Bedingung erstellen möchten, und wählen Sie **Neue Bedingung**aus.  
  
6.  Geben Sie im Dialogfeld **Neue Bedingung erstellen** im Feld **Name** den Namen der neuen Bedingung ein.  
  
7.  Bestätigen Sie das richtige Facet in der Liste **Facet** , oder wählen Sie ein anderes Facet aus.  
  
8.  Erstellen Sie unter **Ausdruck**Bedingungsausdrücke, indem Sie eine Faceteigenschaft im Feld **Feld** zusammen mit dem dazugehörigen Operator und Wert auswählen. Wenn Sie mehrere Ausdrücke hinzufügen, können die Ausdrücke mit **Und** oder **Oder**verbunden werden. Weitere Informationen zu den Optionen in diesem Dialogfeld finden Sie unter [Dialogfeld 'Neue Bedingung erstellen' oder 'Bedingung öffnen', Seite 'Allgemein'](../../integration-services/general-page-of-integration-services-designers-options.md), [Dialogfeld 'Neue Bedingung erstellen' oder 'Bedingung öffnen', Seite 'Beschreibung'](create-new-condition-or-open-condition-dialog-box-description-page.md) und [Dialogfeld 'Erweiterte Bearbeitung &#40;Bedingung&#41;'](advanced-edit-condition-dialog-box.md).  
  
9. Wenn Sie fertig sind, klicken Sie auf **OK**.  
  
  
