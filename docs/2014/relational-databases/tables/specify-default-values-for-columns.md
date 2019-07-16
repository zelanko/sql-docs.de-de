---
title: Angeben von Standardwerten für Spalten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- columns [SQL Server], defaults
- default values
ms.assetid: 64514aed-b846-407b-992e-cf813f9a1a91
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8a02385a6cd12b85be1661c738488c000f810510
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "68196723"
---
# <a name="specify-default-values-for-columns"></a>Angeben von Standardwerten für Spalten
  Sie können einen Standardwert angeben, der mit [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] oder [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] in die Spalte in [!INCLUDE[tsql](../../includes/tsql-md.md)]eingegeben wird. Wenn kein Standardwert zugewiesen ist und Benutzer die Spalte leer lassen, wird wie folgt verfahren:  
  
-   Wenn NULL-Werte zugelassen sind, wird NULL in die Spalte eingefügt.  
  
-   Wenn NULL-Werte nicht zugelassen sind, bleibt die Spalte leer. Die Zeile kann jedoch erst dann gespeichert werden, wenn ein Wert in die Spalte eingegeben wird.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Sicherheit](#Security)  
  
-   **So geben Sie einen benutzerdefinierten Standardwert an mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Restrictions"></a> Einschränkungen  
  
-   Wenn die Eingabe im Feld **Standardwert** einen gebundenen Standardwert ersetzt (der ohne Klammern angezeigt wird), werden Sie aufgefordert, die Bindung des Standardwerts aufzuheben und ihn durch den neuen Standardwert zu ersetzen.  
  
-   Werte für Zeichenfolgen müssen in einfache Anführungszeichen (') gesetzt werden. Verwenden Sie keine doppelten Anführungszeichen ("), da diese für in Anführungszeichen gesetzte Bezeichner reserviert sind.  
  
-   Um einen numerischen Standardwert einzugeben, geben Sie die Zahl ohne Anführungszeichen ein.  
  
-   Wenn Sie ein Objekt bzw. eine Funktion eingeben, geben Sie den Namen des Objekts bzw. der Funktion ein, ohne ihn in Anführungszeichen einzuschließen.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Erfordert die ALTER-Berechtigung für die Tabelle.  
  
##  <a name="SSMSProcedure"></a> Verwendung von SQL Server Management Studio  
  
#### <a name="to-specify-a-default-value-for-a-column"></a>So geben Sie einen Standardwert für eine Spalte an  
  
1.  Klicken Sie im **Objekt-Explorer**mit der rechten Maustaste auf die Tabelle mit den Spalten, für die Sie Dezimalstellen ändern möchten, und klicken Sie auf **Entwerfen**.  
  
2.  Wählen Sie die Spalte aus, für die Sie einen Standardwert angeben möchten.  
  
3.  Geben Sie den neuen Standardwert auf der Registerkarte **Spalteneigenschaften** in der Eigenschaft **Standardwert oder -bindung** ein.  
  
    > [!NOTE]  
    >  Um einen numerischen Standardwert einzugeben, geben Sie die Zahl ein. Geben Sie bei einem Objekt oder einer Funktion den entsprechenden Namen ein. Geben Sie für einen alphanumerischen Standardwert den Wert in einfachen Anführungszeichen ein.  
  
4.  Klicken Sie im Menü **Datei** auf **Speichern**_table name_.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-specify-a-default-value-for-a-column"></a>So geben Sie einen Standardwert für eine Spalte an  
  
1.  Stellen Sie im **Objekt-Explorer**eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    CREATE TABLE dbo.doc_exz ( column_a INT, column_b INT) ;  
    GO  
    INSERT INTO dbo.doc_exz (column_a)VALUES ( 7 ) ;  
    GO  
    ALTER TABLE dbo.doc_exz  
    ADD CONSTRAINT col_b_def  
    DEFAULT 50 FOR column_b ;  
    GO  
  
    ```  
  
 Weitere Informationen finden Sie unter [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).  
  
###  <a name="TsqlExample"></a>  
