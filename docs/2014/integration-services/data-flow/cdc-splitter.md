---
title: CDC-Splitter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.cdcsplitter.f1
ms.assetid: 167bc5c6-fa36-439d-987c-b20acd1a77e2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 290cc29a8bdf4ebb3a7b8cd0e4d2c3c11610987a
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85432357"
---
# <a name="cdc-splitter"></a>CDC-Splitter
  Der CDC-Splitter teilt einen einzelnen Fluss von Änderungszeilen aus einem CDC-Quelldatenfluss in unterschiedliche Datenflüsse für Einfüge-, Update und Löschvorgänge auf. Der Datenfluss wird basierend auf der erforderlichen Spalte `__$operation` und seinen Standardwerten in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Änderungstabellen geteilt.  
  
|Wert des Vorgangs|Output|BESCHREIBUNG|  
|------------------------|------------|-----------------|  
|1|Löschen|Gelöschte Zeile|  
|2|Einfügen|Eingefügte Zeile (nicht verfügbar bei Verwendung des CDC-Modus **Net with merge** )|  
|3|Aktualisieren|Zeile vor Update (nur bei Verwendung des CDC-Modus **All with Old Values** verfügbar)|  
|4|Aktualisieren|Zeile nach Update (folgt auf die Zeile vor Update)|  
|5|Aktualisieren|Mergezeile (nur bei Verwendung des CDC-Modus **Net with merge** verfügbar)|  
|Andere|Fehler||  
  
 Sie können den Splitter verwenden, um vordefinierte INSERT-, DELETE- und UPDATE-Ausgaben zur weiteren Verarbeitung zu verbinden.  
  
 Die CDC-Splittertransformation weist eine normale Eingabe und eine Fehlerausgabe auf.  
  
## <a name="error-handling"></a>Fehlerbehandlung  
 Die CDC-Splittertransformation weist eine Fehlerausgabe auf. Eingabezeilen mit einem ungültigen Wert für die Spalte $operation werden als fehlerhaft angesehen und gemäß der **ErrorRowDisposition** -Eigenschaft der Eingabe behandelt.  
  
 Die Komponentenfehlerausgabe enthält die folgenden Ausgabespalten:  
  
-   **Fehlercode**: Auf 1 festgelegt.  
  
-   **Fehlerspalte**: Die Quellspalte, die den Fehler verursacht (für Konvertierungsfehler).  
  
-   **Fehlerzeilenspalten**: Die Eingabespalten der Zeile, die den Fehler verursacht hat.  
  
## <a name="configuring-the-cdc-splitter"></a>Konfigurieren des CDC-Splitters  
 Für den CDC-Splitter sind keine konfigurierbaren Eigenschaften vorhanden.  
  
 Weitere Informationen zur Verwendung des CDC-Splitters finden Sie unter CDC-Komponenten für Microsoft SQL Server Integration Services.  
  
 Das Dialogfeld **Erweiterter Editor** enthält die Eigenschaften, die programmgesteuert festgelegt werden können.  
  
 So öffnen Sie das Dialogfeld **Erweiterter Editor** :  
  
-   Klicken Sie auf dem Bildschirm **Datenfluss** des [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] -Projekts mit der rechten Maustaste auf den CDC-Splitter, und wählen Sie **Erweiterten Editor anzeigen**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Weiterleiten des CDC-Datenstroms gemäß Änderungstyp](direct-the-cdc-stream-according-to-the-type-of-change.md)  
  
  
