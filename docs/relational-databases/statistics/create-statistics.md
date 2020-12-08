---
title: Erstellen von Statistiken | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie die Abfrageoptimierungsstatistiken von Spalten einer Tabelle oder einer indizierten Sicht in SQL Server mithilfe von SQL Server Management Studio oder Transact-SQL erstellen.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
f1_keywords:
- sql13.swb.stat.properties.f1
- sql13.swb.statistics.filter.f1
- sql13.swb.stat.columns.f1
- sql13.swb.statistics.propertis.f1
helpviewer_keywords:
- creating statistics
- statistics [SQL Server], creating
ms.assetid: 95a455fb-664d-4c95-851e-c6b62d7ebe04
author: WilliamDAssafMSFT
ms.author: wiassaf
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 7b2d5dc3f6822a7becc311367a7f0c6893a91f6f
ms.sourcegitcommit: 0e0cd9347c029e0c7c9f3fe6d39985a6d3af967d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2020
ms.locfileid: "96506549"
---
# <a name="create-statistics"></a>Erstellen von Statistiken
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
  Sie können Abfrageoptimierungsstatistiken in einer oder mehreren Spalten einer Tabelle oder indizierten Sicht in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] erstellen, indem Sie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]verwenden. Bei den meisten Abfragen generiert der Abfrageoptimierer automatisch die notwendigen Statistiken für einen hochwertigen Abfrageplan. In einigen Fällen müssen Sie weitere Statistiken erstellen.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Security](#Security)  
  
-   **So erstellen Sie Statistiken mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Einschränkungen  
  
-   Vergewissern Sie sich vor dem Erstellen von Statistiken mit der CREATE STATISTICS-Anweisung, dass auf Datenbankebene die AUTO_CREATE_STATISTICS-Option festgelegt ist. Dadurch wird sichergestellt, dass der Abfrageoptimierer weiterhin routinemäßig einspaltige Statistiken für Abfrageprädikatsspalten erstellt.  
  
-   Sie können bis zu 32 Spalten pro Statistikobjekt auflisten.  
  
-   Sie können die Definition einer in einem Prädikat der gefilterten Statistik definierten Tabellenspalte nicht löschen, umbenennen oder ändern.  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Erfordert, dass der Benutzer der Besitzer der Tabelle oder indizierten Sicht oder ein Mitglied einer der folgenden Rollen ist: feste Serverrolle **sysadmin** , feste Datenbankrolle **db_owner** oder feste Datenbankrolle **db_ddladmin** .  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-create-statistics"></a>So erstellen Sie Statistiken  
  
1.  Klicken Sie im **Objekt-Explorer** auf das Pluszeichen, um die Datenbank zu erweitern, in der Sie eine neue Statistik erstellen möchten.  
  
2.  Klicken Sie auf das Pluszeichen, um den Ordner **Tabellen** zu erweitern.  
  
3.  Klicken Sie auf das Pluszeichen, um die Tabelle zu erweitern, in der Sie eine neue Statistik erstellen möchten.  
  
4.  Klicken Sie mit der rechten Maustaste auf den Ordner **Statistik**, und wählen Sie dann **New Statistics...** (Neue Statistiken…).  
  
     Die folgenden Eigenschaften werden auf der Seite **Allgemein** im Dialogfeld **Neue Statistik für Tabelle**_Tabellenname_ angezeigt.  
  
     **Tabellenname**  
     Zeigt den Namen der Tabelle an, die von den Statistiken beschrieben wird.  
  
     **Statistikname**  
     Zeigt den Namen des Datenbankobjekts an, in dem die Statistiken gespeichert sind.  
  
     **Statistikspalten**  
     Dieses Raster zeigt die von dieser Gruppe von Statistiken beschriebenen Spalten an. Alle Werte im Raster sind schreibgeschützt.  
  
     **Name**  
     Zeigt den Namen der Spalte an, die von den Statistiken beschrieben wird. Dabei kann es sich um eine einzelne Spalte oder eine Kombination aus Spalten in einer einzelnen Tabelle handeln.  
  
     **Datentyp**  
     Gibt den Datentyp der von den Statistiken beschriebenen Spalten an.  
  
     **Größe**  
     Zeigt jeweils die Größe des Datentyps für die einzelnen Spalten an.  
  
     **Identität**  
     Gibt eine Identitätsspalte an, wenn diese Option aktiviert ist.  
  
     **NULL-Werte zulassen**  
     Gibt an, ob die Spalte NULL-Werte annimmt.  
  
     **Add (Hinzufügen)**  
     Fügt dem Statistikraster zusätzliche Spalten aus der Tabelle hinzu.  
  
     **Remove**  
     Entfernt die ausgewählte Spalte aus dem Statistikraster.  
  
     **Nach oben**  
     Verschiebt die ausgewählte Spalte an eine frühere Position im Statistikraster. Die Position im Raster kann in erheblichem Maß die Eignung der Statistiken beeinflussen.  
  
     **Nach unten**  
     Verschiebt die ausgewählte Spalte an eine spätere Position im Statistikraster.  
  
     **Die Statistiken für diese Spalten wurden zuletzt aktualisiert:**  
     Gibt das Alter von Statistiken an. Statistiken sind wertvoller, wenn Sie aktuell sind. Aktualisieren Sie Statistiken nach umfangreichen Änderungen an den Daten bzw. nach Hinzufügen atypischer Daten. Statistiken für Tabellen mit konsistenter Verteilung der Daten müssen seltener aktualisiert werden.  
  
     **Statistiken für diese Spalten aktualisieren**  
     Aktivieren Sie diese Option, wenn die Statistiken beim Schließen des Dialogfelds aktualisiert werden sollen.  
  
     Die folgende Eigenschaft wird auf der Seite **Filter** im Dialogfeld **Neue Statistik für Tabelle**_Tabellenname_ angezeigt.  
  
     **Filterausdruck**  
     Definiert, welche Datenzeilen in die gefilterte Statistik eingeschlossen werden sollen. Zum Beispiel, `Production.ProductSubcategoryID IN ( 1,2,3 )`  
  
5.  Klicken Sie im Dialogfeld **Neue Statistik für Tabelle**_Tabellenname_ auf der Seite **Allgemein** auf **Hinzufügen**.  
  
     Die folgenden Eigenschaften werden im Dialogfeld **Spalten auswählen** angezeigt. Diese Informationen sind schreibgeschützt.  
  
     **Name**  
     Zeigt den Namen der Spalte an, die von den Statistiken beschrieben wird. Dabei kann es sich um eine einzelne Spalte oder eine Kombination aus Spalten in einer einzelnen Tabelle handeln.  
  
     **Datentyp**  
     Gibt den Datentyp der von den Statistiken beschriebenen Spalten an.  
  
     **Größe**  
     Zeigt jeweils die Größe des Datentyps für die einzelnen Spalten an.  
  
     **Identität**  
     Gibt eine Identitätsspalte an, wenn diese Option aktiviert ist.  
  
     **NULL-Werte zulassen**  
     Gibt an, ob die Spalte NULL-Werte annimmt.  
  
6.  Aktivieren Sie im Dialogfeld **Spalten auswählen** das oder die Kontrollkästchen der einzelnen Spalten, für die Sie eine Statistik erstellen möchten, und klicken Sie auf **OK**.  
  
7.  Klicken Sie im Dialogfeld **Neue Statistik für Tabelle**_Tabellenname_ auf **OK**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-create-statistics"></a>So erstellen Sie Statistiken  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    -- Create new statistic object called ContactMail1  
    -- on the BusinessEntityID and EmailPromotion columns in the Person.Person table.   
  
    CREATE STATISTICS ContactMail1  
        ON Person.Person (BusinessEntityID, EmailPromotion);   
    GO  
    ```  
  
4.  Die oben erstellte Statistik kann zu einer Verbesserung der Ergebnisse für die folgende Abfrage führen.  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    SELECT LastName, FirstName  
    FROM Person.Person  
    WHERE EmailPromotion = 2  
    ORDER BY LastName, FirstName;   
    GO  
    ```  
  
 Weitere Informationen finden Sie unter [CREATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/create-statistics-transact-sql.md).  
  
  
