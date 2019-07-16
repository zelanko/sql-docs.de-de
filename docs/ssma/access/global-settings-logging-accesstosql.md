---
title: Global Settings (Logging) (AccessToSQL) Einstellungen | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 835b09b5-eb42-47ea-b46e-e115d4d6461f
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 72efa0f050a3b930ebaa99ff425b48e1fe9b6ba5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67986651"
---
# <a name="global-settings-logging-accesstosql"></a>Globale Einstellungen (Protokollierung) (AccessToSQL)
Verwenden der **globale Einstellungen** (Dialogfeld), um die protokollierungseinstellungen für SSMA anzugeben. In der Regel würden Sie diese Einstellungen ändern, nur bei der Arbeit mit Microsoft Support Services.  
  
Zum Zugriff auf dieses Dialogfeld, in der **Tools** , wählen Sie im Menü **globale Einstellungen** , und klicken Sie dann auf die **Protokollierung** unten auf die Schaltfläche im linken Bereich.  
  
## <a name="options"></a>Optionen  
**Nachrichten-Ebene**  
Die folgenden Optionen sind verfügbar unter **Nachrichten Ebene**:  
  
|Option|Beschreibung|  
|----------|---------------|  
|**[alle Kategorien]**|Verwendet, um den Protokolliergrad auf für alle der folgenden Optionen festlegen.|  
|**Datensammler**|Sammelt Metadaten über das Quellschema und speichert es in das Projekt.|  
|**Konverter**|Strukturen der Source-Datenbankobjekte wie Tabellen und gespeicherte Prozeduren, in entsprechenden konvertiert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Strukturen.|  
|**Daten migrator**|Migrieren von Daten aus der Quelldatenbank in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**Formatter**|Unterkomponente des Konverters, der generiert Skripts für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Schema.|  
|**Grafische Benutzeroberfläche**|Nachrichten, die angezeigt werden, wenn Sie das SSMA-Tool verwenden.|  
|**Linker**|Löst SQL-Bezeichner auf und enthält Informationen zu anderen Komponenten.|  
|**Andere**|Alle Nachrichten, die nicht in einer beliebigen anderen Kategorie enthalten sind.|  
|**Parser**|Analysiert das Quellschema an.|  
|**Für die domänensynchronisierung**|Lädt Quell-Datenbankobjekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**TreeConverter**|Konvertiert Objekte in der Quell-Metadaten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Metadaten.|  
  
Für jede Option unter **Nachrichten Ebene**, konfigurieren Sie eine der folgenden Protokolliergrade für SSMA:  
  
|||  
|-|-|  
|**Schwerwiegender Fehler**|Geschrieben Sie nur schwerwiegende Meldungen in das Protokoll.|  
|**Fehler**|Geschrieben Sie Fehler und schwerwiegende Meldungen in das Protokoll.|  
|**Warnung**|Geschrieben Sie Warnung, Fehler und schwerwiegende Meldungen in das Protokoll.|  
|**Info**|Geschrieben Sie nur zu Informationszwecken, Warnung, Fehler und schwerwiegende Meldungen in das Protokoll.|  
|**Debuggen**|Alle Nachrichten, einschließlich der Debugmeldungen in das Protokoll zu schreiben.|  
  
**Pfad der Protokolldatei**  
Den Dateipfad und den Namen der SSMA-Protokolldateien. Um einen anderen Namen anzugeben, klicken Sie auf den aktuellen Pfad aus, und klicken Sie dann auf die Schaltfläche zum Durchsuchen ( **...** ) Schaltfläche.  
  
**Größe der Protokolldatei**  
Die maximale Größe der Protokolldatei in KB. Die minimale Größe beträgt 10 KB. Die Standardgröße ist 10240 KB.  
  
**Gesamtanzahl der Protokolldateien**  
Wenn ein Protokoll voll ist, wird die SSMA benennen Sie die Log-Datei und starten eine neue. Geben Sie mit dieser Einstellung die maximale Anzahl von aufbewahrten Protokolldateien. Der Mindestwert beträgt 2.  
  
