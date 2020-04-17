---
title: Implementieren von Assemblys | Microsoft Docs
description: Erfahren Sie, wie Sie mit Assemblys arbeiten, die auf SQL Server gehostet werden, einschließlich erstellen/ändern von Assemblys, Löschen oder Aktivieren/Deaktivieren von Assemblys und Verwalten von Versionen.
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- assemblies [CLR integration], implementing
ms.assetid: c228d7bf-a906-4f37-a057-5d464d962ff8
author: rothja
ms.author: jroth
ms.openlocfilehash: 807ed6a6f0d59444cd38f7fdf902a7c3fc1b47d8
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81488043"
---
# <a name="assemblies---implementing"></a>Assemblys: Implementierung
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Dieser Abschnitt enthält Informationen zu folgenden Themen, die Sie hilfreich beim Implementieren und Arbeiten mit Assemblys in der Datenbank sind:  
  
-   Erstellen von Assemblys  
  
-   Ändern von Assemblys  
  
-   Löschen, Deaktivieren und Aktivieren von Assemblys  
  
-   Verwalten von Assemblyversionen  
  
## <a name="creating-assemblies"></a>Erstellen von Assemblys  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] werden Assemblys mit der [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung CREATE ASSEMBLY erstellt. In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] mit dem Assembly-Editorassistenten. Darüber hinaus registriert die Bereitstellung [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] eines SQL Server-Projekts in einer Assembly in der Datenbank, die für das Projekt angegeben wurde. Weitere Informationen finden Sie unter [Deploying CLR Database Objects](../../relational-databases/clr-integration/deploying-clr-database-objects.md).  
  
 **Erstellen einer Assembly mit Transact-SQL**  
  
