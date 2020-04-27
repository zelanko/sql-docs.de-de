---
title: Verwenden von in-Memory-OLTP in einer VM-Umgebung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 27ec7eb3-3a24-41db-aa65-2f206514c6f9
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e7f7f04b04792167fe9c4733f3e066c362f3cae4
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62843060"
---
# <a name="using-in-memory-oltp-in-a-vm-environment"></a>Verwenden von In-Memory OLTP in einer VM-Umgebung
  Servervirtualisierung kann durch eine verbesserte Anwendungsbereitstellung, Wartung, Verfügbarkeit sowie Sicherungs- und Wiederherstellungsprozesse das IT-Kapital und die Betriebskosten Ihres Unternehmens senken und die IT-Effizienz steigern. Dank der neuesten technologischen Entwicklungen können komplexe Datenbankarbeitslasten mithilfe der Virtualisierung leichter konsolidiert werden. Dieses Thema enthält bewährte Methoden zur Verwendung von [!INCLUDE[hek_1](../includes/hek-1-md.md)] in einer virtualisierten Umgebung.  
  
##  <a name="memory-pre-allocation"></a><a name="bkmk_memoryPreAllocation"></a>Vorab Zuordnung von Arbeitsspeicher  
 Für den Arbeitsspeicher in einer virtualisierten Umgebung sind bessere Leistung und erweiterte Unterstützung zentrale Faktoren. Sie müssen sowohl in der Lage sein, virtuellen Computern auf Basis der jeweiligen Anforderungen (Last zu Spitzenzeiten und außerhalb von Spitzenzeiten) schnell Arbeitsspeicher zuzuordnen als auch sicherzustellen, dass dieser Arbeitsspeicher nicht verschwendet wird. Der dynamischer Arbeitsspeicher von Hyper-V erhöht die Flexibilität bei der Zuweisung und Verwaltung von Arbeitsspeicher zwischen virtuellen Computern, die auf einem Host ausgeführt werden.  
  
 Einige bewährte Methoden für die Virtualisierung und Verwaltung von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] müssen geändert werden, wenn eine Datenbank mit speicheroptimierten Tabellen virtualisiert wird. Ohne speicheroptimierte Tabellen lauten zwei bewährte Methoden wie folgt:  
  
-   Bei Verwendung von MIN_SERVER_MEMORY sollte nur die tatsächlich erforderliche Speichermenge zugewiesen werden, sodass ausreichend Speicher für andere Prozesse verbleibt (und Auslagerungen vermieden werden).  
  
-   Legen Sie den Wert für die Vorabbelegung von Arbeitsspeicher nicht zu hoch fest. Andernfalls erhalten andere Prozesse u. U. nicht ausreichend Speicher, wenn sie ihn brauchen. Dies kann zu Speicherauslagerungen führen.  
  
 Wenn Sie für eine Datenbank mit speicheroptimierten Tabellen die oben genannten Methoden verwenden, kann der Versuch, die Datenbank wiederherzustellen, dazu führen, dass die Datenbank im Status „Wiederherstellung steht aus“ hängen bleibt, obwohl genügend Arbeitsspeicher zum Wiederherstellen der Datenbank verfügbar ist. Die Ursache hierfür ist, dass [!INCLUDE[hek_2](../includes/hek-2-md.md)] die Daten beim Starten aggressiver in den Speicher lädt, als die dynamische Speicherbelegung den Arbeitsspeicher der Datenbank zuweist.  
  
 **Lösung**  
  
 Um dieses Risiko abzuschwächen, ordnen Sie der Datenbank vorab genügend Arbeitsspeicher zu, um die Datenbank wiederherzustellen oder neu zu starten. Verwenden Sie hierfür nicht den Minimalwert auf Basis des dynamischen Speichers, um den zusätzlichen Arbeitsspeicher bei Bedarf bereitzustellen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [In-Memory-OLTP &#40;Arbeitsspeicheroptimierung&#41;](../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
