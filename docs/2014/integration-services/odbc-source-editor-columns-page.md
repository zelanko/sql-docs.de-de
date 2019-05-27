---
title: Quellen-Editor für ODBC (Spaltenseite) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.odbcsource.columns.f1
ms.assetid: 565984eb-8318-4be7-bebc-262209cf5065
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 5bfda61e5a57dabd62289f32d04d6367695b070b
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66057170"
---
# <a name="odbc-source-editor-columns-page"></a>Quellen-Editor für ODBC (Seite Spalten)
  Auf der Seite **Spalten** des Dialogfelds **Quellen-Editor für ODBC** können Sie jeder externen Spalte (Quellspalte) eine Ausgabespalte zuordnen.  
  
 Weitere Informationen zur ODBC-Quelle finden Sie unter [ODBC Source](data-flow/odbc-source.md).  
  
## <a name="task-list"></a>Aufgabenliste  
 **So öffnen Sie die Seite "Spalten" des Quellen-Editors für ODBC**  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]das [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] -Paket, das die ODBC-Quelle enthält.  
  
2.  Doppelklicken Sie auf der Registerkarte **Datenfluss** auf die ODBC-Quelle.  
  
3.  Klicken Sie im **Quellen-Editor für ODBC**auf **Spalten**.  
  
## <a name="options"></a>Optionen  
  
### <a name="available-external-columns"></a>Verfügbare externe Spalten  
 Eine Liste der in der Datenquelle verfügbaren externen Spalten. Mit der Tabelle können keine Spalten hinzugefügt oder gelöscht werden. Wählen Sie die zu verwendenden Spalten aus der Datenquelle aus. Die ausgewählten Spalten werden der Liste **Externe Spalte** in der Reihenfolge hinzugefügt, in der Sie sie auswählen.  
  
 Aktivieren Sie das Kontrollkästchen **Alle auswählen** , um alle Spalten auszuwählen.  
  
### <a name="external-column"></a>Externe Spalte  
 Eine Ansicht der externen Spalten (Quellspalten) in der Reihenfolge, in der sie angezeigt werden, wenn Sie Komponenten konfigurieren, die Daten aus dieser Quelle verwenden.  
  
### <a name="output-column"></a>Ausgabespalte  
 Geben Sie für jede Ausgabespalte einen eindeutigen Namen ein. Standardmäßig wird der Name der ausgewählten externen (Quell-)Spalte verwendet. Sie können jedoch auch einen beschreibenden Namen angeben, sofern dieser eindeutig ist. Der eingegebene Name wird im SSIS-Designer angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 [Quellen-Editor für ODBC &#40;Seite „Verbindungs-Manager“&#41;](../../2014/integration-services/odbc-source-editor-connection-manager-page.md)   
 [Quellen-Editor für ODBC &#40;Seite „Fehlerausgabe“&#41;](../../2014/integration-services/odbc-source-editor-error-output-page.md)  
  
  
