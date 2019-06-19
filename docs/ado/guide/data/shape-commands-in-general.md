---
title: Shape-Befehle in der Regel | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- shape commands [ADO]
- data shaping [ADO], shape commands
ms.assetid: 1fac7831-a187-4b15-9b43-aad380c5556c
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: f44063e4f1994e01f3685fdb2c7c47a5c41d4998
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66704893"
---
# <a name="shape-commands-in-general"></a>Shape-Befehle im Allgemeinen
Strukturieren von Daten definiert die Spalten von einer geformten **Recordset**, die Beziehungen zwischen den Entitäten, die durch die Spalten und die Art und Weise, in dem dargestellt wird die **Recordset** mit Daten aufgefüllt wird.  
  
 Eine geformten **Recordset** können, bestehen die folgenden Typen von Spalten.  
  
|Spaltentyp|Description|  
|-----------------|-----------------|  
|data|Felder aus einem **Recordset** von einem Abfragebefehl zurückgegeben wird für einem Datenanbieter, Tabelle oder zuvor strukturiert **Recordset**.|  
|Kapitel|Ein Verweis auf einen anderen **Recordset**Namens eine *Kapitel*. Kapitelspalten können sie definieren eine *über-und untergeordneten* Beziehung, in denen die *übergeordneten* ist die **Recordset** , enthält das Kapitelspalte und die *untergeordneten* ist die **Recordset** durch das Kapitel dargestellt wird.|  
|Aggregat (aggregate)|Der Wert der Spalte ergibt sich durch Ausführen einer *Aggregatfunktion* auf alle Zeilen oder eine Spalte aller Zeilen eines untergeordneten Elements **Recordset**. (Im folgenden Thema finden Sie in Aggregatfunktionen [Aggregatfunktionen, die CALC-Funktion und das neue Schlüsselwort](../../../ado/guide/data/aggregate-functions-the-calc-function-and-the-new-keyword.md).)|  
|berechneter Ausdruck|Der Wert der Spalte ergibt sich durch Berechnen eines Visual Basic für Applikationen-Ausdruck für Spalten in der gleichen Zeile von der **Recordset**. Der Ausdruck ist das Argument für die CALC-Funktion. (Finden Sie unter berechneter Ausdruck im folgenden Thema [Aggregatfunktionen, die CALC-Funktion und das neue Schlüsselwort](../../../ado/guide/data/aggregate-functions-the-calc-function-and-the-new-keyword.md) und [Visual Basic for Applications-Funktionen](../../../ado/guide/data/visual-basic-for-applications-functions.md).)|  
|new|Leere erstellte Felder, die zu einem späteren Zeitpunkt mit Daten aufgefüllt werden können. Die Spalte wird mit dem neuen Schlüsselwort definiert. (Siehe NEW-Schlüsselwort in das folgende Thema, [Aggregatfunktionen, die CALC-Funktion und das neue Schlüsselwort](../../../ado/guide/data/aggregate-functions-the-calc-function-and-the-new-keyword.md).)|  
  
 Ein Shape-Befehl darf eine Klausel, ein Abfragebefehls für eine zugrunde liegende Datenanbieter angibt, der zurückgegeben wird, ein **Recordset** Objekt. Die Syntax der Abfrage hängt von den Anforderungen der zugrunde liegenden Datenanbieters ab. Dies wird in der Regel SQL sein, obwohl ADO die Verwendung von bestimmte Abfragesprache nicht erforderlich ist.  
  
 Shape-Befehle können ausgestellt werden, indem **Recordset** Objekte oder durch Festlegen der [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) Eigenschaft der [Befehl](../../../ado/reference/ado-api/command-object-ado.md) und anschließend durch Aufrufen der [ausführen ](../../../ado/reference/ado-api/execute-method-ado-command.md) Methode.  
  
 Sie können eine SQL-JOIN-Klausel verwenden, zum Verknüpfen von zwei Tabellen; allerdings eine hierarchische **Recordset** die Informationen können effizienter darstellen. Jede Zeile eine **Recordset** durch redundant aus einer der Tabellen JOIN Wiederholungen Informationen erstellt. Eine hierarchische **Recordset** hat nur ein übergeordnetes Element **Recordset** für jede der verschiedenen untergeordneten **Recordset** Objekte.  
  
 Shape-Befehle können geschachtelt werden. D. h. die *übergeordnete Befehl* oder *untergeordneten Befehl* selbst ist möglicherweise ein anderes Shape-Befehl.  
  
 Der Shape-Anbieter gibt immer einem Clientcursor wird zurück, selbst wenn der Benutzer eine Cursorposition des angibt **AdUseServer**.  
  
 Sie erreichen die **Recordset** Bestandteile der geformten **Recordset** programmgesteuert oder über eine geeignete visuelle Steuerelemente.  
  
 Microsoft bietet ein visuelles Tool, das Shape-Befehlen generiert (finden Sie unter den [Umgebung Datendesigner](https://go.microsoft.com/fwlink/?LinkId=5689) in der Dokumentation zu Visual Basic 6) und eine andere, die hierarchische Cursor angezeigt (siehe "Verwenden der Microsoft hierarchische Flex-Tabelle Control"in der Dokumentation zu Visual Basic 6).  
  
 Informationen zum Navigieren durch eine hierarchische **Recordset**, finden Sie unter [den Zugriff auf Zeilen in einem hierarchischen Recordset](../../../ado/guide/data/accessing-rows-in-a-hierarchical-recordset.md).  
  
 Genaue Informationen syntaktisch korrekte Shape-Befehlen finden Sie unter [formale Grammatik für Formen](../../../ado/guide/data/formal-shape-grammar.md).  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Aggregatfunktionen, die CALC-Funktion und das NEW-Schlüsselwort](../../../ado/guide/data/aggregate-functions-the-calc-function-and-the-new-keyword.md)  
  
-   [Ausgeben von Befehlen an den zugrunde liegenden Datenanbieter](../../../ado/guide/data/issuing-commands-to-the-underlying-data-provider.md)
