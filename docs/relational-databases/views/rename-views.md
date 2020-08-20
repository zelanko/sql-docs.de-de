---
description: Umbenennen von Sichten
title: Umbenennen von Sichten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: table-view-index, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- views [SQL Server], renaming
- renaming views
ms.assetid: 5eed0488-81d2-40e8-8fdf-b0a640a591d0
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 135bccd7ff94a88f7f1036b4bce4e55451eab4e6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88463665"
---
# <a name="rename-views"></a>Umbenennen von Sichten
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-pdw-md.md)]
  Sie können in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] eine Sicht mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]umbenennen.  
  
> [!WARNING]  
>  Wenn Sie eine Sicht umbenennen, kann es vorkommen, dass Code und Anwendungen, die von der Sicht abhängen, fehlerhaft ausgeführt werden. Dies schließt andere Sichten, Abfragen, gespeicherte Prozeduren, benutzerdefinierte Funktionen und Clientanwendungen ein. Beachten Sie, dass dabei ein Fehler durch Verkettung weitere Fehler nach sich ziehen kann.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Voraussetzungen](#Prerequisites)  
  
     [Security](#Security)  
  
-   **So benennen Sie eine Sicht um mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Follow Up:**  [After renaming a view](#FollowUp)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Voraussetzungen  
 Rufen Sie eine Liste aller Abhängigkeiten der Sicht ab. Für alle Objekte, Skripts oder Anwendungen, die auf die Sicht verweisen, muss der neue Name der Sicht festgelegt werden. Weitere Informationen finden Sie unter [Get Information About a View](../../relational-databases/views/get-information-about-a-view.md). Es ist ratsam, die Sicht zu verwerfen und unter einem neuen Namen neu zu erstellen, anstatt die Sicht umzubenennen. Indem Sie die Sicht neu erstellen, aktualisieren Sie die Abhängigkeitsinformationen für die Objekte, auf die in der Sicht verwiesen wird.  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Erfordert die ALTER-Berechtigung für SCHEMA oder die CONTROL-Berechtigung für OBJECT sowie die CREATE VIEW-Berechtigung in der Datenbank.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-rename-a-view"></a>So benennen Sie eine Sicht um  
  
1.  Erweitern Sie im **Objekt-Explorer**die Datenbank mit der Sicht, die Sie umbenennen möchten, und erweitern Sie dann den Ordner **Sicht** .  
  
2.  Klicken Sie mit der rechten Maustaste auf die Sicht, die Sie umbenennen möchten, und wählen Sie die Option **Umbenennen**.  
  
3.  Geben Sie den neuen Namen der Ansicht ein.  

##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 **So benennen Sie eine Sicht um**  
  
 Sie können den Namen der Sicht zwar mit **sp_rename** ändern, aber es wird empfohlen, die vorhandene Sicht zu löschen und dann unter einem neuen Namen neu zu erstellen.  
  
 Weitere Informationen finden Sie unter [CREATE VIEW &#40;Transact-SQL&#41;](../../t-sql/statements/create-view-transact-sql.md) und [DROP VIEW &#40;Transact-SQL&#41;](../../t-sql/statements/drop-view-transact-sql.md).  
  
##  <a name="follow-up-after-renaming-a-view"></a><a name="FollowUp"></a> Nachverfolgung: Nach dem Umbenennen einer Sicht  
 Stellen Sie sicher, dass alle Objekte, Skripts und Anwendungen, die auf den alten Namen der Ansicht verweisen, jetzt den neuen Namen verwenden.  
  
  
