---
description: SHAPE APPEND-Klausel
title: Shape-APPEND-Klausel | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- shape commands [ADO]
- data shaping [ADO], APPEND clause
- append clause [ADO]
ms.assetid: f90fcf55-6b24-401d-94e1-d65bd24bd342
author: rothja
ms.author: jroth
ms.openlocfilehash: 11d2c02d24753460f90452ddd6cc6b1e1589b80b
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88979621"
---
# <a name="shape-append-clause"></a>SHAPE APPEND-Klausel
Die Form Befehl-Append-Klausel fügt eine Spalte oder Spalten an ein **Recordset**an. Häufig handelt es sich bei diesen Spalten um Kapitel Spalten, die auf ein untergeordnetes **Recordset**verweisen.  
  
## <a name="syntax"></a>Syntax  
  
```  
SHAPE [parent-command [[AS] parent-alias]] APPEND column-list  
```  
  
## <a name="description"></a>BESCHREIBUNG  
 Diese Klausel enthält folgende Teile:  
  
 *Parent-Command*  
 NULL oder eine der folgenden (Sie können den über *geordneten Befehl* vollständig weglassen):  
  
-   Ein Anbieter Befehl, der in geschweiften Klammern ("") eingeschlossen ist und {} ein **Recordset** -Objekt zurückgibt. Der Befehl wird an den zugrunde liegenden Datenanbieter ausgegeben, und seine Syntax hängt von den Anforderungen dieses Anbieters ab. Dies ist normalerweise die SQL-Sprache, auch wenn ADO keine bestimmte Abfragesprache erfordert.  
  
-   Ein anderer Shape-Befehl, der in Klammern eingebettet ist.  
  
-   Das Tabellen Schlüsselwort, gefolgt vom Namen einer Tabelle im Datenanbieter.  
  
 *übergeordneter Alias*  
 Ein optionaler Alias, der auf das übergeordnete **Recordset**verweist.  
  
 *Spaltenliste*  
 Eine oder mehrere der folgenden:  
  
-   Eine Aggregat Spalte.  
  
-   Eine berechnete Spalte.  
  
-   Eine neue Spalte, die mithilfe der New-Klausel erstellt wurde.  
  
-   Eine Kapitel Spalte. Eine Kapitel Spaltendefinition ist in Klammern ("()") eingeschlossen. Siehe folgende Syntax.  
  
```  
SHAPE [parent-command [[AS] parent-alias]]  
   APPEND (child-recordset [ [[AS] child-alias]   
      RELATE parent-column TO child-column | PARAMETER param-number, ... ])  
   [[AS] chapter-alias]   
   [, ... ]  
```  
  
## <a name="remarks"></a>Bemerkungen  
 *untergeordnetes Recordset*  
 -   Ein Anbieter Befehl, der in geschweiften Klammern ("") eingeschlossen ist und {} ein **Recordset** -Objekt zurückgibt. Der Befehl wird an den zugrunde liegenden Datenanbieter ausgegeben, und seine Syntax hängt von den Anforderungen dieses Anbieters ab. Dies ist normalerweise die SQL-Sprache, auch wenn ADO keine bestimmte Abfragesprache erfordert.  
  
-   Ein anderer Shape-Befehl, der in Klammern eingebettet ist.  
  
-   Der Name eines vorhandenen geformten **Recordsets**.  
  
-   Das Tabellen Schlüsselwort, gefolgt vom Namen einer Tabelle im Datenanbieter.  
  
 *untergeordneter Alias*  
 Ein Alias, der auf das untergeordnete **Recordset**verweist.  
  
 *übergeordnete Spalte*  
 Eine Spalte in dem **Recordset** , das vom über *geordneten-Befehl* zurückgegeben wird.  
  
 *untergeordnete Spalte*  
 Eine Spalte in dem **Recordset** , das vom untergeordneten *Befehl*zurückgegeben wird.  
  
 *param-Nummer*  
 Siehe [Vorgang von parametrisierten Befehlen](../../../ado/guide/data/operation-of-parameterized-commands.md).  
  
 *Kapitel-Alias*  
 Ein Alias, der auf die Kapitel Spalte verweist, die an das übergeordnete Element angehängt ist.  
  
> [!NOTE]
>  Die *"Parent-Column* to *child-column"-* Klausel ist tatsächlich eine Liste, in der jede definierte Beziehung durch ein Komma getrennt ist.  
  
> [!NOTE]
>  Die Klausel nach dem Append-Schlüsselwort ist tatsächlich eine Liste, wobei jede Klausel durch ein Komma getrennt wird und eine andere Spalte definiert, die an das übergeordnete Element angefügt werden soll.  
  
Wenn Sie Anbieter Befehle aus Benutzereingaben als Teil eines Shape-Befehls erstellen, behandelt Shape den vom Benutzer bereitgestellten Anbieter Befehl als nicht transparente Zeichenfolge und übergibt sie an den Anbieter. Beispielsweise wird im folgenden Shape-Befehl  
  
```  
SHAPE {select * from t1} APPEND ({select * from t2} RELATE k1 TO k2)  
```  
  
 Shape führt zwei Befehle aus: `select * from t1` und ( `select * from t2 RELATE k1 TO k2)` . Wenn der Benutzer einen Verbund Befehl bereitstellt, der aus mehreren durch Semikolons getrennten Anbieter Befehlen besteht, kann die Form den Unterschied nicht unterscheiden. Im folgenden Shape-Befehl:  
  
```  
SHAPE {select * from t1; drop table t1} APPEND ({select * from t2} RELATE k1 TO k2)  
```  
  
 Shape führt `select * from t1; drop table t1` und `select * from t2 RELATE k1 TO k2),` aus (es wird nicht erkannt, dass `drop table t1` es sich um einen separaten und in diesem Fall um einen gefährlichen Anbieter Befehl handelt. Anwendungen müssen immer die Benutzereingaben validieren, um zu verhindern, dass potenzielle Hackerangriffe auftreten.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Verarbeitung nicht-parametrisierter Befehle](../../../ado/guide/data/operation-of-non-parameterized-commands.md)  
  
-   [Verarbeitung parametrisierter Befehle](../../../ado/guide/data/operation-of-parameterized-commands.md)  
  
-   [Hybridbefehle](../../../ado/guide/data/hybrid-commands.md)  
  
-   [Zwischenschalten von SHAPE COMPUTE-Klauseln](../../../ado/guide/data/intervening-shape-compute-clauses.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für Daten Strukturierung](../../../ado/guide/data/data-shaping-example.md)   
 [Formale Form Grammatik](../../../ado/guide/data/formal-shape-grammar.md)   
 [Shape-Befehle im Allgemeinen](../../../ado/guide/data/shape-commands-in-general.md)
