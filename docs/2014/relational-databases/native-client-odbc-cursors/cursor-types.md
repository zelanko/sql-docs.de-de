---
title: Cursor Typen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, cursors
- ODBC applications, cursors
- cursors [ODBC], types
- ODBC cursors, types
ms.assetid: 3a916cc7-f352-42cb-8b83-f78e06cef991
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6d88b48c1fc4166b32821da9cdaaa5eb7f6c2e60
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63070999"
---
# <a name="cursor-types"></a>Cursortypen
  ODBC definiert vier Cursor Typen, die von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Microsoft und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dem Native Client-ODBC-Treiber unterstützt werden. Diese Cursor unterscheiden sich in ihrer Fähigkeit, Änderungen am Resultset und in den von Ihnen genutzten Ressourcen zu erkennen, wie z. b. Arbeitsspeicher und Speicherplatz in **tempdb**. Ein Cursor kann Änderungen an Zeilen nur dann erkennen, wenn er versucht, diese Zeilen erneut abzurufen. Es gibt keine Möglichkeit, wie die Datenquelle den Cursor über Änderungen an den derzeit abgerufenen Zeilen informieren könnte. Die Fähigkeit eines Cursors, Änderungen, die nicht durch den Cursor vorgenommen wurden, zu erkennen, hängt außerdem von der Transaktionsisolationsstufe ab.  
  
 Die vier von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützten ODBC-Cursortypen sind:  
  
-   Vorwärtscursor unterstützen keine Bildläufe, sondern ausschließlich das serielle Abrufen von Zeilen vom Anfang bis zum Ende des Cursors.  
  
-   Statische Cursor werden in **tempdb** erstellt, wenn der Cursor geöffnet wird. Das Resultset wird immer angezeigt, wenn der Cursor geöffnet wurde. Änderungen an den Daten werden nicht wiedergegeben. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : Statische Cursor sind immer schreibgeschützt. Da ein statischer Server Cursor als Arbeits Tabelle in **tempdb**erstellt wird, darf die Größe des Cursorresultsets die maximale Zeilengröße nicht über [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]schreiten, die von zulässig ist.  
  
-   In einem keysetgesteuerten Cursor werden Mitgliedschaft und Reihenfolge der Zeilen beim Öffnen des Cursors festgelegt. Änderungen an Nichtschlüsselspalten sind durch den Cursor sichtbar.  
  
-   Dynamische Cursor sind das Gegenteil von statischen Cursorn. Dynamische Cursor spiegeln alle Änderungen an den Zeilen in den Resultsets wider. Die Datenwerte, Reihenfolge und Mitgliedschaft der Zeilen im Resultset können sich bei jedem Abrufvorgang ändern.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwenden von Cursorn &#40;ODBC-&#41;](using-cursors-odbc.md)  
  
  
