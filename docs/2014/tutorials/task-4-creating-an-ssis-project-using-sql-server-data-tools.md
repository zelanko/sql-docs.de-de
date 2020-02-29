---
title: 'Aufgabe 4: Erstellen eines SSIS-Projekts mit SQL Server Data Tools | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 8603ea91-2ec4-40b6-8070-4f824332f5d3
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: bcf16dc7d63e6a4acca6c30871666d1ffe996192
ms.sourcegitcommit: 2d4067fc7f2157d10a526dcaa5d67948581ee49e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/28/2020
ms.locfileid: "78171719"
---
# <a name="task-4-creating-an-ssis-project-using-sql-server-data-tools"></a>Aufgabe 4: Erstellen eines SSIS-Projekts mit SQL Server Data Tools
  In dieser Aufgabe erstellen Sie ein SSIS-Projekt mithilfe **SQL Server Data Tools** , um die Bereinigung und den Abgleich der Lieferantendaten zu automatisieren.

1.  Starten Sie **SQL Server Data Tools**. Klicken Sie auf Start, zeigen Sie auf **Alle Programme**, erweitern Sie **Microsoft SQL Server 2012**, und klicken Sie auf **SQL Server Data Tools**.

2.  Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie auf **Projekt**.

3.  Erweitern Sie im Bereich **installierte Vorlagen** die Option **Business Intelligence** , und wählen Sie **Integration Services**aus.

     ![Visual Studio – Neues Projekt (Dialogfeld)](../../2014/tutorials/media/et-creatinganssisprojectusingsqlsdt-01.jpg "Visual Studio – Neues Projekt (Dialogfeld)")

4.  Wählen Sie **Integration Services Projekt** in der **Liste der Projekttypen**aus.

5.  Geben Sie **clean\andcurratesuppliers** als **Name** ein, und klicken Sie auf **OK**.

6.  Klicken Sie in **Projektmappen-Explorer** Fenster mit der rechten Maustaste auf **Package. DTX** , und wählen Sie **Umbenennen**aus. Wenn **Projektmappen-Explorer** Fenster nicht angezeigt wird, klicken Sie auf der Menüleiste auf **Ansicht** , und klicken Sie auf **Projektmappen-Explorer**.

     ![Package.dtsx – Umbenennen (Menü)](../../2014/tutorials/media/et-creatinganssisprojectusingsqlsdt-02.jpg "Package.dtsx – Umbenennen (Menü)")

7.  Geben Sie **cleantandcursor. dzx** ein, und drücken **Sie die Eingabe**Taste. Stellen Sie sicher, dass die **Erweiterung** **. DTX**beibehalten wird.

## <a name="next-step"></a>Nächster Schritt
 [Aufgabe 5: Hinzufügen eines Datenflusstasks](task-5-adding-data-flow-task.md)


