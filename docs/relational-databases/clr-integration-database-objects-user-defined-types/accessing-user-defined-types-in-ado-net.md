---
title: Zugreifen auf benutzerdefinierte Typen in ADO.net | Microsoft-Dokumentation
description: UDTs, die in .NET Framework CLR-Sprachen geschrieben wurden, ermöglichen es einer SQL Server Datenbank, Objekte und benutzerdefinierte Datenstrukturen zu speichern. In ADO.net macht ein Anbieter UDTs verfügbar.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
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
ms.openlocfilehash: cbbff72ab506238ec2134da8a91f91e3a315eb3f
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85727851"
---
# <a name="accessing-user-defined-types-in-adonet"></a>Zugreifen auf benutzerdefinierte Typen in ADO.NET
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Benutzerdefinierte Typen (User-Defined Types, UDTs) werden mit einer beliebigen Sprache geschrieben, die von der [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework Common Language Runtime (CLR) unterstützt wird, die überprüfbaren Code erzeugt. Dazu gehören [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# und [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic. UDTs ermöglichen das Speichern von Objekten und benutzerdefinierten Datenstrukturen in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank. Die Daten werden als öffentliche Elemente einer .NET Framework-Klasse oder -Struktur verfügbar gemacht. Das Verhalten wird durch die Methoden der Klasse oder Struktur definiert. Ein UDT kann als Spaltendefinition einer Tabelle, als Variable in einem [!INCLUDE[tsql](../../includes/tsql-md.md)]-Batch oder als Argument einer [!INCLUDE[tsql](../../includes/tsql-md.md)]-Funktion oder gespeicherten Prozedur verwendet werden.  
  
 In ADO.NET stellt der **System. Data. SqlClient** -Anbieter UDTs auf folgende Weise bereit:  
  
-   Über den **System. Data. SqlClient. SqlDataReader** als Objekt.  
  
-   Über **SqlDataReader** als Rohdaten bytes.  
  
-   Als Parameter eines **System. Data. SqlClient. SqlParameter** -Objekts.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Abrufen von UDT-Daten](../../relational-databases/clr-integration-database-objects-user-defined-types/accessing-user-defined-types-retrieving-udt-data.md)  
 Beschreibt, wie UDT-Daten abgerufen und Parameter angegeben werden.  
  
 [Aktualisieren von UDT-Spalten mit DataAdapters](../../relational-databases/clr-integration-database-objects-user-defined-types/accessing-user-defined-types-updating-udt-columns-with-dataadapters.md)  
 Beschreibt das Arbeiten mit UDTs in **DataSets** und das Aktualisieren von UDT-Daten mithilfe von **DataAdapters**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Benutzerdefinierte CLR-Typen](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)  
  
  
