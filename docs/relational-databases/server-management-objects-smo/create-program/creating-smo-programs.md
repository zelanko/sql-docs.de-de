---
title: Erstellen von SMO-Programmen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- Visual Basic [SMO]
- Visual C# [SMO]
- programming [SMO]
- SQL Server Management Objects, programming
- SMO [SQL Server], programming
ms.assetid: 7d2f0bcf-f1ae-45b8-bc3f-7aea4fae7e45
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 5b55c30746542a09a84f4b8eacde8e78f3dae8ed
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "70148748"
---
# <a name="creating-smo-programs"></a>Erstellen von SMO-Programmen
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  Die allgemeinen Programmierungsaufgaben für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO)-Objekte umfassen Bereiche, die allen Objekten gemein sind, wie z. B. das Ausführen von Methoden, das Einstellen von Eigenschaften oder die Bearbeitung von Auflistungen.  
  
|Thema|BESCHREIBUNG|  
|-----------|-----------------|  
|[Herstellen einer Verbindung zu einer Instanz von SQL Server](../../../relational-databases/server-management-objects-smo/create-program/connecting-to-an-instance-of-sql-server.md)|Das grundlegendste SMO-Programm, das eine Verbindung zu einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] herstellt. Veranschaulicht die Windows-Authentifizierung und die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Authentifizierung. Enthält zudem Beispiele, die das Herstellen einer Verbindung mit einer lokalen und einer Remoteinstanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] zeigen.|  
|[Trennen der Verbindung zu einer Instanz von SQL Server](../../../relational-databases/server-management-objects-smo/create-program/disconnecting-from-an-instance-of-sql-server.md)|Ein Programm, das veranschaulicht, wie die Verbindung zur Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] getrennt wird.|  
|[Aufrufen von Methoden](../../../relational-databases/server-management-objects-smo/create-program/calling-methods.md)|In diesem Abschnitt wird die allgemeine Vorgehensweise zum Aufrufen von Methoden beschrieben. Zeigt die Verwendung von Parametern und die Handhabung von Tabellen mit Daten, die in einem <xref:System.Data.DataTable>-Objekt zurückgegeben wurden. Enthält auch ein Beispiel zum aufzurufen eines Objektkonstruktors und zum Abrufen der **Klon** Methode.|  
|[Festlegen von Eigenschaften – SMO](../../../relational-databases/server-management-objects-smo/create-program/setting-properties-smo.md)|In diesem Abschnitt wird beschrieben, wie verschiedene Eigenschaftentypen festgelegt werden. Es wird gezeigt, wie Objekteigenschaften festgelegt und abgerufen werden. Zudem werden Beispiele für das Festlegen von Objekteigenschaften bei Erstellung des Objekts gegeben, und es wird erläutert, wie alle Eigenschaften eines Objekts durchlaufen werden.|  
|[Verwenden von Auflistungen](../../../relational-databases/server-management-objects-smo/create-program/using-collections.md)|Verschiedene Programme, mit denen die für Objektauflistungen verwendeten Techniken erläutert werden. Zeigt, wie mit Auflistungen auf ein Objekt verwiesen wird. Beinhaltet auch ein Beispiel, das verdeutlicht, wie die Elemente einer Auflistung durchlaufen werden.|  
|[Behandeln von SMO-Ereignissen](../../../relational-databases/server-management-objects-smo/create-program/handling-smo-events.md)|In diesem Abschnitt wird beschrieben, wie Ereignisse in SMO eingerichtet und behandelt werden. Anhand eines Beispiels wird gezeigt, wie ein Ereignishandler und das Ereignisabonnement eingerichtet werden.|  
|[Behandeln von SMO-Ausnahmen](../../../relational-databases/server-management-objects-smo/create-program/handling-smo-exceptions.md)|In diesem Abschnitt wird beschrieben, wie Ausnahmen in SMO aufgefangen werden. Er enthält zudem Beispiele, wie eine Ausnahme erfasst und eine innere Ausnahme angezeigt wird.|  
|[Arbeiten mit Datentypen](../../../relational-databases/server-management-objects-smo/create-program/working-with-data-types.md)|In diesem Abschnitt wird beschrieben, wie mit den verschiedenen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datentypen gearbeitet wird. Es wird darauf eingegangen, wie ein Datentyp mit der Spezifikation im Objektkonstruktor erstellt wird. Anhand eines Beispiels wird außerdem erläutert, wie ein Datentyp mit dem Standardkonstruktor erstellt wird.|  
|[Verwenden von Transaktionen](../../../relational-databases/server-management-objects-smo/create-program/using-transactions.md)|In diesem Abschnitt wird beschrieben, wie die Transaktionsverarbeitung in einem SMO-Programm implementiert wird. Ein Beispiel veranschaulicht, wie Transaktionen in einem SMO-Programm verwendet werden.|  
|[Verwenden des Aufzeichnungsmodus](../../../relational-databases/server-management-objects-smo/create-program/using-capture-mode.md)|In diesem Abschnitt wird beschrieben, wie die Ausgabe des SMO-Programms aufgezeichnet wird. Im Beispiel wird das SMO-Programm als [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Anweisung zur späteren Ausführung an die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanz gesendet.|  
  
  
