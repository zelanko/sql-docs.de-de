---
title: Memory-Eigenschaften | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- LowMemoryLimit property
- MinimumAllocatedMemory property
- MidMemoryPrice property
- MemoryHeapType property
- memory [Analysis Services]
- DefaultPagesCountToReuse property
- TotalMemoryLimit property
- SessionMemoryLimit property
- VirtualMemoryLimit property
- WaitCountIfHighMemory property
- HighMemoryPrice property
- HeapTypeForObjects property
ms.assetid: 085f5195-7b2c-411a-9813-0ff5c6066d13
caps.latest.revision: 22
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 77902cfe21cf2f486007f802c0556bd410f46d4e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37286376"
---
# <a name="memory-properties"></a>Speichereigenschaften
  In [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] werden die in der folgenden Tabelle aufgeführten Serverarbeitsspeichereigenschaften unterstützt. Einen Leitfaden zum Festlegen dieser Eigenschaften finden Sie im [SQL Server 2008 R2 Analysis Services-Betriebshandbuch](http://go.microsoft.com/fwlink/?LinkID=225539).  
  
 Werte zwischen 1 und 100 stellen Prozentsätze von **Gesamter physischer Speicher** bzw. **Virtueller Adressraum**dar, je nachdem, welcher geringer ist. Werte über 100 stellen Arbeitsspeichergrenzwerte in Bytes dar.  
  
 **Gilt für:** Mehrdimensionaler und tabellarischer Servermodus, sofern nichts anderes angegeben ist.  
  
## <a name="properties"></a>Eigenschaften  
 `LowMemoryLimit`  
 Eine 64-Bit-Gleitkommazahl mit doppelter Genauigkeit und Vorzeichen, die den Punkt definiert, ab dem der Server als knapp an Arbeitsspeicher gilt, ausgedrückt als Prozentsatz des gesamten physischen Arbeitsspeichers. Wenn dieser Grenzwert erreicht wird, beginnt die Instanz langsam, Arbeitsspeicher in Caches zu bereinigen, indem abgelaufene Sitzungen geschlossen und nicht verwendete Berechnungen entladen werden. Der Server gibt keinen Arbeitsspeicher unter diesem Grenzwert frei. Der Standardwert ist 65. Dieser Wert besagt, dass der Grenzwert für ungenügenden Arbeitsspeicher 65 % des physischen Speichers bzw. virtuellen Adressraums entspricht, je nachdem, welcher dieser Werte niedriger ist.  
  
 `TotalMemoryLimit`  
 Definiert einen Schwellenwert, ab dem der Server Arbeitsspeicher aggressiver freigibt. Der Standardwert ist 80 % des physischen Speichers oder des virtuellen Adressraums, je nachdem, welcher dieser Werte niedriger ist.  
  
 Beachten Sie, dass `TotalMemoryLimit` immer kleiner als `HardMemoryLimit` sein muss.  
  
 `HardMemoryLimit`  
 Gibt einen Arbeitsspeicherschwellenwert an, ab dem die Instanz aktive Benutzersitzungen aggressiv beendet, um die Speicherauslastung zu reduzieren. Alle beendeten Sitzungen empfangen eine Fehlermeldung, dass der Abbruch der Sitzung durch ungenügenden Arbeitsspeicher bedingt ist. Der Standardwert 0 (null) bedeutet, dass die `HardMemoryLimit` festgelegt auf einen mittleren Wert zwischen `TotalMemoryLimit` und der gesamte physische Speicher des Systems festgelegt wird; Wenn der physische Speicher des Systems größer als der virtuelle Adressraum der Prozesses ist, dann virtuelle Adresse Speicherplatz wird stattdessen verwendet werden, berechnen `HardMemoryLimit`.  
  
 `VirtualMemoryLimit`  
 Eine erweiterte Eigenschaft, die nur mithilfe der Schritte in [!INCLUDE[msCoName](../../includes/msconame-md.md)] geändert werden sollte.  
  
 `VertiPaqPagingPolicy`  
 Gibt das Auslagerungsverhalten an, das bei ungenügendem Arbeitsspeicher des Servers angewendet wird. Gültige Werte sind:  
  
 0 (null) (**0**) deaktiviert das Auslagern. Wenn der Arbeitsspeicher nicht ausreicht, schlägt die Verarbeitung mit dem Fehler "Nicht genügend Arbeitsspeicher" fehl. Wenn Sie die Auslagerung deaktivieren, müssen Sie für das Dienstkonto Windows-Berechtigungen erteilen. Anweisungen finden Sie unter [Konfigurieren von Dienstkonten &#40;Analysis Services&#41;](../instances/configure-service-accounts-analysis-services.md).  
  
 Der Standardwert ist**1** . Diese Eigenschaft ermöglicht die Auslagerung auf Datenträger unter Verwendung der Auslagerungsdatei des Betriebssystems (pagefile.sys).  
  
 Wenn `VertiPaqPagingPolicy` je nastaven Verarbeitung auf 1 ist weniger wahrscheinlich aufgrund von arbeitsspeicherbeschränkungen fehlschlägt, da der Server versucht wird, um anhand der von Ihnen angegebenen Methode auf Datenträger auszulagern. Das Festlegen der `VertiPaqPagingPolicy`-Eigenschaft ist keine Garantie dafür, dass niemals Arbeitsspeicherfehler auftreten. Unter folgenden Bedingungen können weiterhin Fehler aufgrund von unzureichendem Arbeitsspeicher auftreten:  
  
-   Es ist nicht genügend Arbeitsspeicher für alle Wörterbücher verfügbar. Während der Verarbeitung wird Analysis Services die Wörterbüchern für jede Spalte im Arbeitsspeicher gesperrt, und diese dürfen nicht mehr als der angegebene Wert für `VertiPaqMemoryLimit`.  
  
-   Der virtuelle Adressraum reicht nicht aus, um den Prozess aufzunehmen.  
  
 Um wiederholte Fehler aufgrund von unzureichendem Arbeitsspeicher zu vermeiden, können Sie das Modell umgestalten, um die verarbeitete Datenmenge zu reduzieren, oder den physischen Arbeitsspeicher des Computers erweitern.  
  
 Gilt nur für den tabellarischen Servermodus.  
  
 `VertiPaqMemoryLimit`  
 Wenn die Auslagerung auf Datenträger zulässig ist, gibt diese Eigenschaft die Arbeitsspeichernutzung (als Prozentsatz des gesamten Arbeitsspeichers) beim Start der Auslagerung an. Der Standardwert ist 60. Wenn die Arbeitsspeichernutzung weniger als 60 Prozent beträgt, führt der Server keine Auslagerung auf Datenträger aus.  
  
 Diese Eigenschaft hängt die `VertiPaqPagingPolicyProperty`, die muss festgelegt werden, um 1, damit auslagerungen stattfinden.  
  
 Gilt nur für den tabellarischen Servermodus.  
  
 `HighMemoryPrice`  
 Eine erweiterte Eigenschaft, die nur mithilfe der Schritte in [!INCLUDE[msCoName](../../includes/msconame-md.md)] geändert werden sollte.  
  
 `MemoryHeapType`  
 Eine erweiterte Eigenschaft, die nur mithilfe der Schritte in [!INCLUDE[msCoName](../../includes/msconame-md.md)] geändert werden sollte.  
  
 Gilt nur für den mehrdimensionalen Servermodus.  
  
 `HeapTypeForObjects`  
 Eine erweiterte Eigenschaft, die nur mithilfe der Schritte in [!INCLUDE[msCoName](../../includes/msconame-md.md)] geändert werden sollte.  
  
 Gilt nur für den mehrdimensionalen Servermodus.  
  
 `DefaultPagesCountToReuse`  
 Eine erweiterte Eigenschaft, die nur mithilfe der Schritte in [!INCLUDE[msCoName](../../includes/msconame-md.md)] geändert werden sollte.  
  
 `HandleIA64AlignmentFaults`  
 Eine erweiterte Eigenschaft, die nicht ohne die Unterstützung von [!INCLUDE[msCoName](../../includes/msconame-md.md)] geändert werden sollte.  
  
 `MidMemoryPrice`  
 Eine erweiterte Eigenschaft, die nicht ohne die Unterstützung von [!INCLUDE[msCoName](../../includes/msconame-md.md)] geändert werden sollte.  
  
 `MinimumAllocatedMemory`  
 Eine erweiterte Eigenschaft, die nicht ohne die Unterstützung von [!INCLUDE[msCoName](../../includes/msconame-md.md)] geändert werden sollte.  
  
 `PreAllocate`  
 Eine erweiterte Eigenschaft, die nicht ohne die Unterstützung von [!INCLUDE[msCoName](../../includes/msconame-md.md)] geändert werden sollte.  
  
 `SessionMemoryLimit`  
 Eine erweiterte Eigenschaft, die nicht ohne die Unterstützung von [!INCLUDE[msCoName](../../includes/msconame-md.md)] geändert werden sollte.  
  
 `WaitCountIfHighMemory`  
 Eine erweiterte Eigenschaft, die nur mithilfe der Schritte in [!INCLUDE[msCoName](../../includes/msconame-md.md)] geändert werden sollte.  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren von Servereigenschaften in Analysis Services](server-properties-in-analysis-services.md)   
 [Bestimmen des Servermodus einer Analysis Services-Instanz](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
