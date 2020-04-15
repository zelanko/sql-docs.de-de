---
title: Importieren von Daten aus einer Visual FoxPro-Datenbank in Microsoft Excel | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- importing data [ODBC]
- FoxPro ODBC driver [ODBC], Excel
- Visual FoxPro data [ODBC], Excel
- Visual FoxPro data [ODBC], importing
- Visual FoxPro ODBC driver [ODBC], Excel
ms.assetid: 3085bc4c-00a7-40e5-bffb-c3962cd3d509
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1bfd86233e5a0a406febcb30bf7a4fae595e53d2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81287670"
---
# <a name="importing-data-into-microsoft-excel-from-a-visual-foxpro-database"></a>Importieren von Daten in Microsoft Excel aus einer Visual FoxPro-Datenbank
Sie können Visual FoxPro-Daten in Ihr Microsoft Excel-Arbeitsblatt importieren, wenn Sie eine Datenquelle dafür definiert haben. Informationen zum Erstellen einer Visual FoxPro-Datenquelle finden Sie [unter Zugriff auf eine Visual FoxPro-Datenquelle aus Microsoft Excel](../../odbc/microsoft/accessing-a-visual-foxpro-data-source-from-microsoft-excel.md).  
  
### <a name="to-import-visual-foxpro-data-into-an-microsoft-excel-worksheet"></a>So importieren Sie Visual FoxPro-Daten in ein Microsoft Excel-Arbeitsblatt  
  
1.  Öffnen Sie eine Microsoft Excel-Tabelle.  
  
2.  Wählen Sie im Menü Daten externe Daten abrufen aus. Microsoft Query wird geöffnet.  
  
3.  Wählen Sie im Dialogfeld Datenquelle auswählen eine Visual FoxPro-Datenquelle aus, und klicken Sie dann auf Verwenden.  
  
4.  Wenn die Datenbank, auf die von der Datenquelle zugegriffen wird, Tabellen enthält, wählen Sie im Dialogfeld Tabellen hinzufügen eine Tabelle aus. Microsoft Query zeigt die hinzugefügte Tabelle in der oberen Hälfte des Abfrage-Designers an.  
  
    > [!NOTE]  
    >  Die Besitzerliste ist in diesem Dialogfeld nicht verfügbar, da der Treiber keine Besitzer unterstützt. Die Datenbankliste ist nicht verfügbar, da der Treiber nicht mehrere Datenbanken in einer Datenquelle unterstützt.  
  
5.  Wählen Sie Felder für Ihre Abfrage aus, indem Sie sie aus der Tabelle in die untere Hälfte des Designers ziehen.  
  
6.  Schließen Sie Microsoft Query. Die ausgewählten Daten werden in Ihre Microsoft Excel-Tabelle importiert.
