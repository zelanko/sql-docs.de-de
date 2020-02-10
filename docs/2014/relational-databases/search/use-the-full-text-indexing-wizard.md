---
title: Verwenden des Volltextindizierungs-Assistenten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextindexingwizard.selecttablecolumns.f1
- sql12.swb.fulltextindexingwizard.welcome.f1
- sql12.swb.fulltextindexingwizard.selectacatalog.f1
- sql12.swb.fulltextindexingwizard.progress.f1
- sql12.swb.fulltextindexingwizard.selectorcreatepopschedules.f1
- sql12.swb.fulltextindexingwizard.selectatableorview.f1
- sql12.swb.fulltextindexingwizard.selectchangetracking.f1
- sql12.swb.fulltextindexingwizard.selectanindex.f1
- sql12.swb.fulltextindexingwizard.summary.f1
helpviewer_keywords:
- Full-Text Indexing Wizard
- full-text search [SQL Server], Full-Text Indexing Wizard
ms.assetid: 3e9d9605-6525-4781-9168-fdaa06db3459
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: f7bab4ee8f03eb666e1a8396fbf8957b1e42f2c7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66010900"
---
# <a name="use-the-full-text-indexing-wizard"></a>Verwenden des Volltextindizierungs-Assistenten
  Der Volltextindizierungs-Assistent führt Sie durch eine Reihe von Arbeitsschritten, die Ihnen das Erstellen eines Volltextindexes erleichtern.  
  
#### <a name="to-use-the-full-text-indexing-wizard"></a>So verwenden Sie den Volltextindizierungs-Assistenten  
  
