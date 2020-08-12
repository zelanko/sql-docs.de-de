---
title: Anzeigen und Bearbeiten von Daten in einer Tabelle
description: In diesem Artikel wird erläutert, wie Sie mit dem Daten-Editor Daten in einer bestehenden Tabelle anzeigen, bearbeiten und löschen. Außerdem erfahren Sie, wie Sie Änderungen in Skriptform anzeigen und in einer Skriptdatei speichern.
ms.prod: sql
ms.technology: ssdt
ms.topic: conceptual
f1_keywords:
- SQL.DATA.TOOLS.QUERYRESULTS.F1
- sql.data.tools.queryresults.executequerydeletingrow
ms.assetid: bb67ce83-a87a-4e14-84cd-9a5930fe74c8
author: markingmyname
ms.author: maghan
ms.reviewer: “”
ms.custom: seo-lt-2019
ms.date: 02/09/2017
ms.openlocfilehash: 7c8321f4f1264b8bf0352f459bde02a07e439dd3
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85895791"
---
# <a name="how-to-view-and-edit-data-in-a-table"></a>Gewusst wie: Anzeigen und Bearbeiten von Daten in einer Tabelle

Sie können Daten in einer vorhandenen Tabelle mithilfe eines visuellen Daten-Editors anzeigen, bearbeiten und löschen.  
  
> [!WARNING]  
> Bei den folgenden Vorgehensweisen werden die Entitäten verwendet, die in vorherigen Vorgehensweisen im Abschnitt [Entwicklung verbundener Datenbanken](../ssdt/connected-database-development.md) erstellt wurden.  
  
### <a name="to-edit-data-in-a-table-visually-using-the-data-editor"></a>So bearbeiten Sie Daten in einer Tabelle visuell mit dem Daten-Editor  
  
1.  Klicken Sie im **SQL Server-Objekt-Explorer** mit der rechten Maustaste auf die Tabelle **Products**, und klicken Sie auf die Option **Daten anzeigen**.  
  
2.  Der Daten-Editor wird gestartet. Beachten Sie die Zeilen, die der Tabelle in vorherigen Prozeduren hinzugefügt wurden.  
  
3.  Klicken Sie im SQL Server-Objekt-Explorer mit der rechten Maustaste auf die Tabelle **Fruits**, und klicken Sie auf die Option **Daten anzeigen**.  
  
4.  Geben Sie im Daten-Editor für **Id****1** und für **Perishable****True** ein. Drücken Sie dann entweder die EINGABE- oder TAB-TASTE, um den Fokus von der neuen Zeile zu entfernen und einen Commit der Zeile in der Datenbank auszuführen.  
  
5.  Wiederholen Sie den obigen Schritt, und geben Sie **2** und **False** sowie **3** und **False** für die Tabelle ein.  
  
    Wenn Sie eine Zeile bearbeiten, können Sie die Änderungen an einer Zelle immer rückgängig machen, indem Sie ESC drücken.  
  
6.  Sie können die Bearbeitungsschritte als Skript anzeigen, indem Sie auf der Symbolleiste auf die Schaltfläche **Skript** klicken. Sie können jedoch auch auf die Schaltfläche **Skript in Datei schreiben** klicken, um das Skript für die spätere Ausführung in einer SQL-Skriptdatei zu speichern.  
  
7.  Klicken Sie mit der rechten Maustaste auf die Datenbank **Trade** im **SQL Server-Objekt-Explorer**, und klicken Sie auf **Neue Abfrage**. Geben Sie im Editor `select * from dbo.PerishableFruits` ein, und klicken Sie auf die Schaltfläche **Abfrage ausführen**, um die von der `PerishableFruits`-Sicht dargestellten Daten zurückzugeben.  
  
