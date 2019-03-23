---
title: 'Schritt 3: Ändern die Flat File Connection Manager | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 459e3995-2116-4f15-aaa2-32f26113869c
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: c251a77d0272e069d57b46940f8fcb06144653a0
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2019
ms.locfileid: "58389698"
---
# <a name="step-3-modifying-the-flat-file-connection-manager"></a>Schritt 3: Ändern des Flatfile-Verbindungs-Managers
  In dieser Aufgabe ändern Sie den in Lektion 1 konfigurierten und erstellten Flatfile-Verbindungs-Manager. Bei der ursprünglichen Erstellung wurde der Flatfile-Verbindungs-Manager so konfiguriert, dass eine einzelne Datei statisch geladen wird. Damit der Flatfile-Verbindungs-Manager Dateien iterativ laden kann, müssen Sie die ConnectionString-Eigenschaft des Verbindungs-Managers so ändern, dass die benutzerdefinierte Variable `User:varFileName`, die den Pfad der zur Laufzeit zu ladenden Datei enthält, akzeptiert wird.  
  
 Indem Sie den Verbindungs-Manager so ändern, dass er den Wert der benutzerdefinierten Variable `User::varFileName`verwendet, um die ConnectionString-Eigenschaft des Verbindungs-Managers aufzufüllen, kann der Verbindungs-Manager eine Verbindung mit verschiedenen Flatfiles herstellen. Zur Laufzeit aktualisiert dann jede Iteration des Foreach-Schleifencontainers die `User::varFileName` -Variable. Durch das Aktualisieren der Variable stellt der Verbindungs-Manager wiederum eine Verbindung zu einer anderen Flatfile her, und der Datenflusstask verarbeitet andere Daten.  
  
### <a name="to-configure-the-flat-file-connection-manager-to-use-a-variable-for-the-connection-string"></a>So konfigurieren Sie den Flatfile-Verbindungs-Manager auf die Verwendung einer Variable für die Verbindungszeichenfolge  
  
1.  Klicken Sie im Bereich **Verbindungs-Manager** mit der rechten Maustaste auf **Sample Flat File Source Data**(Beispielquelldaten von Flatfiles), und wählen Sie **Eigenschaften**aus.  
  
2.  Klicken Sie im Eigenschaftenfenster für **Ausdrücke** in die leere Zelle, und klicken Sie auf die Schaltfläche mit den Auslassungspunkten **(...)**.  
  
3.  In der **Eigenschaftsausdrucks-Editor** Dialogfeld die **Eigenschaft** Spalte eingeben oder auswählen `ConnectionString`.  
  
4.  Klicken Sie in der Spalte **Ausdruck** auf die Schaltfläche mit den Auslassungspunkten **(...)**, um das Dialogfeld **Ausdrucks-Generator** zu öffnen.  
  
5.  Erweitern Sie im Dialogfeld **Ausdrucks-Generator** den Knoten **Variablen** .  
  
6.  Ziehen Sie die Variable **User::varFileName**, in das Feld **Ausdruck** .  
  
7.  Klicken Sie auf **OK** , um das Dialogfeld **Ausdrucks-Generator** zu schließen.  
  
8.  Klicken Sie auf **OK** , um das Dialogfeld **Eigenschaftsausdrucks-Editor** zu schließen.  
  
## <a name="next-lesson-task"></a>Aufgabe in der nächsten Lektion  
 [Schritt 4: Testen des Lektion 2-Tutorialpakets](../integration-services/lesson-2-4-testing-the-lesson-2-tutorial-package.md)  
  
  
