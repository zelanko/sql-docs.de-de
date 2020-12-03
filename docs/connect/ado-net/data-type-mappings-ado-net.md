---
title: Datentypzuordnungen
description: Erfahren Sie mehr zu den Datentypen, die vom Microsoft SqlClient-Datenanbieter für SQL Server verwendet werden.
ms.date: 11/13/2020
ms.assetid: d4afab94-ada6-4c77-a73c-41f17bae6b5a
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-chmalh
ms.openlocfilehash: 03af2a8544763aab7609fd713790622bbb1bfef4
ms.sourcegitcommit: debaff72dbfae91b303f0acd42dd6d99e03135a2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/01/2020
ms.locfileid: "96419761"
---
# <a name="data-type-mappings-in-adonet"></a>Datentypzuordnungen in ADO.NET

[!INCLUDE[appliesto-netfx-netcore-netst-md](../../includes/appliesto-netfx-netcore-netst-md.md)]

[!INCLUDE[Driver_ADONET_Download](../../includes/driver_adonet_download.md)]

ADO.NET basiert auf dem allgemeinen Typsystem, das definiert, wie Typen in der Runtime deklariert, verwendet und verwaltet werden. Es besteht aus Werttypen und Verweistypen, die alle vom <xref:System.Object>-Basistyp abgeleitet sind. Bei Datenquellen wird über den Datenanbieter auf den Datentyp geschlossen, wenn dieser nicht explizit angegeben ist. Ein <xref:System.Data.DataSet>-Objekt ist z. B. von keiner bestimmten Datenquelle abhängig. Daten in einem `DataSet` werden aus einer Datenquelle abgerufen, und Änderungen werden mithilfe eines `DataAdapter` in die Datenquelle übernommen. Dieser Programmablauf bedeutet, dass, wenn ein `DataAdapter` eine <xref:System.Data.DataTable> in einem `DataSet` mit Werten aus einer Datenquelle füllt, die resultierenden Datentypen der Spalten in der `DataTable` .NET Framework-Typen und keine Typen sind, die spezifisch für den Microsoft SqlClient-Datenanbieter für SQL Server sind, der zur Herstellung einer Verbindung mit der Datenquelle verwendet wird.

Wenn ein `DataReader`-Objekt einen Wert aus einer Datenquelle zurückgibt, wird dieser Wert entsprechend in einer lokalen Variablen gespeichert, die einen .NET Framework-Typ aufweist. Für die `Fill`-Vorgänge von `DataAdapter` und die `Get`-Methoden von `DataReader` wird der .NET Framework-Typ vom Wert abgeleitet, der vom Microsoft SqlClient-Datenanbieter für SQL Server zurückgegeben wird.

Sie können auch die typisierten Zugriffsmethoden des `DataReader` verwenden, wenn Sie den Typ des zurückgegebenen Werts kennen, anstatt den hergeleiteten Datentyp zu verwenden. Mit typisierten Accessormethoden erzielen Sie eine bessere Leistung, da ein Wert als bestimmter .NET Framework-Typ zurückgegeben wird und somit keine weitere Typkonvertierung erforderlich ist.

> [!NOTE]
> NULL-Werte für Datentypen des Microsoft SqlClient-Datenanbieters für SQL Server werden durch `DBNull.Value` dargestellt.

## <a name="in-this-section"></a>In diesem Abschnitt

[SQL Server-Datentypzuordnungen](sql-server-data-type-mappings.md) Listet die abgeleiteten Datentypzuordnungen und Datenaccessormethoden für <xref:Microsoft.Data.SqlClient> auf.

[Gleitkommazahlen](floating-point-numbers.md) Beschreibt Probleme, die beim Arbeiten mit Gleitkommazahlen häufig auftreten.

## <a name="see-also"></a>Weitere Informationen

- [SQL Server-Datentypen und ADO.NET](./sql/sql-server-data-types.md)
- [Konfigurieren von Parametern](configure-parameters.md)
