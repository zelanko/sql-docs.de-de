---
title: Global Settings (Logging) (DB2ToSQL) Einstellungen | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: d314a2ca-ea2e-46e0-ae5e-8774841da91b
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 7d632b040a5124d73470ce825af91e254866a0ae
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47857318"
---
# <a name="global-settings-logging-db2tosql"></a>Globale Einstellungen (Protokollierung) (DB2ToSQL)
Verwenden der **globale Einstellungen** (Dialogfeld), um die protokollierungseinstellungen für SSMA anzugeben. In der Regel würden Sie diese Einstellungen ändern, nur bei der Arbeit mit Microsoft Support Services.  
  
Zum Zugriff auf dieses Dialogfeld, in der **Tools** , wählen Sie im Menü **globale Einstellungen** , und klicken Sie dann auf die **Protokollierung** unten auf die Schaltfläche im linken Bereich.  
  
## <a name="options"></a>Tastatur  
**Nachrichten-Ebene**  
Die folgenden Optionen sind verfügbar unter **Nachrichten Ebene**:  
  
|Option|Description|  
|----------|---------------|  
|**[alle Kategorien]**|Verwendet, um den Protokolliergrad auf für alle der folgenden Optionen festlegen.|  
|**Datensammler**|Sammelt Metadaten über das Quellschema und speichert es in das Projekt.|  
|**Konverter**|Strukturen der Source-Datenbankobjekte wie Tabellen und gespeicherte Prozeduren, in entsprechenden konvertiert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Strukturen.|  
|**Daten migrator**|Migrieren von Daten aus der Quelldatenbank in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**Formatierer**|Unterkomponente des Konverters, der generiert Skripts für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Schema.|  
|**Grafische Benutzeroberfläche**|Nachrichten, die angezeigt werden, wenn Sie das SSMA-Tool verwenden.|  
|**Linker**|Löst SQL-Bezeichner auf und enthält Informationen zu anderen Komponenten.|  
|**Andere**|Alle Nachrichten, die nicht in einer beliebigen anderen Kategorie enthalten sind.|  
|**Parser**|Analysiert das Quellschema an.|  
|**Für die domänensynchronisierung**|Lädt Quell-Datenbankobjekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**TreeConverter**|Konvertiert Objekte in der Quell-Metadaten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Metadaten.|  
|**Tester**|Nachrichten, die bei der Verwendung der SSMA-Tester angezeigt werden.|  
  
Für jede Option unter **Nachrichten Ebene**, konfigurieren Sie eine der folgenden Protokolliergrade für SSMA:  
  
|||  
|-|-|  
|**Schwerwiegender Fehler**|Geschrieben Sie nur schwerwiegende Meldungen in das Protokoll.|  
|**Fehler**|Geschrieben Sie Fehler und schwerwiegende Meldungen in das Protokoll.|  
|**Warnung**|Geschrieben Sie Warnung, Fehler und schwerwiegende Meldungen in das Protokoll.|  
|**Info**|Geschrieben Sie nur zu Informationszwecken, Warnung, Fehler und schwerwiegende Meldungen in das Protokoll.|  
|**Debuggen**|Alle Nachrichten, einschließlich der Debugmeldungen in das Protokoll zu schreiben.|  
  
**Pfad der Protokolldatei**  
Den Dateipfad und den Namen der SSMA-Protokolldateien. Um einen anderen Namen anzugeben, klicken Sie auf den aktuellen Pfad aus, und klicken Sie dann auf die Schaltfläche zum Durchsuchen (**...** ) Schaltfläche.  
  
**Größe der Protokolldatei**  
Die maximale Größe der Protokolldatei in KB. Die minimale Größe beträgt 10 KB. Die Standardgröße ist 10240 KB.  
  
**Gesamtanzahl der Protokolldateien**  
Wenn ein Protokoll voll ist, wird die SSMA benennen Sie die Log-Datei und starten eine neue. Geben Sie mit dieser Einstellung die maximale Anzahl von aufbewahrten Protokolldateien. Der Mindestwert beträgt 2.  
  