-   [CREATE ASSEMBLY &#40;Transact-SQL&#41;](../../t-sql/statements/create-assembly-transact-sql.md)  
  
 **Erstellen einer Assembly mit SQL Server Management Studio**  
  
-   [Assemblyeigenschaften &#40;allgemeine s&#41;](../../relational-databases/clr-integration/assemblies-properties.md)  
  
## <a name="modifying-assemblies"></a>Ändern von Assemblys  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] werden Assemblys mit der [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung ALTER ASSEMBLY geändert. In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] mit dem Assembly Assisted Editor. Eine Assembly können Sie wie folgt ändern:  
  
-   Ändern der Implementierung der Assembly durch Hochladen einer neueren Version der Binärdateien der Assembly. Weitere Informationen finden Sie unter [Verwalten von Assemblyversionen](#_managing) weiter unten in diesem Thema.  
  
-   Ändern des Berechtigungssatzes der Assembly. Weitere Informationen finden Sie unter [Entwerfen von Assemblys](../../relational-databases/clr-integration/assemblies-designing.md).  
  
-   Ändern der Sichtbarkeit der Assembly. Sichtbare Assemblys sind in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] für Verweise verfügbar. Nicht sichtbare Assemblys sind nicht verfügbar, dies gilt auch dann, wenn sie in die Datenbank hochgeladen wurden. Assemblys, die in eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] hochgeladen wurden, sind standardmäßig sichtbar.  
  
-   Hinzufügen oder Löschen einer der Assembly zugeordneten Debug- oder Quelldatei.  
  
 **Ändern einer Assembly mit Transact-SQL**  
  
-   [ALTER ASSEMBLY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-assembly-transact-sql.md)  
  
 **Ändern einer Assembly mit SQL Server Management Studio**  
  
-   [Assemblyeigenschaften &#40;allgemeine s&#41;](../../relational-databases/clr-integration/assemblies-properties.md)  
  
## <a name="dropping-disabling-and-enabling-assemblies"></a>Löschen, Deaktivieren und Aktivieren von Assemblys  
 Assemblys werden mit der [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung DROP ASSEMBLY oder mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] gelöscht.  
  
 **Löschen einer Assembly mit Transact-SQL**  
  
-   [DROP ASSEMBLY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-assembly-transact-sql.md)  
  
 **Löschen einer Assembly mit SQL Server Management Studio**  
  
-   [Objekte löschen](../../ssms/object/delete-objects.md)  
  
 Standardmäßig ist die Ausführung aller in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erstellten Assemblys deaktiviert. Sie können die Option **clr enabled** der **sp_configure** gespeicherten Systemprozedur verwenden, um [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]die Ausführung aller Assemblys zu deaktivieren oder zu aktivieren, die in hochgeladen werden. Die Deaktivierung der Assemblyausführung verhindert die Ausführung von CLR-Funktionen (Common Language Runtime), gespeicherter Prozeduren, Trigger, Aggregate und benutzerdefinierter Typen – gerade ausgeführte werden beendet. Die Deaktivierung der Assemblyausführung deaktiviert nicht die Möglichkeit, Assemblys zu erstellen, zu ändern oder zu löschen. Weitere Informationen finden Sie unter [clr enabled Server Configuration Option](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md).  
  
 **Deaktivieren und Aktivieren der Assemblyausführung**  
  
-   [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
##  <a name="managing-assembly-versions"></a><a name="_managing"></a>Verwalten von Assemblyversionen  
 Wenn eine Assembly in eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz hochgeladen wird, wird es in den Datenbanksystemkatalogen gespeichert und verwaltet. Alle Änderungen, die an der [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Definition der Assembly im assembly vorgenommen werden, sollten an die Assembly weitergegeben werden, die im Datenbankkatalog gespeichert ist.  
  
 Zum Ändern einer Assembly müssen Sie eine ALTER ASSEMBLY-Anweisung ausgeben, die die Assembly in der Datenbank aktualisiert. Dadurch wird die Assembly mit der aktuellsten Kopie der [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]-Module aktualisiert, die ihre Implementierung enthalten.  
  
 Mit der WITH UNCHECKED DATA-Klausel der ALTER ASSEMBLY-Anweisung wird [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] angewiesen, auch die Assemblys zu aktualisieren, von denen in der Datenbank persistente Daten abhängen. WITH UNCHECKED DATA müssen Sie insbesondere dann angeben, wenn folgende Bedingungen erfüllt sind:  
  
-   Persistente berechnete Spalten, die über [!INCLUDE[tsql](../../includes/tsql-md.md)]-Funktionen oder -Methoden entweder direkt oder indirekt auf Methoden der Assembly verweisen.  
  
-   Spalten eines CLR-benutzerdefinierten Typs, die von der Assembly abhängen, wobei der Typ ein Serialisierungsformat vom Typ **UserDefined** (nicht **Native**) implementiert.  
  
> [!CAUTION]  
>  Wird WITH UNCHECKED DATA nicht angegeben, versucht [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], die Ausführung von ALTER ASSEMBLY zu verhindern, wenn die neue Assemblyversion Auswirkungen auf vorhandene Daten in Tabellen, Indizes oder anderen persistenten Sites hat. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] garantiert jedoch nicht, dass berechnete Spalten, Indizes, indizierte Sichten oder Ausdrücke mit den zugrunde liegenden Routinen und Typen konsistent sein werden, wenn die CLR-Assembly aktualisiert wird. Gehen Sie beim Ausführen von ALTER ASSEMBLY mit Vorsicht vor, um sicherzustellen, dass es keine fehlende Übereinstimmung zwischen dem Ergebnis eines Ausdrucks und einem auf diesem Ausdruck basierenden Wert, der in der Assembly gespeichert ist, gibt.  
  
 Nur Mitglieder der **db_owner-** und **db_ddlowner** festen Datenbankrolle können ALTER ASSEMBLY mithilfe der WITH UNCHECKED DATA-Klausel ausführen.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sendet eine Meldung an das Windows-Anwendungsereignisprotokoll, die angibt, dass die Assembly mit ungeprüften Daten in den Tabellen geändert wurde. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] markiert anschließend alle Tabellen mit Daten, die von der Assembly abhängen, als ungeprüft. Die **Spalte has_unchecked_assembly_data** der Katalogansicht **sys.tables** enthält den Wert 1 für Tabellen, die ungeprüfte Daten enthalten, und 0 für Tabellen ohne ungeprüfte Daten.  
  
 Um die Integrität ungeprüfter Daten aufzulösen, führen Sie DBCC CHECKDB WITH EXTENDED_LOGICAL_CHECKS für jede Tabelle aus, die über ungeprüfte Daten verfügt. Wenn DBCC CHECKDB WITH EXTENDED_LOGICAL_CHECKS fehlschlägt, müssen Sie entweder die ungültigen Tabellenzeilen löschen oder den Assemblycode ändern, um Probleme zu beheben, und dann zusätzliche ALTER ASSEMBLY-Anweisungen ausstellen.  
  
 Mit ALTER ASSEMBLY wird die Assemblyversion geändert. Das Kultur- und das öffentliche Schlüsseltoken der Assembly bleiben unverändert. SQL Server erlaubt nicht das Registrieren verschiedener Versionen einer Assembly mit demselben Namen, derselben Kultur und demselben öffentlichen Schlüssel.  
  
### <a name="interactions-with-computer-wide-policy-for-version-binding"></a>Interaktionen mit der für den gesamten Computer geltenden Richtlinie zur Versionsbindung  
 Wenn in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gespeicherte Verweise auf Assemblys mit der Herausgeberrichtlinie oder einer für den gesamten Computer geltenden Administratorrichtlinie an spezifische Versionen umgeleitet werden, müssen Sie eine der folgenden Maßnahmen ergreifen:  
  
-   Stellen Sie sicher, dass sich die neue Version, auf die umgeleitet wird, in der Datenbank befindet.  
  
-   Ändern Sie alle Anweisungen der externen Richtliniendatei des Computers oder der Herausgeberrichtlinie, damit diese auf die in der Datenbank vorhandene Version verweisen.  
  
 Anderenfalls verursacht das Laden einer neuen Assemblyversion in die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz einen Fehler.  
  
 **Aktualisieren der Version einer Assembly**  
  
-   [ALTER ASSEMBLY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-assembly-transact-sql.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Assemblys &#40;Database Engine&#41;](../../relational-databases/clr-integration/assemblies-database-engine.md)   
 [Abrufen von Informationen zu Assemblys](../../relational-databases/clr-integration/assemblies-getting-information.md)  
  
  
