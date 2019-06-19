---
title: 'Schritt 3: Ändern des Verbindungs-Managers für Flatfiles | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/03/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 459e3995-2116-4f15-aaa2-32f26113869c
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: eed92adad122587a031a3126322e4156a05bde58
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65722548"
---
# <a name="lesson-2-3-modify-the-flat-file-connection-manager"></a>Lektion 2.3: Ändern des Verbindungs-Managers für Flatfiles

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]



In dieser Aufgabe ändern Sie die Verbindungs-Manager-Instanz für Flatfiles aus Lektion 1. Dieser Manager ist so konfiguriert, dass eine einzelne Datei statisch geladen wird. Damit der Verbindungs-Manager für Flatfiles Dateien auf iterative Weise laden kann, müssen Sie die Eigenschaft „ConnectionString“ des Verbindungs-Managers so ändern, dass die benutzerdefinierte Variable `User::varFileName` akzeptiert wird, die den Pfad der zur Laufzeit zu ladenden Datei enthält.  
  
Wenn Sie den Verbindungs-Manager so ändern, dass der Wert der benutzerdefinierten Variablen verwendet wird, um die Eigenschaft „ConnectionString“ des Verbindungs-Managers aufzufüllen, wird eine Verbindung mit verschiedenen Flatfiles hergestellt. Zur Laufzeit aktualisiert dann jede Iteration des Foreach-Schleifencontainers die `User::varFileName` -Variable. Durch das Aktualisieren der Variable stellt der Verbindungs-Manager wiederum eine Verbindung zu einer anderen Flatfile her, und der Datenflusstask verarbeitet andere Daten.  
  
## <a name="configure-the-flat-file-connection-manager-to-use-a-variable"></a>Konfigurieren des Verbindungs-Managers für Flatfiles für die Verwendung einer Variablen  
  
1.  Klicken Sie im Bereich **Verbindungs-Manager** mit der rechten Maustaste auf **Sample Flat File Source Data**(Beispielquelldaten von Flatfiles), und wählen Sie **Eigenschaften**aus.  

2.  Stellen Sie im Fenster **Eigenschaften** sicher, dass der **PackagePath** mit **\Package.Connections** beginnt. Wenn nicht, klicken Sie im Bereich **Verbindungs-Manager** mit der rechten Maustaste auf **Beispielquelldaten von Flatfiles**, und wählen Sie **In Paketverbindung konvertieren**.
  
3.  Klicken Sie im Fenster **Eigenschaften** für **Ausdrücke** in die leere Zelle, und klicken Sie anschließend auf die Schaltfläche mit den Auslassungspunkten **(...)** .  
  
4.  Geben Sie in das Dialogfeld **Eigenschaftsausdrucks-Editor** in der Spalte **Eigenschaft** die Option **ConnectionString** ein, oder wählen Sie sie aus.  
  
5.  Klicken Sie in der Spalte **Ausdruck** auf die Schaltfläche mit den Auslassungspunkten **(...)** , um das Dialogfeld **Ausdrucks-Generator** zu öffnen.  
  
6.  Erweitern Sie im Dialogfeld **Ausdrucks-Generator** den Knoten **Variablen**.  
  
7.  Ziehen Sie die Variable **User::varFileName** in das Feld **Ausdruck**.  
  
8.  Klicken Sie auf **OK**, um das Dialogfeld **Ausdrucks-Generator** zu schließen.  
  
9.  Klicken Sie auf **OK**, um das Dialogfeld **Eigenschaftsausdrucks-Editor** zu schließen.  
  
## <a name="go-to-next-task"></a>Weiter zur nächsten Aufgabe  
[Schritt 4: Testen des Tutorialpakets aus Lektion 2](../integration-services/lesson-2-4-testing-the-lesson-2-tutorial-package.md)  
  
  
  
