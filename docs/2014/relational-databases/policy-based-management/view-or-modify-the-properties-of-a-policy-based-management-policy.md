---
title: Anzeigen oder Ändern der Eigenschaften einer Richtlinie der richtlinienbasierten Verwaltung | Microsoft-Dokumentation
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
- Policy-Based Management, modify policies
- Policy-Based Management, view policies
ms.assetid: ba805504-5db5-4731-a8da-a0e89cb20c37
caps.latest.revision: 8
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b64630b7a586eb8b32f225110da026656cdc4325
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36149359"
---
# <a name="view-or-modify-the-properties-of-a-policy-based-management-policy"></a>Anzeigen oder Ändern der Eigenschaften einer Richtlinie der richtlinienbasierten Verwaltung
  In diesem Thema wird beschrieben, wie Sie die Eigenschaften einer Richtlinie der richtlinienbasierten Verwaltung mithilfe von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] oder [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] in [!INCLUDE[tsql](../../includes/tsql-md.md)]ändern.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Security](#Security)  
  
-   **Anzeigen oder Ändern der Eigenschaften einer Richtlinie mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungsmaßnahmen  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Erfordert die Mitgliedschaft in der PolicyAdministratorRole-Rolle in der msdb-Datenbank.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-view-the-properties-of-all-policies-on-an-object"></a>So zeigen Sie die Eigenschaften aller Richtlinien für ein Objekt an  
  
1.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf einen Server, ein Serverobjekt, eine Datenbank oder ein Datenbankobjekt, zeigen Sie auf **Richtlinien** , und wählen Sie dann **Anzeigen**aus. Weitere Informationen zu den verfügbaren Optionen im Dialogfeld **Richtlinien anzeigen** > *Objektname* finden Sie unter [Dialogfeld 'Richtlinien anzeigen'](view-policies-dialog-box.md).  
  
2.  Wenn Sie fertig sind, klicken Sie auf **Schließen**.  
  
#### <a name="to-view-or-modify-a-specific-policys-properties"></a>So zeigen Sie die Eigenschaften einer bestimmten Richtlinie an bzw. ändern sie  
  
1.  Klicken Sie im **Objekt-Explorer**auf das Pluszeichen, um den Server zu erweitern, der die Richtlinie der richtlinienbasierten Verwaltung enthält, die Sie anzeigen oder ändern möchten.  
  
2.  Klicken Sie auf das Pluszeichen, um den Ordner **Verwaltung** zu erweitern.  
  
3.  Klicken Sie auf das Pluszeichen, um **Richtlinienverwaltung**zu erweitern.  
  
4.  Klicken Sie auf das Pluszeichen, um den Ordner **Richtlinien** zu erweitern.  
  
5.  Klicken Sie mit der rechten Maustaste auf die Richtlinie, die Sie anzeigen oder ändern möchten, und wählen Sie **Eigenschaften**aus. Weitere Informationen zu den verfügbaren Optionen im Dialogfeld **Richtlinie öffnen** > *Richtlinienname* finden Sie unter [Dialogfeld 'Neue Richtlinie erstellen' oder 'Richtlinie öffnen', Seite 'Allgemein'](../../integration-services/general-page-of-integration-services-designers-options.md) und [Dialogfeld 'Neue Richtlinie erstellen' oder 'Richtlinie öffnen', Seite 'Beschreibung'](create-new-policy-or-open-policy-dialog-box-description-page.md).  
  
6.  Wenn Sie fertig sind, klicken Sie auf **OK**.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-view-a-policys-properties"></a>So zeigen Sie die Eigenschaften einer Richtlinie an  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    USE msdb;  
    GO  
    SELECT name,  
       execution_mode,  
       description,  
       is_enabled,  
       job_id  
    FROM syspolicy_policies;  
    GO  
    ```  
  
 Weitere Informationen finden Sie unter [syspolicy_policies &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/syspolicy-policies-transact-sql).  
  
  
