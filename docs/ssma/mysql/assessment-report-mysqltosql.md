---
title: Assessment Report (MySQLToSQL)) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 5525d989-024c-402d-9e84-faa4721cc5b9
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 72b6171864c0ab801e89d3eba5a19ff61031a81e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63253293"
---
# <a name="assessment-report-mysqltosql"></a>Bewertungsbericht (MySqlToSql)
Die Fenster "Assessment Report" zeigt die Ergebnisse der Konvertierung von Datenbankobjekten zu [!INCLUDE[tsql](../../includes/tsql-md.md)] Syntax, und kann ebenfalls dazu beitragen, die Sie schätzen, die Komplexität und Kosten für Ihren Migrationsprojekten.  
  
Der Bewertungsbericht, Objekte gleichzeitig auszuwählen, für die Konvertierung in den Quellen-Metadaten-Explorer, den Zugriff auf Informationen zu diesem mit der rechten Maustaste **Schemas**, und wählen Sie dann **Bericht erstellen**.  
  
## <a name="options"></a>Optionen  
  
|||  
|-|-|  
|**Begriff**|**Definition**|  
|**Konvertierungsstatistiken**|Zeigt die Konvertierungsstatistiken nach Anweisungstyp. In diesem Bereich ist sichtbar, wenn ein Gruppenobjekt, z. B. ein Schema, oder ein Objekt ohne den Code im linken Bereich ausgewählt ist.|  
|**Objekte nach Kategorien**|Zeigt die Anzahl von Objekten nach Kategorie. In diesem Bereich ist nur sichtbar, wenn ein Gruppenobjekt, z. B. ein Schema, oder ein Objekt ohne den Code im linken Bereich ausgewählt ist.|  
|**Statistik**|Zeigt die Konvertierungsstatistiken für das ausgewählte Objekt an. In diesem Bereich ist sichtbar, nur, wenn ein einzelnes Objekt mit Code im linken Bereich ausgewählt ist. Möglicherweise müssen Sie erweitern **Statistiken**, d.h. sofort über die **Quelle** Bereich, um diesen Bereich anzuzeigen.|  
|**Quelle**|Zeigt den MySQL-Code für das ausgewählte Objekt und Code, der nicht in konvertiert wurde hervorgehoben [!INCLUDE[tsql](../../includes/tsql-md.md)]. In diesem Bereich ist sichtbar, nur, wenn ein einzelnes Objekt mit Code im linken Bereich ausgewählt ist.<br /><br />Klicken Sie auf die Zeilennummern einstellen oder Löschen von Lesezeichen. Mithilfe der Schaltflächen am oberen Rand des Bereichs, um den Code zu navigieren.|  
|**Target**|Zeigt die Konvertierung der resultierende [!INCLUDE[tsql](../../includes/tsql-md.md)] Code für das ausgewählte Objekt und Fehlermeldungen für Code, der nicht konvertiert wurden. In diesem Bereich ist sichtbar, nur, wenn ein einzelnes Objekt mit Code im linken Bereich ausgewählt ist.<br /><br />Klicken Sie auf die Zeilennummern einstellen oder Löschen von Lesezeichen. Mithilfe der Schaltflächen am oberen Rand des Bereichs, um den Code zu navigieren.|  
|**Meldungsbereich**|Zeigt die Fehler, Warnungen und informationsmeldungen, die beim Erstellen des Bewertungsberichts generiert wurden. Nachrichten werden nach Anzahl gruppiert. Um den Code anzuzeigen, die den Fehler verursacht hat, klicken Sie auf **Fehler**, **Warnungen**, oder **Informationen**, erweitern Sie die Kategorie von Nachrichten, und klicken Sie dann auf eine Nachricht.|  
  
