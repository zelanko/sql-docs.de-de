---
title: Konfigurieren allgemeiner Eigenschaften der richtlinienbasierten Verwaltung | Microsoft Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.dmf.PolicyManagement.f1
helpviewer_keywords:
- Policy-Based Management, configure properties
ms.assetid: 6d1e0e37-29ea-408a-a055-384984d884be
caps.latest.revision: 8
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: e06b3431cee345d4cec6448fabe37ad6bbbd7476
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37162341"
---
# <a name="configure-the-general-properties-of-policy-based-management"></a>Konfigurieren allgemeiner Eigenschaften der richtlinienbasierten Verwaltung
  In diesem Thema wird beschrieben, wie die Eigenschaften für die richtlinienbasierte Verwaltung in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]konfiguriert werden.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Security](#Security)  
  
-   **Konfigurieren der richtlinienbasierten Verwaltung mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungsmaßnahmen  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Datenbankrolle PolicyAdministratorRole.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-configure-policy-based-management"></a>So konfigurieren Sie die richtlinienbasierte Verwaltung  
  
1.  Klicken Sie im **Objekt-Explorer**auf das Pluszeichen, um den Server zu erweitern, auf dem Sie die Eigenschaften der richtlinienbasierten Verwaltung konfigurieren möchten.  
  
2.  Klicken Sie auf das Pluszeichen, um den Ordner **Verwaltung** zu erweitern.  
  
3.  Klicken Sie mit der rechten Maustaste auf **Richtlinienverwaltung** , und wählen Sie dann **Eigenschaften**aus.  
  
     Die folgenden Optionen sind im Dialogfeld **Richtlinienverwaltungseigenschaften** verfügbar.  
  
     **Enabled**  
     Gibt an, ob die richtlinienbasierte Verwaltung aktiviert ist.  
  
     **HistoryRetentionInDays**  
     Gibt die Anzahl der Tage an, wie lange der Richtlinienauswertungsverlauf beibehalten werden soll. Wenn dieser Wert 0 ist (Standardeinstellung), wird der Verlauf nicht automatisch entfernt.  
  
     **LogOnSuccess**  
     Gibt an, ob die richtlinienbasierte Verwaltung erfolgreiche Richtlinienauswertungen protokolliert.  
  
    -   Wenn dieser Wert false ist (Standardeinstellung), werden nur fehlerhafte Richtlinienauswertungen protokolliert.  
  
    -   Wenn dieser Wert true ist, werden sowohl erfolgreiche als auch fehlerhafte Richtlinienauswertungen protokolliert.  
  
4.  Wenn Sie fertig sind, klicken Sie auf **OK**.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-configure-policy-based-management"></a>So konfigurieren Sie die richtlinienbasierte Verwaltung  
  
1.  Stellen Sie im **Objekt-Explorer**eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    -- enables Policy-Based Management   
    USE msdb;  
    GO  
    EXEC dbo.sp_syspolicy_configure   
         @name = N'Enabled',   
         @value = 1;  
    GO  
    ```  
  
 Weitere Informationen finden Sie unter [sp_syspolicy_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syspolicy-configure-transact-sql).  
  
  
