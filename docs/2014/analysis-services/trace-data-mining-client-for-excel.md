---
title: Ablaufverfolgung (Datamining-Client für Excel) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- tracer
- connections
ms.assetid: 4aea3e17-cd0f-48dd-8f22-b54a6c716426
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 576cb395f7f488eec8ebf28ab5bc7f226cb81809
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66065887"
---
# <a name="trace-data-mining-client-for-excel"></a>Ablaufverfolgung (Data Mining-Client für Excel)
  ![Schaltfläche "Ablaufverfolgung"](media/misc-trace.gif "Schaltfläche \"Ablaufverfolgung\"")  
  
 Die **Überwachungstoken** Dialogfeld können Sie die Anweisungen überwachen, die mit der Instanz von gesendet werden [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , die Sie für das Datamining verwenden. Nach dem Erstellen einer Verbindungs mit einer Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], alle Interaktionen zwischen dem Client und dem Server angemeldet sind die **Überwachungstoken** Bereich, z. B. Anweisungen, die Strukturen zu erstellen und Hinzufügen von Miningmodellen stellen Vorhersagen, als auch einige Nachrichten, die vom Server zurückgegeben werden.  
  
 Je nach der angeforderten Aktion kann es sich bei der Anweisung um eine DMX-Datendefinitionsabfrage (Data Mining Extensions, Data Mining-Erweiterungen) oder eine DMX-Datenbearbeitungsabfrage, ein ASSL-Paket (Analysis Services Scripting Language) oder einen Aufruf einer gespeicherten Analysis Services-Prozedur handeln. Tatsächliche numerische Ergebnisse und Datenwerte werden jedoch nicht angezeigt.  
  
 **Ablaufverfolgung** überwacht nur die aktuelle Verbindung und den Inhalt der **Überwachungstoken** im Dialogfeld werden nicht gespeichert.  
  
## <a name="options"></a>Optionen  
 Ablaufverfolgung (Bereich)  
 Listet alle Anweisungen auf, die vom Excel-Client an den Server gesendet wurden.  
  
 Abhängig von der angeforderten Aktion kann es sich bei der Anweisung um eine DMX-Datenbearbeitungsanweisung oder -Datendefinitionsanweisung, einen Aufruf einer gespeicherten Analysis Services-Prozedur oder ein XML/A-Paket handeln.  
  
 **Aktuelle Verbindung**  
 Klicken Sie auf diese Option, um die Definition der aktuellen Verbindung anzuzeigen. Die Definition enthält den Namen der Verbindung, des Anbieters, der Datenquelle und des Katalogs, sowie den Zeitpunkt der letzten Verwendung der Verbindung für eine Transaktion und den aktuellen Verbindungsstatus (Offen, Inaktiv).  
  
 **Sitzungsmodelle verwenden**  
 Aktivieren Sie dieses Kontrollkästchen, um Data Mining-Modelle und -Strukturen als temporäre Objekte auf dem Server zu speichern. Die Modelle und Strukturen, die Sie erstellen, sind nur für die Dauer der aktuellen Sitzung verfügbar.  
  
 Deaktivieren Sie diese Option, um die Modelle oder Strukturen zu speichern, indem Sie sie auf einem Analysis Services-Server speichern.  
  
 **Beachten Sie** steht die Möglichkeit, temporäre Objekte verwenden, nur, wenn Sie die Tabellenanalysetools für Excel verwenden. Für die Data Mining-Vorlagen für Visio und den Data Mining-Client für Excel müssen die Strukturen und Modelle auf dem Server gespeichert werden.  
  
## <a name="tracing-temporary-structures-and-models"></a>Überwachen von temporären Strukturen und Modellen  
 Wenn Sie die Tabellenanalysetools verwenden, die standardmäßig temporäre Strukturen und Modelle erstellen, wird die Aktivität zwischen dem Server und dem Client zwar überwacht, die erstellten Modelle und Strukturen werden jedoch nicht dauerhaft auf dem Server gespeichert.  
  
 Wenn Sie Ihre Arbeit beibehalten werden soll, wenn eine der Tabellenanalysetools verwenden möchten, können Sie deaktivieren Sie die Option **sitzungsmodelle verwenden**, um die dazu führen, dass Ihre Modelle dauerhaft auf dem Server gespeichert werden. Sie können auch die Anweisungen im Kopieren der **Überwachungstoken** Bereich in eine Datei, damit Sie Ihre Arbeit später neu erstellen können.  
  
