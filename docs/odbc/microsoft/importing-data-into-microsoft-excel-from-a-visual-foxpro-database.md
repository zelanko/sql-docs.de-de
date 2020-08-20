---
description: Importieren von Daten in Microsoft Excel aus einer Visual FoxPro-Datenbank
title: Importieren von Daten in Microsoft Excel aus einer Visual FoxPro-Datenbank | Microsoft-Dokumentation
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
ms.openlocfilehash: 9a4bd1cf7983ed0a552de4f9d0f491960b48f0d7
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88500293"
---
# <a name="importing-data-into-microsoft-excel-from-a-visual-foxpro-database"></a>Importieren von Daten in Microsoft Excel aus einer Visual FoxPro-Datenbank
Sie können Visual FoxPro-Daten in das Microsoft Excel-Arbeitsblatt importieren, wenn Sie eine Datenquelle dafür definiert haben. Weitere Informationen zum Erstellen einer Visual FoxPro-Datenquelle finden Sie unter [zugreifen auf eine Visual FoxPro-Datenquelle aus Microsoft Excel](../../odbc/microsoft/accessing-a-visual-foxpro-data-source-from-microsoft-excel.md).  
  
### <a name="to-import-visual-foxpro-data-into-an-microsoft-excel-worksheet"></a>So importieren Sie Visual FoxPro-Daten in ein Microsoft Excel-Arbeitsblatt  
  
1.  Öffnen Sie eine Microsoft Excel-Tabelle.  
  
2.  Wählen Sie im Menü Daten die Option externe Daten erhalten aus. Microsoft-Abfrage wird geöffnet.  
  
3.  Wählen Sie im Dialogfeld Datenquelle auswählen eine Visual FoxPro-Datenquelle aus, und klicken Sie dann auf verwenden.  
  
4.  Wenn die Datenbank, auf die von der Datenquelle zugegriffen wird, Tabellen enthält, wählen Sie im Dialogfeld Tabellen hinzufügen eine Tabelle aus. Microsoft Query zeigt die hinzugefügte Tabelle in der oberen Hälfte des Abfrage-Designers an.  
  
    > [!NOTE]  
    >  Die Liste der Besitzer ist in diesem Dialogfeld nicht verfügbar, da der Treiber keine Besitzer unterstützt. Die Daten Bank Liste ist nicht verfügbar, da der Treiber nicht mehrere Datenbanken in einer Datenquelle unterstützt.  
  
5.  Wählen Sie Felder für die Abfrage aus, indem Sie Sie aus der Tabelle in die untere Hälfte des Designers ziehen.  
  
6.  Schließen Sie Microsoft Query. Die Daten, die Sie ausgewählt haben, werden in das Microsoft Excel-Arbeitsblatt importiert.
