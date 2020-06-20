---
title: Servereigenschaften (Seite „Speicher“) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.serverproperties.memory.f1
ms.assetid: 46a77d4e-ab92-49d3-a14b-423462e50715
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0ee690ddfc4cc02769db6d07d226cb154f3c4eae
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84934921"
---
# <a name="server-properties-memory-page"></a>Servereigenschaften (Seite Arbeitsspeicher)
  Auf dieser Seite können Sie die Arbeitsspeichereinstellungen für den Server anzeigen und bearbeiten. Wenn für **Minimaler Serverarbeitsspeicher** 0 und für **Maximaler Serverarbeitsspeicher** 2147483647 MB festgelegt sind, kann [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zu jeder Zeit die optimale Menge an Arbeitsspeicher nutzen, abhängig davon, wie viel Arbeitsspeicher vom Betriebssystem und von anderen Anwendungen aktuell verwendet wird. Mit der wechselnden Auslastung des Computers und von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ändert sich auch der zugeordnete Arbeitsspeicher. Sie können außerdem diese dynamische Arbeitsspeicherbelegung mit den unten angegebenen Minimal- und Maximalwerten begrenzen.  
  
## <a name="options"></a>Tastatur  
 **Minimaler Serverarbeitsspeicher (in MB)**  
 Gibt an, dass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mit der angegebenen Mindestgröße des zugeordneten Speichers beginnen und unterhalb dieses Werts keinen Speicher freigeben sollte. Legen Sie diesen Wert auf der Basis der Größe und Aktivität Ihrer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]fest. Diese Option sollte immer auf einen geeigneten Wert festgelegt werden, um sicherzustellen, dass das Betriebssystem nicht zu viel Arbeitsspeicher von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] anfordert und dadurch die Leistung von Windows beeinträchtigt.  
  
 **Maximaler Serverarbeitsspeicher (in MB)**  
 Gibt an, wie viel Arbeitsspeicher [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] beim Starten und zur Laufzeit maximal zuordnen kann. Diese Serverkonfigurationsoption kann auf einen bestimmten Wert festgelegt werden, wenn Sie wissen, dass mehrere Anwendungen gleichzeitig mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt werden, und Sie sicherstellen möchten, dass diese Anwendungen über genügend Arbeitsspeicher verfügen. Wenn diese Anwendungen, z. B. Webserver oder E-Mail-Server, Arbeitsspeicher nur bei Bedarf anfordern, legen Sie die Option nicht fest, da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in diesem Fall Arbeitsspeicher für sie nach Bedarf freigibt. Viele Anwendungen verwenden jedoch beim Starten den gesamten verfügbaren Arbeitsspeicher und fordern keinen weiteren Arbeitsspeicher mehr an, selbst wenn er benötigt wird. Wenn eine Anwendung, die sich so verhält, auf demselben Computer gleichzeitig mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ausgeführt wird, legen Sie die Option auf einen Wert fest, der sicherstellt, dass der von der Anwendung benötigte Arbeitsspeicher nicht von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]zugeordnet wird. Die Mindestmenge an Arbeitsspeicher, die Sie für **Max. Server Arbeitsspeicher** angeben können, beträgt 64 Megabyte (MB) für 32-Bit-Systeme und 128 MB für 64-Bit-Systeme.  
  
 **Arbeitsspeicher für Indexerstellung (in KB, 0 = dynamischer Speicher)**  
 Gibt die Größe des Arbeitsspeichers (in kB) an, die während der Sortiervorgänge bei der Indexerstellung verwendet wird. Der Standardwert 0 ermöglicht die dynamische Zuordnung und sollte in den meisten Fällen ohne weitere Anpassungen funktionsfähig sein. Der Benutzer kann jedoch einen anderen Wert zwischen 704 und 2147483647 eingeben.  
  
> [!NOTE]  
>  Werte zwischen 1 und 703 sind nicht zulässig. Wenn ein Wert innerhalb dieses Bereichs eingegeben wird, wird er mit 704 überschrieben.  
  
 **Minimaler Arbeitsspeicher pro Abfrage (in KB)**  
 Gibt die Größe des Arbeitsspeichers (in kB) an, der für die Ausführung einer Abfrage zugeordnet wird. Der Benutzer kann einen Wert zwischen 512 und 2147483647 kB festlegen. Der Standardwert ist 1024 KB.  
  
 **Konfigurierte Werte**  
 Zeigt für die Optionen in diesem Bereich konfigurierte Werte an. Wenn Sie diese Werte ändern, klicken Sie anschließend auf **Ausgeführte Werte** , um zu sehen, ob die Änderungen wirksam sind. Sind sie nicht wirksam, muss die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zuerst neu gestartet werden.  
  
 **Ausgeführte Werte**  
 Zeigt die derzeit aktiven Werte für die Optionen in diesem Bereich an. Diese Werte sind schreibgeschützt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [Serverkonfigurationsoptionen für den Serverarbeitsspeicher](server-memory-server-configuration-options.md)  
  
  
