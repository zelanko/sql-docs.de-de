---
title: Schnelle Analyse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- fast parse [Integration Services]
ms.assetid: 6688707d-3c5b-404e-aa2f-e13092ac8d95
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: b13ddc498962ca23e6bc1f5e7a10d88af47ff7d6
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66058868"
---
# <a name="fast-parse"></a>Fast Parse
  Die schnelle Analyse stellt schnelle, einfache Routinen zum Analysieren von Daten bereit. Diese Routinen sind nicht gebietsschemaspezifisch und unterstützen nur eine Teilmenge von Datums-, Uhrzeit- und Ganzzahlformaten.  
  
## <a name="requirements-and-limitations"></a>Anforderungen und Einschränkungen  
 Durch Implementieren der schnellen Analyse ist das Interpretieren von Datum, Uhrzeit und numerischen Daten in gebietsschemaspezifischen Formaten sowie in häufig verwendeten ISO 8601-Basisformaten und erweiterten Formaten über ein Paket nicht möglich. Jedoch trägt dies zur Leistungssteigerung des Pakets bei. Beispielsweise unterstützt die schnelle Analyse nur die gängigsten Datumsformatdarstellungen, wie z. B. YYYYMMDD und YYYY-MM-DD, führt keine gebietsschemaspezifische Analyse durch, erkennt keine Sonderzeichen in Währungsdaten und kann die hexadezimale oder wissenschaftliche Darstellung von ganzen Zahlen nicht konvertieren.  
  
 Die schnelle Analyse ist nur bei Verwenden der Flatfilequelle oder der Transformation für Datenkonvertierung verfügbar. Die Leistungssteigerung kann sehr erheblich sein. Daher sollten Sie nach Möglichkeit die schnelle Analyse in diesen Datenflusskomponenten verwenden.  
  
 Wenn der Datenfluss im Paket eine gebietsschemabezogene Analyse erfordert, wird stattdessen die Standardanalyse empfohlen. So erkennt die schnelle Analyse beispielsweise keine gebietsschemabezogenen Daten mit Dezimalsymbolen wie dem Komma, anderen Datenformaten als dem Jahr-Monat-Datum-Format und Währungssymbolen.  
  
 Abgeschnittene Darstellungen, die mindestens ein Datumsteil implizieren, wie z. B. ein Jahrhundert, ein Jahr oder ein Monat, werden von der schnellen Analyse nicht erkannt. Die schnelle Analyse erkennt z.B. weder das Format **-JJMM**, das ein Jahr und einen Monat in einem implizierten Jahrhundert angibt, noch **--MM**, das einen Monat in einem implizierten Jahr angibt. Bestimmte Darstellungen mit reduzierter Genauigkeit werden jedoch erkannt. Beispielsweise erkennt die schnelle Analyse das Format 'hhmm;', das nur die Stunde und die Minute angibt, sowie '**YYYY**', das nur das Jahr angibt.  
  
 Die schnelle Analyse wird auf Spaltenebene angegeben. In der Flatfilequelle und der Transformation für Datenkonvertierung können Sie die schnelle Analyse für Ausgabespalten festlegen. Eingaben und Ausgaben können gebietsschemabezogene und gebietsschemaneutrale Spalten enthalten.  
  
 Weitere Informationen zu den von der schnellen Analyse unterstützten Datenformaten finden Sie unter [Numeric Data Formats](../../2014/integration-services/numeric-data-formats.md) und [Date and Time Formats](../../2014/integration-services/date-and-time-formats.md).  
  
## <a name="related-tasks"></a>Related Tasks  
 [Festlegen der schnellen Analyse](../../2014/integration-services/set-fast-parse.md)  
  
  
