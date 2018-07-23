---
title: 'Gewusst wie: Herstellen einer Verbindung mit einer Datenbank und Durchsuchen vorhandener Objekte | Microsoft-Dokumentation'
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql.data.tools.connectionpicker.f1
ms.assetid: 9b331800-3806-4459-ac58-88cdc98124d3
caps.latest.revision: 10
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f342f1427b9943d14216fc5b785036036dd57345
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39082682"
---
# <a name="how-to-connect-to-a-database-and-browse-existing-objects"></a>Gewusst wie: Herstellen einer Verbindung mit einer Datenbank und Durchsuchen vorhandener Objekte
Eine häufige Aufgabe für Datenbankadministratoren und -entwickler besteht darin, eine Verbindung mit einer Livedatenbank herzustellen, deren Schema zu entwerfen oder zu durchsuchen und auf die enthaltenen Objekte abzufragen. Der SQL Server-Objekt-Explorer in Visual Studio enthält nun einen dedizierten Knoten **SQL Server**, unter dem sämtliche verbundenen SQL Server-Instanzen zusammen mit ihren Datenbanken in einer Hierarchie gruppiert sind, die der von SSMS ähnelt. Die verbundenen SQL Server-Instanzen können lokale Instanzen (z.B. eine ausgeführte SQL Server 2008-Instanz) oder eine externe SQL Azure-Instanz darstellen.  
  
In der folgenden Prozedur wird davon ausgegangen, dass die AdventureWorks-Beispieldatenbank bereits installiert ist. Auf [CodePlex](http://msftdbprodsamples.codeplex.com/) finden Sie Beispieldatenbanken, die für unterschiedliche SQL Server-Versionen verwendet und installiert werden können. Falls gewünscht, können Sie die Schritte auch unter Verwendung einer auf Ihrem Server vorhandenen Datenbank ausführen.  
  
### <a name="to-connect-to-a-database-instance"></a>So stellen Sie eine Verbindung mit einer Datenbankinstanz her  
  
1.  Stellen Sie in Visual Studio sicher, dass der **SQL Server-Objekt-Explorer** geöffnet ist. Wenn dies nicht der Fall ist, klicken Sie auf das Menü **Ansicht**, und wählen Sie **SQL Server-Objekt-Explorer** aus.  
  
2.  Klicken Sie im **SQL Server-Objekt-Explorer** mit der rechten Maustaste auf den Knoten **SQL Server**, und klicken Sie auf **SQL Server hinzufügen**.  
  
3.  Geben Sie im Dialogfeld **Verbindung mit Server herstellen** im Feld **Servername** den Namen der Serverinstanz ein, mit der eine Verbindung hergestellt werden soll, geben Sie Ihre Anmeldeinformationen ein, und klicken Sie auf **Verbinden**.  
  
4.  Erweitern Sie im **SQL Server-Objekt-Explorer** unter der Serverinstanz den Knoten **Datenbanken**. Unter dem Knoten **Datenbanken** wurden alle Datenbanken hinzugefügt, die sich auf dieser Serverinstanz befinden.  
  
5.  Erweitern Sie den Knoten **AdventureWorks** (oder einen anderen Datenbankknoten). Alle Datenbankentitäten sind in einer Hierarchie organisiert, die der von SQL Server Management Studio ähnelt.  
  