## <a name="understanding-sessions"></a>Grundlegendes zu Sitzungen  
 Wenn Sie eine Verbindung mit einer Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] herstellen, wird vom Data Mining-Add-In eine Sitzung gestartet. Jede Sitzung erhält eine Sitzungs-ID, mit der eine vorhandene Sitzung in der Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] identifiziert wird. Mit dieser Sitzungs-ID wird jedoch nicht sichergestellt, dass die Sitzung gültig bleibt. Die Sitzung kann aufgrund eines Sitzungstimeouts ablaufen, oder die zugewiesene Verbindung wird getrennt. Wenn die Sitzung abläuft und nicht mehr gültig ist, wird die Sitzung in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] beendet, und es wird ein Rollback aller derzeit verarbeiteten Transaktionen ausgeführt. Für alle Meldungen, die mit einer nicht mehr gültigen Sitzungs-ID gesendet werden, wird ein Fehler mit der Meldung ausgelöst, dass die angegebene Sitzung nicht gefunden werden kann.  
  
 Bestimmte Data Mining-Modelle werden explizit auf dem Server gespeichert, nicht jedoch Sitzungsminingmodelle und -strukturen, sodass sitzungsbezogene Data Mining-Aktivitäten nicht dauerhaft sind. Da temporäre Miningmodelle und -strukturen gelöscht werden, sobald Sie die Sitzung beenden, sollten Sie Excel-Arbeitsmappen erst schließen, nachdem Sie alle Daten, die Sie behalten möchten, gespeichert haben.  
  
## <a name="changing-connections"></a>Ändern von Verbindungen  
 Durch das Ändern von Verbindungen werden Ablaufverfolgungen von vorherigen Verbindungen nicht gelöscht. Nur durch das Schließen der Arbeitsmappe wird die Sitzung entfernt.  
  
 Wenn Sie Verbindungen bei der Arbeit in einer Excel-Arbeitsmappe ändern, wird die Änderung von Verbindungen nicht in erfasst die **Überwachungstoken** Bereich. Um die Namen und den Status der aktuellen Verbindung explizit zu anzuzeigen, klicken Sie auf **aktuelle Verbindung**.  
  
## <a name="understanding-statements-in-the-tracer"></a>Grundlegendes zu Anweisungen in der Überwachung  
 Mit der Programmiersprache DMX können Sie Data Mining-Modelle in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] erstellen und mit diesen Modellen arbeiten. Sie können DMX verwenden, um die Struktur der neuen Datamining-Modelle erstellen, Trainieren der Modelle und zu durchsuchen, verwalten und Vorhersagen. DMX besteht aus DDL-Anweisungen (Data Definition Language, Datendefinitionssprache), DML-Anweisungen (Data Manipulation Language, Datenbearbeitungssprache) sowie aus Funktionen und Operatoren.  
  
 Ein umfassende Beschreibung der DMX-Anweisungen und deren Syntax geht über den Rahmen dieses Themas hinaus. Sie können jedoch die Informationen in den **Überwachungstoken** ausführliche Informationen über das Verhalten einer DMX-Anweisung finden Sie im Bereich. Die Data Mining-Add-Ins für Excel helfen Ihnen auch, komplexe DMX-Anweisungen zu erstellen und mit einem [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Server zu interagieren. Weitere Informationen finden Sie unter [Abfrage &#40;SQL Server Data Mining-Add-ins&#41;](query-sql-server-data-mining-add-ins.md).  
  
> [!NOTE]  
>  Viele DMX-Anweisungen verwenden Parameter. Für einfache Typen sind die Werte der Parameter unter der Anweisung aufgeführt. Für komplexe Typen wird jedoch nur der Typ des Parameters aufgeführt.  
  
 SQL Server Analysis Services verwendet auch das XMLA (XML for Analysis)-Protokoll zum Behandeln der gesamten Kommunikation zwischen Clientanwendungen, einschließlich des Data Mining-Clients für Excel und einer Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
 Weitere Informationen zur DMX-Syntax und zu Befehlen und Elementen in XMLA finden Sie in der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Onlinedokumentation.  
  
 Einige der Anweisungen, die an den Server gesendet werden, enthalten möglicherweise Abfragen, die gespeicherte Analysis Services-Systemprozeduren genannt werden. Weitere Informationen finden Sie in der SQL Server-Onlinedokumentation.  
  
  
