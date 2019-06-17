---
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: de81b606d31514cf6e7a518deeb68794d1011132
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63127286"
---
# <a name="importing-data-into-microsoft-excel-from-a-visual-foxpro-database"></a>Importieren von Daten in Microsoft Excel aus einer Visual FoxPro-Datenbank
Sie können Visual FoxPro-Daten in Microsoft Excel-Arbeitsblatt importieren, wenn Sie eine Datenquelle für sie definiert haben. Weitere Informationen zum Erstellen einer Visual FoxPro-Datenquelle, finden Sie unter [den Zugriff auf einer Visual FoxPro-Datenquelle aus Microsoft Excel](../../odbc/microsoft/accessing-a-visual-foxpro-data-source-from-microsoft-excel.md).  
  
### <a name="to-import-visual-foxpro-data-into-an-microsoft-excel-worksheet"></a>Visual FoxPro-Daten in einer Microsoft Excel-Arbeitsblatt importieren  
  
1.  Öffnen Sie Microsoft Excel-Arbeitsblatt ein.  
  
2.  Wählen Sie aus dem Menü "Daten" Externe Daten abrufen. Microsoft Query wird geöffnet.  
  
3.  Klicken Sie im Dialogfeld "Datenquelle auswählen" Wählen Sie eine Visual FoxPro-Datenquelle, und klicken Sie dann auf verwenden.  
  
4.  Wenn die Datenbank zugegriffen werden, indem Sie die Datenquelle Tabellen enthält, wählen Sie eine Tabelle im Dialogfeld Tabellen hinzufügen. Microsoft Query hinzugefügte Tabelle in der oberen Hälfte des Abfrage-Designers angezeigt.  
  
    > [!NOTE]  
    >  Die Liste der Besitzer ist nicht in diesem Dialogfeld verfügbar, da der Treiber Besitzer nicht unterstützt. Die Datenbankliste ist nicht verfügbar, da der Treiber nicht über mehrere Datenbanken in einer Datenquelle unterstützt.  
  
5.  Wählen Sie Felder für die Abfrage durch Ziehen aus der Tabelle auf der unteren Hälfte des Designers.  
  
6.  Schließen Sie Microsoft-Abfrage. Die Daten, die Sie ausgewählt haben, werden in der Microsoft Excel-Tabelle importiert.
