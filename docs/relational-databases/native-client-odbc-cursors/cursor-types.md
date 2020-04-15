---
title: Cursortypen | Microsoft Docs
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
ms.openlocfilehash: 4782c61c2f150e36c9632d09170468229c238cbb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305463"
---
# <a name="cursor-types"></a>Cursortypen
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  ODBC definiert vier Cursortypen, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von Microsoft und dem Native Client ODBC-Treiber unterstützt werden. Diese Cursor unterscheiden sich in ihrer Fähigkeit, Änderungen am Resultset und an den Ressourcen, die sie verbrauchen, wie Z. B. Arbeitsspeicher und Speicherplatz in **tempdb**, zu erkennen. Ein Cursor kann Änderungen an Zeilen nur dann erkennen, wenn er versucht, diese Zeilen erneut abzurufen. Es gibt keine Möglichkeit, wie die Datenquelle den Cursor über Änderungen an den derzeit abgerufenen Zeilen informieren könnte. Die Fähigkeit eines Cursors, Änderungen, die nicht durch den Cursor vorgenommen wurden, zu erkennen, hängt außerdem von der Transaktionsisolationsstufe ab.  
  
 Die vier von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützten ODBC-Cursortypen sind:  
  
-   Vorwärtscursor unterstützen keine Bildläufe, sondern ausschließlich das serielle Abrufen von Zeilen vom Anfang bis zum Ende des Cursors.  
  
-   Statische Cursor werden in **tempdb** erstellt, wenn der Cursor geöffnet wird. Sie zeigen das Resultset immer so an, wie es war, als der Cursor geöffnet wurde. Änderungen an den Daten werden nicht wiedergegeben. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : Statische Cursor sind immer schreibgeschützt. Da ein statischer Servercursor als Arbeitstabelle in **tempdb**erstellt wird, darf die Größe [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]des Cursorresultsets die von zulässige maximale Zeilengröße nicht überschreiten.  
  
-   In einem keysetgesteuerten Cursor werden Mitgliedschaft und Reihenfolge der Zeilen beim Öffnen des Cursors festgelegt. Änderungen an Nichtschlüsselspalten sind durch den Cursor sichtbar.  
  
-   Dynamische Cursor sind das Gegenteil von statischen Cursorn. Dynamische Cursor spiegeln alle Änderungen an den Zeilen in den Resultsets wider. Die Datenwerte, Reihenfolge und Mitgliedschaft der Zeilen im Resultset können sich bei jedem Abrufvorgang ändern.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwenden von Cursorn &#40;ODBC-&#41;](../../relational-databases/native-client-odbc-cursors/using-cursors-odbc.md)  
  
  
