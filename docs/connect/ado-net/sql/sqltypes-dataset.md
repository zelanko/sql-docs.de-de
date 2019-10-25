---
title: SqlTypes und das Dataset
description: Beschreibt die Typunterstützung für SqlTypes im DataSet.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 9172c20a-9876-4b3b-9c97-1963c02b1993
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: 70efb8615a70677c709abd6d9129c63de9420ffc
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72451982"
---
# <a name="sqltypes-and-the-dataset"></a>SqlTypes und das Dataset

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[ADO.NET herunterladen](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

ADO.NET 2,0 hat eine erweiterte Typunterstützung für die `DataSet` über den <xref:System.Data.SqlTypes>-Namespace eingeführt. Die Typen in <xref:System.Data.SqlTypes> sind so konzipiert, dass Datentypen mit derselben Semantik und Präzision wie die Datentypen in einer SQL Server Datenbank bereitgestellt werden. Für jeden Datentyp in <xref:System.Data.SqlTypes> gibt es einen äquivalenten Datentyp in SQL Server mit derselben zugrunde liegenden Datendarstellung.  
  
Wenn Sie <xref:System.Data.SqlTypes> direkt in einem <xref:System.Data.DataSet> verwenden, werden beim Arbeiten mit SQL Server-Datentypen mehrere Vorteile geboten. <xref:System.Data.SqlTypes> unterstützt die gleiche Semantik wie SQL Server systemeigene Datentypen. Wenn Sie einen der <xref:System.Data.SqlTypes> in der Definition einer <xref:System.Data.DataColumn> angeben, entfällt der Genauigkeits Verlust, der beim Umrechnen von dezimalen oder numerischen Datentypen in einen der Common Language Runtime Datentypen (CLR) auftreten kann.  

Im folgenden Beispiel wird ein <xref:System.Data.DataTable>-Objekt erstellt. Dabei werden explizit die <xref:System.Data.DataColumn>-Datentypen definiert, wobei anstelle von CLR-Typen <xref:System.Data.SqlTypes> verwendet werden. Der Code füllt die <xref:System.Data.DataTable> mit Daten aus der Sales.SalesOrderDetail-Tabelle in der SQL Server-AdventureWorks-Datenbank. Die im Konsolenfenster angezeigte Ausgabe zeigt den Datentyp der einzelnen Spalten und die Werte, die aus SQL Server abgerufen werden.  
  
[!code-csharp[DataWorks DataColumn_DataType#1](~/../sqlclient/doc/samples/DataColumn_DataType.cs#1)]
