---
title: Wichtige Änderungen von Analysis Services-Funktionen in SQLServer 2014 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- breaking changes [Analysis Services]
- upgrading Analysis Services
ms.assetid: aeb02542-5a6c-458c-a110-13413dd3e9d9
caps.latest.revision: 46
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 6c073653411a1d6a06569c2873d68e29b6a39719
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36147796"
---
# <a name="breaking-changes-to-analysis-services-features-in-sql-server-2014"></a>Wichtige Änderungen von Analysis Services-Funktionen in SQL Server 2014
  In diesem Thema werden wichtige Änderungen in [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)]beschrieben. Diese Änderungen können zur Funktionsunfähigkeit von Anwendungen, Skripts oder Funktionen führen, die auf früheren Versionen von SQL Server basieren.  
  
 In diesem Thema:  
  
-   [Wichtige Änderungen in SQLServer 2014](#bkmk_sql2014)  
  
-   [Wichtige Änderungen in SQL Server 2012 SP1](#bkmk_2012Sp1)  
  
-   [Wichtige Änderungen in SQLServer 2012](#bkmk_sql11)  
  
-   [Wichtige Änderungen in SQL Server 2008 oder SQL Server 2008 R2](#bkmk_sql10)  
  
##  <a name="bkmk_sql2014"></a> Wichtige Änderungen in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]  
 Es gibt keine neuen aktuellen Änderungen für tabellarische, mehrdimensionale, Datamining-angekündigt oder [!INCLUDE[ssGeminiShort](../includes/ssgeminishort-md.md)] Funktionen in dieser Version.  Allerdings da [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)] sehr ähnelt der [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] und [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)] Versionen werden aktuelle Änderungen aus den beiden vorherigen Versionen finden Sie hier zur Vereinfachung für den Fall, dass beim Aktualisieren von [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)].  
  
##  <a name="bkmk_2012Sp1"></a> Wichtige Änderungen in SQL Server 2012 SP1  
 Globalisierungsbezogene Codeänderungen haben in der Vergangenheit zur Funktionsunfähigkeit einiger Anwendungen geführt. Zu den bekannten Problemen gehören:  
  
 **Kleinschreibung von Objektbezeichnern**  
 Eine Codeänderung, die dazu vorgesehen war, die Groß-/Kleinschreibung bei allen Objektbezeichnern nicht zu unterscheiden, hat für einige Sprachen den gegenteiligen Effekt. Die Absicht ist, dass bei allen Objektbezeichnern unabhängig von der Sortierung keine Unterscheidung nach Groß-/Kleinschreibung erfolgt. Diese Änderung richtet Analysis Services an anderen Anwendungen aus, die normalerweise im gleichen Projektmappenstapel verwendet werden.  
  
 Für Sprachen, die auf den 26 Zeichen des standardlateinischen Alphabets basieren, wird bei Objektbezeichnern die Groß-/Kleinschreibung jetzt nicht mehr unterschieden, wie ursprünglich beabsichtigt.  
  
 Bei Kyrillisch und anderen „bikameralen“ Sprachskripts, die Groß- und Kleinbuchstaben verwenden (Griechisch, Armenisch und Koptisch), wird bei Objektbezeichnern jetzt die Groß-/Kleinschreibung unterschieden. Problematische Änderungen treten am wahrscheinlichsten auf, wenn es einen Unterschied zwischen der Schreibweise eines Objektbezeichners und der Art und Weise gibt, wie auf ihn verwiesen wird (z. B. ein Verarbeitungsskript, das auf den klein geschriebenen Objektbezeichner verweist). Dieses Verhalten ändert sich wahrscheinlich in der Zukunft, aber als vorübergehende Problemumgehung wird empfohlen, die Skripts so zu ändern, dass sie die gleiche Schreibweise wie der Objektbezeichner verwenden.  
  
##  <a name="bkmk_sql11"></a> Wichtige Änderungen in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]  
 In diesem Abschnitt werden die Änderungen, die für ausgegebene [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Funktionen in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)].  
  
|Problem|Description|  
|-----------|-----------------|  
|Setupbefehle für eine [!INCLUDE[ssGeminiShort](../includes/ssgeminishort-md.md)]-Installation wurden entfernt.|[!INCLUDE[ssGeminiShort](../includes/ssgeminishort-md.md)] wird von Setup installiert, aber nicht mehr konfiguriert. Setupbefehle, die Werte für Konfigurationsaktionen sammelten, wurden entfernt. Dazu gehören /FARMACCOUNT, /FARMPASSWORD, /PASSPHRASE und /FARMADMINPORT.<br /><br /> Wenn Sie Installationsskripts für ein unbeaufsichtigtes Setup erstellt haben, müssen Sie diese Skripts zu einer [!INCLUDE[ssGeminiShort](../includes/ssgeminishort-md.md)]-Installation ändern. Alternativ können Sie PowerShell-Cmdlets verwenden, um den Server im unbeaufsichtigten Modus zu konfigurieren. Weitere Informationen finden Sie unter [Installieren von PowerPivot über die Eingabeaufforderung](../../2014/sql-server/install/install-powerpivot-from-the-command-prompt.md) und [PowerPivot-Konfiguration mit Windows PowerShell](power-pivot-sharepoint/power-pivot-configuration-using-windows-powershell.md).|  
  
##  <a name="bkmk_sql10"></a> Wichtige Änderungen in [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]/[!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]  
 Dieser Abschnitt enthält alle wichtigen Änderungen gegenüber vorherigen Versionen. Wenn Sie ein Upgrade von [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] ausführen, sollten Sie die wichtigen Änderungen überprüfen, die in [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] und [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] eingeführt wurden.  
  
