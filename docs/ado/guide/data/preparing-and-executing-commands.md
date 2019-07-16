---
title: Vorbereiten und Ausführen von Befehlen | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Command object [ADO], preparing and executing commands
ms.assetid: 7448d9ee-7f4b-47e3-be54-2df8c9bbac32
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2295d421f8b802f2f3b531d7de3fc086e43ad572
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67924561"
---
# <a name="preparing-and-executing-commands"></a>Vorbereiten und Ausführen von Befehlen
Befehle sind Anweisungen, die zu einem Anbieter ausgestellt werden, zum Durchführen bestimmter Vorgänge für die zugrunde liegenden Datenquelle. Eine SQL-Anweisung ist z. B. einen Befehl an den Microsoft SQL-Datenanbieter. In ADO, Befehle in der Regel durch dargestellt **Befehl** Objekte aufweist, obwohl der einfache Befehle auch ausgegeben werden können, können Sie über **Verbindung** oder **Recordset** Objekte.  
  
 Sie können die **Befehl** Objekt, das Anfordern von jeder unterstützte Typs des Vorgangs vom Anbieter, vorausgesetzt, dass der Anbieter die Befehlszeichenfolge richtig interpretieren kann. Ein allgemeiner Vorgang für Datenanbieter wird zum Abfragen einer Datenbank und Zurückgeben von Datensätzen in einer **Recordset** -Objekt, das, die als Container für das Ergebnis und ein Tool, um das Resultset anzuzeigen vorstellen können. Wie bei vielen ADO-Objekte, einige **Befehl** Auflistungen, Methoden oder Eigenschaften generieren möglicherweise Fehler bei der, abhängig von den Funktionen des Anbieters auf die verwiesen wird.  
  
 Zusätzlich zur Verwendung von **Befehl** Objekte aufweist, können Sie die **Execute** Methode für die **Verbindung** Objekt oder die **öffnen** Methode für die  **Recordset** Objekt, das einen Befehl auszugeben und ausführen. Allerdings sollten Sie verwenden eine **Befehl** Objekt, wenn Sie einen Befehl in Ihrem Code wiederverwenden möchten, oder ausführliche Parameterinformationen mit dem Befehl übergeben werden sollen. Diese Szenarien werden weiter unten in diesem Abschnitt noch ausführlicher behandelt.  
  
> [!NOTE]
>  Bestimmte **Befehl**s kann zurückgeben ein Resultsets als binären Datenstrom oder ein einzelner **Datensatz** statt als ein **Recordset**, wenn dies vom Anbieter unterstützt wird. Darüber hinaus einige **Befehl**s sollen keine Resultsets überhaupt (z. B. eine SQL Update-Abfrage) zurück. Dieser Abschnitt erläutert das typische Szenario, jedoch: Ausführen von **Befehl**s, die Ergebnisse als Zurückgeben einer **Recordset** Objekt. Weitere Informationen zum Zurückgeben von Ergebnissen in **Datensatz**s oder **Stream**s, finden Sie unter [Datensätze und Datenströme](../../../ado/guide/data/records-and-streams.md).  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Command-Objekte (Übersicht)](../../../ado/guide/data/command-object-overview.md)  
  
-   [Erstellen und Ausführen eines einfachen Befehls](../../../ado/guide/data/creating-and-executing-a-simple-command.md)  
  
-   [Befehlsobjekt-Parameter](../../../ado/guide/data/command-object-parameters.md)  
  
-   [Aufrufen einer gespeicherten Prozedur mit einem Befehl](../../../ado/guide/data/calling-a-stored-procedure-with-a-command.md)  
  
-   [Aufrufen einer gespeicherten Prozedur als Methode für ein Verbindungsobjekt](../../../ado/guide/data/calling-a-stored-procedure-as-a-method-on-a-connection-object.md)  
  
-   [Benannte Befehle](../../../ado/guide/data/named-commands.md)  
  
-   [Übergeben von Parametern an einen benannten Befehl](../../../ado/guide/data/passing-parameters-to-a-named-command.md)
