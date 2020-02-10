---
title: Quellen-Editor für ODBC (Seite Verbindungs-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.odbcsource.connection.f1
ms.assetid: e2c8dc83-6394-4d6c-9232-97e94be72431
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: bea70ca9d5d511660ff19a84165a7fc7921b6de1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66057222"
---
# <a name="odbc-source-editor-connection-manager-page"></a>Quellen-Editor für ODBC (Seite Verbindungs-Manager)
  Auf der Seite **Verbindungs-Manager** des Dialogfelds **Quellen-Editor für ODBC** können Sie den ODBC-Verbindungs-Manager für die Quelle auswählen. Außerdem können Sie auf dieser Seite eine Tabelle oder Sicht aus der Datenbank auswählen.  
  
 Weitere Informationen zur ODBC-Quelle finden Sie unter [ODBC Source](data-flow/odbc-source.md).  
  
## <a name="task-list"></a>Aufgabenliste  
 **So öffnen Sie die Seite "Verbindungs-Manager" des Quellen-Editors für ODBC**  
  
-   Öffnen Sie in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]das [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] -Paket, das die ODBC-Quelle enthält.  
  
-   Doppelklicken Sie auf der Registerkarte **Datenfluss** auf die ODBC-Quelle.  
  
## <a name="options"></a>Tastatur  
  
### <a name="connection-manager"></a>Ziel-Editor für Dimensionsverarbeitung  
 Wählen Sie in der Liste einen vorhandenen ODBC-Verbindungs-Manager aus, oder klicken Sie auf **Neu** , um eine neue Verbindung zu erstellen. Sie können eine Verbindung mit jeder von ODBC unterstützten Datenbank erstellen.  
  
### <a name="new"></a>Neu  
 Klicken Sie auf **Neu**. Das Dialogfeld **ODBC-Verbindungs-Manager konfigurieren** , in dem Sie einen neuen ODBC-Verbindungs-Manager erstellen können, wird geöffnet.  
  
### <a name="data-access-mode"></a>Datenzugriffsmodus  
 Wählen Sie die Methode für die Auswahl von Daten aus der Quelle aus. Die Optionen sind in der folgenden Tabelle aufgeführt:  
  
|Option|BESCHREIBUNG|  
|------------|-----------------|  
|Tabellenname|Ruft Daten aus einer Tabelle oder Sicht in der ODBC-Datenquelle ab. Bei Auswahl dieser Option wählen Sie einen der folgenden Werte in der Liste aus:|  
||**Name der Tabelle oder Sicht**: Wählen Sie in der Liste eine verfügbare Tabelle oder Sicht aus, oder geben Sie einen regulären Ausdruck ein, um die Tabelle zu identifizieren.|  
||Diese Liste enthält nur die ersten 1000 Tabellen. Wenn die Datenbank mehr als 1000 Tabellen enthält, können Sie den Anfang eines Tabellennamens eingeben oder das Platzhalterzeichen (*) verwenden, um einen beliebigen Teil des Namens einzugeben und die gewünschten Tabellen anzuzeigen.|  
|SQL-Befehl|Ruft mit einer SQL-Abfrage Daten aus der ODBC-Datenquelle ab. Die Abfrage sollte in der Syntax der verwendeten Quelldatenbank geschrieben werden. Bei Auswahl dieser Option geben Sie anhand einer der folgenden Methoden eine Abfrage ein:|  
||Geben Sie den Text der SQL-Abfrage im Feld **SQL-Befehlstext** ein.|  
||Klicken Sie auf **Durchsuchen** , um die SQL-Abfrage aus einer Textdatei zu laden.|  
||Klicken Sie auf **Abfrage analysieren** , um die Syntax des Abfragetextes zu überprüfen.|  
  
### <a name="preview"></a>Vorschau  
 Klicken Sie auf **Vorschau** , um die ersten 200 Zeilen (max.) der Daten anzuzeigen, die aus der ausgewählten Tabelle bzw. Sicht extrahiert wurden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Benutzerdefinierte Eigenschaften der ODBC-Quelle](data-flow/odbc-source-custom-properties.md)   
 [Quellen-Editor für ODBC &#40;Seite „Spalten“&#41;](../../2014/integration-services/odbc-source-editor-columns-page.md)   
 [Quellen-Editor für ODBC &#40;Seite „Fehlerausgabe“&#41;](../../2014/integration-services/odbc-source-editor-error-output-page.md)  
  
  
