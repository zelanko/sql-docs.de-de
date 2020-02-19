---
title: Vergleichen von GUID- und uniqueidentifier-Werten
description: Veranschaulicht das Arbeiten mit GUID- und uniqueidentifier-Werten in SQL Server und .NET.
ms.date: 09/30/2019
dev_langs:
- csharp
ms.assetid: aababd75-2335-43e3-ace8-4b7ae84191a8
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: 35fc93a9ce6eb5b1709c6671adb21eb3030dea63
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "75247851"
---
# <a name="comparing-guid-and-uniqueidentifier-values"></a>Vergleichen von GUID- und uniqueidentifier-Werten

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[ADO.NET herunterladen](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Der Datentyp GUID (Globally Unique Identifier) in SQL Server wird vom Datentyp `uniqueidentifier` dargestellt, der einen Binärwert mit 16 Bytes speichert. Ein GUID ist eine Binärzahl, und wird hauptsächlich als Bezeichner verwendet, der in einem Netzwerk mit vielen Computern an vielen Standorten eindeutig sein muss. GUIDs können durch Aufrufen der Transact-SQL-Funktion NEWID generiert werden und sind weltweit eindeutig. Weitere Informationen finden Sie unter [uniqueidentifier (Transact-SQL)](../../../t-sql/data-types/uniqueidentifier-transact-sql.md).  
  
## <a name="working-with-sqlguid-values"></a>Arbeiten mit SqlGuid-Werten  
Aufgrund ihrer langen und unverständlichen Werte sind GUIDs für Benutzer nicht aussagekräftig. Wenn zufällig generierte GUIDs für Schlüsselwerte verwendet werden und Sie viele Zeilen einfügen, erfolgen in Ihren Indizes zufällige E/A-Vorgänge, was sich negativ auf die Leistung auswirken kann. Außerdem sind GUIDs im Vergleich mit anderen Datentypen relativ lang. Generell wird empfohlen, GUIDs nur in sehr eng umgrenzten Szenarien zu verwenden, für die kein anderer Datentyp geeignet ist.  
  
### <a name="comparing-guid-values"></a>Vergleichen von GUID-Werten  
Vergleichsoperatoren können mit `uniqueidentifier`-Werten verwendet werden. Allerdings erfolgt das Sortieren nicht durch Vergleichen der Bitmuster der beiden Werte. Die einzigen für einen `uniqueidentifier`-Wert zulässigen Operationen sind das Vergleichen (=, <>, \<, >, \<=, >=) und das Überprüfen auf NULL (IS NULL und IS NOT NULL). Andere arithmetische Operationen sind nicht zulässig.  
  
<xref:System.Guid> und <xref:System.Data.SqlTypes.SqlGuid> verfügen über eine `CompareTo`-Methode zum Vergleichen unterschiedlicher GUID-Werte. `System.Guid.CompareTo` und `SqlTypes.SqlGuid.CompareTo` werden jedoch unterschiedlich implementiert. <xref:System.Data.SqlTypes.SqlGuid> implementiert `CompareTo` mit SQL Server-Verhalten, wobei die letzten 6 Bytes eines Werts am signifikantesten sind. <xref:System.Guid> wertet alle 16 Bytes aus. Im folgenden Beispiel werden diese unterschiedlichen Verhaltensweisen veranschaulicht. Der erste Codeabschnitt zeigt unsortierte <xref:System.Guid>-Werte, der zweite die sortierten <xref:System.Guid>-Werte. Der dritte Abschnitt enthält die sortierten <xref:System.Data.SqlTypes.SqlGuid>-Werte. Die Ausgabe wird unter der Codeliste gezeigt.  
  
[!code-csharp[DataWorks SqlGuid#1](~/../sqlclient/doc/samples/SqlGuid.cs#1)]
  
Hierdurch werden folgende Ergebnisse generiert.  
  
```console
Unsorted Guids:  
3aaaaaaa-bbbb-cccc-dddd-2eeeeeeeeeee  
2aaaaaaa-bbbb-cccc-dddd-1eeeeeeeeeee  
1aaaaaaa-bbbb-cccc-dddd-3eeeeeeeeeee  
  
Sorted Guids:  
1aaaaaaa-bbbb-cccc-dddd-3eeeeeeeeeee  
2aaaaaaa-bbbb-cccc-dddd-1eeeeeeeeeee  
3aaaaaaa-bbbb-cccc-dddd-2eeeeeeeeeee  
  
Sorted SqlGuids:  
2aaaaaaa-bbbb-cccc-dddd-1eeeeeeeeeee  
3aaaaaaa-bbbb-cccc-dddd-2eeeeeeeeeee  
1aaaaaaa-bbbb-cccc-dddd-3eeeeeeeeeee  
```  
  
## <a name="next-steps"></a>Nächste Schritte
- [SQL Server-Datentypen und ADO.NET](sql-server-data-types.md)
