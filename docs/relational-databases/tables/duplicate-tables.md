---
title: Duplizieren von Tabellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: table-view-index, sql-database, sql-data-warehouse, pdw
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
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 45fabf20b18fb0f3227f99ab2a6b5270e245562a
ms.sourcegitcommit: 2a06c87aa195bc6743ebdc14b91eb71ab6b91298
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2019
ms.locfileid: "72907311"
---
# <a name="duplicate-tables"></a>Duplizieren von Tabellen
[!INCLUDE[tsql-appliesto-ss2016-all-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  Sie können mit [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] oder [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] eine vorhandene Tabelle in [!INCLUDE[tsql](../../includes/tsql-md.md)] duplizieren, indem Sie eine neue Tabelle erstellen und dann Spalteninformationen aus einer vorhandenen Tabelle kopieren.  
  
> [!IMPORTANT]  
>  Mit diesem Vorgang wird nur die Struktur einer Tabelle dupliziert, nicht die einzelnen Tabellenzeilen.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Security](#Security)  
  
-   **So duplizieren Sie eine Tabelle mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Erfordert die CREATE TABLE-Berechtigung in der Zieldatenbank.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-duplicate-a-table"></a>So duplizieren Sie eine Tabelle  
  
1.  Stellen Sie sicher, dass eine Verbindung mit der Datenbank vorhanden ist, in der Sie die Tabelle erstellen möchten, und dass die Datenbank im Objekt-Explorer ausgewählt ist.  
  
2.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf **Tabellen** , und klicken Sie dann auf **Neue Tabelle**.  
  
3.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf die Tabelle, die Sie kopieren möchten, und klicken Sie dann auf **Entwerfen**.  
  
4.  Wählen Sie in der vorhandenen Tabelle die Spalten aus, und klicken Sie im Menü **Bearbeiten** auf **Kopieren**.  
  
5.  Wechseln Sie zurück in die neue Tabelle, und markieren Sie die erste Zeile.  
  
6.  Klicken Sie im Menü **Bearbeiten** auf **Einfügen**.  
  
7.  Klicken Sie im Menü **Datei** auf **Speichern**_table name_.  
  
8.  Geben Sie im Dialogfeld **Namen auswählen** einen Namen für die neue Tabelle ein, und klicken Sie auf **OK**.  

##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-duplicate-a-table-in-query-editor"></a>So duplizieren Sie eine Tabelle im Abfrage-Editor  
  
1.  Stellen Sie sicher, dass eine Verbindung mit der Datenbank vorhanden ist, in der Sie die Tabelle erstellen möchten, und dass die Datenbank im Objekt-Explorer ausgewählt ist.  
  
2.  Klicken Sie mit der rechten Maustaste auf die Tabelle, die Sie duplizieren möchten, zeigen Sie auf **Skript für Tabelle als**, zeigen Sie dann auf **CREATE in**, und wählen Sie **Neues Abfrage-Editor-Fenster**aus.  
  
3.  Ändern Sie den Namen der Tabelle.  
  
4.  Entfernen Sie alle Spalten, die nicht in der neuen Tabelle benötigt werden.  
  
5.  Klicken Sie auf **Ausführen**.  
  
  
