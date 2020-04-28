---
title: Globale Einstellungen (Protokollierung) (oracleto SQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 12dbcd77-2b90-4fa1-9cf9-239231ea5773
author: Shamikg
ms.author: Shamikg
manager: shamikg
ms.openlocfilehash: 374630b5e5eab1602bb33e176e6f205ee1375af9
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68264431"
---
# <a name="global-settings-logging-oracletosql"></a>Globale Einstellungen (Protokollierung) (OracleToSQL)
Verwenden Sie das Dialogfeld **globale Einstellungen** , um die Protokollierungs Einstellungen für SSMA anzugeben. In der Regel ändern Sie diese Einstellungen nur, wenn Sie mit dem Produktsupport arbeiten.  
  
Um auf dieses Dialogfeld zuzugreifen, wählen Sie **im Menü Extras die Option** **globale Einstellungen** aus, und klicken Sie dann unten im linken Bereich auf die Schaltfläche **Protokollierung** .  
  
## <a name="options"></a>Optionen  
**Nachrichten Ebene**  
Die folgenden Optionen sind unter **Nachrichten Ebene**verfügbar:  
  
|Option|BESCHREIBUNG|  
|----------|---------------|  
|**[alle Kategorien]**|Wird verwendet, um den Protokolliergrad für alle folgenden Optionen festzulegen.|  
|**Collector**|Sammelt Metadaten über das Quell Schema und speichert Sie im Projekt.|  
|**Converter**|Konvertiert Strukturen von Quelldaten Bank Objekten, z. b. Tabellen und gespeicherte Prozeduren, in entsprechende [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Strukturen.|  
|**Datenmigrierer**|Migriert Daten von der Quelldatenbank zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**Formatierungsprogramm**|Unterkomponente des Konverters, der Skripts für das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Schema generiert.|  
|**Grafische Benutzeroberfläche**|Meldungen, die angezeigt werden, wenn Sie das SSMA-Tool verwenden.|  
|**Linker**|Löst SQL-Bezeichner auf und stellt Informationen für andere Komponenten bereit.|  
|**Andere**|Alle Nachrichten, die nicht in einer anderen Kategorie vorhanden sind.|  
|**Parser**|Analysiert das Quell Schema.|  
|**Synchronisierung**|Lädt Quelldaten Bank Objekte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]in.|  
|**Treeconverter**|Konvertiert Objekte in den Quell Metadaten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Metadaten.|  
|**Tester**|Meldungen, die angezeigt werden, wenn Sie den SSMA-Tester verwenden.|  
  
Konfigurieren Sie für jede Option unter **Nachrichten Ebene**einen der folgenden Protokolliergrade für SSMA:  
  
|||  
|-|-|  
|**Schwerwiegender Fehler**|Schreiben Sie nur schwerwiegende Fehlermeldungen in das Protokoll.|  
|**Fehler**|Schreiben Sie Fehler-und schwerwiegende Fehlermeldungen in das Protokoll.|  
|**Warning**|Schreiben Sie Warnungs-, Fehler-und schwerwiegende Fehlermeldungen in das Protokoll.|  
|**Info**|Schreiben Sie Informations-, Warnungs-, Fehler-und schwerwiegende Fehlermeldungen in das Protokoll.|  
|**Debuggen**|Schreiben Sie alle Meldungen, einschließlich des Debuggens von Nachrichten, in das Protokoll.|  
  
**Protokolldateipfad**  
Der Dateipfad und der Name der SSMA-Protokolldateien. Wenn Sie einen anderen Namen angeben möchten, klicken Sie auf den aktuellen Pfad, und klicken Sie dann auf die Schaltfläche zum Durchsuchen (**..**.).  
  
**Größe der Protokolldatei**  
Die maximale Größe der Protokolldatei in KB. Die Mindestgröße beträgt 10 KB. Die Standardgröße ist 10240 KB.  
  
**Gesamtanzahl der Protokolldateien**  
Wenn ein Protokoll ausgefüllt wird, benennt SSMA die Protokolldatei um und startet ein neues. Geben Sie mit dieser Einstellung die maximale Anzahl von Protokolldateien an, die aufbewahrt werden sollen. Der Minimalwert ist 2.  
  
