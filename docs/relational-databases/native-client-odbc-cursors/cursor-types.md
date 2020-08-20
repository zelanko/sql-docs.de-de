---
description: Cursortypen
title: Cursor Typen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, cursors
- ODBC applications, cursors
- cursors [ODBC], types
- ODBC cursors, types
ms.assetid: 3a916cc7-f352-42cb-8b83-f78e06cef991
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a7459f8a312cbfbb960d6cfdf87e64d5b8015429
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88460799"
---
# <a name="cursor-types"></a>Cursortypen
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  ODBC definiert vier Cursor Typen, die von Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber unterstützt werden. Diese Cursor unterscheiden sich in ihrer Fähigkeit, Änderungen am Resultset und in den von Ihnen genutzten Ressourcen zu erkennen, wie z. b. Arbeitsspeicher und Speicherplatz in **tempdb**. Ein Cursor kann Änderungen an Zeilen nur dann erkennen, wenn er versucht, diese Zeilen erneut abzurufen. Es gibt keine Möglichkeit, wie die Datenquelle den Cursor über Änderungen an den derzeit abgerufenen Zeilen informieren könnte. Die Fähigkeit eines Cursors, Änderungen, die nicht durch den Cursor vorgenommen wurden, zu erkennen, hängt außerdem von der Transaktionsisolationsstufe ab.  
  
 Die vier von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützten ODBC-Cursortypen sind:  
  
-   Vorwärtscursor unterstützen keine Bildläufe, sondern ausschließlich das serielle Abrufen von Zeilen vom Anfang bis zum Ende des Cursors.  
  
-   Statische Cursor werden in **tempdb** erstellt, wenn der Cursor geöffnet wird. Das Resultset wird immer angezeigt, wenn der Cursor geöffnet wurde. Änderungen an den Daten werden nicht wiedergegeben. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : Statische Cursor sind immer schreibgeschützt. Da ein statischer Server Cursor als Arbeits Tabelle in **tempdb**erstellt wird, darf die Größe des Cursorresultsets die maximale Zeilengröße nicht überschreiten, die von zulässig ist [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   In einem keysetgesteuerten Cursor werden Mitgliedschaft und Reihenfolge der Zeilen beim Öffnen des Cursors festgelegt. Änderungen an Nichtschlüsselspalten sind durch den Cursor sichtbar.  
  
-   Dynamische Cursor sind das Gegenteil von statischen Cursorn. Dynamische Cursor spiegeln alle Änderungen an den Zeilen in den Resultsets wider. Die Datenwerte, Reihenfolge und Mitgliedschaft der Zeilen im Resultset können sich bei jedem Abrufvorgang ändern.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwenden von Cursorn &#40;ODBC-&#41;](../../relational-databases/native-client-odbc-cursors/using-cursors-odbc.md)  
  
  
