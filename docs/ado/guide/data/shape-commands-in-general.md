---
title: Shape-Befehle im allgemeinen | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 0554da0486b58aff8da6fcf012732b6012f70ae6
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82760856"
---
# <a name="shape-commands-in-general"></a>Shape-Befehle im Allgemeinen
Die Daten Strukturierung definiert die Spalten eines geformten **Recordsets**, die Beziehungen zwischen den Entitäten, die durch die Spalten dargestellt werden, und die Art und Weise, in der das **Recordset** mit Daten aufgefüllt wird.  
  
 Ein geformtes **Recordset** kann aus den folgenden Spaltentypen bestehen.  
  
|Spaltentyp|Beschreibung|  
|-----------------|-----------------|  
|data|Felder aus einem **Recordset** , das von einem Abfragebefehl an einen Datenanbieter, eine Tabelle oder ein zuvor geformtes **Recordset**zurückgegeben wurde.|  
|geschlagen|Ein Verweis auf ein anderes **Recordset**, das als *Kapitel*bezeichnet wird. Mit den Kapitel Spalten können Sie eine Beziehung zwischen über *geordneten* und untergeordneten Elementen definieren, wobei das übergeordnete Element das **Recordset** ist, das die Kapitel-Spalte enthält, *und das unter* *geordnete* Element das **Recordset** , das durch das Kapitel|  
|aggregate|Der Wert der Spalte wird durch Ausführen einer *Aggregatfunktion* für alle Zeilen oder eine Spalte aller Zeilen eines untergeordneten **Recordsets**abgeleitet. (Siehe Aggregatfunktionen im folgenden Thema, [Aggregatfunktionen, die Calc-Funktion und das New-Schlüsselwort](../../../ado/guide/data/aggregate-functions-the-calc-function-and-the-new-keyword.md).)|  
|Berechneter Ausdruck|Der Wert der Spalte wird durch Berechnen eines Visual Basic for Applications Ausdrucks für Spalten in derselben Zeile des **Recordsets**abgeleitet. Der Ausdruck ist das Argument für die Calc-Funktion. (Siehe berechneter Ausdruck im folgenden Thema, [Aggregatfunktionen, die Calc-Funktion und das New-Schlüsselwort](../../../ado/guide/data/aggregate-functions-the-calc-function-and-the-new-keyword.md) und in [Visual Basic for Applications Funktionen](../../../ado/guide/data/visual-basic-for-applications-functions.md).)|  
|neu|Leere, fabrizierte Felder, die zu einem späteren Zeitpunkt mit Daten aufgefüllt werden können. Die Spalte wird mit dem New-Schlüsselwort definiert. (Siehe das New-Schlüsselwort im folgenden Thema, [Aggregatfunktionen, die Calc-Funktion und das New-Schlüsselwort](../../../ado/guide/data/aggregate-functions-the-calc-function-and-the-new-keyword.md).)|  
  
 Ein Shape-Befehl kann eine-Klausel enthalten, die einen Abfragebefehl an einen zugrunde liegenden Datenanbieter angibt, der ein **Recordset** -Objekt zurückgibt. Die Syntax der Abfrage hängt von den Anforderungen des zugrunde liegenden Datenanbieters ab. Dies ist normalerweise SQL, obwohl ADO die Verwendung einer bestimmten Abfragesprache nicht erfordert.  
  
 Shape-Befehle können von **Recordset** -Objekten oder durch Festlegen der [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) -Eigenschaft des [Command](../../../ado/reference/ado-api/command-object-ado.md) -Objekts und anschließendes Aufrufen der [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md) -Methode ausgegeben werden.  
  
 Sie können eine SQL Join-Klausel verwenden, um zwei Tabellen in Beziehung zu setzen. Allerdings kann ein hierarchisches **Recordset** die Informationen effizienter darstellen. Jede Zeile eines **Recordsets** , das von einem Join erstellt wurde, wiederholt Informationen redundant aus einer der Tabellen. Ein hierarchisches **Recordset** verfügt nur über ein übergeordnetes **Recordset** für jedes untergeordnete **Recordset-Objekt.**  
  
 Shape-Befehle können eingebettet werden. Das heißt, dass der über *geordnete Befehl* oder der untergeordnete Befehl selbst ein anderer Shape *-* Befehl sein kann.  
  
 Der Shape-Anbieter gibt immer einen Client Cursor zurück, auch wenn der Benutzer eine Cursorposition von **adstreameserver**angibt.  
  
 Sie können Programm gesteuert oder über ein entsprechendes visuelles Steuerelement auf die **recordsetkomponenten** des geformten **Recordsets** zugreifen.  
  
 Microsoft stellt ein visuelles Tool bereit, das Shape-Befehle generiert (Weitere Informationen finden Sie im [Data Environment Designer](https://go.microsoft.com/fwlink/?LinkId=5689) in der Dokumentation zu Visual Basic 6) und eine weitere mit hierarchischen Cursorn (Weitere Informationen finden Sie in der Dokumentation zu Visual Basic 6 unter "Verwenden des hierarchischen Microsoft-Steuer Elements  
  
 Informationen zum Navigieren in einem hierarchischen **Recordset**finden Sie unter [zugreifen auf Zeilen in einem hierarchischen Recordset](../../../ado/guide/data/accessing-rows-in-a-hierarchical-recordset.md).  
  
 Genaue Informationen zu syntaktisch korrekten Shape-Befehlen finden Sie unter [formale Shape-Grammatik](../../../ado/guide/data/formal-shape-grammar.md).  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Aggregatfunktionen, die CALC-Funktion und das NEW-Schlüsselwort](../../../ado/guide/data/aggregate-functions-the-calc-function-and-the-new-keyword.md)  
  
-   [Ausgeben von Befehlen an den zugrunde liegenden Datenanbieter](../../../ado/guide/data/issuing-commands-to-the-underlying-data-provider.md)
