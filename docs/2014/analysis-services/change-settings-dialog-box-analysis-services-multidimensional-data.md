---
title: Dialog Feld "Einstellungen ändern" (Analysis Services Mehrdimensionale Daten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.process.batchsettingsdialog.f1
ms.assetid: 0041e042-d7ce-48f9-a690-a6dc65471ff3
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 43dfc1dca2e60fe2f5e467556ee36c3add1a9da3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66088251"
---
# <a name="change-settings-dialog-box-analysis-services---multidimensional-data"></a>Dialogfeld 'Einstellungen ändern' (Analysis Services – Mehrdimensionale Daten)
  Mithilfe des in **und** bereitgestellten Dialogfelds [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] Einstellungen ändern [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] können Sie die Einstellungen ändern, mit denen die Verarbeitung der im Dialogfeld **Verarbeiten** aufgeführten Objekte gesteuert wird. Zum Anzeigen des Dialogfelds **Einstellungen ändern** klicken Sie im Dialogfeld **Verarbeiten** auf **Einstellungen ändern** .  
  
> [!NOTE]  
>  Mit den in diesem Dialogfeld angegebenen Einstellungen werden die Standardeinstellungen überschrieben, die von der [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank an die im Dialogfeld **Verarbeiten** aufgeführten Objekte vererbt wurden.  
  
## <a name="options"></a>Tastatur  
 **Verarbeitungsoptionen**  
 Auf dieser Registerkarte können Sie Einstellungen zu Verarbeitungsreihenfolge, Rückschreibetabelle und den vom Verarbeitungsvorgang betroffenen Objekten ändern. Die Registerkarte enthält die folgenden Optionen:  
  
 **Parallel**  
 Klicken Sie hier, um Objekte parallel zu verarbeiten.  
  
 **Maximal auszuführende parallele Tasks**  
 Wählen Sie die maximale Anzahl der Tasks aus, die vom Verarbeitungsvorgang parallel ausgeführt werden können, oder wählen Sie die Option **Entscheidung dem Server überlassen** aus, um die optimale Anzahl der parallel ausführbaren Tasks von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] bestimmen zu lassen.  
  
 **Sequenziell**  
 Klicken Sie hier, um die Objekte sequenziell zu verarbeiten.  
  
 **Transaktionsmodus**  
 Wählen Sie den Transaktionsmodus für die sequenzielle Verarbeitung von Objekten aus:  
  
-   **Eine Transaktion** verarbeitet alle Objekte in derselben Transaktion.  
  
-   Bei **separaten Transaktionen** werden alle Objekte, einschließlich abhängiger Objekte, in separaten Transaktionen verarbeitet.  
  
> [!NOTE]  
>  Diese Option ist nur aktiviert, wenn **Sequenziell** ausgewählt wird.  
  
 **Rück schreibe Tabellen Option**  
 Wählen Sie die Option zum Verwalten der Rückschreibetabelle aus.  
  
-   **Create** erstellt eine Rück schreibe Tabelle, wenn Sie nicht vorhanden ist. Wenn bereits eine Rückschreibetabelle vorhanden ist, wird ein Fehler gemeldet.  
  
-   **Create erstellt immer** eine Rück schreibe Tabelle, wenn Sie nicht vorhanden ist, oder überschreibt die vorhandene Rück schreibe Tabelle, wenn Sie vorhanden ist.  
  
-   **Vorhandene verwenden** verwendet die vorhandene Rück schreibe Tabelle, sofern vorhanden. Wenn keine Rückschreibetabelle vorhanden ist, wird ein Fehler gemeldet.  
  
 **Betroffene Objekte verarbeiten**  
 Aktivieren Sie diese Option, um Objekte aufzunehmen und zu verarbeiten, die von Objekten im Verarbeitungsvorgang abhängig sind.  
  
 **Dimensions Schlüsselfehler**  
 Auf dieser Registerkarte können Sie Einstellungen zur Fehlerkonfiguration ändern, die für den Verarbeitungsvorgang verwendet wird. Die Registerkarte enthält die folgenden Optionen:  
  
 **Standardfehler Konfiguration verwenden**  
 Aktivieren Sie diese Option, um für Objekte im Verarbeitungsvorgang die Standardfehlerkonfiguration zu verwenden.  
  
 **Benutzerdefinierte Fehlerkonfiguration verwenden**  
 Aktivieren Sie diese Option, um für Objekte im Verarbeitungsvorgang die Fehlerkonfiguration zu definieren.  
  
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
  
-   **Melden und Fortfahren** meldet den Fehler und setzt den Verarbeitungsvorgang fort.  
  
-   **Melden und beenden** meldet den Fehler und beendet den Verarbeitungsvorgang.  
  
 **Doppelter Schlüssel**  
 Geben Sie eine der folgenden Aktionen an, die ausgeführt wird, wenn bei der Verarbeitung eines Objekts ein doppelter Schlüssel gefunden wird:  
  
-   **Fehler ignorieren** ignoriert den Fehler.  
  
-   **Melden und Fortfahren** meldet den Fehler und setzt den Verarbeitungsvorgang fort.  
  
-   **Melden und beenden** meldet den Fehler und beendet den Verarbeitungsvorgang.  
  
 **NULL-Schlüssel in unbekanntes konvertiert**  
 Geben Sie eine der folgenden Aktionen an, die ausgeführt wird, wenn dem unbekannten Element bei der Verarbeitung des Objekts ein Elementschlüssel NULL hinzugefügt wird:  
  
-   **Fehler ignorieren** ignoriert den Fehler.  
  
-   **Melden und Fortfahren** meldet den Fehler und setzt den Verarbeitungsvorgang fort.  
  
-   **Melden und beenden** meldet den Fehler und beendet den Verarbeitungsvorgang.  
  
 **NULL-Schlüssel nicht zulässig**  
 Geben Sie eine der folgenden Aktionen an, die ausgeführt wird, wenn bei der Verarbeitung eines Objekts ein unzulässiger NULL-Schlüssel gefunden wird:  
  
-   **Fehler ignorieren** ignoriert den Fehler.  
  
-   **Melden und Fortfahren** meldet den Fehler und setzt den Verarbeitungsvorgang fort.  
  
-   **Melden und beenden** meldet den Fehler und beendet den Verarbeitungsvorgang.  
  
 **Fehlerprotokoll Pfad**  
 Geben Sie den vollständigen Pfad und Dateinamen für die Fehlerprotokolldatei ein.  
  
 **Durchsuchen**  
 Klicken Sie hier, um das Dialogfeld **Öffnen** zu öffnen und dort den vollständigen Pfad und Dateinamen der Fehlerprotokolldatei auszuwählen.  
  
 **Betroffene Objekte verarbeiten**  
 Klicken Sie hier, um die Objekte zu verarbeiten, die eine Abhängigkeit von den im Dialogfeld **Verarbeiten** ausgewählten Objekten aufweisen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Analysis Services Designer und Dialog Felder &#40;Mehrdimensionale Daten&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Verarbeiten (Dialog Feld) &#40;Analysis Services-mehrdimensionalen Daten&#41;](process-dialog-box-analysis-services-multidimensional-data.md)  
  
  
