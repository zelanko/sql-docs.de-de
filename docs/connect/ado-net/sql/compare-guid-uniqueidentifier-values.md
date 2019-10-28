---
title: Vergleichen von GUID- und uniqueidentifier-Werten
description: Veranschaulicht das Arbeiten mit GUID-und uniqueidentifier-Werten in SQL Server und .net.
ms.date: 09/30/2019
dev_langs:
- csharp
ms.assetid: aababd75-2335-43e3-ace8-4b7ae84191a8
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: 8a4c5fcc63c2d2ddb8414227ea049e78db1cba10
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72452284"
---
# <a name="comparing-guid-and-uniqueidentifier-values"></a>Vergleichen von GUID- und uniqueidentifier-Werten

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[ADO.NET herunterladen](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Der Globally Unique Identifier (GUID)-Datentyp in SQL Server wird durch den `uniqueidentifier`-Datentyp dargestellt, der einen 16-Byte-Binärwert speichert. Ein GUID ist eine Binärzahl, und wird hauptsächlich als Bezeichner verwendet, der in einem Netzwerk mit vielen Computern an vielen Standorten eindeutig sein muss. GUIDs können durch Aufrufen der Transact-SQL-Funktion "netwid" generiert werden und sind auf der ganzen Welt eindeutig. Weitere Informationen finden Sie unter [uniqueidentifier (Transact-SQL)](../../../t-sql/data-types/uniqueidentifier-transact-sql.md).  
  
## <a name="working-with-sqlguid-values"></a>Arbeiten mit SqlGuid-Werten  
Da GUIDs-Werte lang und undurchsichtig sind, sind Sie für Benutzer nicht von Bedeutung. Wenn zufällig generierte GUIDs für Schlüsselwerte verwendet werden und Sie viele Zeilen einfügen, erhalten Sie zufällige e/a-Vorgänge in Ihren Indizes, was sich negativ auf die Leistung auswirken kann. GUIDs sind im Vergleich zu anderen Datentypen ebenfalls relativ groß. Im Allgemeinen wird die Verwendung von GUIDs nur für sehr schmale Szenarien empfohlen, für die kein anderer Datentyp geeignet ist.  
  
### <a name="comparing-guid-values"></a>Vergleichen von GUID-Werten  
Vergleichsoperatoren können mit `uniqueidentifier`-Werten verwendet werden. Allerdings erfolgt das Sortieren nicht durch Vergleichen der Bitmuster der beiden Werte. Die einzigen für einen `uniqueidentifier`-Wert zulässigen Operationen sind das Vergleichen (=, <>, \<, >, \<=, >=) und das Überprüfen auf NULL (IS NULL und IS NOT NULL). Andere arithmetische Operationen sind nicht zulässig.  
  
Sowohl <xref:System.Guid> als auch <xref:System.Data.SqlTypes.SqlGuid> haben eine `CompareTo`-Methode zum Vergleichen unterschiedlicher GUID-Werte. `System.Guid.CompareTo` und `SqlTypes.SqlGuid.CompareTo` werden jedoch anders implementiert. <xref:System.Data.SqlTypes.SqlGuid> implementiert `CompareTo` mit SQL Server Verhalten. in den letzten sechs Bytes eines Werts sind die wichtigsten Werte. <xref:System.Guid> wertet alle 16 Bytes aus. Im folgenden Beispiel werden diese unterschiedlichen Verhaltensweisen veranschaulicht. Der erste Code Abschnitt zeigt unsortierte <xref:System.Guid> Werte an, und der zweite Code Abschnitt zeigt die sortierten <xref:System.Guid> Werte. Der dritte Abschnitt zeigt die sortierten <xref:System.Data.SqlTypes.SqlGuid> Werte an. Die Ausgabe wird unterhalb der Code Auflistung angezeigt.  
  
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
