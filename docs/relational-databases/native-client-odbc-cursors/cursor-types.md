---
title: Cursortypen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, cursors
- ODBC applications, cursors
- cursors [ODBC], types
- ODBC cursors, types
ms.assetid: 3a916cc7-f352-42cb-8b83-f78e06cef991
caps.latest.revision: 28
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: a2a553a94f091bb7bab344eabfa65901e6e1fcdd
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/06/2018
ms.locfileid: "39562404"
---
# <a name="cursor-types"></a>Cursortypen
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  ODBC definiert vier Cursortypen, die von Microsoft unterstützt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber. Diese Cursor sind im Hinblick auf ihre Fähigkeit, Änderungen am Resultset zu erkennen und in den Ressourcen zu nutzen, z. B. Arbeitsspeicher und Speicherplatz in **Tempdb**. Ein Cursor kann Änderungen an Zeilen nur dann erkennen, wenn er versucht, diese Zeilen erneut abzurufen. Es gibt keine Möglichkeit, wie die Datenquelle den Cursor über Änderungen an den derzeit abgerufenen Zeilen informieren könnte. Die Fähigkeit eines Cursors, Änderungen, die nicht durch den Cursor vorgenommen wurden, zu erkennen, hängt außerdem von der Transaktionsisolationsstufe ab.  
  
 Die vier von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützten ODBC-Cursortypen sind:  
  
-   Vorwärtscursor unterstützen keine Bildläufe, sondern ausschließlich das serielle Abrufen von Zeilen vom Anfang bis zum Ende des Cursors.  
  
-   Statische Cursor sind integriert **Tempdb** beim Öffnen des Cursors. Diese zeigen immer des Resultsets vorlag, wenn der Cursor geöffnet wurde. Änderungen an den Daten werden nicht wiedergegeben. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : Statische Cursor sind immer schreibgeschützt. Da es sich bei ein statischen Servercursor als Arbeitstabelle in basiert **Tempdb**, die das Resultset des Cursors darf nicht größer als die zulässige maximale Zeilengröße [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   In einem keysetgesteuerten Cursor werden Mitgliedschaft und Reihenfolge der Zeilen beim Öffnen des Cursors festgelegt. Änderungen an Nichtschlüsselspalten sind durch den Cursor sichtbar.  
  
-   Dynamische Cursor sind das Gegenteil von statischen Cursorn. Dynamische Cursor spiegeln alle Änderungen an den Zeilen in den Resultsets wider. Die Datenwerte, Reihenfolge und Mitgliedschaft der Zeilen im Resultset können sich bei jedem Abrufvorgang ändern.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden von Cursorn &#40;ODBC&#41;](../../relational-databases/native-client-odbc-cursors/using-cursors-odbc.md)  
  
  
