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
ms.openlocfilehash: ef6ba1926d23990399be8571ed117b87dd2edb8b
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2020
ms.locfileid: "84528383"
---
# <a name="error-configuration-mining-structure-dialog-box-analysis-services---multidimensional-data"></a>Fehlerkonfiguration (Dialogfeld "Miningstruktur") (Analysis Services &ndash; Mehrdimensionale Daten)
  Auf der Seite **Fehlerkonfiguration** im Dialogfeld **Miningstruktureigenschaften** können Sie in **SQL Server Management Studio** die Eigenschaften der Fehlerkonfiguration einer Miningstruktur in einer [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank festlegen.  
  
## <a name="options"></a>Optionen  
 **Standardfehler Konfiguration verwenden**  
 Aktivieren Sie diese Option, um für Objekte im Verarbeitungsvorgang die Standardfehlerkonfiguration zu verwenden.  
  
 **Schlüsselfehler Aktion**  
 Wählen Sie eine der folgenden Aktionen aus, die ausgeführt werden soll, wenn während der Verarbeitung ein neuer Schlüssel erkannt wird, der nicht ermittelt werden kann:  
  
-   Mit**In unbekanntes Element konvertieren** werden die Informationen für den Datensatz im unbekannten Element zusammengesetzt.  
  
-   Mit**Datensatz verwerfen** werden die Informationen für den Datensatz von der Verarbeitung mit dem Objekt ausgeschlossen.  
  
 **Fehler Anzahl ignorieren**  
 Klicken Sie hier, um bei der Verarbeitung auftretende Fehler grundsätzlich zu ignorieren.  
  
 **Bei Fehler abbrechen**  
 Klicken Sie hier, um die Verarbeitung bei Auftreten eines Fehlers zu beenden. Durch diese Option werden die Optionen **Anzahl von Fehlern** und **Aktion bei Fehler** aktiviert.  
  
 **Anzahl von Fehlern**  
 Geben Sie die Anzahl der Fehler ein, die ignoriert werden, bevor die Verarbeitung beendet wird.  
  
 **Aktion bei Fehler**  
 Wählen Sie eine der folgenden Aktionen aus, die ausgeführt wird, wenn die Anzahl der Fehler den in **Anzahl von Fehlern**angegebenen Wert überschreitet:  
  
-   Mit**Verarbeitung beenden** wird der Verarbeitungsvorgang beendet.  
  
-   Mit**Protokollierung beenden** werden Protokollierungsfehler beendet, während der Verarbeitungsvorgang weiter ausgeführt wird.  
  
 **Schlüssel nicht gefunden**  
 Geben Sie eine der folgenden Aktionen an, die ausgeführt wird, wenn ein Schlüssel bei der Verarbeitung eines Objekts nicht gefunden wird:  
  
-   **Fehler ignorieren** ignoriert den Fehler.  
  
-   Mit**Melden und Vorgang fortsetzen** wird der Fehler gemeldet und der Verarbeitungsvorgang fortgesetzt.  
  
-   Mit**Melden und Vorgang beenden** wird der Fehler gemeldet und der Verarbeitungsvorgang beendet.  
  
 **Doppelter Schlüssel**  
 Geben Sie eine der folgenden Aktionen an, die ausgeführt wird, wenn bei der Verarbeitung eines Objekts ein doppelter Schlüssel gefunden wird:  
  
-   **Fehler ignorieren** ignoriert den Fehler.  
  
-   Mit**Melden und Vorgang fortsetzen** wird der Fehler gemeldet und der Verarbeitungsvorgang fortgesetzt.  
  
-   Mit**Melden und Vorgang beenden** wird der Fehler gemeldet und der Verarbeitungsvorgang beendet.  
  
 **NULL-Schlüssel in unbekanntes konvertiert**  
 Geben Sie eine der folgenden Aktionen an, die ausgeführt wird, wenn dem unbekannten Element bei der Verarbeitung des Objekts ein Elementschlüssel NULL hinzugefügt wird.  
  
-   **Fehler ignorieren** ignoriert den Fehler.  
  
-   Mit**Melden und Vorgang fortsetzen** wird der Fehler gemeldet und der Verarbeitungsvorgang fortgesetzt.  
  
-   Mit**Melden und Vorgang beenden** wird der Fehler gemeldet und der Verarbeitungsvorgang beendet.  
  
 **NULL-Schlüssel nicht zulässig**  
 Geben Sie eine der folgenden Aktionen an, die ausgeführt wird, wenn bei der Verarbeitung eines Objekts ein unzulässiger NULL-Schlüssel gefunden wird.  
  
-   **Fehler ignorieren** ignoriert den Fehler.  
  
-   Mit**Melden und Vorgang fortsetzen** wird der Fehler gemeldet und der Verarbeitungsvorgang fortgesetzt.  
  
-   Mit**Melden und Vorgang beenden** wird der Fehler gemeldet und der Verarbeitungsvorgang beendet.  
  
 **Fehlerprotokollpfad**  
 Geben Sie den vollständigen Pfad und Dateinamen für die Fehlerprotokolldatei ein.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Mining Struktur Eigenschaften-Dialog &#40;Analysis Services-Data Mining-&#41;](mining-structure-properties-dialog-analysis-services-data-mining.md)   
 [Das Dialog Feld allgemeine &#40;Mining Struktur&#41; &#40;Analysis Services Data Mining-&#41;](general-mining-structure-dialog-box-analysis-services-data-mining.md)  
  
  
