---
title: 'Lektion 2: Bereinigung von Lieferantendaten mithilfe der Wissensdatenbank "Suppliers" | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 215c14de-fc3f-46de-a022-bf69b9ea2a96
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: b99676a9f51bf76dc9db294365a5a628dd25fa2e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "65488474"
---
# <a name="lesson-2-cleansing-supplier-data-using-the-suppliers-knowledge-base"></a>Aufgabe 2: Bereinigung von Lieferantendaten mithilfe der Wissensdatenbank 'Suppliers'
  In dieser Lektion bereinigen Sie die Lieferantendaten in einer Excel-Datei, indem Sie die Wissensdatenbank **Suppliers** verwenden, die Sie in der ersten Lektion erstellt haben. Die Datenbereinigung in DQS umfasst einen **computergestützten Prozess** , der analysiert, wie Daten den Kenntnissen in einer Wissensdatenbank entsprechen, sowie einen **interaktiven Prozess** , mit dem Sie die Ergebnisse des computergestützten Prozesses überprüfen und ändern können. Die Datenbereinigungsfunktion identifiziert falsche Daten in der Datenquelle und korrigiert diese anschließend oder schlägt Korrekturen für die falschen Daten vor. Darüber hinaus standardisiert und erweitert sie Kundendaten unter Verwendung von Domänenwerten, führenden Werten für Synonyme, Domänenregeln, begriffsbasierten Beziehungen und Verweisdaten. Sie können die vom computergestützten Prozess vorgeschlagenen Änderungen interaktiv genehmigen oder ablehnen. Weitere Informationen finden Sie unter [Datenbereinigung](https://msdn.microsoft.com/library/gg524800.aspx) .  
  
 Der computergestützte Prozess verwendet die folgenden Schwellenwerte, die Sie mithilfe der Konfigurationsoption auf der DQS-Client-Hauptseite konfigurieren können.  
  
-   **Minimale Bewertung für Vorschläge:** Das minimale Ergebnis oder der Vertrauensgrad, der von DQS zum vorschlagen der Ersetzung für einen Wert verwendet wird.  
  
-   **Minimale Bewertung für automatische Korrekturen:** Das minimale Ergebnis oder der Vertrauensgrad, der von DQS zum automatischen Korrigieren eines Werts verwendet wird.  
  
 Ausführliche Informationen zum Konfigurieren dieser Einstellungen finden Sie unter [Konfigurieren der Schwellenwerte für Bereinigung und](https://msdn.microsoft.com/library/hh510415.aspx) Abgleich.  
  
 In dieser Lektion führen Sie die folgenden Aufgaben für die Wissensdatenbank "Suppliers" aus, um die Eingabedaten zu bereinigen.  
  
1.  Erstellen Sie ein Data Quality-Projekt für die Bereinigung, wählen Sie die Wissensdatenbank "Suppliers" als Wissensdatenbank für die Analyse und Bereinigung der Quelldaten in einer Excel-Datei aus, und wählen Sie die Bereinigungsaktivität aus.  
  
2.  Ordnen Sie die Excel-Spalten, die Sie bereinigen möchten, entsprechenden DQS-Domänen/Verbunddomänen in der Wissensdatenbank zu.  
  
3.  Führen Sie die computergestützte Bereinigungsaktivität aus. Der computergestützte Prozess zeigt Informationen zur Datenqualität im Data Quality-Client an, mit dem Sie die Daten interaktiv bereinigen können.  
  
4.  Zeigen Sie die Ergebnisse der Bereinigungsaktivität an, und verwalten Sie sie. Sie können die Werte überprüfen, die vom computergestützten Prozess als richtig, falsch aber korrigiert, falsch mit einem Änderungsvorschlag oder ungültig bewertet werden. Sie können die Änderungen interaktiv genehmigen oder ablehnen und dabei den Vorschlag des computergestützten Prozesses im Feld "Korrigieren in" korrigieren oder überschreiben.  
  
5.  Exportieren Sie die Ergebnisse des Bereinigungsprozesses in eine Excel-Datei.  
  
6.  Importieren Sie die Werte aus dem Bereinigungs Projekt in Domänen, um das Wissen in der Wissensdatenbank durch neue Regeln, Werte, Korrekturen usw. zu erweitern.  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 1: Erstellen eines Data Quality-Projekts](../../2014/tutorials/task-1-creating-a-data-quality-project.md)  
  
  
