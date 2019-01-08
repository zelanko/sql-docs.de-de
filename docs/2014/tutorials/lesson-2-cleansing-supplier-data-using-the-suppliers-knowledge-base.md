---
title: "Lektion 2: Bereinigung von Lieferantendaten mithilfe der Wissensdatenbank ' Suppliers ' | Microsoft-Dokumentation"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.topic: conceptual
ms.assetid: 215c14de-fc3f-46de-a022-bf69b9ea2a96
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e8366781f25829b0063479c2874a56c184e73bad
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/13/2018
ms.locfileid: "53355704"
---
# <a name="lesson-2-cleansing-supplier-data-using-the-suppliers-knowledge-base"></a>Lektion 2: Bereinigung von Lieferantendaten mithilfe der Wissensdatenbank 'Suppliers'
  In dieser Lektion bereinigen Sie die Lieferantendaten in einer Excel-Datei mithilfe der **Lieferanten** Wissensdatenbank, die Sie in der ersten Lektion erstellt haben. DatenBereinigung in DQS umfasst einen **computergestützten Prozess** , der analysiert, wie Daten mit den Informationen in einer Wissensdatenbank übereinstimmen und eine **interaktiver Prozess** , mit der Sie zum Überprüfen und ändern die Ergebnisse des computergestützten Prozesses. Die Datenbereinigungsfunktion identifiziert falsche Daten in der Datenquelle und korrigiert diese anschließend oder schlägt Korrekturen für die falschen Daten vor. Darüber hinaus standardisiert und erweitert sie Kundendaten unter Verwendung von Domänenwerten, führenden Werten für Synonyme, Domänenregeln, begriffsbasierten Beziehungen und Verweisdaten. Sie können die vom computergestützten Prozess vorgeschlagenen Änderungen interaktiv genehmigen oder ablehnen. Finden Sie unter [DatenBereinigung](https://msdn.microsoft.com/library/gg524800.aspx) Weitere Details.  
  
 Der computergestützte Prozess verwendet die folgenden Schwellenwerte, die Sie mithilfe der Konfigurationsoption auf der DQS-Client-Hauptseite konfigurieren können.  
  
-   **Mindestergebnis für Vorschläge:** Das Mindestergebnis bzw. der Vertrauensgrad, der von DQS zum Vorschlagen eines Ersatzes für einen Wert verwendet wird.  
  
-   **Mindestergebnis für automatische Korrekturen:** Das Mindestergebnis bzw. der Vertrauensgrad, der von DQS zum automatischen Korrigieren eines Werts verwendet wird.  
  
 Finden Sie unter [Konfigurieren der Schwellenwerte für Bereinigung und Abgleich](https://msdn.microsoft.com/library/hh510415.aspx) ausführliche Anleitungen zum Konfigurieren dieser Einstellungen.  
  
 In dieser Lektion führen Sie die folgenden Aufgaben für die Wissensdatenbank "Suppliers" aus, um die Eingabedaten zu bereinigen.  
  
1.  Erstellen Sie ein Data Quality-Projekt für die Bereinigung, wählen Sie die Wissensdatenbank "Suppliers" als Wissensdatenbank für die Analyse und Bereinigung der Quelldaten in einer Excel-Datei aus, und wählen Sie die Bereinigungsaktivität aus.  
  
2.  Ordnen Sie die Excel-Spalten, die Sie bereinigen möchten, entsprechenden DQS-Domänen/Verbunddomänen in der Wissensdatenbank zu.  
  
3.  Führen Sie die computergestützte Bereinigungsaktivität aus. Der computergestützte Prozess zeigt Informationen zur Datenqualität im Data Quality-Client an, mit dem Sie die Daten interaktiv bereinigen können.  
  
4.  Zeigen Sie die Ergebnisse der Bereinigungsaktivität an, und verwalten Sie sie. Sie können die Werte überprüfen, die vom computergestützten Prozess als richtig, falsch aber korrigiert, falsch mit einem Änderungsvorschlag oder ungültig bewertet werden. Sie können die Änderungen interaktiv genehmigen oder ablehnen und dabei den Vorschlag des computergestützten Prozesses im Feld "Korrigieren in" korrigieren oder überschreiben.  
  
5.  Exportieren Sie die Ergebnisse des Bereinigungsprozesses in eine Excel-Datei.  
  
6.  Importieren Sie die Werte aus dem bereinigungsprojekt in Domänen, um die Informationen in der Wissensdatenbank mit neue Regeln, Werte, Korrekturen usw. zu erweitern...  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 1: Erstellen ein Data Quality-Projekt](../../2014/tutorials/task-1-creating-a-data-quality-project.md)  
  
  
