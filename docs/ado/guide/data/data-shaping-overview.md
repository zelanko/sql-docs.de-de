---
title: Daten strukturieren (Übersicht) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- data shaping [ADO], overview
ms.assetid: 4cb5fd29-4e56-46ac-ae48-a6771c321c0c
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 6d693ccbeb06860cd4633a933e80b9ccbe6526a8
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66702224"
---
# <a name="data-shaping-overview"></a>Datenstrukturierung – Übersicht
*Data shaping* bedeutet die Entwicklung von hierarchischer Beziehungen zwischen mindestens zwei logische Entitäten in einer Abfrage. Die Hierarchie finden Sie in der über-/ unterordnungsbeziehungen zwischen einem Datensatz eines [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md), und eine oder mehrere Datensätze (auch bekannt als ein Kapitel) eines anderen **Recordset**. In einer über-/ unterordnungsbeziehung, die das übergeordnete Element **Recordset** enthält die untergeordneten **Recordset**. Ein Beispiel für eine hierarchische Beziehung ist, Kunden und Bestellungen. Für jeden Kunden in einer Datenbank können NULL oder mehrere Bestellungen vorhanden sein. Die hierarchische Beziehung kann rekursiv sein, was bedeutet, dass zwei Ebenen untergeordneten Datensätzen in einem untergeordneten Datensatz geschachtelt werden können. Im Prinzip kann ein hierarchischer Datensatz in einer beliebigen Tiefe geschachtelt werden. In der Praxis eingeschränkt ADO die Rekursion auf maximal 512 **Recordset**s.  
  
 In allgemeinen Spalten von einer geformten **Recordset** kann Daten von einem Datenanbieter wie Microsoft® SQL Server, Verweise auf einen anderen enthalten **Recordset**, Werte, die von einer Berechnung in eine einzelne Zeile mit einem abgeleitet **Recordset**, oder Werte, die aus einem Vorgang für eine Spalte für eine gesamte abgeleitete **Recordset**. Eine Spalte kann auch neu erstellt wurde und leer sein.  
  
 Beim Abrufen des Wert einer Spalte, die einen Verweis auf eine andere enthält **Recordset**, ADO gibt automatisch den tatsächlichen **Recordset** durch den Verweis dargestellt wird. Der Verweis auf eine **Recordset** ist tatsächlich ein Verweis auf eine Teilmenge des untergeordneten Elements, dem Namen einer *Kapitel*. Ein einzelnes übergeordnetes Element kann mehr als ein untergeordnetes Element verweisen **Recordset**.  
  
 ADO-Unterstützung für die datenstrukturierung können Sie zum Abfragen einer Datenquelle und Zurückgeben einer **Recordset** in der ein Datensatz (übergeordneten) ein (untergeordnetes) darstellt **Recordset**. In der Customer-Order-Szenario können Sie Daten zu Kunden als auch für die Bestellungen von jedem Kunden in einer einzigen Abfrage abrufen. Die resultierenden **Recordset** ist auch bekannt als strukturiert **Recordset**.  
  
 Darüber hinaus für die datenstrukturierung in ADO können Sie zum Erstellen von neuen **Recordset** Objekte ohne eine zugrunde liegende Datenquelle mithilfe der **neu** Schlüsselwort, um die Felder von der übergeordneten und untergeordneten beschreiben  **Durch Recordsets**. Die neue **Recordset** Objekt kann dann mit Daten gefüllt und dauerhaft gespeichert. Entwickler können auch durchführen, verschiedene Berechnungen oder Aggregationen (z. B. **Summe**, **AVG**, und **MAX**) für untergeordnete Felder. Strukturieren von Daten kann auch ein übergeordnetes Element erstellen **Recordset** von einem untergeordneten **Recordset** durch Gruppieren von Datensätzen in der untergeordneten und eine Zeile in das übergeordnete Element für jede Gruppe in das untergeordnete Element platzieren.  
  
 Reguläre SQL können Sie zum Abrufen von Daten mithilfe von **JOIN** Syntax, aber dies kann ineffizient sein und sehr unhandlich da redundante übergeordneten Daten in jedem Datensatz zurückgegeben, die für einen angegebenen über-/ unterordnungsbeziehung wiederholt werden. Strukturieren von Daten können Sie einen einzelnen übergeordneten Datensatz im übergeordneten Element verknüpfen **Recordset** mit mehreren untergeordneten Datensätzen in der untergeordneten **Recordset**, vermeiden die Redundanz der ein **JOIN**. Die meisten Benutzer finden Sie den übergeordneten und untergeordneten mehrere **Recordset** Programmiermodell natürlicheren und einfacher zu verwenden als die einzelne **Recordset JOIN** Modell.