|Problem|Description|  
|-----------|-----------------|  
|Die flache Exists-Funktion funktioniert jetzt anders für benannte Mengen, die aufgelistete Mitglieder oder Kreuzverknüpfungen von Enumsets enthalten.|In [!INCLUDE[ssASversion2005](../includes/ssasversion2005-md.md)] konnte die flache Exists-Funktion nicht für benannte Mengen verwendet werden, die aufgelistete Member oder Kreuzjoins von Enumsets enthielt. Um eine Abwärtskompatibilität zur Originalversion und SP1 von [!INCLUDE[ssASversion2005](../includes/ssasversion2005-md.md)] zu erzielen, können Sie die Konfigurationseigenschaft ConfigurationSettings\OLAP\Query\NamedSetShallowExistsMode auf 1 setzen, und für die Abwärtskompatibilität mit [!INCLUDE[ssASversion2005](../includes/ssasversion2005-md.md)] SP2 auf 2.|  
|VBA-Funktionen behandeln Nullwerte und leere Werte anders, als dies im Fall war. [!INCLUDE[ssASversion2005](../includes/ssasversion2005-md.md)]|In [!INCLUDE[ssASversion2005](../includes/ssasversion2005-md.md)], gaben VBA-Funktionen zurückgegebenen 0 oder eine leere Zeichenfolge, wenn entweder null-Werte oder leere Werte als Argumente verwendet wurden. In [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] wird NULL zurückgegeben.|  
|Der Paketmigrations-Assistent schlägt fehl, da DSO nicht standardmäßig installiert wird.|Standardmäßig installiert SQL Server 2008 die DSO-Abwärtskompatibilitätskomponente (Decision Support Objects) nicht. Das Abwärtskompatibilitätskomponenten-Paket wird zwar standardmäßig installiert, aber die DSO-Komponente des Pakets wird deaktiviert. Da der SQL Server-Migrations-Assistent für Analysis Services auf diese Komponente angewiesen ist, schlägt er fehl, wenn die Komponente nicht installiert wird. Gehen Sie zum Installieren der DSO-Komponente wie folgt vor:<br /><br /> (1) Öffnen der Systemsteuerung.<br />2) Wählen Sie in Windows XP oder Windows Server 2003, **Software**. Wählen Sie unter Windows Vista und Windows Server 2008 **Programme und Funktionen**aus.<br />(3) mit der rechten Maustaste **Microsoft SQL Server 2005-Abwärtskompatibilität**, und wählen Sie **Änderung**.<br />(4) im Backward Compatibility-Setup-Assistenten, klicken Sie auf **Weiter**.<br />5) Wählen Sie auf der Seite "Programmwartung" **ändern**, und klicken Sie dann auf **Weiter**.<br />6) auf der Seite "Funktionsauswahl", wenn Decision Support Objects (DSO) nicht verfügbar ist, klicken Sie auf den Pfeil nach unten, und wählen Sie **dieses Feature wird auf der lokalen Festplatte installiert**. Klicken Sie auf **Weiter**.<br />7) kann nun auf der Seite "Programm" zu ändern, klicken Sie auf **installieren**.<br />8) Wenn die Installation abgeschlossen ist, klicken Sie auf **Fertig stellen**.<br /><br /> <br /><br /> Sie können die DSO nach Abschluss der Migration mit den folgenden Schritten entfernen und die Option für DSO in**Diese Funktion wird nicht verfügbar sein**ändern.<br /><br /> Wenn das Abwärtskompatibilitätspaket nicht installiert wurde, können Sie es von den SQL Server 2008-Verteilungsmedien installieren. Beachten Sie, dass es Versionen für jede Zielarchitektur (x86, x64, ia64) gibt. Diese Versionen befinden sich an den folgenden Speicherorten:<br /><br /> x86\Setup\x86\SQLServer2005_BC.msi<br /><br /> x64\Setup\x64\SQLServer2005_BC.msi<br /><br /> ia64\Setup\ia64\SQLServer2005_BC.msi|  
|Es wird nicht empfohlen, den Speicherort der Partition im Datenordner abzulegen.|Der Server verwaltet die Datenordner und erstellt oder löscht Ordner, wenn Objekte erstellt, gelöscht und geändert werden. Deshalb wird dringend davon abgeraten, einen Partitionsspeicherort im Datenordner anzugeben, insbesondere in den Unterordnern für Datenbanken, Cubes und Dimensionen. Obwohl der Server das Erstellen oder Ändern zulässt, zeigt er eine Warnung an. Beim Aktualisieren von Datenbanken von SQL Server 2005 Analysis Services auf [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] Analysis Services, die partitionsspeicherorte im Datenordner verfügen, funktioniert es. Zum Wiederherstellen oder Synchronisieren müssen Sie die Partitionsspeicherorte aus dem Datenordner verschieben.|  
|Möglicherweise erhalten Sie unerwartete Ergebnisse für Abfragen, die das MDX-Schlüsselwort „EXISTING“ in ProClarity Analytics Server und Microsoft Office PerformancePoint Server 2007 verwenden.|ProClarity Analytics Server und Microsoft Office PerformancePoint Server 2007 verwenden das Schlüsselwort EXISTING in bestimmten Szenarien in MDX nicht korrekt. Aufgrund von Änderungen in [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] Analysis Services, diese Abfragen möglicherweise unerwartete Ergebnisse zurück.|  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services-Abwärtskompatibilität](analysis-services-backward-compatibility.md)  
  
  