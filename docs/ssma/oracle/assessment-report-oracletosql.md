---
title: Assessment Report (OracleToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 168b7465-a6d6-4329-b46e-fc6c5a3f2d9d
caps.latest.revision: 4
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: 2dd0a63d9637a44f387c3e3f862387a8c4866d18
ms.sourcegitcommit: b70b99c2e412b4d697021f3bf1a92046aafcbe37
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2018
ms.locfileid: "40394031"
---
# <a name="assessment-report-oracletosql"></a>Bewertungsbericht (OracleToSQL)
Die Fenster "Assessment Report" zeigt die Ergebnisse der Konvertierung von Datenbankobjekten zu [!INCLUDE[tsql](../../includes/tsql-md.md)] Syntax, und kann ebenfalls dazu beitragen, die Sie schätzen, die Komplexität und Kosten für Ihren Migrationsprojekten.  
  
Der Bewertungsbericht, Objekte gleichzeitig auszuwählen, für die Konvertierung in den Quellen-Metadaten-Explorer, den Zugriff auf Informationen zu diesem mit der rechten Maustaste **Schemas** oder **Synonyme**, und wählen Sie dann **Bericht erstellen**.  
  
## <a name="options"></a>Tastatur  
  
|||  
|-|-|  
|Begriff|Definition|  
|**Konvertierungsstatistiken**|Zeigt die Konvertierungsstatistiken nach Anweisungstyp. In diesem Bereich ist sichtbar, wenn ein Gruppenobjekt, z. B. ein Schema, oder ein Objekt ohne den Code im linken Bereich ausgewählt ist.|  
|**Objekte nach Kategorien**|Zeigt die Anzahl von Objekten nach Kategorie. In diesem Bereich ist nur sichtbar, wenn ein Gruppenobjekt, z. B. ein Schema, oder ein Objekt ohne den Code im linken Bereich ausgewählt ist.|  
|**Statistik**|Zeigt die Konvertierungsstatistiken für das ausgewählte Objekt an. In diesem Bereich ist sichtbar, nur, wenn ein einzelnes Objekt mit Code im linken Bereich ausgewählt ist. Möglicherweise müssen Sie erweitern **Statistiken**, d.h. sofort über die **Quelle** Bereich, um diesen Bereich anzuzeigen.|  
|**Quelle**|Zeigt den Oracle-Code für das ausgewählte Objekt und Code, der nicht in konvertiert wurde hervorgehoben [!INCLUDE[tsql](../../includes/tsql-md.md)]. In diesem Bereich ist sichtbar, nur, wenn ein einzelnes Objekt mit Code im linken Bereich ausgewählt ist.<br /><br />Klicken Sie auf die Zeilennummern einstellen oder Löschen von Lesezeichen. Mithilfe der Schaltflächen am oberen Rand des Bereichs, um den Code zu navigieren.|  
|**Target**|Zeigt die Konvertierung der resultierende [!INCLUDE[tsql](../../includes/tsql-md.md)] Code für das ausgewählte Objekt und Fehlermeldungen für Code, der nicht konvertiert wurden. In diesem Bereich ist sichtbar, nur, wenn ein einzelnes Objekt mit Code im linken Bereich ausgewählt ist.<br /><br />Klicken Sie auf die Zeilennummern einstellen oder Löschen von Lesezeichen. Mithilfe der Schaltflächen am oberen Rand des Bereichs, um den Code zu navigieren.|  
|**Meldungsbereich**|Zeigt die Fehler, Warnungen und informationsmeldungen, die beim Erstellen des Bewertungsberichts generiert wurden. Nachrichten werden nach Anzahl gruppiert. Um den Code anzuzeigen, die den Fehler verursacht hat, klicken Sie auf **Fehler**, **Warnungen**, oder **Informationen**, erweitern Sie die Kategorie von Nachrichten, und klicken Sie dann auf eine Nachricht.|  
  
