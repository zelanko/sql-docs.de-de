---
title: Hinzufügen von Einzügen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 9dce05c1-c52f-455d-8b8d-6f303e242760
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 009f61563548e0c060350a75e9627804e18a7c54
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63222948"
---
# <a name="adding-indentation"></a>Hinzufügen von Einzügen
  Der Abfrage-Editor ermöglicht es Ihnen, mit nur einem Schritt einen Einzug für große Codeabschnitte festzulegen. Außerdem können Sie die Größe des Einzugs ändern.  
  
## <a name="indenting-code"></a>Festlegen von Einzügen für Code  
  
#### <a name="to-indent-multiple-lines-of-code"></a>So legen Sie einen Einzug für mehrere Codezeilen fest  
  
1.  Klicken Sie auf der Symbolleiste auf **Neue Abfrage**.  
  
2.  Erstellen Sie eine zweite Abfrage, über die die Spalten **BusinessEntityID**, FirstName, **MiddleName**und **LastName** aus der Tabelle **Person** der Schemas **Person** ausgewählt werden. Platzieren Sie jede Spalte in eine separate Zeile, sodass der Code wie folgt aussieht:  
  
    ```  
    -- Search for a contact  
    SELECT   
    BusinessEntityID,  
    FirstName,   
    MiddleName,   
    LastName  
    FROM Person.Person  
    WHERE LastName = 'Sanchez';  
    GO  
    ```  
  
3.  Markieren Sie den gesamten Text von `BusinessEntityID` bis `LastName`.  
  
4.  Klicken Sie auf der Symbolleiste **SQL-Editor** auf **Einzug vergrößern** , um für alle Zeilen gleichzeitig einen Einzug festzulegen.  
  
#### <a name="to-change-the-default-indentation"></a>So ändern Sie den Standardeinzug  
  
1.  Klicken Sie im Menü **Extras** auf **Optionen**.  
  
2.  Erweitern Sie **Text-Editor**, erweitern Sie **Alle Sprachen**, und klicken Sie dann auf **Tabstopps** , um die gewünschten Werte für die Einzüge festzulegen. Beachten Sie, dass Sie die Größe des Einzugs und der Tabstopps festlegen können und angeben können, ob Tabstopps in Leerzeichen umgewandelt werden sollen.  
  
     ![Darstellung des Dialogfelds 'Registerkarten'](media/tabsdialog.gif "Darstellung des Dialogfelds 'Registerkarten'")  
  
3.  Klicken Sie auf **OK**.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in der Lektion  
 [Maximieren des Abfrage-Editors](lesson-2-3-maximizing-query-editor.md)  
  
  