1.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf die Tabelle, für die Sie einen Volltextindex erstellen möchten, zeigen Sie auf **Volltextindex**, und klicken Sie anschließend auf **Volltextindex definieren**.  
  
     **Eindeutiger Index**  
     Wählen Sie einen Index aus der Dropdownliste aus. Der Index muss genau eine Schlüsselspalte haben, muss eindeutig sein und darf keine NULL-Werte zulassen. Wählen Sie als eindeutigen Volltextschlüssel stets den kleinsten eindeutigen Index aus. Für die bestmögliche Leistung ist ein gruppierter Index zu empfehlen.  
  
     **Verfügbare Spalten**  
     Um eine Spalte in den Index einzuschließen, aktivieren Sie das Kontrollkästchen neben dem Spaltennamen. Spalten, die für eine Volltextindizierung nicht infrage kommen, werden grau angezeigt, und die entsprechenden Kontrollkästchen sind deaktiviert.  
  
     **Sprache für die Wörter Trennung**  
     Wählen Sie eine Sprache aus der Dropdownliste aus. Diese Auswahl wird von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet, um die richtigen Wörtertrennungen für den Index zu identifizieren. 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] In werden mithilfe von Wörtertrennzeichen Wortgrenzen in den volltextindizierten Daten gekennzeichnet.  
  
     **Typspalte**  
     Wählen Sie den Namen der Spalte aus, in der der Dokumenttyp der volltextindizierten Spalte enthalten ist.  
  
     Die **Typspalte** ist nur aktiviert, wenn die Spalte mit dem Namen in der Spalte **Verfügbare Spalten** den Typ `varbinary(max)` oder `image`hat.  
  
     **Statistische Semantik**  
     Wählen Sie aus, ob die semantische Indizierung für die ausgewählte Spalte aktiviert werden soll. Weitere Informationen finden Sie unter [Semantische Suche &#40;SQL Server&#41;](semantic-search-sql-server.md).  
  
     Wenn Sie eine **Sprache** vor der Option **Statistische Semantik**auswählen und die ausgewählte Sprache über kein zugeordnetes semantisches Sprachmodell verfügt, ist das Kontrollkästchen **Statistische Semantik** deaktiviert. Wenn Sie **Statistische Semantik** vor einer **Sprache**auswählen, werden im Dropdown-Kombinationsfeld nur die Sprachen angezeigt, für die das semantische Sprachmodell unterstützt wird.  
  
2.  Aktivieren Sie die Optionen zur Änderungsnachverfolgung.  
  
     **Automatischer**  
     Wählen Sie diese Optionsschaltfläche, wenn der Volltextindex im Falle von Änderungen an den zugrunde liegenden Daten automatisch aktualisiert werden soll.  
  
     **Eller**  
     Wählen Sie diese Optionsschaltfläche, wenn der Volltextindex im Falle von Änderungen an den zugrunde liegenden Daten nicht automatisch aktualisiert werden soll. Die Änderungen an den zugrunde liegenden Daten bleiben erhalten. Um jedoch die Änderungen im Volltextindex zu berücksichtigen, müssen Sie diesen Prozess manuell oder über einen Zeitplan starten.  
  
     **Änderungen nicht nachverfolgen**  
     Wählen Sie diese Optionsschaltfläche, wenn der Volltextindex bei Änderungen an den zugrunde liegenden Daten nicht aktualisiert werden soll.  
  
     **Vollständige Auffüllung bei der Indexerstellung starten**  
     Wählen Sie diese Optionsschaltfläche, um nach erfolgreichem Abschluss dieses Assistenten eine vollständige Auffüllung zu starten. Dabei wird die Volltext-Indexstruktur im Katalog erstellt und der Katalog mit volltextindizierten Daten aufgefüllt.  
  
3.  Wählen Sie den Katalog, die Indexdateigruppe und die Stoppliste aus.  
  
     **Voll Text Katalog auswählen**  
     Wählen Sie einen Volltextkatalog aus der Liste aus. Der Standardkatalog für die Datenbank entspricht standardmäßig dem in der Liste ausgewählten Element. Wenn keine Kataloge verfügbar sind, wird die Liste deaktiviert, und das Kontrollkästchen **Neuen Katalog erstellen** wird überprüft und deaktiviert.  
  
    |||  
    |-|-|  
    |**Neuen Katalog erstellen**|Aktivieren Sie dieses Kontrollkästchen, um einen neuen Volltextkatalog zu erstellen.|  
  
     **Name**  
     Geben Sie einen Namen für den neuen Volltextkatalog ein.  
  
     **Als Standardkatalog festlegen**  
     Wählen Sie diese Option aus, um diesen Katalog als Standardkatalog für die Datenbank festzulegen.  
  
     **Akzent**  
     Geben Sie an, ob für den neuen Katalog nach Akzenten unterschieden wird. Wenn in der Datenbank nach Akzent unterschieden wird, ist die Option **Mit Unterscheidung** standardmäßig ausgewählt.  
  
     **Index Dateigruppe auswählen**  
     Geben Sie die Dateigruppe an, für die der Volltextindex erstellt werden soll.  
  
     Folgende Werte sind möglich:  
  
    |value|BESCHREIBUNG|  
    |-----------|-----------------|  
    |**\<Standard>**|Wenn die Tabelle oder Sicht nicht partitioniert ist, wählen Sie diese Option, um dieselbe Dateigruppe wie die zugrunde liegende Tabelle oder Sicht zu verwenden. Wenn die Tabelle oder Sicht partitioniert ist, wird die primäre Dateigruppe verwendet.|  
    |**Vorrangiges**|Wählen Sie diese Option, um die primäre Dateigruppe für den neuen Volltextindex zu verwenden.|  
    |*Eine vom Benutzer angegebene Standarddateigruppe*|Wenn eine benutzerdefinierte Standardstoppliste vorhanden ist, wählen Sie den Namen in der Liste aus, um die zugehörige Dateigruppe für den neuen Volltextindex zu verwenden.|  
  
     **Volltext-Stopp Liste auswählen**  
     Geben Sie eine Stoppliste an, die für den Volltextindex verwendet werden soll, oder deaktivieren Sie die Stopplistenverwendung.  
  
     In [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] und neueren Versionen werden Stoppwörter in Datenbanken über Objekte verwaltet, die als Stopplisten bezeichnet werden. Eine *Stoppliste* ist eine Liste mit Stoppwörtern, die, wenn sie einem Volltextindex zugeordnet ist, auf Volltextabfragen für diesen Index angewendet wird. Weitere Informationen finden sie unter [Konfigurieren und Verwalten von Stoppwörtern und Stopplisten für Volltextsuche](configure-and-manage-stopwords-and-stoplists-for-full-text-search.md).  
  
     Folgende Werte sind möglich:  
  
    |value|BESCHREIBUNG|  
    |-----------|-----------------|  
    |**\<System>**|Wählen Sie diese Option, um die Systemstoppliste für den neuen Volltextindex zu verwenden. Dies ist die Standardeinstellung.|  
    |**\<aus>**|Wählen Sie diese Option, um Stopplisten für den neuen Volltextindex zu deaktivieren.|  
    |*benutzerdefinierter-Stopp Listen Name*|Die Liste enthält die Namen aller benutzerdefinierten Stopplisten (falls vorhanden), die für die Datenbank erstellt wurden. Wählen Sie eine beliebige benutzerdefinierte Stoppliste zur Verwendung für den neuen Volltextindex aus.|  
  
4.  Optional können Sie auch den Auffüllungszeitplan definieren. Sofern Sie die Ausführung nicht für die Zukunft geplant haben, beginnen die Indizierungsvorgänge sofort. Die Zeitpläne werden sofort erstellt, sie werden jedoch erst zum festgelegten Zeitpunkt ausgeführt.  
  
     **Neuer Tabellen Zeitplan**  
     Definieren eines Auffüllungszeitplans für eine Tabelle.  
  
     **Neuer Katalog Zeitplan**  
     Definieren eines Auffüllungszeitplans für einen Volltextkatalog.  
  
     **Bearbeiten**  
     Bearbeiten eines Zeitplans.  
  
     **Löschen**  
     Löschen eines Zeitplans.  
  
5.  Zeigen Sie den Status des Volltextindizierungs-Assistenten an, bzw. steuern Sie ihn.  
  
     **Beenden**  
     Unterbricht den aktuellen Vorgang und verhindert die Ausführung nachfolgender Volltextvorgänge durch den Assistenten während dieser Sitzung.  
  
     **Report**  
     Wenn alle Vorgänge ausgeführt wurden, können Sie auf diese Schaltfläche klicken, um auf einen Bericht zu den ausgeführten Vorgängen zuzugreifen. Sie können den Bericht anzeigen, in eine Datei drucken, in die Zwischenablage kopieren oder ihn per E-Mail versenden.  
  
  
