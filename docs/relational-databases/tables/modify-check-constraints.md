---
description: Ändern von CHECK-Einschränkungen
title: Ändern von Check-Einschränkungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/28/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- CHECK constraints, modifying
- modifying constraints
- constraints [SQL Server], check
- constraints [SQL Server], modifying
ms.assetid: f22daef8-e350-40ef-8ff0-b5f87d1d9e56
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 024897c426ed1bee082a75f44365698274424977
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88488561"
---
# <a name="modify-check-constraints"></a>Ändern von CHECK-Einschränkungen
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Sie können eine CHECK-Einschränkung mit [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] oder [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] in [!INCLUDE[tsql](../../includes/tsql-md.md)] ändern, wenn Sie entweder den Einschränkungsausdruck oder die Optionen ändern möchten, mit denen die Einschränkung unter bestimmten Bedingungen aktiviert bzw. deaktiviert werden.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Security](#Security)  
  
-   **So ändern Sie eine CHECK-Einschränkung mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Erfordert die ALTER-Berechtigung für die Tabelle.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-modify-a-check-constraint"></a>So ändern Sie eine CHECK-Einschränkung  
  
1.  Klicken Sie im **Objekt-Explorer**mit der rechten Maustaste auf die Tabelle mit der CHECK-Einschränkung, und wählen Sie dann **Entwerfen**aus.  
  
2.  Klicken Sie im Menü **Tabellen-Designer** auf **Einschränkungen überprüfen...** .  
  
3.  Wählen Sie im Dialogfeld **CHECK-Einschränkungen** unter **Ausgewählte CHECK-Einschränkung**die Einschränkung aus, die Sie bearbeiten möchten.  
  
4.  Führen Sie eine Aktion aus der folgenden Tabelle aus:  
  
    |An|Schritte|  
    |--------|------------------------|  
    |Ändern des Einschränkungsausdrucks|Geben Sie im Feld **Ausdruck** den neuen Ausdruck ein.|  
    |Umbenennen der Einschränkung|Geben Sie im Feld **Name** einen neuen Namen ein.|  
    |Anwenden der Einschränkung auf die vorhandenen Daten|Aktivieren Sie die Option **Vorhandene Daten bei Erstellung oder Aktivierung überprüfen** .|  
    |Deaktivieren der Einschränkung, wenn der Tabelle neue Daten hinzugefügt werden oder wenn die vorhandenen Daten in der Tabelle aktualisiert werden|Deaktivieren Sie die Option **Einschränkung für INSERT und UPDATE erzwingen** .|  
    |Deaktivieren Sie die Einschränkung, wenn ein Replikations-Agent Daten in die Tabelle einfügt oder darin aktualisiert.|Deaktivieren Sie die Option **Für Replikation erzwingen** .|  
  
    > [!NOTE]  
    >  Die Funktionsweise der CHECK-Einschränkung kann je nach Datenbank unterschiedlich ausfallen.  
  
5.  Klicken Sie auf **Schließen**.  
  
6.  Klicken Sie im Menü **Datei** auf _Tabellenname_**speichern**.  

##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 **So ändern Sie eine CHECK-Einschränkung**  
  
 Um eine `CHECK` -Einschränkung mit [!INCLUDE[tsql](../../includes/tsql-md.md)]zu ändern, müssen Sie zuerst die vorhandene `CHECK` -Einschränkung löschen und sie dann mit der neuen Definition neu erstellen. Weitere Informationen finden Sie unter [Löschen von CHECK-Einschränkungen](../../relational-databases/tables/delete-check-constraints.md) und [Erstellen von CHECK-Einschränkungen](../../relational-databases/tables/create-check-constraints.md).  
  
###  <a name="TsqlExample"></a>  
