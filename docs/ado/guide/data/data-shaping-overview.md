---
title: Übersicht über die Daten Strukturierung | Microsoft-Dokumentation
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
ms.openlocfilehash: b3bce50892520dbc889a62960065ce3d8e423a81
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67925623"
---
# <a name="data-shaping-overview"></a>Datenstrukturierung – Übersicht
Die *Daten Strukturierung* bedeutet, dass hierarchische Beziehungen zwischen mindestens zwei logischen Entitäten in einer Abfrage aufgebaut werden. Die Hierarchie kann in Beziehungen zwischen übergeordneten und untergeordneten Elementen zwischen einem Datensatz eines [Recordsets](../../../ado/reference/ado-api/recordset-object-ado.md)und einem oder mehreren Datensätzen (auch als Kapitel bezeichnet) eines anderen **Recordsets**angezeigt werden. In einer über-/Unterordnungsbeziehung enthält das übergeordnete **Recordset** das untergeordnete **Recordset**. Ein Beispiel für eine solche hierarchische Beziehung sind Kunden und Bestellungen. Für jeden Kunden in einer Datenbank können NULL oder mehr Bestellungen vorhanden sein. Die hierarchische Beziehung kann rekursiv sein. Dies bedeutet, dass Datensätze mit zwei untergeordneten Datensätzen in einem untergeordneten Datensatz eingefügt werden können Im Prinzip kann ein hierarchischer Datensatz in beliebiger Tiefe schachtelt werden. In der Praxis beschränkt ADO die Rekursion auf maximal 512 **Recordsets**.  
  
 Im Allgemeinen können Spalten eines geformten **Recordsets** Daten von einem Datenanbieter enthalten, wie z. b. Microsoft® SQL Server, Verweise auf ein anderes **Recordset**, Werte, die von einer Berechnung in einer einzelnen Zeile eines **Recordsets**abgeleitet werden, oder Werte, die von einem Vorgang für eine Spalte eines gesamten **Recordsets**abgeleitet werden. Eine Spalte kann auch neu erfunden und leer sein.  
  
 Wenn Sie den Wert einer Spalte abrufen, die einen Verweis auf ein anderes **Recordset**enthält, gibt ADO automatisch das tatsächliche **Recordset** zurück, das durch den Verweis dargestellt wird. Der Verweis auf ein **Recordset** ist tatsächlich ein Verweis auf eine Teilmenge des untergeordneten Elements, das als *Kapitel*bezeichnet wird. Ein einzelnes übergeordnetes Element kann auf mehr als ein untergeordnetes **Recordset**verweisen.  
  
 Mithilfe der ADO-Unterstützung für die Daten Strukturierung können Sie eine Datenquelle Abfragen und ein **Recordset** zurückgeben, in dem ein (übergeordneter) Datensatz ein (untergeordnetes) **Recordset**darstellt. Im Kundenauftrags Szenario können Sie mithilfe der Daten Strukturierung die Informationen von Kunden und die Bestellungen der einzelnen Kunden in einer einzelnen Abfrage abrufen. Das resultierende **Recordset** wird auch als geformtes **Recordset**bezeichnet.  
  
 Darüber hinaus können Sie mithilfe der Daten Strukturierung in ADO neue **Recordsetobjekte** ohne zugrunde liegende Datenquelle erstellen, indem Sie das **New** -Schlüsselwort verwenden, um die Felder des übergeordneten und des untergeordneten **Recordsets**zu beschreiben. Das neue **Recordset** -Objekt kann dann mit Daten aufgefüllt und permanent gespeichert werden. Entwickler können auch verschiedene Berechnungen oder Aggregationen (z. b. **Sum**, **AVG**und **Max**) für untergeordnete Felder durchführen. Die Daten Strukturierung kann auch ein übergeordnetes **Recordset** aus einem untergeordneten **Recordset** erstellen, indem Datensätze im untergeordneten Element gruppiert werden und eine Zeile in der übergeordneten Gruppe für jede Gruppe im untergeordneten Element platziert wird.  
  
 Reguläres SQL ermöglicht das Abrufen von Daten **mithilfe der** joinsyntax, dies kann jedoch ineffizient und unhandlich sein, da redundante übergeordnete Daten in jedem Datensatz wiederholt werden, der für eine bestimmte über-/Unterordnungsbeziehung zurückgegeben wurde Die Daten Strukturierung kann einen einzelnen übergeordneten Datensatz im übergeordneten **Recordset** mit mehreren untergeordneten Datensätzen im untergeordneten **Recordset**verknüpfen und so die Redundanz **eines Joins vermeiden.** Die meisten Leute finden das über-/unterordnungsmodell mit mehreren **Recordsets** natürlicher und einfacher zu arbeiten als das einzelne **Recordset** -joinmodell.
