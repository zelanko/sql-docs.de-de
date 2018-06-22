---
title: Erstellen von SMO-Programmen | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Visual Basic [SMO]
- Visual C# [SMO]
- programming [SMO]
- SQL Server Management Objects, programming
- SMO [SQL Server], programming
ms.assetid: 7d2f0bcf-f1ae-45b8-bc3f-7aea4fae7e45
caps.latest.revision: 34
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2115b0e807e8308b802a2d0f104c71304ad40154
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36057549"
---
# <a name="creating-smo-programs"></a>Erstellen von SMO-Programmen
  Die allgemeinen Programmierungsaufgaben für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO)-Objekte umfassen Bereiche, die allen Objekten gemein sind, wie z. B. das Ausführen von Methoden, das Einstellen von Eigenschaften oder die Bearbeitung von Auflistungen.  
  
|Thema|Description|  
|-----------|-----------------|  
|[Herstellen einer Verbindung zu einer Instanz von SQL Server](connecting-to-an-instance-of-sql-server.md)|Das grundlegendste SMO-Programm, das eine Verbindung zu einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] herstellt. Veranschaulicht die Windows-Authentifizierung und die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Authentifizierung. Enthält zudem Beispiele, die das Herstellen einer Verbindung mit einer lokalen und einer Remoteinstanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] zeigen.|  
|[Trennen der Verbindung zu einer Instanz von SQL Server](disconnecting-from-an-instance-of-sql-server.md)|Ein Programm, das veranschaulicht, wie die Verbindung zur Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] getrennt wird.|  
|[Aufrufen von Methoden](calling-methods.md)|In diesem Abschnitt wird die allgemeine Vorgehensweise zum Aufrufen von Methoden beschrieben. Zeigt die Verwendung von Parametern und die Handhabung von Tabellen mit Daten, die in einem <xref:System.Data.DataTable>-Objekt zurückgegeben wurden. Enthält zudem ein Beispiel dafür, wie ein Objektkonstruktor und die `Clone`-Methode aufgerufen werden.|  
|[Festlegen von Eigenschaften](setting-properties-smo.md)|In diesem Abschnitt wird beschrieben, wie verschiedene Eigenschaftentypen festgelegt werden. Es wird gezeigt, wie Objekteigenschaften festgelegt und abgerufen werden. Zudem werden Beispiele für das Festlegen von Objekteigenschaften bei Erstellung des Objekts gegeben, und es wird erläutert, wie alle Eigenschaften eines Objekts durchlaufen werden.|  
|[Verwenden von Auflistungen](using-collections.md)|Verschiedene Programme, mit denen die für Objektauflistungen verwendeten Techniken erläutert werden. Zeigt, wie mit Auflistungen auf ein Objekt verwiesen wird. Beinhaltet auch ein Beispiel, das verdeutlicht, wie die Elemente einer Auflistung durchlaufen werden.|  
|[Behandeln von SMO-Ereignissen](handling-smo-events.md)|In diesem Abschnitt wird beschrieben, wie Ereignisse in SMO eingerichtet und behandelt werden. Anhand eines Beispiels wird gezeigt, wie ein Ereignishandler und das Ereignisabonnement eingerichtet werden.|  
|[Behandeln von SMO-Ausnahmen](handling-smo-exceptions.md)|In diesem Abschnitt wird beschrieben, wie Ausnahmen in SMO aufgefangen werden. Er enthält zudem Beispiele, wie eine Ausnahme erfasst und eine innere Ausnahme angezeigt wird.|  
|[Arbeiten mit Datentypen](working-with-data-types.md)|In diesem Abschnitt wird beschrieben, wie mit den verschiedenen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datentypen gearbeitet wird. Es wird darauf eingegangen, wie ein Datentyp mit der Spezifikation im Objektkonstruktor erstellt wird. Anhand eines Beispiels wird außerdem erläutert, wie ein Datentyp mit dem Standardkonstruktor erstellt wird.|  
|[Verwenden von Transaktionen](using-transactions.md)|In diesem Abschnitt wird beschrieben, wie die Transaktionsverarbeitung in einem SMO-Programm implementiert wird. Ein Beispiel veranschaulicht, wie Transaktionen in einem SMO-Programm verwendet werden.|  
|[Verwenden des Aufzeichnungsmodus](using-capture-mode.md)|In diesem Abschnitt wird beschrieben, wie die Ausgabe des SMO-Programms aufgezeichnet wird. Im Beispiel wird das SMO-Programm als [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Anweisung zur späteren Ausführung an die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanz gesendet.|  
  
  