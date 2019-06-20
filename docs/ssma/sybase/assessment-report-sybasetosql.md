---
title: Assessment Report (SybaseToSQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: af24f2c4-5e86-4135-a4f3-a24faaeeefe7
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: aae49bb6eb8ecf067911b2cb64017af0f3143aa0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63132803"
---
# <a name="assessment-report-sybasetosql"></a>Bewertungsbericht (SybaseToSQL)
Die Fenster "Assessment Report" zeigt die Ergebnisse der Konvertierung von Datenbankobjekten zu [!INCLUDE[tsql](../../includes/tsql-md.md)] Syntax, und kann ebenfalls dazu beitragen, die Sie schätzen, die Komplexität und Kosten für Ihren Migrationsprojekten.  
  
Der Bewertungsbericht, Objekte gleichzeitig auszuwählen, für die Konvertierung in den Quellen-Metadaten-Explorer, den Zugriff auf Informationen zu diesem mit der rechten Maustaste **Datenbanken**, und wählen Sie dann **Bericht erstellen**.  
  
## <a name="options"></a>Optionen  
**Konvertierungsstatistiken**  
Zeigt die Konvertierungsstatistiken nach Anweisungstyp. In diesem Bereich ist nur sichtbar, wenn ein Gruppenobjekt, z. B. ein Schema, oder ein Objekt ohne den Code im linken Bereich ausgewählt ist.  
  
**Objekte nach Kategorie**  
Zeigt die Konvertierungsstatistiken nach Objekttyp. In diesem Bereich ist nur sichtbar, wenn ein Gruppenobjekt, z. B. ein Schema, oder ein Objekt ohne den Code im linken Bereich ausgewählt ist.  
  
**Statistik**  
Zeigt die Konvertierungsstatistiken für das ausgewählte Objekt an. In diesem Bereich ist sichtbar, nur, wenn ein einzelnes Objekt mit Code im linken Bereich ausgewählt ist. Möglicherweise müssen Sie erweitern **Statistiken** um diesen Bereich anzuzeigen.  
  
**Navigation Quellcode**  
Zeigt den ASE-Code für das ausgewählte Objekt und Code, der nicht in konvertiert wurde hervorgehoben [!INCLUDE[tsql](../../includes/tsql-md.md)]. In diesem Bereich ist sichtbar, nur, wenn ein einzelnes Objekt mit Code im linken Bereich ausgewählt ist.  
  
Klicken Sie auf die Zeilennummern einstellen oder Löschen von Lesezeichen. Mithilfe der Schaltflächen am oberen Rand des Bereichs, um den Code zu navigieren.  
  
**Ziel-navigation**  
Zeigt die Konvertierung der resultierende [!INCLUDE[tsql](../../includes/tsql-md.md)] Code für das ausgewählte Objekt und Fehlermeldungen für Code, der nicht konvertiert wurden. In diesem Bereich ist sichtbar, nur, wenn ein einzelnes Objekt mit Code im linken Bereich ausgewählt ist.  
  
Klicken Sie auf die Zeilennummern einstellen oder Löschen von Lesezeichen. Mithilfe der Schaltflächen am oberen Rand des Bereichs, um den Code zu navigieren.  
  
**Meldungsbereich**  
Zeigt die Fehler, Warnungen und informationsmeldungen, die beim Erstellen des Bewertungsberichts generiert werden. Nachrichten werden nach Anzahl gruppiert. Um den Code anzuzeigen, die den Fehler verursacht hat, klicken Sie auf **Fehler**, **Warnung**, oder **Informationen**, erweitern Sie die Kategorie von Nachrichten, und klicken Sie dann auf eine Nachricht.  
  
