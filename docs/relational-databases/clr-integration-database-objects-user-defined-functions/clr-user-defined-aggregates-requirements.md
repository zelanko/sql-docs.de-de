---
title: Anforderungen an benutzerdefinierte CLR-Aggregate | Microsoft-Dokumentation
description: SQL Server CLR-Integration ermöglicht es Ihnen, benutzerdefinierte Aggregatfunktionen in verwaltetem Code zu erstellen. Sie müssen den erforderlichen Aggregations Vertrag implementieren.
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81487946"
---
# <a name="clr-user-defined-aggregates---requirements"></a>Benutzerdefinierte CLR-Aggregate: Anforderungen
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Ein Typ in einer CLR-Assembly (Common Language Runtime) kann als benutzerdefinierte Aggregatfunktion registriert werden, solange der erforderliche Aggregationsvertrag implementiert wird. Dieser Vertrag besteht aus dem **SqlUserDefinedAggregate** -Attribut und den Aggregations Vertrags Methoden. Der Aggregations Vertrag enthält den Mechanismus zum Speichern des zwischen Status der Aggregation und den Mechanismus zum kumulieren neuer Werte, der aus vier Methoden besteht: **Init**, **Kumulierung**, **Merge**und **End.** Wenn Sie diese Anforderungen erfüllt haben, sind Sie in der Lage, benutzerdefinierte Aggregate in in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]vollem Umfang zu nutzen. Die folgenden Abschnitte zu diesem Thema enthalten zusätzliche Details zum Erstellen von benutzerdefinierten Aggregaten und ihrer Verwendungsweise. Ein Beispiel finden Sie unter [Aufrufen von benutzerdefinierten CLR-Aggregatfunktionen](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregate-invoking-functions.md).  
  
## <a name="sqluserdefinedaggregate"></a>SqlUserDefinedAggregate  
 Weitere Informationen finden Sie unter [SqlUserDefinedAggregateAttribute](https://go.microsoft.com/fwlink/?LinkId=124626).  
  
## <a name="aggregation-methods"></a>Aggregationsmethoden  
 Die als benutzerdefiniertes Aggregat registrierte Klasse muss die folgenden Instanzmethoden unterstützen. Diese Methoden werden vom Abfrageprozessor verwendet, um die Aggregation zu berechnen:  
  
|Methode|Syntax|BESCHREIBUNG|  
|------------|------------|-----------------|  
|**Init**|`public void Init();`|Der Abfrageprozessor verwendet diese Methode, um die Berechnung der Aggregation zu initialisieren. Diese Methode wird einmal für jede Gruppe aufgerufen, die der Abfrageprozessor aggregiert. Der Abfrageprozessor verwendet möglicherweise dieselbe Instanz der Aggregatklasse mehrfach, um Aggregate für mehrere Gruppen zu berechnen. Die **Init** -Methode sollte bei Bedarf alle Bereinigungs Vorgänge aus früheren Verwendungsmöglichkeiten dieser Instanz durchführen und die Initialisierung einer neuen Aggregat Berechnung ermöglichen.|  
|**Reichert**|`public void Accumulate ( input-type value[, input-type value, ...]);`|Ein oder mehrere Parameter, die die Parameter der Funktion darstellen. *INPUT_TYPE* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] muss der verwaltete Datentyp sein, der dem System [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eigenen Datentyp entspricht, der durch *input_sqltype* in der **Create Aggregate** -Anweisung angegeben wird. Weitere Informationen finden Sie unter [Mapping von CLR-Parameter Daten](../../relational-databases/clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md).<br /><br /> Für benutzerdefinierte Typen (User-Defined Types, UDTs) entspricht der Eingabetyp dem UDT-Typ. Der Abfrageprozessor verwendet diese Methode, um die Aggregatwerte zu sammeln. Sie wird einmal für jeden Wert in der zu aggregierenden Gruppe aufgerufen. Der Abfrage Prozessor ruft dies immer nur auf, nachdem die **Init** -Methode für die angegebene Instanz der Aggregat Klasse aufgerufen wurde. Durch die Implementierung dieser Methode wird der Instanzstatus auf den momentanen Stand der übergebenen Argumentwertansammlung aktualisiert.|  
|**Merge** (Zusammenführen)|`public void Merge( udagg_class value);`|Diese Methode kann verwendet werden, um eine andere Instanz dieser Aggregatklasse mit der aktuellen Instanz zusammenzuführen. Der Abfrageprozessor verwendet diese Methode, um mehrere Teilberechnungen einer Aggregation zusammenzuführen.|  
|**Terminate**|`public return_type Terminate();`|Diese Methode schließt die Aggregatberechnung ab und gibt das Ergebnis der Aggregation zurück. Der *return_type* sollte ein verwalteter [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datentyp sein, der das verwaltete Äquivalent von *return_sqltype* ist, das in der **Create Aggregate** -Anweisung angegeben ist. Der *return_type* kann auch ein benutzerdefinierter Typ sein.|  
  
### <a name="table-valued-parameters"></a>Tabellenwertparameter  
 Tabellenwertparameter (Table Valued Parameters, TVPs), benutzerdefinierte Tabellentypen, die an eine Prozedur oder Funktion übergeben werden, bieten eine effiziente Methode zum Übergeben mehrerer Datenzeilen an den Server. TVPs verfügen über eine ähnliche Funktionalität wie Parameterarrays, bieten aber größere Flexibilität und engere Integration mit [!INCLUDE[tsql](../../includes/tsql-md.md)]. Außerdem verfügen sie auch über ein besseres Leistungspotenzial. TVPs helfen auch, die Anzahl von Roundtrips zum Server zu reduzieren. Anstatt mehrere Anforderungen an den Server zu senden, z. B. mit einer Liste von skalaren Parametern, können Daten als TVP an den Server gesendet werden. Ein benutzerdefinierter Tabellentyp kann nicht als Tabellenwertparameter an eine verwaltete gespeicherte Prozedur oder Funktion übergeben werden, die im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Prozess ausgeführt wird, oder von einer solchen Prozedur oder Funktion zurückgegeben werden. Auch können TVPs nicht innerhalb des Bereichs einer Kontextverbindung verwendet werden. Allerdings kann ein TVP, sofern er nicht als Kontextverbindung verwendet wird, mit SqlClient in verwalteten gespeicherten Prozeduren oder Funktionen verwendet werden, die im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Prozess ausgeführt werden. Die Verbindung kann zum gleichen Server erfolgen, der die verwaltete Prozedur oder Funktion ausführt. Weitere Informationen zu TVPs finden Sie unter [Verwenden von Tabellenwert Parametern &#40;Datenbank-Engine&#41;](../../relational-databases/tables/use-table-valued-parameters-database-engine.md).  
  
## <a name="change-history"></a>Änderungsverlauf  
  
|Aktualisierter Inhalt|  
|---------------------|  
|Die Beschreibung der **Akkumulations** Methode wurde aktualisiert. Es akzeptiert nun mehr als einen Parameter.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Benutzerdefinierte CLR-Typen](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)   
 [Aufrufen von CLR-benutzerdefinierten Aggregatfunktionen](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregate-invoking-functions.md)  
  
  
