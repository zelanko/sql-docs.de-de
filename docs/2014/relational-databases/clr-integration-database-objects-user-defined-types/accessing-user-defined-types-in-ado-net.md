---
title: Zugreifen auf benutzerdefinierte Typen in ADO.NET | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- ADO.NET [CLR integration]
- UDTs [CLR integration], ADO.NET
- user-defined types [CLR integration], ADO.NET
ms.assetid: 4b0d876c-8066-490e-8e18-327c0e942b19
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 893b2c69a20974bb379cc032f442e5fcb3525ec5
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48129120"
---
# <a name="accessing-user-defined-types-in-adonet"></a>Zugreifen auf benutzerdefinierte Typen in ADO.NET
  Benutzerdefinierte Typen (UDTs) werden in einer beliebigen von unterstützten Sprachen der [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework common Language Runtime (CLR, die überprüfbaren Code generiert). Dazu gehören [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# und [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic. UDTs ermöglichen das Speichern von Objekten und benutzerdefinierten Datenstrukturen in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank. Die Daten werden als öffentliche Elemente einer .NET Framework-Klasse oder -Struktur verfügbar gemacht. Das Verhalten wird durch die Methoden der Klasse oder Struktur definiert. Ein UDT kann als Spaltendefinition einer Tabelle, als Variable in einem [!INCLUDE[tsql](../../includes/tsql-md.md)]-Batch oder als Argument einer [!INCLUDE[tsql](../../includes/tsql-md.md)]-Funktion oder gespeicherten Prozedur verwendet werden.  
  
 In ADO.NET macht der `System.Data.SqlClient`-Anbieter UDTs wie folgt verfügbar:  
  
-   Über `System.Data.SqlClient.SqlDataReader` als Objekt.  
  
-   Über `SqlDataReader` als Rohbytes.  
  
-   Als Parameter eines `System.Data.SqlClient.SqlParameter`-Objekts.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Abrufen von UDT-Daten](accessing-user-defined-types-retrieving-udt-data.md)  
 Beschreibt, wie UDT-Daten abgerufen und Parameter angegeben werden.  
  
 [Aktualisieren von UDT-Spalten mit DataAdapters](accessing-user-defined-types-updating-udt-columns-with-dataadapters.md)  
 Beschreibt, wie mit UDTs in `DataSets` gearbeitet wird und wie UDT-Daten mit `DataAdapters` aktualisiert werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Benutzerdefinierte CLR-Typen](clr-user-defined-types.md)  
  
  
