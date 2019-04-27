---
title: Ändern von Einstellungen (Dialogfeld) (Analysis Services – mehrdimensionale Daten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.process.batchsettingsdialog.f1
ms.assetid: 0041e042-d7ce-48f9-a690-a6dc65471ff3
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e549e9b4121d116adc627c34dad017b85099a825
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62681167"
---
# <a name="change-settings-dialog-box-analysis-services---multidimensional-data"></a>Dialogfeld 'Einstellungen ändern' (Analysis Services – Mehrdimensionale Daten)
  Mithilfe des in **und** bereitgestellten Dialogfelds [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] Einstellungen ändern [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] können Sie die Einstellungen ändern, mit denen die Verarbeitung der im Dialogfeld **Verarbeiten** aufgeführten Objekte gesteuert wird. Zum Anzeigen des Dialogfelds **Einstellungen ändern** klicken Sie im Dialogfeld **Verarbeiten** auf **Einstellungen ändern** .  
  
> [!NOTE]  
>  Mit den in diesem Dialogfeld angegebenen Einstellungen werden die Standardeinstellungen überschrieben, die von der [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank an die im Dialogfeld **Verarbeiten** aufgeführten Objekte vererbt wurden.  
  
## <a name="options"></a>Optionen  
 **Verarbeitungsoptionen**  
 Auf dieser Registerkarte können Sie Einstellungen zu Verarbeitungsreihenfolge, Rückschreibetabelle und den vom Verarbeitungsvorgang betroffenen Objekten ändern. Die Registerkarte enthält die folgenden Optionen:  
  
 **Parallel**  
 Klicken Sie hier, um Objekte parallel zu verarbeiten.  
  
 **Maximal auszuführende parallele tasks**  
 Wählen Sie die maximale Anzahl der Tasks aus, die vom Verarbeitungsvorgang parallel ausgeführt werden können, oder wählen Sie die Option **Entscheidung dem Server überlassen** aus, um die optimale Anzahl der parallel ausführbaren Tasks von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] bestimmen zu lassen.  
  
 **Sequential**  
 Klicken Sie hier, um die Objekte sequenziell zu verarbeiten.  
  
 **Transaktionsmodus**  
 Wählen Sie den Transaktionsmodus für die sequenzielle Verarbeitung von Objekten aus:  
  
-   Bei Auswahl von**Eine Transaktion** werden alle Objekte in ein und derselben Transaktion verarbeitet.  
  
-   Bei Auswahl von**Separate Transaktionen** werden alle Objekte, einschließlich abhängiger Objekte, in separaten Transaktionen verarbeitet.  
  
> [!NOTE]  
>  Diese Option ist nur aktiviert, wenn **Sequenziell** ausgewählt wird.  
  
 **Rückschreibetabelle (Option)**  
 Wählen Sie die Option zum Verwalten der Rückschreibetabelle aus.  
  
-   Mit**Erstellen** wird eine Rückschreibetabelle erstellt, sofern noch keine vorhanden ist. Wenn bereits eine Rückschreibetabelle vorhanden ist, wird ein Fehler gemeldet.  
  
-   Mit**Immer erstellen** wird eine Rückschreibetabelle erstellt, sofern noch keine vorhanden ist. Eine bereits vorhandene Rückschreibetabelle wird dabei überschrieben.  
  
-   Bei**Vorhandene verwenden** wird eine bereits vorhandene Rückschreibetabelle verwendet. Wenn keine Rückschreibetabelle vorhanden ist, wird ein Fehler gemeldet.  
  
 **Betroffene Objekte verarbeiten**  
 Aktivieren Sie diese Option, um Objekte aufzunehmen und zu verarbeiten, die von Objekten im Verarbeitungsvorgang abhängig sind.  
  
 **Dimensionsschlüsselfehler**  
 Auf dieser Registerkarte können Sie Einstellungen zur Fehlerkonfiguration ändern, die für den Verarbeitungsvorgang verwendet wird. Die Registerkarte enthält die folgenden Optionen:  
  
 **Standardfehlerkonfiguration verwenden**  
 Aktivieren Sie diese Option, um für Objekte im Verarbeitungsvorgang die Standardfehlerkonfiguration zu verwenden.  
  
 **Benutzerdefinierte Fehlerkonfiguration verwenden**  
 Aktivieren Sie diese Option, um für Objekte im Verarbeitungsvorgang die Fehlerkonfiguration zu definieren.  
  
 **Schlüsselfehleraktion**  
 Wählen Sie eine der folgenden Aktionen aus, die ausgeführt werden soll, wenn während der Verarbeitung ein neuer Schlüssel erkannt wird, der nicht ermittelt werden kann:  
  
-   Mit**In unbekanntes Element konvertieren** werden die Informationen für den Datensatz im unbekannten Element zusammengesetzt.  
  
-   Mit**Datensatz verwerfen** werden die Informationen für den Datensatz von der Verarbeitung mit dem Objekt ausgeschlossen.  
  
 **Fehleranzahl ignorieren**  
 Klicken Sie hier, um bei der Verarbeitung auftretende Fehler grundsätzlich zu ignorieren.  
  
 **Bei Fehler beenden**  
 Klicken Sie hier, um die Verarbeitung bei Auftreten eines Fehlers zu beenden. Durch diese Option werden die Optionen **Anzahl von Fehlern** und **Aktion bei Fehler** aktiviert.  
  
 **Anzahl von Fehlern**  
 Geben Sie die Anzahl der Fehler ein, die ignoriert werden, bevor die Verarbeitung beendet wird.  
  
 **Aktion bei Fehler**  
 Wählen Sie eine der folgenden Aktionen aus, die ausgeführt wird, wenn die Anzahl der Fehler den in **Anzahl von Fehlern**angegebenen Wert überschreitet:  
  
-   Mit**Verarbeitung beenden** wird der Verarbeitungsvorgang beendet.  
  
-   Mit**Protokollierung beenden** werden Protokollierungsfehler beendet, während der Verarbeitungsvorgang weiter ausgeführt wird.  
  
 **Schlüssel nicht gefunden**  
 Geben Sie eine der folgenden Aktionen an, die ausgeführt wird, wenn ein Schlüssel bei der Verarbeitung eines Objekts nicht gefunden wird:  
  
-   Mit**Fehler ignorieren** wird der Fehler ignoriert.  
  
-   Mit**Melden und Vorgang fortsetzen** wird der Fehler gemeldet und der Verarbeitungsvorgang fortgesetzt.  
  
-   Mit**Melden und Vorgang beenden** wird der Fehler gemeldet und der Verarbeitungsvorgang beendet.  
  
 **Doppelter Schlüssel**  
 Geben Sie eine der folgenden Aktionen an, die ausgeführt wird, wenn bei der Verarbeitung eines Objekts ein doppelter Schlüssel gefunden wird:  
  
-   Mit**Fehler ignorieren** wird der Fehler ignoriert.  
  
-   Mit**Melden und Vorgang fortsetzen** wird der Fehler gemeldet und der Verarbeitungsvorgang fortgesetzt.  
  
-   Mit**Melden und Vorgang beenden** wird der Fehler gemeldet und der Verarbeitungsvorgang beendet.  
  
 **NULL-Schlüssel in unbekanntes Element konvertiert**  
 Geben Sie eine der folgenden Aktionen an, die ausgeführt wird, wenn dem unbekannten Element bei der Verarbeitung des Objekts ein Elementschlüssel NULL hinzugefügt wird:  
  
-   Mit**Fehler ignorieren** wird der Fehler ignoriert.  
  
-   Mit**Melden und Vorgang fortsetzen** wird der Fehler gemeldet und der Verarbeitungsvorgang fortgesetzt.  
  
-   Mit**Melden und Vorgang beenden** wird der Fehler gemeldet und der Verarbeitungsvorgang beendet.  
  
 **NULL-Schlüssel nicht zulässig**  
 Geben Sie eine der folgenden Aktionen an, die ausgeführt wird, wenn bei der Verarbeitung eines Objekts ein unzulässiger NULL-Schlüssel gefunden wird:  
  
-   Mit**Fehler ignorieren** wird der Fehler ignoriert.  
  
-   Mit**Melden und Vorgang fortsetzen** wird der Fehler gemeldet und der Verarbeitungsvorgang fortgesetzt.  
  
-   Mit**Melden und Vorgang beenden** wird der Fehler gemeldet und der Verarbeitungsvorgang beendet.  
  
 **Fehlerprotokollpfad**  
 Geben Sie den vollständigen Pfad und Dateinamen für die Fehlerprotokolldatei ein.  
  
 **Durchsuchen**  
 Klicken Sie hier, um das Dialogfeld **Öffnen** zu öffnen und dort den vollständigen Pfad und Dateinamen der Fehlerprotokolldatei auszuwählen.  
  
 **Betroffene Objekte verarbeiten**  
 Klicken Sie hier, um die Objekte zu verarbeiten, die eine Abhängigkeit von den im Dialogfeld **Verarbeiten** ausgewählten Objekten aufweisen.  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services-Designer und-Dialogfelder &#40;mehrdimensionale Daten&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Verarbeiten Sie das Dialogfeld &#40;Analysis Services – mehrdimensionale Daten&#41;](process-dialog-box-analysis-services-multidimensional-data.md)  
  
  
