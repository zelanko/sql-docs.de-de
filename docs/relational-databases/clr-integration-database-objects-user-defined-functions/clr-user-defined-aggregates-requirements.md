---
title: Anforderungen an benutzerdefinierte CLR-Aggregate | Microsoft Docs
description: Mit der SQL Server CLR-Integration können Sie benutzerdefinierte Aggregatfunktionen in verwaltetem Code erstellen. Sie müssen den erforderlichen Aggregationsvertrag implementieren.
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- aggregate functions [CLR integration]
- user-defined types [CLR integration], user-defined aggregates
- CREATE AGGREGATE statement
- SqlUserDefinedAggregate attribute
- aggregate methods [CLR integration]
- assemblies [CLR integration], user-defined aggregate functions
- custom aggregates [CLR integration]
- user-defined functions [CLR integration]
- UDTs [CLR integration], user-defined aggregates
ms.assetid: dbf9eb5a-bd99-42f7-b275-556d0def045d
author: rothja
ms.author: jroth
ms.openlocfilehash: 9dd27cf3751400d3902ddd4199daee8aeef78b80
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81487946"
---
# <a name="clr-user-defined-aggregates---requirements"></a>Benutzerdefinierte CLR-Aggregate: Anforderungen
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Ein Typ in einer CLR-Assembly (Common Language Runtime) kann als benutzerdefinierte Aggregatfunktion registriert werden, solange der erforderliche Aggregationsvertrag implementiert wird. Dieser Vertrag besteht aus dem **SqlUserDefinedAggregate-Attribut** und den Aggregationsvertragsmethoden. Der Aggregationsvertrag enthält den Mechanismus zum Speichern des Zwischenzustands der Aggregation und den Mechanismus zum Ansammeln neuer Werte, der aus vier Methoden besteht: **Init**, **Accumulate**, **Merge**und **Terminate**. Wenn Sie diese Anforderungen erfüllt haben, können Sie die benutzerdefinierten [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Aggregate in voll ausschöpfen. Die folgenden Abschnitte zu diesem Thema enthalten zusätzliche Details zum Erstellen von benutzerdefinierten Aggregaten und ihrer Verwendungsweise. Ein Beispiel finden Sie [unter Aufrufen von benutzerdefinierten AGGREGATfunktionen](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregate-invoking-functions.md)von CLR .  
  
## <a name="sqluserdefinedaggregate"></a>SqlUserDefinedAggregate  
 Weitere Informationen finden Sie unter [SqlUserDefinedAggregateAttribute](https://go.microsoft.com/fwlink/?LinkId=124626).  
  
## <a name="aggregation-methods"></a>Aggregationsmethoden  
 Die als benutzerdefiniertes Aggregat registrierte Klasse muss die folgenden Instanzmethoden unterstützen. Diese Methoden werden vom Abfrageprozessor verwendet, um die Aggregation zu berechnen:  
  
|Methode|Syntax|BESCHREIBUNG|  
|------------|------------|-----------------|  
|**Init**|`public void Init();`|Der Abfrageprozessor verwendet diese Methode, um die Berechnung der Aggregation zu initialisieren. Diese Methode wird einmal für jede Gruppe aufgerufen, die der Abfrageprozessor aggregiert. Der Abfrageprozessor verwendet möglicherweise dieselbe Instanz der Aggregatklasse mehrfach, um Aggregate für mehrere Gruppen zu berechnen. Die **Init-Methode** sollte bei Bedarf eine Bereinigung aus früheren Verwendungen dieser Instanz durchführen und es ihr ermöglichen, eine neue Aggregatberechnung neu zu starten.|  
|**Sammeln**|`public void Accumulate ( input-type value[, input-type value, ...]);`|Ein oder mehrere Parameter, die die Parameter der Funktion darstellen. *input_type* sollte der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwaltete Datentyp [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sein, der dem systemeigenen Datentyp entspricht, der von *input_sqltype* in der **CREATE AGGREGATE-Anweisung** angegeben wird. Weitere Informationen finden Sie unter [Mapping CLR-Parameterdaten](../../relational-databases/clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md).<br /><br /> Für benutzerdefinierte Typen (User-Defined Types, UDTs) entspricht der Eingabetyp dem UDT-Typ. Der Abfrageprozessor verwendet diese Methode, um die Aggregatwerte zu sammeln. Sie wird einmal für jeden Wert in der zu aggregierenden Gruppe aufgerufen. Der Abfrageprozessor ruft dies immer erst auf, nachdem er die **Init-Methode** auf der angegebenen Instanz der Aggregatklasse aufgerufen hat. Durch die Implementierung dieser Methode wird der Instanzstatus auf den momentanen Stand der übergebenen Argumentwertansammlung aktualisiert.|  
|**Merge** (Zusammenführen)|`public void Merge( udagg_class value);`|Diese Methode kann verwendet werden, um eine andere Instanz dieser Aggregatklasse mit der aktuellen Instanz zusammenzuführen. Der Abfrageprozessor verwendet diese Methode, um mehrere Teilberechnungen einer Aggregation zusammenzuführen.|  
|**Terminate**|`public return_type Terminate();`|Diese Methode schließt die Aggregatberechnung ab und gibt das Ergebnis der Aggregation zurück. Bei *return_type* sollte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] es sich um einen verwalteten Datentyp handelt, der das verwaltete Äquivalent von *return_sqltype* ist, das in der **CREATE AGGREGATE-Anweisung** angegeben ist. Bei *return_type* kann es sich auch um einen benutzerdefinierten Typ handelt.|  
  
### <a name="table-valued-parameters"></a>Tabellenwertparameter  
 Tabellenwertparameter (Table Valued Parameters, TVPs), benutzerdefinierte Tabellentypen, die an eine Prozedur oder Funktion übergeben werden, bieten eine effiziente Methode zum Übergeben mehrerer Datenzeilen an den Server. TVPs verfügen über eine ähnliche Funktionalität wie Parameterarrays, bieten aber größere Flexibilität und engere Integration mit [!INCLUDE[tsql](../../includes/tsql-md.md)]. Außerdem verfügen sie auch über ein besseres Leistungspotenzial. TVPs helfen auch, die Anzahl von Roundtrips zum Server zu reduzieren. Anstatt mehrere Anforderungen an den Server zu senden, z. B. mit einer Liste von skalaren Parametern, können Daten als TVP an den Server gesendet werden. Ein benutzerdefinierter Tabellentyp kann nicht als Tabellenwertparameter an eine verwaltete gespeicherte Prozedur oder Funktion übergeben werden, die im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Prozess ausgeführt wird, oder von einer solchen Prozedur oder Funktion zurückgegeben werden. Auch können TVPs nicht innerhalb des Bereichs einer Kontextverbindung verwendet werden. Allerdings kann ein TVP, sofern er nicht als Kontextverbindung verwendet wird, mit SqlClient in verwalteten gespeicherten Prozeduren oder Funktionen verwendet werden, die im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Prozess ausgeführt werden. Die Verbindung kann zum gleichen Server erfolgen, der die verwaltete Prozedur oder Funktion ausführt. Weitere Informationen zu TVPs finden Sie unter Verwenden von [Tabellenwertparametern &#40;Datenbankmodul&#41;](../../relational-databases/tables/use-table-valued-parameters-database-engine.md).  
  
## <a name="change-history"></a>Änderungsverlauf  
  
|Aktualisierter Inhalt|  
|---------------------|  
|Die Beschreibung der **Accumulate-Methode** wurde aktualisiert; es akzeptiert jetzt mehr als einen Parameter.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Benutzerdefinierte CLR-Typen](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)   
 [Aufrufen von CLR-benutzerdefinierten Aggregatfunktionen](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregate-invoking-functions.md)  
  
  
