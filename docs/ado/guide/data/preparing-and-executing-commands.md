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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67924561"
---
# <a name="preparing-and-executing-commands"></a>Vorbereiten und Ausführen von Befehlen
Befehle sind Anweisungen, die an einen Anbieter ausgegeben werden, um einige Vorgänge für die zugrunde liegende Datenquelle auszuführen. Eine SQL-Anweisung ist z. b. ein Befehl für den Microsoft SQL-Datenanbieter. In ADO werden Befehle in der Regel durch **Befehls** Objekte dargestellt, obwohl einfache Befehle auch über **Verbindungs** -oder **Recordsetobjekte** ausgegeben werden können.  
  
 Sie können das **Command** -Objekt verwenden, um einen beliebigen unterstützten Vorgangstyp vom Anbieter anzufordern. dabei wird davon ausgegangen, dass der Anbieter die Befehls Zeichenfolge ordnungsgemäß interpretieren kann. Ein gängiger Vorgang für Datenanbieter besteht darin, eine Datenbank abzufragen und Datensätze in einem **Recordset** -Objekt zurückzugeben. Dies ist als Container für das Ergebnis und ein Tool zum Anzeigen des Ergebnisses gedacht. Wie bei vielen ADO-Objekten können einige **Befehls** Objekt Auflistungen, Methoden oder Eigenschaften Fehler erzeugen, wenn auf Sie verwiesen wird. Dies hängt von der Funktionalität des Anbieters ab.  
  
 Zusätzlich zur Verwendung von **Command** -Objekten können Sie die **Execute** -Methode für das **Verbindungs** Objekt oder die **Open** -Methode des **Recordset** -Objekts verwenden, um einen Befehl auszugeben und ihn auszuführen. Sie sollten jedoch ein **Befehls** Objekt verwenden, wenn Sie einen Befehl in Ihrem Code wieder verwenden müssen, oder wenn Sie ausführliche Parameterinformationen mit dem Befehl übergeben müssen. Diese Szenarios werden weiter unten in diesem Abschnitt ausführlicher behandelt.  
  
> [!NOTE]
>  Bestimmte **Befehle**können ein Resultset als binären Stream oder als einen einzelnen **Datensatz** und nicht als **Recordset**zurückgeben, wenn dies vom Anbieter unterstützt wird. Außerdem sind einige **Befehle**nicht für das Zurückgeben eines Resultsets (z. b. eine SQL-Aktualisierungs Abfrage) vorgesehen. In diesem Abschnitt wird das üblichste Szenario behandelt: das Ausführen von **Befehlen**, die Ergebnisse als **Recordset** -Objekt zurückgeben. Weitere Informationen zum Zurückgeben von Ergebnissen in **Datensatz**s oder **Stream**s finden Sie unter [Datensätze und Streams](../../../ado/guide/data/records-and-streams.md).  
  
 Dieser Abschnitt enthält die folgenden Themen:  
  
-   [Command-Objekt – Übersicht](../../../ado/guide/data/command-object-overview.md)  
  
-   [Erstellen und Ausführen eines einfachen Befehls](../../../ado/guide/data/creating-and-executing-a-simple-command.md)  
  
-   [Parameter für Command-Objekt](../../../ado/guide/data/command-object-parameters.md)  
  
-   [Aufrufen einer gespeicherten Prozedur mit einem Befehl](../../../ado/guide/data/calling-a-stored-procedure-with-a-command.md)  
  
-   [Aufrufen einer gespeicherten Prozedur als Methode für ein Verbindungs Objekt](../../../ado/guide/data/calling-a-stored-procedure-as-a-method-on-a-connection-object.md)  
  
-   [Benannte Befehle](../../../ado/guide/data/named-commands.md)  
  
-   [Übergeben von Parametern an einen benannten Befehl](../../../ado/guide/data/passing-parameters-to-a-named-command.md)
