---
title: Fehler Konfiguration (Dialog Feld "Mining Struktur") (Analysis Services-Mehrdimensionale Daten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.miningstructuredialog.general.f1
ms.assetid: d9aa028b-bad9-49c7-a81c-c2150e4dd481
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e8973d9dd6fb5d96afc9cf66ded4b894f0dfe6df
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66081370"
---
# <a name="error-configuration-mining-structure-dialog-box-analysis-services---multidimensional-data"></a>Fehlerkonfiguration (Dialogfeld "Miningstruktur") (Analysis Services &ndash; Mehrdimensionale Daten)
  Auf der Seite **Fehlerkonfiguration** im Dialogfeld **Miningstruktureigenschaften** können Sie in **SQL Server Management Studio** die Eigenschaften der Fehlerkonfiguration einer Miningstruktur in einer [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank festlegen.  
  
## <a name="options"></a>Tastatur  
 **Standardfehler Konfiguration verwenden**  
 Aktivieren Sie diese Option, um für Objekte im Verarbeitungsvorgang die Standardfehlerkonfiguration zu verwenden.  
  
 **Schlüsselfehler Aktion**  
 Wählen Sie eine der folgenden Aktionen aus, die ausgeführt werden soll, wenn während der Verarbeitung ein neuer Schlüssel erkannt wird, der nicht ermittelt werden kann:  
  
-   In " **Unknown konvertieren** " aggregiert die Informationen für den Datensatz in das unbekannte Element.  
  
-   Der **Datensatz verwerfen** schließt die Informationen für den Datensatz von der Verarbeitung mit dem-Objekt aus.  
  
 **Fehler Anzahl ignorieren**  
 Klicken Sie hier, um bei der Verarbeitung auftretende Fehler grundsätzlich zu ignorieren.  
  
 **Bei Fehler abbrechen**  
 Klicken Sie hier, um die Verarbeitung bei Auftreten eines Fehlers zu beenden. Durch diese Option werden die Optionen **Anzahl von Fehlern** und **Aktion bei Fehler** aktiviert.  
  
 **Anzahl von Fehlern**  
 Geben Sie die Anzahl der Fehler ein, die ignoriert werden, bevor die Verarbeitung beendet wird.  
  
 **Aktion bei Fehler**  
 Wählen Sie eine der folgenden Aktionen aus, die ausgeführt wird, wenn die Anzahl der Fehler den in **Anzahl von Fehlern**angegebenen Wert überschreitet:  
  
-   Durch die **Verarbeitung beenden** wird der Verarbeitungsvorgang beendet.  
  
-   Wenn die **Protokollierung beendet** wird, werden Fehler protokolliert, der Verarbeitungsvorgang wird jedoch fortgesetzt  
  
 **Schlüssel nicht gefunden**  
 Geben Sie eine der folgenden Aktionen an, die ausgeführt wird, wenn ein Schlüssel bei der Verarbeitung eines Objekts nicht gefunden wird:  
  
-   **Fehler ignorieren** ignoriert den Fehler.  
  
-   **Bericht und Fortsetzung** meldet den Fehler und setzt den Verarbeitungsvorgang fort  
  
-   **Melden und beenden** meldet den Fehler und beendet den Verarbeitungsvorgang.  
  
 **Doppelter Schlüssel**  
 Geben Sie eine der folgenden Aktionen an, die ausgeführt wird, wenn bei der Verarbeitung eines Objekts ein doppelter Schlüssel gefunden wird:  
  
-   **Fehler ignorieren** ignoriert den Fehler.  
  
-   **Bericht und Fortsetzung** meldet den Fehler und setzt den Verarbeitungsvorgang fort  
  
-   **Melden und beenden** meldet den Fehler und beendet den Verarbeitungsvorgang.  
  
 **NULL-Schlüssel in unbekanntes konvertiert**  
 Geben Sie eine der folgenden Aktionen an, die ausgeführt wird, wenn dem unbekannten Element bei der Verarbeitung des Objekts ein Elementschlüssel NULL hinzugefügt wird.  
  
-   **Fehler ignorieren** ignoriert den Fehler.  
  
-   **Bericht und Fortsetzung** meldet den Fehler und setzt den Verarbeitungsvorgang fort  
  
-   **Melden und beenden** meldet den Fehler und beendet den Verarbeitungsvorgang.  
  
 **NULL-Schlüssel nicht zulässig**  
 Geben Sie eine der folgenden Aktionen an, die ausgeführt wird, wenn bei der Verarbeitung eines Objekts ein unzulässiger NULL-Schlüssel gefunden wird.  
  
-   **Fehler ignorieren** ignoriert den Fehler.  
  
-   **Bericht und Fortsetzung** meldet den Fehler und setzt den Verarbeitungsvorgang fort  
  
-   **Melden und beenden** meldet den Fehler und beendet den Verarbeitungsvorgang.  
  
 **Fehlerprotokoll Pfad**  
 Geben Sie den vollständigen Pfad und Dateinamen für die Fehlerprotokolldatei ein.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Mining Struktur Eigenschaften-Dialog &#40;Analysis Services-Data Mining-&#41;](mining-structure-properties-dialog-analysis-services-data-mining.md)   
 [Das Dialog Feld allgemeine &#40;Mining Struktur&#41; &#40;Analysis Services Data Mining-&#41;](general-mining-structure-dialog-box-analysis-services-data-mining.md)  
  
  
