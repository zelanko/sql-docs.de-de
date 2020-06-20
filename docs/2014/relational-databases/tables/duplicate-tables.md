---
title: Duplizieren von Tabellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- copying tables
- tables [SQL Server], duplicating
- duplicating tables
- table copying [SQL Server]
ms.assetid: c6b07423-d1e5-4e5e-8681-5088921f5df3
author: stevestein
ms.author: sstein
ms.openlocfilehash: d07777b7f55d6471127cb1cbe4adbafb36679573
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85068113"
---
# <a name="duplicate-tables"></a>Duplizieren von Tabellen
  Sie können mit [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] oder [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] eine vorhandene Tabelle in [!INCLUDE[tsql](../../includes/tsql-md.md)] duplizieren, indem Sie eine neue Tabelle erstellen und dann Spalteninformationen aus einer vorhandenen Tabelle kopieren.  
  
> [!IMPORTANT]  
>  Mit diesem Vorgang wird nur die Struktur einer Tabelle dupliziert, nicht die einzelnen Tabellenzeilen.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Sicherheit](#Security)  
  
-   **So duplizieren Sie eine Tabelle mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Erfordert die CREATE TABLE-Berechtigung in der Zieldatenbank.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-duplicate-a-table"></a>So duplizieren Sie eine Tabelle  
  
1.  Stellen Sie sicher, dass eine Verbindung mit der Datenbank vorhanden ist, in der Sie die Tabelle erstellen möchten, und dass die Datenbank im Objekt-Explorer ausgewählt ist.  
  
2.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf **Tabellen** , und klicken Sie dann auf **Neue Tabelle**.  
  
3.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf die Tabelle, die Sie kopieren möchten, und klicken Sie dann auf **Entwerfen**.  
  
4.  Wählen Sie in der vorhandenen Tabelle die Spalten aus, und klicken Sie im Menü **Bearbeiten** auf **Kopieren**.  
  
5.  Wechseln Sie zurück in die neue Tabelle, und markieren Sie die erste Zeile.  
  
6.  Klicken Sie im Menü **Bearbeiten** auf **Einfügen**.  
  
7.  Klicken Sie im Menü **Datei** auf **Speichern**_table name_.  
  
8.  Geben Sie im Dialogfeld **Namen auswählen** einen Namen für die neue Tabelle ein, und klicken Sie auf **OK**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-duplicate-a-table-in-query-editor"></a>So duplizieren Sie eine Tabelle im Abfrage-Editor  
  
1.  Stellen Sie sicher, dass eine Verbindung mit der Datenbank vorhanden ist, in der Sie die Tabelle erstellen möchten, und dass die Datenbank im Objekt-Explorer ausgewählt ist.  
  
2.  Klicken Sie mit der rechten Maustaste auf die Tabelle, die Sie duplizieren möchten, zeigen Sie auf **Skript für Tabelle als**, zeigen Sie dann auf **CREATE in**, und wählen Sie **Neues Abfrage-Editor-Fenster**aus.  
  
3.  Ändern Sie den Namen der Tabelle.  
  
4.  Entfernen Sie alle Spalten, die nicht in der neuen Tabelle benötigt werden.  
  
5.  Klicken Sie auf **Ausführen**.  
  
  
