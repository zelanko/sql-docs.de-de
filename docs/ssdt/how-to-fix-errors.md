---
title: 'Gewusst wie: Beheben von Fehlern | Microsoft-Dokumentation'
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0d504e00-4ff0-4fdf-b874-85280bbd8668
caps.latest.revision: 11
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f4984e28ae3397b6296f8d1a39a6d32474b27f9c
ms.sourcegitcommit: 2f07d285824a8982c279f3816b220e61a2d91b06
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/29/2018
ms.locfileid: "37094252"
---
# <a name="how-to-fix-errors"></a>Vorgehensweise: Beheben von Fehlern
Im Bereich "Fehlerliste" werden alle Bereitstellungs- und Buildfehler angezeigt. Wenn Sie Datenbankentitäten und ihre Definitionen bearbeiten, werden durch die Bearbeitung im Transact\-SQL-Editor oder Tabellen-Designer verursachte Syntax- und Semantikfehler ebenfalls in der Liste angezeigt. Die Fehlerliste wird dynamisch aktualisiert, wenn Sie Skripts auf unterschiedlichen Registerkarten bearbeiten. Sie können dann die identifizierten Fehler für die weitere Problembehandlung nachverfolgen.  
  
> [!WARNING]  
> Bei den folgenden Vorgehensweisen werden Entitäten verwendet, die in den Vorgehensweisen in den Abschnitten [Entwicklung verbundener Datenbanken](../ssdt/connected-database-development.md) und [Projektorientierte Entwicklung von Offlinedatenbanken](../ssdt/project-oriented-offline-database-development.md) erstellt wurden.  
  
### <a name="to-fix-errors"></a>So beheben Sie die Fehler  
  
1.  Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf die Tabelle **Product** (Product.sql), und wählen Sie **Sicht-Designer** aus.  
  
2.  Klicken Sie im Spaltenraster des Designers mit der rechten Maustaste auf die Spalte **ShelfLife**, und klicken Sie auf **Löschen**, um diese Spalte aus der Tabelle zu löschen.  
  
3.  Beachten Sie, dass im Bereich **Fehlerliste** am unteren Bildschirmrand sofort eine Warnung und ein Fehler mit folgendem Text angezeigt werden.  
  
**Warnung SQL71502: Funktion: [dbo].[GetProductsBySupplier] enthält einen nicht aufgelösten Verweis auf ein Objekt. Entweder ist das Objekt nicht vorhanden, oder der Verweis ist mehrdeutig, da er auf die folgenden Objekte verweisen könnte: [dbo].[Product].[p]::[ShelfLife] oder [dbo].[Product].[ShelfLife]. Fehler SQL71501: CHECK-Einschränkung: [dbo].[CK_Product_ShelfLife] enthält einen nicht aufgelösten Verweis auf das Objekt „[dbo].[Product].[ShelfLife]“.**  
  
4.  Sie können mit der rechten Maustaste auf die **Fehlerliste** klicken, um mit den Kontextmenüs die Ergebnisse zu sortieren und die anzuzeigenden Einträge sowie die Informationsspalten zu filtern, die für jeden Eintrag angezeigt werden sollen.  
  
    Doppelklicken Sie auf die erste identifizierte Warnung, und wechseln Sie zu der Skriptdatei, die die Warnung generiert hat. Der problematische Codeabschnitt wird hervorgehoben. In diesem Beispiel wird die Warnung erzeugt, weil in einer zuvor erstellten Tabellenwertfunktion die Spalte `ShelfLife` sowohl von der `RETURN`-Anweisung als auch von der `SELECT`-Anweisung verwendet wird.  
  
5.  Entfernen Sie im Transact\-SQL-Editor `ShelfLife` aus der Funktion.  
  
6.  Beheben Sie den zweiten Fehler auf die gleiche Weise, indem Sie die CHECK-Einschränkung entfernen.  
  
7.  Beachten Sie, dass sofort nach dem Beheben der Probleme die Warnung und der Fehler nicht mehr in der **Fehlerliste** angezeigt werden.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[Verwenden des Transact-SQL-Editors zum Bearbeiten und Ausführen von Skripts](../ssdt/use-transact-sql-editor-to-edit-and-execute-scripts.md)  
  
