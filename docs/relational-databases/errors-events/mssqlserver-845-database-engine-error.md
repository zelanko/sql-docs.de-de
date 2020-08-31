---
description: MSSQLSERVER_845
title: MSSQLSERVER_845 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 845 (Database Engine error)
ms.assetid: 8fff6ad4-234c-44be-b123-e25d5e1cd63e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b4d474714579397d18e22f2c32cc540ff30d5ac0
ms.sourcegitcommit: a0245fdae1ff9045f587a3a67b72f34405d35a4f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/19/2020
ms.locfileid: "88618075"
---
# <a name="mssqlserver_845"></a>MSSQLSERVER_845
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Details  
  
| attribute | Wert |  
| :-------- | :---- |  
|Produktname|SQL Server|  
|Ereignis-ID|845|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|BUFLATCH_TIMEOUT|  
|Meldungstext|Timeout beim Warten auf Pufferlatchtyp %d für Seite %S_PGID, Datenbank-ID %d.|  
  
## <a name="explanation"></a>Erklärung  
Ein Prozess hat auf die Beschaffung eines Latchs gewartet, aber für den Prozess wurde so lange gewartet, bis das Zeitlimit abgelaufen und die Beschaffung nicht mehr möglich war. Dies kann auftreten, wenn das Ausführen eines E/A-Vorgangs zu lange dauert, was normalerweise daraus resultiert, dass Systemprozesse durch andere Tasks blockiert werden. In manchen Fällen kann dieser Fehler auch das Ergebnis eines Hardwarefehlers sein.  
  
## <a name="cause"></a>Ursache
Diese Fehlermeldung hängt von der allgemeinen Umgebung Ihres Systems ab. Jeder der folgenden Umstände kann zu einem überbeanspruchten System führen:

- Hardware, die Ihre Anforderungen an E/A (Eingabe/Ausgabe) und Arbeitsspeicher nicht erfüllen kann
- Fehlerhaft konfigurierte und getestete Einstellungen
- Ineffizienter Entwurf

 Möglicherweise tritt der Fehler 845 auf, wenn Ihr System stark ausgelastet ist und die Arbeitsauslastungsanforderungen nicht erfüllen kann. Einige der häufigsten Gründe für eine überbeanspruchte Umgebung sind die folgenden:

- Hardwareprobleme
- Komprimierte Volumes
- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Konfigurationseinstellungen, die nicht den Standardwerten entsprechen
- Ineffiziente Abfragen oder ineffizienter Indexentwurf
- Häufige AutoGrow- oder AutoShrink-Datenbankvorgänge

## <a name="user-action"></a>Benutzeraktion  
Versuchen Sie Folgendes, um zu verhindern, dass der Fehler erneut auftritt:  
  
- Ermitteln Sie, ob Hardwareengpässe vorliegen. Unter [Identifizieren von Engpässen](../performance/identify-bottlenecks.md) erhalten Sie Informationen hierzu. Führen Sie, wenn erforderlich, ein Upgrade für Ihre Hardware durch, damit sie die Anforderungen der Konfiguration Ihrer Umgebung, Ihrer Abfragen und der Auslastung erfüllen kann.

- Überprüfen Sie, ob alle Hardwarefunktionen fehlerfrei funktionieren. Überprüfen Sie alle protokollierten Fehler, und führen Sie alle von Ihrem Hardwarehersteller bereitgestellten Diagnosen aus. Führen Sie eine Überprüfung auf zugehörige E/A-Fehler im Fehlerprotokoll oder Ereignisprotokoll aus. E/A-Fehler deuten normalerweise auf eine Datenträgerfehlfunktion hin.  
- Sorgen Sie dafür, dass Ihre Datenträgervolumes nicht komprimiert sind. Das Speichern von Daten sowie Protokolldateien für komprimierte Laufwerke werden nicht unterstützt. Weitere Informationen hierzu finden Sie unter [Datenbankdateien und Dateigruppen](../databases/database-files-and-filegroups.md). Weitere Informationen zur Unterstützung komprimierter Laufwerke finden Sie im folgenden Artikel: [Beschreibung der Unterstützung für SQL Server-Datenbanken auf komprimierten Laufwerken](https://support.microsoft.com/EN-US/help/231347)

- Überprüfen Sie, ob die Fehlermeldungen nicht mehr angezeigt werden, wenn Sie alle der folgenden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Konfigurationsoptionen deaktivieren:
   - Die [Option für Prioritätserhöhung](../../database-engine/configure-windows/configure-the-priority-boost-server-configuration-option.md)
   - Die [Lightweightpoolingoption (Fibermodus)](../../database-engine/configure-windows/lightweight-pooling-server-configuration-option.md)
   - Die [Option „Festgelegte Workingsetgröße“](../../database-engine/configure-windows/set-working-set-size-server-configuration-option.md)

    Weitere Informationen finden Sie unter [ Bestimmen geeigneter SQL Server-Konfigurationseinstellungen](https://support.microsoft.com/EN-US/help/319942)

- Optimieren Sie die Abfragen, um die für das System verwendeten Ressourcen zu reduzieren. Durch Leistungsoptimierung kann die Belastung für ein System reduziert und die Reaktionszeit für einzelne Abfragen verbessert werden.
- Legen Sie die AutoShrink-Eigenschaft auf OFF fest, um den Aufwand für Änderungen an der Datenbankgröße zu verringern.
- Stellen Sie sicher, dass Sie die AutoGrow-Eigenschaft auf Inkremente festlegen, die groß genug sind und somit nicht häufig auftreten. Planen Sie einen Auftrag, um den verfügbaren Speicherplatz in den Datenbanken zu überprüfen, und erhöhen Sie dann die Datenbankgröße außerhalb der Spitzenzeiten.
- Überprüfen Sie das Fehlerprotokoll auf Tasks, die kein Ergebnis bereitstellen, sowie auf andere kritische Fehler. Beheben Sie diese Fehler zunächst, da sie auf die Grundursache des zugrunde liegenden Problems hindeuten könnten.
- Wenn kritische Fehler, z. B. Assert-Vorgänge, häufig auftreten, beheben Sie diese Probleme.
- Wenn 845-Fehlermeldungen selten auftreten, können Sie sie ignorieren.